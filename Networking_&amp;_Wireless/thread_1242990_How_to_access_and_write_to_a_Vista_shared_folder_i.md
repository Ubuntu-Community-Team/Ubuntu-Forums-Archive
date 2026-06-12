---
title: "How to access and write to a Vista shared folder in Ubuntu?"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2009-08-17
Hey

I wanted to transfer files I have on a Ubuntu system to a folder I have shared on my Vista PC. How do I do it?

---

### Post by dmizer on 2009-08-18
Are the Ubuntu and Vista systems on differnet computers, or are you talking about a dual boot where both Ubuntu and Vista are on the same computer?

If they are different computers, then please see the 6th link in my sig. After which, you should be able to view the folder under Places > connect to server

---

### Post by Cuba71 on 2009-08-18
I have two computers running Ubuntu 9.04 on one and Windows XP on the other one with network name HOMENET.
I can access shared folders on the XP machine by going to Places > Network and the Windows Networks shows up.
I can also access the Ubuntu shared folders from the XP machine.

---

### Post by riahc3 on 2009-08-19
> **dmizer said:**
> Are the Ubuntu and Vista systems on differnet computers, or are you talking about a dual boot where both Ubuntu and Vista are on the same computer?

If they are different computers, then please see the 6th link in my sig. After which, you should be able to view the folder under Places > connect to server

Sorry for no details :)

I have PC A with Vista installed and a folder named "share" on my PC A (that has Vista installed) and I want to be able to write to that folder (share) thru PC B....

I have another PC B with Ubuntu installed. I want to be able to browse/copy/cut/paste/edit/etc/ thru the "share" folder that is on PC A which is running Wista.

---

### Post by dmizer on 2009-08-19
Yup, just follow the 6th link in my sig and you should be set :)

---

### Post by riahc3 on 2009-08-19
> **dmizer said:**
> Yup, just follow the 6th link in my sig and you should be set :)


OK I did that and in Network, when I hit the computer that I want to access, a dialog comes up asking for a username, domain, and password.


In Windows, the actual login name is PCNAME/username but here by default it just puts my Ubuntu's user name. My questions:

Do I put the username or the domain/username format (and how is it exactly)?
Do caps count in username (ex: bob is not the same as Bob)?

---

### Post by dmizer on 2009-08-19
Is the Vista share set for password protection? If so, you'll have to add your Ubuntu user to your Vista machine and make sure it's in the allowed users list in the share definition.

If not, you have a problem with your Ubuntu configuration, or perhaps a firewall is interfering.

---

### Post by riahc3 on 2009-08-20
Followed the 6th link and it didnt work. Then I followed the 2nd and it worked....

---

### Post by dmizer on 2009-08-20
> **riahc3 said:**
> Followed the 6th link and it didnt work. Then I followed the 2nd and it worked....

Heh, I usually leave that as a last resort. Most people are pretty reluctant to use it.

Glad you're working though!

---

