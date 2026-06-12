---
title: "realtek wireless cant connect"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by bullet sincar on 2009-11-17
i am brand new to ubuntu and have been surfing these forums for a while trying to get my wireless going.  what i have learned is that i am dangerously under qualified to do this.  im going to tell you what i know and see if anyone can help me.
i am attempting to connect to an existing wireless network with WPA personal protection.  my ubuntu computer detects it, but does not have a WPA option on the security pull down.  i have the newest version of ubuntu.  got it today.  in terminal, when i command :  sudo lshw -C network   
i get
*-network
     description: Ethernet interface
     product: RTL -8139/8139c/8139C+
     vendor: Realtek Semiconductor Co., Ltd.
     physical id: 3
     bus info: pci@0000:02:03.0
     logical name: eth0
     version: 10
     serial: 00:13:d3:0e:42:b7
     size: 10 MB/s
     capacity: 100 MB/s
     width: 32 bits
     clock: 33MHz
    capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
     configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
     resources: irq:20 ioport:dd00(size=256) memory:fdcfe000-fdcfe0ff
*-network
     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: 00:06:25:31:36:16
     capabilities: ethernet physical wireless
     configuration: broadcast=yes multicast=yes wirless=IEEE 802.11-DS

it might be important to note that i am not using ubuntu alongside anything else, i have a computer with only ubuntu on it.  
i also did the command to install a wpasupplicant but it seems it was unnecessary.  thats pretty much where i got lost.  
any help that i could get would be greatly appreciated.

---

### Post by Dude-PWB- on 2009-11-17
What is the output of the networking part of lspci -vv?

---

### Post by bullet sincar on 2009-11-17
i believe this is what you were looking for....?

02:01.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Device 044c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (63000ns min, 3500ns max)
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at fdcff000 (32-bit, non-prefetchable) [size=256]
	Region 1: I/O ports at df00 [size=8]
	Region 2: I/O ports at de00 [size=256]
	Capabilities: <access denied>

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 2a20
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: I/O ports at dd00 [size=256]
	Region 1: Memory at fdcfe000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp

---

### Post by Dude-PWB- on 2009-11-17
Unless I'm missing something, I see you have the realtek 8139 ethernet card, which is not wireless.

But in your first post you show near the bottom, a wlan0 device, but no chipset listed there. Not sure where to take this since I can't tell what wireless adapter you have?

---

### Post by bullet sincar on 2009-11-17
that is all of the output that i can tell is related to networking.  i have a Linksys Wireless-B 2.4GHz (802.11b) USB wireles network adapter plugged into the computer.  the computer detects it and can find the network, but does not offer me a WPA as an option when i want to type in the password.  im pretty lost here.  is there anything else, other info i should try to give you?  thank you for your help.

---

### Post by Dude-PWB- on 2009-11-17
I wonder if you had the model number of the USB adapter to see if we can find what chipset it has.

Since it is USB, what does it tell you that it is when you type lsusb from the terminal?

---

### Post by bullet sincar on 2009-11-17
after lsusb,
there are six listed....but i think the one we are interested in is....

Bus 002 Device 002: ID 1915:2236 Linksys WUSB11 v3.0 802.11b Adapter   

the wireless router i am using is a Netgear   WPN 824

---

### Post by Dude-PWB- on 2009-11-17
Ok, not sure what chipset it has but, you might be able to install ndiswrapper and use it to load the windows driver in ubuntu and have it manage your adapter. I haven't seen any linux drivers listed for it yet.

Have you tried installing wicd from the repositories?

It replaces (removes) the current default network manager with the wicd network manager. Some have had better luck with that program.

If you google 'Linksys WUSB11 Ubuntu linux' you will come up with a pile of results to read through.

Your adapter is version 3.0.

---

### Post by Dude-PWB- on 2009-11-17
Here is another link I found for v4.0 of that adapter.

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29)

---

### Post by bullet sincar on 2009-11-18
dude, thanks for your time on this, i apologize for not figuring it out sooner.

i have been trying a number of different guides but always run into trouble.  it seems one of my problems is unwrapping and installing the newest    ndiswrapper.  i downloaded the 1.55tar on this (my internet connected MAC) as well as ndiswrapper utils and ndisgtk.deb        I copy them to my desktop (this might be my problem, but i dont know where to put them).  in terminal i command,       tar zxvf ndiswrapper-version.tar.gz       which i imagine is intended to unpackage and/or install it, but it fails to locate the directory.  this is a step in many of the guides and i always get (Cannot open: No such file or directory)  i have also tried commands specifically geared towards ndiswrapper-1.55.tar
this was attempting to follow directions here :  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

i also tried here: 
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)
but get stuck at steps 13 and 14 when it tells me to "sudo apt-get install build-essential linux-headers-`uname -r`" and so on.....it gives me error messages that it couldn't find the build essential package or CVS

i will also mention that i tried to DL the driver for linksys WUSB11 v4 from [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB11v4](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB11v4)
but that it is an exe file and does not respond at all.  

perhaps im missing something pretty basic, i pretty much just follow directions on these guides as closely as possible and usually i blindly feel my way through, though this time its not looking so bright.

---

### Post by bullet sincar on 2009-11-18
on this one i get to somewhere in step 2 where it wants me to check the files in cat /etc/iftab but that directory cant be found either.

---

