---
title: "System locks up while running Jackd"
date: 2013-06-06
forum: Multimedia Software
---

### Post by Muaddib86 on 2013-06-06
Hi,

I'm completely new to Ubuntu, and the larger Linux world for that matter, but despite this I've managed to get everything up and running with the aid of the official documentation and the ever helpful posts here on the forum.  That being said though, I've recently hit an impass and have had no luck with my own experimentation nor with finding any previous posts with the same problem...  

It seems that whenever I have Jackd (1.9.9.5) running, regardless of whether i'm currently recording, playing music, or just letting the system sit idle for that matter, my computer will completely freeze forcing me to reset.  Sometimes it'll only take a few minutes, other times it'll run for a few hours.  From what I've read, it seems like everything should be working so i'm at a loss.  I'm currently using a Presonus Firepod, which I've read is supported by the version of FFADO I have installed (2.1 I believe), and from what I can tell I'm not even close to pushing my hardware to its limits -- even using qjackctl to set jackd to the most modest of settings makes no difference.  I'm running Ubuntu 12.04 64 bit with the 3.8.0-22-lowlatency kernel.  Any help would be greatly appreciated.

/0                         bus         SABERTOOTH 990FX R2.0
/0/0                       memory      64KiB BIOS
/0/4                       processor   AMD FX(tm)-8350 Eight-Core Processor
/0/4/5                     memory      384KiB L1 cache
/0/4/6                     memory      8MiB L2 cache
/0/4/7                     memory      8MiB L3 cache
/0/2d                      memory      16GiB System Memory
/0/2d/0                    memory      DIMM Synchronous [empty]
/0/2d/1                    memory      8GiB DIMM DDR3 Synchronous 1333 MHz (0.8 
/0/2d/2                    memory      DIMM Synchronous [empty]
/0/2d/3                    memory      8GiB DIMM DDR3 Synchronous 1333 MHz (0.8 
/0/100                     bridge      RD890 PCI to PCI bridge (external gfx0 po
/0/100/2                   bridge      RD890 PCI to PCI bridge (PCI express gpp 
/0/100/4                   bridge      RD890 PCI to PCI bridge (PCI express gpp 
/0/100/4/0                 storage     ASM1062 Serial ATA Controller
/0/100/5                   bridge      RD890 PCI to PCI bridge (PCI express gpp 
/0/100/5/0                 storage     ASM1062 Serial ATA Controller
/0/100/9                   bridge      RD890 PCI to PCI bridge (PCI express gpp 
/0/100/9/0                 bus         ASM1042 SuperSpeed USB Host Controller
/0/100/a                   bridge      RD890 PCI to PCI bridge (external gfx1 po
/0/100/b                   bridge      RD890 PCI to PCI bridge (NB-SB link)
/0/100/b/0                 display     Juniper [Radeon HD 5700 Series]
/0/100/b/0.1               multimedia  Juniper HDMI Audio [Radeon HD 5700 Series
/0/100/d                   bridge      RD890 PCI to PCI bridge (external gfx1 po
/0/100/11                  storage     SB7x0/SB8x0/SB9x0 SATA Controller [IDE mo
/0/100/12                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                  bus         SBx00 SMBus Controller
/0/100/14.1                storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.3                bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/100/15                  bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15/0                bus         IEEE 1394 Host Controller
/0/100/15.1                bridge      SB700/SB800/SB900 PCI to PCI bridge (PCIE
/0/100/15.1/0  eth0        network     RTL8111/8168B PCI Express Gigabit Etherne
/0/100/15.2                bridge      SB900 PCI to PCI bridge (PCIE port 2)
/0/100/15.2/0              bus         ASM1042 SuperSpeed USB Host Controller
/0/100/15.3                bridge      SB900 PCI to PCI bridge (PCIE port 3)
/0/100/15.3/0              bus         ASM1042 SuperSpeed USB Host Controller
/0/100/16                  bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/16.2                bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/101                     bridge      Family 15h Processor Function 0
/0/102                     bridge      Family 15h Processor Function 1
/0/103                     bridge      Family 15h Processor Function 2
/0/104                     bridge      Family 15h Processor Function 3
/0/105                     bridge      Family 15h Processor Function 4
/0/106                     bridge      Family 15h Processor Function 5
/0/1           scsi0       storage     
/0/1/0.0.0     /dev/sda    disk        250GB ST3250410AS
/0/1/0.0.0/1   /dev/sda1   volume      93MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2   volume      216GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3   volume      15GiB Linux swap volume
/0/2           scsi1       storage     
/0/2/0.0.0     /dev/cdrom  disk        DVDR   PX-880SA
/0/2/0.0.0/0   /dev/cdrom  disk        
/0/3           scsi8       storage     
/0/3/0.0.0     /dev/sdb    disk        250GB SCSI Disk
/0/3/0.0.0/1   /dev/sdb1   volume      232GiB Windows NTFS volume
/1             wlan0       network     Wireless interface

---

### Post by ohnonot on 2013-06-07
welcome to the forums!

if you're doing audio/video production i would highly recommend to install ubuntu studio or some other audio/video orientated linux distro.

apart from that i just found this: [http://ubuntuforums.org/showthread.php?t=2151914](http://ubuntuforums.org/showthread.php?t=2151914)

a good general read: [http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

---

### Post by Muaddib86 on 2013-06-08
Thanks!

I did try my luck with KXStudio at one point, but actually had less success with that.  I think I'll go ahead and give Ubuntu Studio 13.04 a shot though since it comes with that newer version of pulseaudio, and probably some other useful stuff, so maybe that'll do the trick.

---

### Post by ohnonot on 2013-06-10
a tip:
if you have 10GB to spare, setup 3 partitions before reinstalling: one to install *buntu or any everyday linux, one for ubuntu studio, and one for data!

---

### Post by Muaddib86 on 2013-06-10
Ah, well thanks for the tip, though I went all in with the Ubuntu studio install -- it's cool, I actually prefer the interface after using it for a spell now, plus my data is stored on an external drive.  Unfortunately though, Ubuntu studio wasn't the quick fix I was hoping for...

I'm now running jackd 1.9.10 and pulseaudio 3.0 (everything else appears to be the same) under the 13.04 64 bit release and i'm still having the same issue.  I tried playing around with the settings for jackd and had a marginal improvement after the installation -- from about 5 min of operation after the initial clean install to about 2 hours at incredibly low settings.  After the two hours though, my machine still managed to lock up despite jackd reportedly taking up only about 5% of my CPU and under 1% of memory so I'm still not sure this is the source of my problems.

At one point I had considered an IRQ conflict to be the culprit so I did disable the onboard sound card of my motherboard in the bios under the previous installation (and remains to be so).  Ultimately, the problem was still not resolved but now i notice that my video card (a Radeon HD 5700 series) is being recognized as a digital stereo output.  Could it be that this is causing a conflict and so the lock ups?  Also, is there a process by which I could maybe see a log file of what happened (given the fact that the system is totally unreponsive -- mouse, keyboard, everything -- once it does lock up?  I've heard that in cases such as this it often doesn't even have time to generate an error report so I wasn't sure.

---

### Post by ohnonot on 2013-06-12
i have very little experience with non-laptop setups, but the thing that the video card is being recognized as a stereo audio output sounds like a cause for trouble!
(is that generally possible? maybe it *has* a stereo output for monitor-integrated speakers?
you should make web searches for "ubuntu <insert your hardware component>".
yes, you should find log files if the task manager does not help.
have you tried to type 'dmesg | more' in a terminal? it produces a *lot* of output, but you can reduce it with 'dmesg | grep -i <whatyouresearchingfor>'.

ps: if sth is written <likethis> it usually means that you're to insert something there, but without the <>.
i hope this helps.

---

### Post by Muaddib86 on 2013-06-18
While I don't fully understand the video card being recognized as an audio out (it's on the HDMI out for those whom may be more well versed than I), the good news is the problem's been resolved.  Turns out it was entirely hardware related, though not related to my RAM, Firepod, CPU or anything else so crucial.  Based on my IRQ theory, I decided to try, and fortunately I had, an old PCI card that I used to use to provide me with firewire ports (as opposed to the PCIe card I was using most recently), under the assumption that it'd be the safest bet to avoid any potential conflicts with my video card, and, loe and behold, i've now been running Jack for days now without a lock up.  It may be that I could still use my PCIe card in a different slot, or there may have been another solution to this issue, but i'm just super pleased to have it working.  Many thanks to you ohnonot for the help.  Best of all, I now am not forced to make the walk of shame back to Windows XP. :D

---

