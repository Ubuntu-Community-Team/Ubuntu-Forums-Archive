---
title: "Internet wifi problem"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by MarcusA on 2009-03-05
Hello

I just installed a dual boot with Vista and ubuntu 8.10. My wireless internet conection works perfect in Vista but in Ubuntu I don't seem to be connected to the internet; i thought it would connect me automatically but alas.

I'm pretty much a n00b when it comes to computer issues so I don't have a clue what to do next?

This is what I get with ifconfig and iwconfig:


zoran@Omega:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1b:b9:8a:59:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB) 

zoran@Omega:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

zoran@Omega:~$ 

I'd appreciate your help :)

---

### Post by phantom3113 on 2009-03-05
One of the first blush issues you should consider is if your wireless card is supported and/or if they have proprietary drivers. What model of card do you have? The output of lsusb tells you.

---

### Post by MarcusA on 2009-03-05
> **phantom3113 said:**
> One of the first blush issues you should consider is if your wireless card is supported and/or if they have proprietary drivers. What model of card do you have? The output of lsusb tells you.

This is what it tells me:

zoran@Omega:~$ lsusb 
Bus 002 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 046d:c51b Logitech, Inc. 
Bus 001 Device 003: ID 03f0:0f0c Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
zoran@Omega:~$

---

### Post by RedSingularity on 2009-03-05
What does "lspci" give you?

---

### Post by mark bower on 2009-03-06
a USB adapter that works "out of the box" with Ubuntu 8.10 and connects to my router is Belkin F5D7050, sold at Best Buy and Fry's Electronics.  others report success with this adapter easily connecting.  none of my PCI adapters worked, so they are stored for possible future use.  i ended my misery by buying what works with native linux drivers, no ndiswrapper stuff.

mark bower

---

### Post by phantom3113 on 2009-03-06
Whoops, typed the wrong one. While that's not unhelpful, what Shadow suggested would be better:

> What does "lspci" give you?

Sorry for the mistype!

---

### Post by MarcusA on 2009-03-06
:) Ah well lspci gave me this:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1) 
01:06.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01) 
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1) 
zoran@Omega:~$

---

### Post by RedSingularity on 2009-03-06
Looks like you need drivers for that card.  Look [HERE](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.bz2?use_mirror=superb-west).  Download that and install.....see how that goes.

---

### Post by MarcusA on 2009-03-06
Will do! :) Lets try it out..

---

### Post by RedSingularity on 2009-03-06
Yes let me know how that goes.  If it doesn't work i have something else.

---

### Post by MarcusA on 2009-03-06
Just a quick question.. haha I know: I suck, but how do I install it exactelly?

---

### Post by phantom3113 on 2009-03-06
Ok, this shows that your wireless card is "Atheros Communications Inc. AR5413" listed next to Ethernet controller. I did some searching, and it turns out that this is a generally common problem. Others have tried ndiswrapper and MadWifi, with mixed results. I wish I could offer more, but I've been awake for far too long right now as it is, so I'll have to look into this more later. I suggest doing a google search for whats in quotes along with "ubuntu", that should at least lead to some potential fixes.

Oh well, looks as though I was a bit late :P

---

### Post by RedSingularity on 2009-03-06
> **MarcusA said:**
> Just a quick question.. haha I know: I suck, but how do I install it exactelly?

Scratch that one.  Try the one below first.  Install instructions included.

You need wireless drivers located [HERE](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) __[]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2"). Download to desktop, extract to desktop, then in terminal type "cd ~/Desktop/compat-wireless-2009-03-06". Then type "make" and finally type "sudo make install". When finished type "sudo make load". Restart computer.

---

### Post by MarcusA on 2009-03-06
I shall try that out :D hope it works! I really appreciate you guys helping me out here. Goodnight phantom3113.

---

### Post by RedSingularity on 2009-03-06
> **phantom3113 said:**
> Ok, this shows that your wireless card is "Atheros Communications Inc. AR5413" listed next to Ethernet controller. I did some searching, and it turns out that this is a generally common problem. Others have tried ndiswrapper and MadWifi, with mixed results. I wish I could offer more, but I've been awake for far too long right now as it is, so I'll have to look into this more later. I suggest doing a google search for whats in quotes along with "ubuntu", that should at least lead to some potential fixes.

I had the same issue with madwifi.  I tryed ath5k drivers and it worked perfectly!  Those are the ones i just offered Marcus.

---

### Post by MarcusA on 2009-03-06
I am typing this in Ubuntu! :D yay! Thank you so much Shadow121 your solution did the trick.

---

### Post by RedSingularity on 2009-03-06
No problem buddy.  You ever need anything else just come on back.  Everyone here is happy to help :)

---

### Post by MarcusA on 2009-03-06
> **Shadow121 said:**
> No problem buddy.  You ever need anything else just come on back.  Everyone here is happy to help :)

Haha don't worry I will! By the end of the month you'll probably get sick of me :D 

Hopefully I'll be able to help someone myself with ubuntu in the future

---

