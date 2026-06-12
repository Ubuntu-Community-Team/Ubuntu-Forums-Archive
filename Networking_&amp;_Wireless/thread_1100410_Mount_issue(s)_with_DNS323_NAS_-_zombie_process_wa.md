---
title: "Mount issue(s) with DNS323 NAS - zombie process wakes up"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by WildSioux on 2009-03-19
Hello,

First post here...I am using LinuxMint 6 KDE CE RC1 on my P4 2.4 Ghz, 1gig ram, Nvidia 8400GS with 180.29 installed.  So far I am loving it and has been the most stable distros out of many.  I started out trying openSuse in December 2008.  Since then I have jumped around from linuxmint, mandriva, fedora, kubuntu, ubuntu, and sabayon.  All of these had their own problems which led me to move on to the next one.  And since I like KDE over gnome or any other window manager I waited until Mint 6 KDE CE RC1 came out.  I am glad I did since it is the only one that has worked for what I need.  Yes, the RC1 is the most stable I have tried.

[Problem] Ok now to the issue, as you know...Mint 6 is based off Ubuntu 8.10.  I have posted my problem at the Mint forum but haven't had much luck.
[http://forums.linuxmint.com/viewtopic.php?f=150&t=22863]("http://forums.linuxmint.com/viewtopic.php?f=150&t=22863")

I have a Dlink DNS323 NAS that I have managed to be able to mount via a fstab line.  I am able to open files and save (open office).  I finally got around the problem of not being able to save.  And here is my fstab for the DNS323:
```
//IP_Address/User\040&\040Our\040Files /home/user/mnt/DEVICE/USER\040&\040Our\040Files cifs rw,nounix,nobrl,_netdev 0 0
```

I will keep it short here since you can see it in that thread I posted above.  But, with the above fstab on other distros it worked fine.  However, in Mint (ubuntu)...it will auto mount at boot.  But something is waking up the NAS without me even accessing it (navigating to a folder on it, or opening a file).  I have found that when it wakes up, it is either by opening a file in Gimp, OO, a file saved on the desktop, or doing nothing at all.

I have since added "user,noauto" to the fstab because I am tired of it waking up.  I have it set to sleep after 30 minutes of inactivity.  But then it will wake up again a few minutes later.

There is some process that is doing this in Ubuntu/Mint.  Like I said, in the other distros.  I could just boot my computer and go about my business without it waking up...until I actually opened a file or navigate folders in the mounted directory.  

Does anyone know what this process is please???

Also, with "noauto" I am unable to sudo mount -a  I get the password prompt and then nothing.  It won't even show that it is mounted with "mount"

I really do appreciate any help.  And Thank you to the devs of Ubuntu.  I am using it in some way or another through Mint.

---

### Post by WildSioux on 2009-03-19
Page 3 nudge...this forum moves quick.

---

### Post by WildSioux on 2009-03-20
Really hoping someone sees this and knows what the heck is going on.

---

### Post by WildSioux on 2009-03-20
FYI...

I just checked my system logs and there is something funky going on with modprobe and ipv6
```
2009-03-20 11:49:02	MT-mint	modprobe	WARNING: Not loading blacklisted module ipv6 
2009-03-20 11:49:03	MT-mint	modprobe	WARNING: Not loading blacklisted module ipv6 

```


It does this every 2 minutes or so. And this is the same time when it woke up the NAS without me accessing it.

---

### Post by capscrew on 2009-03-20
Maybe [[COLOR="Blue"]**this site's**[/COLOR]]("http://forum.dsmg600.info/") forum can help.

---

