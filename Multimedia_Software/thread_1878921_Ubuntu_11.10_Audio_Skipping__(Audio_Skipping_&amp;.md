---
title: "Ubuntu 11.10 Audio Skipping || (Audio Skipping &amp;&amp; Video Skipping)"
date: 2011-11-10
forum: Multimedia Software
---

### Post by 3246251196 on 2011-11-10
I wish I had never upgraded to .10 OO:

For one, I do not like the new interface. In fact, I hate it. Plus, GNOME Classic is even worse than it was before, unfortunately. Sometimes I question what people are thinking when it comes to these "upgrades"; sure, behind the scenes things might be better, but: If it's not broke, don't fix it!

So be it. I will use this lesser GNOME Classic for now.

Now, besides that is the main issue:

===

$ lspci
...
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
...

===

I remember in 10.10 MM there was no sound for this particular card of mine [X-Fi Xtreme Audio; PCIe] - as a lot of us users know. However, this was BEAUTIFULLY rectified in 11.04 NN. I just wish I had stayed with NN, really! However, I decided - MY ERROR - to upgrade to 11.10 OO.

On youtube videos are either playing at the correct speed but the audio keeps skipping.
On youtube videos are either playing too quickly and skipping.

Using VLC prevails in only every 5-10  seconds being rendered in about 1 second with no sound; i.e. a ridiculously quick video.

I do not know where to start and I am little annoyed; furthermore, I will wait a LONG time before ever committing to an upgrade again. Can someone help, please?

---

### Post by 3246251196 on 2011-11-10
> 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
03:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


Further research tells me that it might not specifically be the sound card. So, I will dump everything from LSPCI.

All I know is that everything was working fine on 11.04

---

### Post by jonikang on 2011-11-12
I can confirm that this is an issue on Ubuntu 11.10. The card is working fine on 11.04.

Anyone has any solution?

---

### Post by johnmay on 2011-11-22
> 0c:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
0d:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBGI have the same card and (from what it *doesn't sound like) the same problem. 

I was not able to use the card at all in 10.04 and 10.10 but it was working in 11.04. 
Now, it looks like a regression has occurred for CA0110-IBG.

*[3246251196]("http://ubuntuforums.org/member.php?u=1258334") is a great alias - not your soc I hope

---

### Post by johnmay on 2011-11-26
I found the solution! 
The first song I listened to was Jimi Hendrix - Bold as Love - then to make doubly sure started watching Machete :grin:

 Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG  IS supported in alsa.

the fix found: [http://ubuntuforums.org/showthread.php?t=1804083](http://ubuntuforums.org/showthread.php?t=1804083)
is to add 
"options snd-hda-intel position_fix=1  model=3stack" 
into /etc/modprobe.d/alsa-base.conf in the options section.

reboot and enjoy!:popcorn:

---

### Post by 3246251196 on 2011-11-27
Johnmay,

thanks. I will try this out imminently.

---

### Post by 3246251196 on 2011-11-27
Okay, = )

I am confirm that this is the way to solve this issue.

Johnmay, thank you very much; Great work!

---

### Post by Dlambert on 2012-03-06
Worked for me! Thanks!

---

### Post by sorceror on 2012-03-19
> **johnmay said:**
> 
the fix found: [http://ubuntuforums.org/showthread.php?t=1804083](http://ubuntuforums.org/showthread.php?t=1804083)
is to add 
"options snd-hda-intel position_fix=1  model=3stack" 
into /etc/modprobe.d/alsa-base.conf in the options section.

Sadly, that didn't work for me on Xubuntu 11.10 amd64. In fact, nothing I've done has managed to get this card to play without skipping. It doesn't seem to be a mixer issue (a la [http://ubuntuforums.org/showthread.php?t=1870596](http://ubuntuforums.org/showthread.php?t=1870596) ) since I'm getting *some* sound.

Anyone have any idea? I'm gonna pull the dang card soon, at this rate...

---

