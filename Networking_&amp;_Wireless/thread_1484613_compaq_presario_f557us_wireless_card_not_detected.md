---
title: "compaq presario f557us wireless card not detected"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by AngelSeph on 2010-05-15
Hello everyone,

I am in need of some help trying to get my wireless working. I have a compaq presario f557us and my wireless card just seems to be dead.
I got this laptop a few years ago and I tried installing ubuntu 7.04. The wireless part did not work out of the box (it took a lot of tinkering but finally got it working by using ndiswrapper). Later I did an OS reinstall but tried ubuntu 8.10 this time and the card was recognized with no problems, I just needed to use the proprietary drivers that ubuntu recommended.
Finally I decided to give 10.04 a try. I don't know if doing an "apt-get upgrade" would've been fine but it's too late for that now; I did a fresh install and the wireless part seems dead.

I already tried installing ndiswrapper as I did before:
$ ndiswrapper -l
bcmwl5 : driver installed

later I tried the fwcutter way:
$ bcm43xx-fwcutter -i bcmwl5.sys 
Sorry, the input file is either wrong or not supported by fwcutter.
I can't find the MD5sum b89bcf0a25aeb3b47030ac83287f894a :(

(it gives me the same error with other bcmwl5.sys files I have downloaded)

This is the output of lspci:
$ lspci 
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
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


I already tried searching the forums but none have worked for me. I would not like to go back to 8.10 or something else but I do need the wireless part working so I would appreciate any advice you can give.

Thanks!

---

### Post by cariboo on 2010-05-16
According to the output of lspci, there isn't a wireless card in your system. Are you using a usb device?

---

### Post by AngelSeph on 2010-05-16
No, that's exactly the problem; ubuntu 10.04 simply does not recognize the card.

There is a switch that is supposed to be amber color when you have the wireless interface turned off and it lights blue when you turn it on, ever since I installed 10.04 it stays amber no matter what I do; it seems as if it's disconnected from the inside but that cant be because using a live cd from another distro (mepis) the card gets recognized.

Too bad, I was really looking forward to use 10.04 but I guess I have to change to another distro.

---

### Post by NUboon2Age on 2010-05-17
Let's get some more data to work with [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?p=6183681")

---

