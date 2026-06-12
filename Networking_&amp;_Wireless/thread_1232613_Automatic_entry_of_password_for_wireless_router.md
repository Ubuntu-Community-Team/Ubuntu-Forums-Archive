---
title: "Automatic entry of password for wireless router"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by rlhoman on 2009-08-05
I have my Ubuntu (under Vista) system set up to logon without asking my name and password.  However when it tries to connect to my wireless router, I get the following message:

Enter password for default keyring to unlock

I must then enter the WEP  for my router.  Is there a way to automate this process so I don't have to key it in each time?

---

### Post by Hobgoblin on 2009-08-05
> **rlhoman said:**
> 
I must then enter the WEP  for my router. 

It should not be asking for the WEP key for the router, the password it is asking for is your default keyring password, the way to stop it asking for that is to log in manually on startup, and have the same password for your default keyring as for your user password.

---

### Post by slakkie on 2009-08-05
Configure it via /etc/network/interfaces, see one of the links in my signature.

---

### Post by rlhoman on 2009-08-06
> **Hobgoblin said:**
> It should not be asking for the WEP key for the router, the password it is asking for is your default keyring password, the way to stop it asking for that is to log in manually on startup, and have the same password for your default keyring as for your user password.
You are right.  It is my user password I enter.

---

