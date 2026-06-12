---
title: "Password for root on localhost?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by pmcotter on 2009-01-25
I am trying to add an XP network printer to a wireless Ubuntu 8.1 system.  I located the printer & installed the recommended driver but the Ubuntu system then requests "Password for root on localhost?".

Is it asking for a password on the XP machine?  On the Ubuntu?  Either way I am still not sure what the password is if it isn't the Ubuntu user password I use on login.

Thnx 4 any help!

---

### Post by puppywhacker on 2009-01-26
root is for linux, administrator is for windows. So it's asking for the Ubuntu, however the root password is not set and you are strongly recommended to use "sudo" when you need to execute something with super hero powers.

I don't know how or where it asks for a password (or why) ...

---

### Post by Coreigh on 2009-01-26
What is actually being asked for is a username and password that is valid for the Windows network to allow access to the printer. It is only suggesting root because you are likely using the sudo or gksudo to execute commands. If there is a Windows user or administrator you could try that password but you would need to have that username in the login box and I hav often seen these where the username part is locked. You will probably have better luck logging in to the Windows box that the printer is installed and shared from, and then editing the security on the printer share to allow everyone access permission. If this is not a private network you would also have to allow everyone access, but only from the IP or IP range that your Ubuntu box is on.

---

### Post by pmcotter on 2009-01-26
Thanks, guys.  The problem is I am a bonehead.  I thought I had logged out of a user account and back into my "admin" account but I hadn't.  It was late.

When I logged in correctly, it didn't ask the question.  BTW, I did give it the admin password for my Ubuntu admin account but it wouldn't work. Nor would it work using the admin name and password together rather than "root" and the admin password.

As I said before, I appreciate your help.

---

### Post by foxy123 on 2011-10-16
I've got the same problem. I wonder why I can use my admin username and password to set up a printer on a standard (non-admin) account.

---

### Post by nothingspecial on 2011-10-16
Please start a new thread rather than bumping an old one to the top.

Closed.

---

