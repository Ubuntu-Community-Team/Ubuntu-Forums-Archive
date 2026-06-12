---
title: "Wireless network is visible but disabled - how to connect?"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by elasticsoul on 2010-07-23
Hello all,
 
I have a weird problem that I can't find the answer for in the forums or docs. I can see the wireless network in Network Manager, but it is grayed-out and inaccessible. Other wireless networks are white and I can click on them and connect to them (or could if I knew the password). 
 
My work computer, an IBM ThinkPad T43 running Win 7, connects. 
My personal computer, a Dell Latitude C640 running Ubuntu 10.04, sees the network as grayed-out and therefore I have no option to connect to it. 
 
I have tried the following:
[LIST]
[*]Checked for hardware drivers - the system says "No proprietary drivers are in use on this system"
[*]Verified that the network security settings are the same on both my work and personal computers: WPA2-Personal
[/LIST]Why can I see the network but it is disabled/grayed-out? 
 
Thanks,
Brian

---

### Post by dca on 2010-07-23
Normally just the headers "Wireless Network" or "Wired Network" is grayed out and if wireless is working, network names will be shown underneath each...

 
This thread kinda' gives you an idea to check the wireless card's chipset and if it's Broadcom, how to get it up...
 
[http://ubuntuforums.org/showthread.php?t=1018216](http://ubuntuforums.org/showthread.php?t=1018216)

---

### Post by elasticsoul on 2010-07-23
Thanks dca (aka Mel?) :)  I looked throught that thread, but unfortunately [[COLOR=#444444]http://blog.sampbar.com/2009/01/broa...untu-intrepid/[/COLOR]]("http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/") is no longer online. I don't know if that's the problem; could be that my chipset doesn't support WPA2?

---

### Post by dca on 2010-07-23
Issue 
 
*sudo lspci | grep -i network *
 
at CLI and see if that gives any idea what kind of wireless chip you have inside the card...

---

### Post by elasticsoul on 2010-07-23
Thanks dca - I typed that in Terminal and got...nothing. Not even OK; it just returned to the next command line.

---

### Post by dca on 2010-07-23
Okay, then just *sudo lspci* and paste in response...  That will list all cards: network, graphics, etc.
 
...while you're at it, *sudo lsusb*, and paste.  That will display anything added to USB Bus Controller.

---

### Post by elasticsoul on 2010-07-23
Ok, here are the results. Note that I just installed WICD, and will have to wait till I'm home to see if that works. Is there anything below related to wireless?
 
sudo lspci:
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
 
sudo lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[LIST]
[*]I gather this means I have nothing plugged into my USB port (this Dell has only one...), which is correct.
[/LIST]

---

### Post by dca on 2010-07-23
Yikes, I don't even see a wireless card listed.  I see the 3Com NIC...
 
Judging by Dell Specs it either has Dell TrueMobile 1500 mini-PCI card or Intel 5000 mini-PCI, hmmm.  This may require 'ndiswrapper' and Windows drivers if we can find out exactly what chipset it uses...

---

### Post by elasticsoul on 2010-07-23
Strange, eh? But it does have wireless. It's a Dell C640, so perhaps the wireless is built-in somehow.

---

