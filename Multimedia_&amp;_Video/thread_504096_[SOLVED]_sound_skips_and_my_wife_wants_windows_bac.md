---
title: "[SOLVED] sound skips and my wife wants windows back!!"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by rickycodie on 2007-07-18
so my wife will be watching videos on the internet and about twenty min. into it the sound skips like a scratched cd!

using firefox, this happens on a toshiba satillite l25-s1216 and pretty much everything on it is ati, so not really surprised to have problems. here is the output of lspci:
```
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

so any ideas?

---

### Post by rickycodie on 2007-07-18
hey i figured it out!! for every body that needs it  here's the solution,

Installing non-standard modules can be a little tricky. Ubuntu provides the module-assistant helper application:

open up the terminal (applications>accesories>terminal) and type

sudo apt-get install module-assistant

Next, run the module-assistant app:

sudo module-assistant

then a ugly 8-bit menu will come up,

First, select the UPDATE menu item to make sure the module-assistant is up to date with the latest information.

Next, select the PREPARE menu item, which will install the packages required to compile kernel modules.

Hit the SELECT menu item, select the realtime-lsm module from the list, and hit OK. From the next menu, select GET, BUILD, and INSTALL in that order.

Ubuntu should now have the realtime-lsm module installed. At this point, if you try to load the module into the kernel, you will get an error (I am not yet sure why). Restart your machine, and everything will be ok.

To configure the realtime-lsm to launch automatically at startup, edit the /etc/ default/realtime file. Ensure that ENABLE=yes and that the gid parameter is the GID of the group you wish to give real-time privileges to. The default of 29 (audio) works well.

---

### Post by LDRoamer on 2007-07-19
For those of us who are still newbies maybe you can offer a bit more explanation as to what you did and why it worked. I have an issue with my sound. I am running on old Comapq laptop (366 PII - 320mbs ram). I had to install a USB sound card on this machine as Feisty broke my onboard sound (works fine in windows).  My problem is that when playing MP3's the sound cuts in and out at random intervals (didn't do this when I had edgy installed and was using the on board chip).  Just wondering if this fix you describe would help me. But I am not really sure what you did so if you could give me a bit more direction that would be great.

---

### Post by rickycodie on 2007-07-22
i edited the instructions and made them clearer, sorry for being so unclear. thanks to ldroamer for pointing this out.

---

### Post by LDRoamer on 2007-07-26
Thanks very much. I am going to give this a try.

---

### Post by ColinIam on 2007-07-30
Worked for me... thank you! :)

---

### Post by proalan on 2007-08-05
i have the same problems where the sound skips like an old  record unless played in xmms. The problem is intermittent but so far so good.

I was wondering how you came across this solution.

changes to the kernel usually require restarts for changes to take effect.

---

### Post by rickycodie on 2007-08-21
sorry about the late reply i don't remember how i found this. i was at the end of my rope trying to find a solution and i found this, i think on like page 15 of my google search. i knew i would never find it again so i posted it here for others to use too.

---

### Post by WinterWeaver on 2007-08-21
Thanks for Sharing dude!! Gonna give this a go when I get home ^_^

---

### Post by ady-e on 2007-11-21
Wow! this really does work! I had the same issue on two different systems both running Gutsy Gibbon so I knew it wasn't a hardware issue. The above solution worked on my Vaio, now to try it on the desktop.

Thanks very much! :D

---

### Post by Wiebelhaus on 2007-11-21
Thanks mate for writing that up , that should be categorized into some kind of official support doc location.

---

### Post by rickycodie on 2007-11-21
hey i'm glad so many people are finding it useful.

---

