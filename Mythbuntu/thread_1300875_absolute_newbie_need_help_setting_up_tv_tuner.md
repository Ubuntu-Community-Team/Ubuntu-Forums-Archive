---
title: "absolute newbie need help setting up tv tuner"
date: 2009-10-25
forum: Mythbuntu
---

### Post by mokrayz on 2009-10-25
can somebody pls guide me through setting up tv tuner. i downloaded myth tv and tv time, but none is picking up the card. been googling this  for weeks but instructions to advanced.

---

### Post by howefield on 2009-10-25
What is the make model of the tv tuner card ?

---

### Post by lovinglinux on 2009-10-25
This is how I configured mine [http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)

I suggest trying to make it work with TVTime or Kaffeine before going through MythTV configuration.

---

### Post by Sef on 2009-10-25
Moved to Mythbuntu forum.

---

### Post by laceration on 2009-10-25
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)

Look for the "Digital Devices (DVB):" heading at the end of the page and go from there to find specifics for your device.  After you setup your device you have to scan for channels.  Unfortunately in Linux this can be challenging for beginners, but it is doable.

---

### Post by mars76 on 2009-10-25
If you don't know the make and model of the card..

post the output of the following..

$ lspci

$ dmesg | grep ivtv

---

### Post by mokrayz on 2009-11-06
$ lspci output:
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)

AND 

dmesg | grep ivtv gives no output

---

### Post by mokrayz on 2009-11-06
On the card it says : Chronos pci 7135

---

### Post by laceration on 2009-11-06
Do a 
$ dmesg | grep SAA713

---

