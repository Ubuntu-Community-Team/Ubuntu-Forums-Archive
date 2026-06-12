---
title: "Enter password for default keyring to unlock?"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by ciaopaulo on 2009-08-19
Hi,

I keep getting this request; "Enter password for default keyring to unlock" when connecting to my wireless network. I suspect this is what is preventing the autoconnect.

Is there a solution to stop this popping up?

I tried to follow this:

> **davidyu said:**
> 
To get rid of the keyring prompt after automatic login in hardy 8.04 you can:

System > Preferences > Encryption and Keyrings
Under Password Keyrings click on "login Automatically unlocked when user logs in."
Click "Change Unlock Password"
Enter your old password, but leave the new password fields blank.
Ok , confirm and you should be set.

Related bug report (kinda) : [https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993](https://bugs.launchpad.net/ubuntu/+s...ng/+bug/108993)

But there is no option titled "Password Keyrings" or anything with the option "login Automatically unlocked when user logs in."

All I see under the "Encryption and Keyrings" GUI is a tab called "Encryption" with only one item in the drop down; "none, prompt for key", then another tab called PGP Passphrases.

Maybe the advice above applies to a previous version?

Anyone help me out?

---

### Post by duanedesign on 2009-08-21
To get passwordless networkmanager login working with 9.04.

1. Applications-> Accessories-> Passwords and Encryption Keys
2. Select Passwords tab
3. Right click on Passwords:login, choose Change Password
4. Enter current password and LEAVE THE NEW AND CONFIRM FIELDS BLANK


i hope this helps.

There is a slightly more destructive method here if you do not have any luck with the above steps.
[http://davestechsupport.com/blog/200...sword-keyring/](http://davestechsupport.com/blog/200...sword-keyring/)

---

### Post by ciaopaulo on 2009-08-28
Thanks duanedesign! That worked. I was confused between the "Passwords and Encryption Keys" under Applcaitions/Accessories and "Encryption and Keyrings" under System/Preferences.

Ta!

---

### Post by The ragman on 2009-08-29
I have the same problem - but I have neither of the solutions available to me. ubuntu 8.04. The applications menu does not have that option, neither does the System menu, any idea why they would not be visible to me?

---

### Post by aharown07 on 2009-08-29
Pop up says this results in unsafe password storage... what would the consequences of that be? As a newbie I'm not sure I want to do that.
What's weird is that my wireless network wasn't prompting me for a keyring password until I--on a whim--changed my "Passwords: login" password in Seahorse. Now it won't quit. Was I using "unsafe storage" before maybe?

---

### Post by ciaopaulo on 2009-09-02
You're right. I suspect that the password you set for the keyring is used to encode the other passwords.

If you set a null password for the keyring then other passwords will be visible.

It would be better if the keyring pass were somehow bound to the login password, so once I enter that password (at login) it unlocks all the encrypted keys on the keyring.

I don't know how the ubuntu security system works though. I'll need to google a bit more.

---

### Post by aharown07 on 2009-09-02
Actually, I think it *is* bound to the logon pwd somehow. When I changed it back to my logon pwd, I stopped being prompted. So I'm guessing that's the reason why.

---

