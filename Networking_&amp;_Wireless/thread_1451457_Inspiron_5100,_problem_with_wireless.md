---
title: "Inspiron 5100, problem with wireless"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by mlthmp on 2010-04-10
Hello everyone! I have installed Ubuntu 9.10 on an older Inspiron 5100 laptop. I have used the 9.10 alt install CD (command line installation) and then installed the lubuntu-dekstop. Needless to say this thing *FLIES* with LXDE running! 

Everything is working great, expect for the wireless. Here is what I have done so far.

In BIOS, I checked to ensure that wireless was enabled. Had 3 options. Application / Application with FN+F2 hotkey / and OFF. I have chosen Application / FN+F2 as I read somewhere that was the way to go. However, I cannot seem to get Ubuntu to recognize this system has wireless. I know the wireless works because I have moved from XP just yesterday and it worked just fine. So I am thinking I am missing a step somewhere?

I have ran the "lspci -nn" command, and located the two following lines which I think are the ones I need,

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

The ethernet works well (am using the system now to post) but I am stuck as to what I need to do to get the wireless working. Any suggestions?

Thanks!
Mike,

---

### Post by tgm4883 on 2010-04-10
> **mlthmp said:**
> Hello everyone! I have installed Ubuntu 9.10 on an older Inspiron 5100 laptop. I have used the 9.10 alt install CD (command line installation) and then installed the lubuntu-dekstop. Needless to say this thing *FLIES* with LXDE running! 

Everything is working great, expect for the wireless. Here is what I have done so far.

In BIOS, I checked to ensure that wireless was enabled. Had 3 options. Application / Application with FN+F2 hotkey / and OFF. I have chosen Application / FN+F2 as I read somewhere that was the way to go. However, I cannot seem to get Ubuntu to recognize this system has wireless. I know the wireless works because I have moved from XP just yesterday and it worked just fine. So I am thinking I am missing a step somewhere?

I have ran the "lspci -nn" command, and located the two following lines which I think are the ones I need,

02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

The ethernet works well (am using the system now to post) but I am stuck as to what I need to do to get the wireless working. Any suggestions?

Thanks!
Mike,

Do you have /usr/bin/jockey-gtk ? That is the hardware drivers utility in Ubuntu which prompts you to install the proprietary drivers for your card. You will need a network connection for it to work though.

---

### Post by mlthmp on 2010-04-10
> **tgm4883 said:**
> Do you have /usr/bin/jockey-gtk ? That is the hardware drivers utility in Ubuntu which prompts you to install the proprietary drivers for your card. You will need a network connection for it to work though.

I do now! Thank you very much! 

Installed, opened it up and it had the wireless card listed right there. Took about a minute to download and install! I appreciate it!

---

### Post by tgm4883 on 2010-04-10
Your welcome. Please mark this thread as resolved

---

### Post by mlthmp on 2010-04-10
> **tgm4883 said:**
> Your welcome. Please mark this thread as resolved


Oppps! Sorry thought I did! Marked.

Thanks again!
Mike,

---

### Post by motnoslo on 2011-01-10
I too am having an issue with the wireless on an Inspiron 5100. After the initial install of 11.04, the network manager applet said that the wireless device was not ready and had missing firmware. I ran lspci -nn  and saw the Broadcom wireless, plus this machine previously was running XP with wireless. I then ran /usr/bin/jockey-gtk.  It found the Broadcom wireless drivers and activated them, but the network manager app still said the device was not ready.

I then ran update manager and rebooted. When I logged backed in the network manager still saw the wireless as not ready with missing firmware. I ran /usr/bin/jockey-gtk again, it found the Broadcom wireless drivers again, but when I tried to activate, I get this message in a pop-up window:
SystemError: installArchives () failed

What am I missing to get the wireless to work?

---

### Post by PatchesTheCaveman on 2011-01-11
Did you try and install the b43 driver firmware or the STA driver?

Run these commands on a terminal:
```
lsmod
ls /lib/firmware/b43/
dpkg-query -s bcmwl-kernel-source
```
Copy and paste the output to a reply to this thread.

---

