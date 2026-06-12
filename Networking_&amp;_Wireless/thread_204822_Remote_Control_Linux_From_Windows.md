---
title: "Remote Control Linux From Windows"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by masterjonny on 2006-06-27
Is it possible for a Windows box to remote control a Linux box remotley?

I have an old 450 MHz PC that I dont use for anything more than downloading and as a file server, and up until a while ago I was running Windows on it and using RAdmin to remote control it. I've just switched it over too Ubuntu and I'm wondering if theres a Linux equivilant too RAdmin, so I can remote control my Linux box from my Windows box?

(Speedy replies appreciated, bulding a new PC tomoro and it will lose its moniter :) )

---

### Post by Maggot on 2006-06-27
TightVNC works. Not sure if the remote desktop that comes with linux works in conjuction with windows.

---

### Post by masterjonny on 2006-06-27
After a quick google I found it so i'll try that now, thanks very much.

---

### Post by masterjonny on 2006-06-27
Ok I hate to ask the retard question, but how do you set this up? I got the RPM but it said it couldnt be opened because it was an unsupported file type, and Im not overly sure what to do with the source...

Any directions?

---

### Post by nzruss on 2006-06-27
I used Ultra VNC. [http://sourceforge.net/project/showfiles.php?group_id=63887](http://sourceforge.net/project/showfiles.php?group_id=63887)

You might want to enable remote desktop under the system menu somewhere. And uncheck the 'require permission' or whatever on your ubuntu machine, and request a password (not system or root tho'). 

If you just want to loginto the command line, I use PuTTY
[http://www.putty.nl/download.html](http://www.putty.nl/download.html)

---

### Post by masterjonny on 2006-06-27
Thanks so much guys, works a charm :)

/love

---

### Post by peanutplanters on 2006-06-27
i have ultravnc viewer on my XP machine, what do i type to remote to my linux machine? theyre both on the same network:-k

---

