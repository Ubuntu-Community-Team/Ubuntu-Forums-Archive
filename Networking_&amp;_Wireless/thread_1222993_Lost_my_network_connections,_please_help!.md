---
title: "Lost my network connections, please help!"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by darrude on 2009-07-25
Hi all,

I'm new to linux, but having just purchased an Acer Aspire Revo, and decided to install ubuntu on it.  I have managed to set everything up just how I want with all necessary programs and everything was working fine.  I then rebooted to let my 4 year old log on and now I can't get a web connection.

I have been searching the web (on my xp laptop) for the last 2 hours but havn't got anywhere.

does anybody have any ideas.

the wireless controller is a Atheros AR242x.  

Thanks in advance,

Regards

Darren

---

### Post by superprash2003 on 2009-07-26
are you able to view wireless network?
post output of
1)sudo iwlist scanning
2)iwconfig
3)ifconfig

---

### Post by darrude on 2009-07-27
> **superprash2003 said:**
> are you able to view wireless network?
post output of
1)sudo iwlist scanning
2)iwconfig
3)ifconfig
 
 
Hi
 
thanks for your resonse.  I managed to to change the driver to MADWIFI and then it refused to boot up so ended up re-installing everything :(  
 
I think it was when it did an update so plan on never doing an update now, is this safe?
 
thanks,
 
darren

---

### Post by hyperAura on 2009-07-27
hi darren.. well not updating in my opinion is not a good decision since many bugs are being fixed after an update.. although something can go bad after an update u can report it and other people will help you, wishfully having the new problem fixed.. :)

---

### Post by ZhuaSD on 2009-07-28
When I first started with the ubuntu, I did a bunch of re-installs.  Fixes that didn't work just became re-installs  ;-))

Like I lost all my panels at one point, the entire desktop was blank!  That was a re-install for sure.

It was just easier, as obviously I had prepared my data for a new install anyway.  It works especially if you format out your drives properly.

After about a month I settled in to an install that became permanent, until I just upgraded last week to 9.04, a year or so later.

Update your system!  If the bug happens regularly then you can figure it out, if not, then the re-install can be a learning experience!:P

---

