---
title: "Broadcom internal wireless stopped working"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by nefrin on 2009-05-14
System Specs:
HP Pavilion tx 1000
Ubuntu 8.04 (updated)
Broadcom built in wireless

This system has been working perfectly for over a year. Recently I have been working with my computer in an area where there is a wireless network, but no internet access, so I turned off the card (slider switch on the front) and unchecked the "Enable Wireless" option on the taskbar icon.

A month passes.

Now I want the net back on my laptop, and I can't get the dang thing to turn on the card or realize there is one there. The slider switch light, which always worked switching from orange to blue (off to on) only stays orange. The network icon has "Enable Networking" checked, but doesn't even show an option for wireless.

Network settings likewise only shows modem and wired connection options. The internal device worked perfectly upon install and up until now, I'm at a complete loss as I haven't messed with any other files.

Have also tried NDISWrapper, but for the life of me cannot find the .inf file I need to make it work. Have tried downloading several versions of the driver, install them under WINE, and use the .inf file, but NDISWrapper keeps kicking them back as incompatible.

---

### Post by Ayuthia on 2009-05-14
Does dmesg|grep b43 show any messages for the wireless card?  I am making the assumption that you are still using the b43 option instead of ndiswrapper.

---

### Post by nefrin on 2009-05-15
the dmesg|grep b43 returned nothing on terminal. Other commands as well have returned nothing (lshw, lspci, etc). It's as if the card is no longer there as far as ubuntu is concerned. 

I was quite pleased that the wireless worked straight out of the box, so to speak, with 8.04, kinda upset that it stopped working for no reason. 

That being said, would like to just get it working again.

---

### Post by Ayuthia on 2009-05-16
Can you post the results of lspci -nn?  It will be helpful in determining which chipset you have.  There are currently three different wireless drivers that you can use for Broadcom now (b43/b43legacy, wl, and ndiswrapper) but some will only work for certain chipsets.

---

### Post by nefrin on 2009-05-18
output of lspci -nn:

username@computername:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce 6150 Go] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
username@computername:~$ 

As you can see, there isn't any info in there about the Broadcom wireless that I used to use, I have no idea where it went.

---

### Post by mickemicke77 on 2009-05-18
Got a clean 9.04 installation.

I been struggling with the same issue as well. without any luck.

Have matching set of HW and have exactly the same result with lspci lshw dmesg etc.

(HP Pavilion tx 1000)

---

### Post by darsie on 2009-05-18
I had the same problem with my HP dv6000. Looks like it's a common problem with HP motherboards as mentioned ([here]("http://forums11.itrc.hp.com/service/forums/questionanswer.do?threadId=1245147").

If you have a dual boot, check in Windows too. My HP was out of warranty so I just gave in and bought a USB adapter.

Hope this isn't the case for you.

---

### Post by mickemicke77 on 2009-05-18
darsie,

The problem started in windows.

So I told my girlfriend that this was probably a vista issue and I didn't want to spend a minute trying to fix it so I convinced her that she could use ubuntu and the laptop would get a new life.

For once Bill wasn't to blame :)

I'll go get a USB wireless device tomorrow.

Many Thanks!

---

### Post by nefrin on 2009-05-18
read through the link provided describing the issues with HP motherboards. My computer is way over warranty, so no luck there.

I'm crossing my fingers that the whole computer doesn't up and die on me, as I plan on keeping this one for school work later this summer. Suffice to say, I'm going to not be keeping any key files on it.

Can anyone recommend a good but inexpensive USB wireless adapter that works well with Ubuntu 8.04? Preferable wireless-g capable.

---

### Post by mickemicke77 on 2009-05-20
nefrin,

I went for D-link DWL-G122 it was just plug n play.
Got it for like $25

// Mikael

---

