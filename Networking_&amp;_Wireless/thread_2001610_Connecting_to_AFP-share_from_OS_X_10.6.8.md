---
title: "Connecting to AFP-share from OS X 10.6.8"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by jan-banan on 2012-06-11
I have a ubuntu 12.04 file server that runs afp to serve files to my OS X 10.6.8. When i boot ubuntu the icon for the share shows up in finder but i cant connect to it. Although i can connect to it if i restart netatalk manually. I have tried different settings in /etc/netatalk/afpd.conf but to availal. These are my current settings:
[http://pastebin.com/GepHb2k2](http://pastebin.com/GepHb2k2)
And when i check out the error messages in OS X i get this when i try to connect to the afp-share:
SharePointBrowser::handleOpenCallBack returned 64
I googled it and there were some suggestions to fix the problem, i have tried the fix from this thread: [https://discussions.apple.com/thread/2034505?start=0&tstart=0](https://discussions.apple.com/thread/2034505?start=0&tstart=0) namely: sudo rm /System/Library/Filesystems/afpfs.fs 
sudo ln -s /System/Library/Filesystems/AppleShare/afpfs.kext /System/Library/Filesystems/afpfs.fs
And i have also tried to connect to it manually using CMD + K and afp://192.168.1.XXX but it didnt work.

I also have a problem with mt-daapd and they might possibly be related since they both started acting up at the same time, here is the thread about mt-daapd: [http://ubuntuforums.org/showthread.php?p=12017023#post12017023](http://ubuntuforums.org/showthread.php?p=12017023#post12017023)

---

### Post by jan-banan on 2012-06-12
I managed to fix this on my own, i deleted mt-daapd from /etc/init.d/ and added it to /etc/rc.local, this also fixed the problem with netatalk. I dont know exactly why they had a conflict but either way it is resolved.

---

