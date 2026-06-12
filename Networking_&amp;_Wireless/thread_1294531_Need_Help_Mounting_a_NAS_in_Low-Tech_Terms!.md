---
title: "Need Help Mounting a NAS in Low-Tech Terms!"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by Lauxmonster on 2009-10-18
Sorry for being the absolute newbie here. I love Ubuntu, but this is really the only issue I have with it.

I have a Buffalo Drive Station FlexNet 640GB (HD-CE640LU2) that works fine as a NAS under Windows, but I haven't a clue how to get it working on Ubuntu. If I go to "Places" and type in the Samba address, I can view all of the files and view and write to the drive. But, if I shut down he computer, it will not be mounted the next time.

So, does anyone have a simple guide to mounting a Network Drive in Ubuntu in really low tech terms? Thanks.

---

### Post by jward3010 on 2009-10-18
There's a way to do this using your fstab file located in /etc/fstab. How exactly, I shall find out for you. It's a simple single line you pop in tat will be mounted at every boot. There's even a chance to do this with a command and Startup Applications.

---

### Post by jward3010 on 2009-10-18
I would regard these as the fundamental failings of Ubuntu, they are simple to acheive yet not in place yet. Lots to do, lots to come in. On it progresses etc. etc.

---

### Post by Lauxmonster on 2009-10-18
Ah thanks so much! I am away from my Ubuntu PC at the moment, but I will see if I can do anything when I can get to it. 

I saw this article, could this work?- [http://r3dux.org/?p=726]("http://r3dux.org/?p=726")
If you can continue to help me out, it would be greatly appreciated.

---

### Post by Lauxmonster on 2009-10-18
And you are definitely right. Making a GUI application for mounting a NAS theoretically should not be a difficult task...but it hasn't been done yet. It's the small things, the small things can really turn the tides to the better or the worst.

Hopefully in 10.04 we will see something...possibly. I hope. ;)

---

### Post by dmizer on 2009-10-18
> **Lauxmonster said:**
> And you are definitely right. Making a GUI application for mounting a NAS theoretically should not be a difficult task...but it hasn't been done yet. It's the small things, the small things can really turn the tides to the better or the worst.

Hopefully in 10.04 we will see something...possibly. I hope. ;)

There already IS a GUI app for permanently mounting shares. If "places > connect to server" isn't working for you, then perhaps you have some small configuration problems. Try looking at the 6th link in my sig.

If that doesn't help you, then try looking here: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

Mounting a NAS is more complicated than you might think. First of all, it's using a protocol built for Windows. Second of all, Ubuntu comes with the latest Samba daemons, and they are updated regularly. Do you know how old the version of Samba is on your NAS device?

While I do recognize that Ubuntu has problems with samba, it's important to realize that it DOES work as well or better than Windows in many (if not most) situations.

---

### Post by Lauxmonster on 2009-10-18
Yes! After months of putting this off, I finally got it permanently mounted. Thanks to all who contributed. You helped me have a better understanding of what is going on. However, I used this guide:

[http://www.marcus-furius.com/?p=59]("http://www.marcus-furius.com/?p=59")

---

