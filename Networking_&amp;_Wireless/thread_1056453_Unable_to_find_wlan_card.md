---
title: "Unable to find wlan card"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by Mikkeren on 2009-01-31
My Atheros WN6302A doesn't show up when i lspci or when i lshw, can anyone help me figure out how to make Ubuntu able to find and use it?

---

### Post by albinootje on 2009-01-31
> **Mikkeren said:**
> My Atheros WN6302A doesn't show up when i lspci or when i lshw, can anyone help me figure out how to make Ubuntu able to find and use it?

Can you post the output of :
```

lsusb
sudo lshw -C network
lspci

```
You might need Ndiswrapper to make it work.

---

### Post by albinootje on 2009-01-31
You've started here another thread on the same subject, it is much better to use "bump" after a certain amount of time.

See also here, where someone comes with a solution :
[http://ubuntuforums.org/showthread.php?t=870016](http://ubuntuforums.org/showthread.php?t=870016)

Which brand and type of laptop it is ?

---

### Post by Mikkeren on 2009-01-31
> **albinootje said:**
> Can you post the output of :
```

lsusb
sudo lshw -C network
lspci

```
You might need Ndiswrapper to make it work.

Sure I can.

lsusb:
```
Bus 002 Device 002: ID 0bf8:100f Fujitsu Siemens Computers 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

sudo lshw -C network:
```
  *-network DISABLED      
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:a4:75:5c:b5:79
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lspci:
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
07:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

> **albinootje said:**
> You've started here another thread on the same subject, it is much better to use "bump" after a certain amount of time.

See also here, where someone comes with a solution :
[http://ubuntuforums.org/showthread.php?t=870016](http://ubuntuforums.org/showthread.php?t=870016)

Which brand and type of laptop it is ?

Yeah, after a while I just figured that this section of the forum was more fitting and that people lurking here would know more.

And I've already tried what's mentioned in that thread, no luck so far.
Also it's a Fujitsu-Siemens Amilo Xa 2528.

---

### Post by MarblePanther on 2009-01-31
Try going into System, Administration, Hardware Drivers and check if there are any drivers listed there.

IMPORTANT--But first make sure you are connected to the internet somehow (ethernet, dialup, etc...)

If you are connected and there is nothing listed there you will need to use ndiswrapper.

Gather your windows driver cd for your laptop or download the wireless driver from your manafacturer's website.

Then go into Synaptic Package Manager (first go into the settings of synaptic, then repositories, third party software, and check the first line that ends with "partner", then hit the reload button) and search for and install ndisgtk.

Then go to System, Administration, Windows Drivers.

It will ask you for the inf file of your driver.

So extract your drivers .exe file to a folder and locate the inf file.

NOTE: this may not work, but give it a try.  I dont know if your driver is supported by ndiswrapper or not.

---

### Post by albinootje on 2009-01-31
Thanks for the output.
I can't find your wifi card in the output :(

Searching for your laptop type shows a few pages :
[http://ubuntuforums.org/archive/index.php/t-699244.html](http://ubuntuforums.org/archive/index.php/t-699244.html)
[http://forum.fujitsu-siemens.de/forum/viewtopic.php?f=62&t=27910](http://forum.fujitsu-siemens.de/forum/viewtopic.php?f=62&t=27910)
where both pages mentioned that wifi is not working.

This page (in german) even says that the author returned the laptop :
[http://www.willemer.de/informatik/unix/Xa2528.htm](http://www.willemer.de/informatik/unix/Xa2528.htm)

Here's another page (in german) where someone recommends trying Ndiswrapper, and posts links for the MS-Windows driver for the wifi card :
[http://www.amilo-forum.de/topic,24622,-Amilo-Xa-2528-Wireless-Lan-Chipsatz.html](http://www.amilo-forum.de/topic,24622,-Amilo-Xa-2528-Wireless-Lan-Chipsatz.html)

YMMV :|

---

### Post by Mikkeren on 2009-01-31
Well, I've just tried using ndiswrapper and even though I've got it installed and under the driver for my card it says "Hardware present: Yes", the wireless card is still nowhere to be found, according to Ubuntu.

---

### Post by albinootje on 2009-01-31
> **Mikkeren said:**
> Well, I've just tried using ndiswrapper and even though I've got it installed and under the driver for my card it says "Hardware present: Yes", the wireless card is still nowhere to be found, according to Ubuntu.

Hmmm, okay, can you post the output of :
```

iwconfig
sudo iwlist scan

```

If I were you I would think about buying a wifi usb stick which is supported by Linux.

---

### Post by MarblePanther on 2009-01-31
If you do get a usb wireless stick, I would not recommend NETGEAR, they get extremely hot (I had to take the plastic case off mine to give it some airflow :) )

---

### Post by Mikkeren on 2009-01-31
> **albinootje said:**
> Hmmm, okay, can you post the output of :
```

iwconfig
sudo iwlist scan

```

If I were you I would think about buying a wifi usb stick which is supported by Linux.

iwconfig:
```
lo        no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.
```

sudo iwlist scan: 
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```


And i must admit it's starting to seem like a good idea with a wireless USB stick.

---

### Post by albinootje on 2009-01-31
> **Mikkeren said:**
>  And i must admit it's starting to seem like a good idea with a wireless USB stick.

You can search for what is supported by Linux here :
[http://hardware4linux.info/search/](http://hardware4linux.info/search/)

---

### Post by Mikkeren on 2009-01-31
> **albinootje said:**
> You can search for what is supported by Linux here :
[http://hardware4linux.info/search/](http://hardware4linux.info/search/)

Thanks alot for your help =)

I guess I'm giving up on making the built-in wlan work then.

---

### Post by albinootje on 2009-01-31
> **Mikkeren said:**
> Thanks alot for your help =)

I guess I'm giving up on making the built-in wlan work then.
Okay, good luck with finding a nice wifi usb stick/card! 
Remember that the people in the computer hardware shops usually don't know much (or enough) about Linux support. 
It's better to do a good research yourself, so e.g. first search what sticks/cards are being supported by Linux, then look what the computer hardware shops have to offer, and then search for postings from people who have it successfully in use with Ubuntu.

---

