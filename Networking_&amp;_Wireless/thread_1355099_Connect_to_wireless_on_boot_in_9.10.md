---
title: "Connect to wireless on boot in 9.10"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Kdar on 2009-12-14
Is it possible to make Ubuntu connect to wireless on boot?

I am using Ubuntu 9.10

---

### Post by diablo75 on 2009-12-15
Yes....  I'm going to assume you're asking this question because by default you're usually asked to enter a password to unlock the encrypted keyring storage that holds the passwords for a few different features of your system; one of which being the WLAN passwords needed to authenticate with a wireless network.  By default, if you don't have you system setup to auto-login, you have to login as yourself and in doing so you're keyring is automatically unlocked for you.  But if you have it setup to auto-login you're asked to enter the keyring password for security reasons.

It is possible to reset the keyring and store passwords into it without a locking password to encrypt the storage of said passwords.  But doing so will result in the passwords being stored on the system in an unencrypted form.  What this means is if someone were savvy enough came along and just turned your computer on, they'd have access to your account and a file that would be storing your passwords in their raw, unencrypted form and they could easily use this information to break into other things you wouldn't want them to, like your SMTP/POP3/IMAP email for example.  If you're computer isn't used by anybody else or you know nobody will have physical access to it, you should be fine.  But the degree of risk increases with any possibility that someone could gain access to it, even if that access is gained by remote (such as an SSH or VNC connection, so if you set services like this up make sure the passwords required for granting access are strong).

I've written a guide for removing the keyring that you can use to clear it and start from scratch and then store the passwords unencrypted so that you can have your system auto-login and then auto connect to your WLAN without asking for a password from anybody.  It was intended for Ubuntu 9.04 so it might not work quite the same for 9.10 (I haven't upgraded to 9.10 yet so I can't test it).  But you might take a look at the guide and give it a shot:

[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

