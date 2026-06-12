---
title: "After going to 12.04 can't connect to Win share"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by jmirick on 2012-05-01
Have for a long time accessed a Win share on a local server from my Ubuntu desktop.  Yesterday upgraded to 12.04 and the Win server is rejecting my credentials -- any credentials.  Other Win workstations can map the drives with no problem, just this one can't.  Samba log says nothing.  Error message is "please verify your credentials" or the like.  Except for 12.04 nothing has changed. So far no luck in loclizing the problem.

I'm also posting this in the installation and upgrade forum.

Thanks in advance for any ideas.

---

### Post by JRV on 2012-05-01
Try to access it from within a terminal with the following command:
```
nautilus smb://WINDOWS_HOSTNAME/WINDOWS_SHARENAME
```
Hopefully the error messages will tell you what is wrong.  
If you don't understand the error messages post them here.

---

### Post by jmirick on 2012-05-01
AHA -- for some reason the domain name has to be in caps, not sure why but sounds like a version change issue to me.  Well, it worked, your suggestion to start from the terminal highlighted it, thanks ever so much!

Jim

---

### Post by jhboricua on 2012-05-02
This is not working for me, I've tried uppercase server name, uppercase Domain but I simply cannot connect to a AD network share after installing 12.04

Trying to connect via terminal and using the nautilus smb: command is not producing any output as to what the problem is. It just keeps asking for the f#^*^*@ credentials. I'm incredibly frustrated right now. How can something like this not be caught before release?

---

### Post by atomicslave on 2012-05-02
Its not working for me either, on domain shares and even my home smb share of my ubuntu 11.10 box to.

---

### Post by blackangelpr on 2012-05-02
> **JRV said:**
> Try to access it from within a terminal with the following command:
```
nautilus smb://WINDOWS_HOSTNAME/WINDOWS_SHARENAME
```Hopefully the error messages will tell you what is wrong.  
If you don't understand the error messages post them here.

Thanks it worked i could see my folder then how i can make it auto mount? same problem i had but even with my sd card reader it only mount the usb :( but thanks for this solution you rock ! :guitar:

---

### Post by PhilMize on 2012-05-15
Using caps for my domain name worked for me.:P

---

