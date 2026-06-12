---
title: "Samba ~ Network Error Message!"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-06-06
Hi.
I used to be able to share files between my desktop and laptop computers. However now I go to Network and get this message [attached].
What must I do to remedy this?

---

### Post by dandnsmith on 2009-06-06
Content of the message suggests you look on the server in the samba logs (if you've said you want them) for more info - it could give a clue.
look in the /var/log (or wherever you selected in samba.conf) for directories for smbd and nmbd holding relevant messages.

Think about what you changed since it worked, and try to work out what it might be from that?

---

### Post by Rytron on 2009-06-07
> **dandnsmith said:**
> Content of the message suggests you look on the server in the samba logs (if you've said you want them) for more info - it could give a clue.
look in the /var/log (or wherever you selected in samba.conf) for directories for smbd and nmbd holding relevant messages.

Think about what you changed since it worked, and try to work out what it might be from that?

Hi.
I don't have a server. I just right clicked on the folders I wanted to copy from my desktop to laptop like so [attached picture].

---

### Post by Iowan on 2009-06-07
Technically, the desktop would be the server... 
[Here]("http://ubuntuforums.org/showthread.php?t=1082148") is a similar thread.  perhaps some suggestions offered there might help.

---

### Post by Rytron on 2009-06-07
> **Iowan said:**
> Technically, the desktop would be the server... 
[Here]("http://ubuntuforums.org/showthread.php?t=1082148") is a similar thread.  perhaps some suggestions offered there might help.

Good point. I forgot to mention. Both my computers can ping each other. I will check your thread link. Thanks.

---

### Post by Rytron on 2009-06-10
Hi. I tried disabling the ufw on both desktop and laptop. Low and behold Samba worked. I want to have the ufw enabled but how do I allow samba through?

---

### Post by doas777 on 2009-06-10
> **Rytron said:**
> Hi. I tried disabling the ufw on both desktop and laptop. Low and behold Samba worked. I want to have the ufw enabled but how do I allow samba through?

do you have gufw installed? I think they have a preset rule you can apply to allow samba traffic.
regardless the ports involved are 135, 137-139, and 445

---

### Post by Lety on 2009-06-19
> **Rytron said:**
> Hi. I tried disabling the ufw on both desktop and laptop. Low and behold Samba worked. I want to have the ufw enabled but how do I allow samba through?
There is an easier way:
```
sudo ufw allow Samba
```
Worked for me with Gufw 9.04.2 in Jaunty (a new rule for Samba appeared automatically in Gufw).

---

### Post by Rytron on 2009-06-20
> **Lety said:**
> There is an easier way:
```
sudo ufw allow Samba
```
Worked for me with Gufw 9.04.2 in Jaunty (a new rule for Samba appeared automatically in Gufw).

Thank you Lety.
:popcorn:

---

### Post by dmizer on 2009-06-20
> **Lety said:**
> There is an easier way:
```
sudo ufw allow Samba
```
Worked for me with Gufw 9.04.2 in Jaunty (a new rule for Samba appeared automatically in Gufw).

Thank you for that. I've added it to my samba browsing tutorial here: [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

