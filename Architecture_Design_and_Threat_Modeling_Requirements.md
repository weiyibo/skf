Authentication is the act of establishing, or confirming, someone (or something) as authentic and that claims made by a person or about a device are correct, resistant to impersonation, and prevent recovery or interception of passwords.

# 2.1.1  Verify that user set passwords are at least 12 characters in length. (C6)

对于密码要给与足够的复杂度
- 至少12位
- 不长于64位
- Unicode字符集中的每个特殊字符都应允许
- 不应该限制同类型字符的个数

# 2.1.10  Verify that there are no periodic credential rotation or password history requirements.

一些规定要求用户在一定周期内更新自己的密码，但是又不能选择和之前的密码类似的密码，这就使得用户不得不选择 weaker 的密码，或者把密码记录在纸上。这反而适得其反。

仅当应用程序强制使用密码强度时，才强制用户更新其密码，由于计算能力的提高，已经不足以抵御暴力攻击。


# 2.1.5  Verify users can change their password.

允许用户修改密码

# 2.1.6  Verify that password change functionality requires the user\s current and new password.
敏感信息的更新需要用户输入密码来完成更新

# 2.1.7  Verify that passwords submitted during account registration, login, and password change are checked against a set of breached passwords either locally (such as the top 1,000 or 10,000 most common passwords which match the system\s password policy) or using an external API. If using an API a zero knowledge proof or other mechanism should be used to ensure that the plain text password is not sent or used in verifying the breach status of the password. If the password is breached, the application must require the user to set a new non-breached password.

在用户注册的时候验证密码，如果使用了已经是泄露过的密码就要阻止注册。例如最常用的100个密码之类的

# 2.1.8  Verify that a password strength meter is provided to help users set a stronger password.

使用一些工具来现实当前密码的强弱

# 2.2.1  Verify that anti-automation controls are effective at mitigating breached credential testing, brute force, and account lockout attacks. Such controls include blocking the most common breached passwords, soft lockouts, rate limiting, CAPTCHA, ever increasing delays between attempts, IP address restrictions, or risk-based restrictions such as location, first login on a device, recent attempts to unlock the account, or similar. Verify that no more than 100 failed attempts per hour is possible on a single account.

例如使用 CAPTCHA 和 a TARPIT(ratelimiting) 来阻止攻击者进行密码猜想。限制尝试的次数

# 2.2.2  Verify that the use of weak authenticators (such as SMS and email) is limited to secondary verification and transaction approval and not as a replacement for more secure authentication methods. Verify that stronger methods are offered before weak methods, users are aware of the risks, or that proper measures are in place to limit the risks of account compromise.

使用 TOTP (Timebased OneTime Password algorithm) 来验证登录。

Example of a hard token mathimatical algorithm would be a yubikey
Example of a soft token TOTP would be google authenticator

# 2.2.3  Verify that secure notifications are sent to users after updates to authentication details, such as credential resets, email or address changes, logging in from unknown or risky locations. The use of push notifications - rather than SMS or email - is preferred, but in the absence of push notifications, SMS or email is acceptable as long as no sensitive information is disclosed in the notification.

在用户的一些敏感信息更新更新的时候，例如 credential resets, email or address changes, logging in from unknown or risky locations。 需要向用户发送提示的信息和email
