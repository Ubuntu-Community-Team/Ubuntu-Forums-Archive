---
title: "Surprise! Network is unreachable"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by tbriggs on 2011-01-24
Noob here, I have tried my best to follow the rules by googling and reading, tinkering and searching. I still can't get an internet connection with 10.10. I HAVE been connected, just long enough to download a tsunami of updates then right back to square one. 

I started with wubi and 10.04. I liked it so much I learned how to make partitions and installed 10.10. Since then I have loaded up ubuntu about 30 times and have had a working network on three occasiions. 

I made a disk for 10.04 with the intention of installing that instead. But I just get an eternal purple screen after the drive spins down. SO I'm stuck and I want to make it work.
My connection is wired.
I have changed cables.
I have bypassed the router.
I have yelled and woke up my wife and children.
I have rebooted
I have power cycled modems and routers.
And finally, I have rebooted and loaded windows so that I could get online and ask for help.
I know there are atleast several other people in the same boat. Would someone that has made it to the other side please enlighten me?
Thank you.

---

### Post by tbriggs on 2011-01-25
Is replacing network manager with wicd the fix for this somewhat common problem?

---

### Post by Iowan on 2011-01-25
Wish I had a brighter light to shine... I've been lucky (so far) getting Ubuntu to load on various systems. If it's a driver issue, then I'm done (but there are some real gurus hanging around...:) ). When you fire up the system, open a terminal (Applications>Accesories> Terminal) and enter:```
ifconfig -a
``` That should show if you have an interface configured. Another valuable command is ```
sudo lshw -C network
``` to get details about your interfaces. You can also redirect it to a file ( sudo lshw -C network > lshw.txt) which you can copy to removable media and paste here from an internet-accessible machine. 
 Hope I haven't forgotten something important...

---

### Post by rezaulkabir on 2011-01-25
Well, it is not a reply. I am also facing similar problem after update manager updates my 10.04 LTS, which resides within WIN XP. Due to which I have to _lock updates for grub-pc and grub-common _under instructions from ubuntu documentation.
The updating had been done through the Broadband Connection which I connected through **sudo pppoeconf** command.
After restart I am not getting network to my surprise. However, when I tried the boot option for recovery mode and selected failsafex mode, it gives me the connection properly.
Can anyone help to solve my problem?
Thanks in advance.

---

