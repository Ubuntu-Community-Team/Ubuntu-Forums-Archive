---
title: "MythTV - only records static"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by Ampsonic on 2007-04-14
Hello,

I've got a mythtv box that was working great for a while. A power outage killed it pretty good, but I reinstalled ubuntu and got myth working pretty easily. After it was set up, I recorded one show just fine. I walked away after setting up my recording prefrences. When I next came back to the box, everything it recorded was just static. The cable is fine, I tested it with a tv. 

Any ideas?


Nick

---

### Post by tgm4883 on 2007-04-14
What kind of tv card? what version ubuntu?  lspci output?

---

### Post by Ampsonic on 2007-04-14
Sorry, I'm a bit frazzled today. I usually know to provide more info than I did.

Running 6.10

Haupagge PVR-150

Sorry, I don't know what lspci output is. 


Thanks!
Nick

---

### Post by newlinux on 2007-04-14
> **Ampsonic said:**
> Sorry, I'm a bit frazzled today. I usually know to provide more info than I did.

Running 6.10

Haupagge PVR-150

Sorry, I don't know what lspci output is. 


Thanks!
Nick
He/She  is asking you to type lspci at a terminal and then paste the output. Can you watch live tv on it? Have you checked your mythbackend logs?

---

### Post by tgm4883 on 2007-04-15
Can you watch tv through mythtv?  Maybe your channel lineup is screwed up

---

### Post by Ampsonic on 2007-04-15
Nope, even in live tv mode it's all static. I will run lspci when I get home. Thanks!

---

### Post by Ampsonic on 2007-04-16
Here is what I get when I run lspci:
```

nick@mythbox:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)
02:08.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

All help is greatly appreciated!

---

### Post by Ampsonic on 2007-04-17
Any ideas?

I really don't want to have to format this guy, but that's the next step if I can't figure this out. 

Thanks!
Nick

---

### Post by newlinux on 2007-04-17
Have you checked the logs when you get static? They may lead to some clues. Run mythfrontend from a terminal and see what it outputs and take a look at your backend logs.

---

### Post by superm1 on 2007-04-17
Only getting static is *never* a good sign.   Lets hope your card didn't take a turn for the worst with that power outage.  Checkout dmesg for any messages about errors with the card and such.

So as to rule out other troubles, are all of your cable line coaxial cables okay?  Perhaps you can hook up a small tv in place of the computer to make sure that you can tune channels there.  

Next, try to do a capture like this:
```
cat /dev/video0 > /tmp/test.mpg
```

Control-C will quit the capture

You can play that file back from mplayer:
```
mplayer /tmp/test.mpg
```

To try to tune other channels, just use ivtv-tune
```
ivtv-tune -c NUMBER
```

where NUMBER is that channel number you want to tune.

---

