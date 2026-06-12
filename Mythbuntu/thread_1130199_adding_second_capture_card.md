---
title: "adding second capture card"
date: 2009-04-19
forum: Mythbuntu
---

### Post by oletechie on 2009-04-19
Hi all,
I am just another noobie in trouble.
I built my own box, it looks like this:
Foxconn motherboard
Pentium 4 running at 3000Mhz
2 gig of ram
VisionTek X1550 AGP video card
2 Hauppauge 1600 tuner cards
I have been playing with Mythbuntu for about three months now and have it working with one capture card. my problem starts when I try to add the second card. 
The DVB Device number only has '0' available. How do I get another DVB device made available?

---

### Post by nickrout on 2009-04-19
when you boot is the second card recognised?

try running ```
dmesg|grep -i dvb
``` and see what comes out. I had a similar problem on a friend's machine that was fixed by reseating the card :)

```
ls /dev/dvb* 
``` should tell you whether there is one or 2 adaptors detected by the operating system.

---

### Post by oletechie on 2009-04-19
Thanks for helping, Here is what I get. I have switched the cards around and tried different pci slots, first putting one in then the other but nothing seems to help.  When I run the commands, both cards are in the slots. It just seems like I am missing something.

mark@ubuntu:~$ dmesg | grep -i dvb
[   23.988714] DVB: registering new adapter (cx18)
[   24.546628] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   24.547085] cx18-0: DVB Frontend registered
mark@ubuntu:~$ ls /dev/dvb*
adapter0
mark@ubuntu:~$

---

### Post by nickrout on 2009-04-19
well it certainly looks like only one card is being recognised!

[LIST]
[*]what is the second card?
[*]have a go at reseating it
[*]what does lspci tell you about the dvb cards?
[/LIST]

---

### Post by oletechie on 2009-04-19
Thanks for your help. I am unable to go any further because my power supply just died. I will get back onto the forum when I get the Power supply replaced.
I would assume a new thread would be best.

---

### Post by nickrout on 2009-04-19
Stick to the same thread, to which I am now "subscribed" - I will see your post when it comes through that way.

---

### Post by oletechie on 2009-04-20
OK, I'm Back up with a spare PSU.
The second card is also a Hauppauge HVR-1600. During the process of testing,I used each card separately to make sure the cards were good, which it seems they are. I was able to watch tv on an individual basis.
I have double and triple checked the seating for the cards. The connections feel good when I push the cards in place.

This is what I get from 'lspci':
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
00:09.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
Thanks for the support.

---

### Post by newlinux on 2009-04-20
lspci shows two cards.... Can you run:

dmesg | grep -i dvb

again just to double check that it still isn't loading both cards, maybe the power issue was affecting seeing both cards?  Maybe the driver has as in issue with two of the same cards... when I get a chance I'll look into it.

---

### Post by oletechie on 2009-04-20
Thanks for taking the time for me.

Here is the requested info:
 dmesg | grep -i dvb
[   23.114814] DVB: registering new adapter (cx18)
[   23.572171] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   23.572538] cx18-0: DVB Frontend registered

The PSU is rated at 480W, I was hoping that would be enough. I do have a CD writer and a DVD writer. At this point I don't think I will ever use the CD writer so I may remove it and reduce my power load.

Any comments?

---

### Post by newlinux on 2009-04-20
I don't think it is a power load issue. I just thought a faulty PSU might be causing problems before - so I don't think you need to remove the CD writer unless oyu want to. your current PSU is probably fine and not the problem. I don't have any immediate ideas, but I'm leaning towards problems getting them both loaded, since they are both "seen" on the bus... I'd do a google to see if anyone is having problems using two of these at in the same system...

---

