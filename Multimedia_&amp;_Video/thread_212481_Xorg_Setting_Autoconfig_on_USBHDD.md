---
title: "Xorg Setting Autoconfig on USBHDD"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by Biteableniles on 2006-07-09
Hello there! I recently recieved a USB harddrive (20gigs) onto which I have successfully installed a copy of Ubuntu 6.06. I've found it works nearly flawlessly except for Xorg, which doesn't like having settings exchanged between computers. When I take the drive to a different computer, I have to reconfigure Xorg to get it to work. It isn't that bad, but I would like to have it autoconfigure the same way the Ubuntu Livecd does. I've searched forever to find the method it uses, but came to "discover1" and have hit a roadblock.

Is there anyway to enable xorg autoconfig on a normal Ubuntu install, or am I out of luck (short of writing my own configure script, which I would kinda need to learn how to do.)

Thanks!

---

### Post by Biteableniles on 2006-07-12
Ok, so I have successfully gotten the harddrive to boot flawlessly on 4 different computers (two of which didn't support USB booting, but that was fixed by way of boot cd), and everything works when I manually configure Xorg. I don't want to have to do this every time, though. Does anyone have any resources I can use to figure out how to automagically configure Xorg on boot? 

Oh, and another issue that I've found is that the fstab is persistant, so I have to manually mount harddrives. Another harmless annoyance, but I know theres a way to have auto-configured fstabs on boot, as well, as all the livecds do it. Is that going to be along the same lines?

---

### Post by rebelfallen on 2006-07-12
I am having this very same issue. It is MOST frustrating. I need an autoconfig hardware tool, and I am sort of tired of mounting all of the time.

---

