---
title: "compaq F700 with ubuntu no wireless driver"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by mjc314 on 2011-06-08
Hi people who read this this is been an on going problem it started over 2 years ago when I had windows vista on this computer and my wifi went down for good. Well recently my girlfriend was having problems with her wireless and I put ubuntu on it yesterday and then it worked well that made me wonder so I installed ubuntu over my operating system on this computer.

I have not much experience in linux but I have tried most things I have read and when i went to the hardware drivers in the system's drop down a wireless driver doesn't show up I have no driver on here and of course after i wiped the drive and put this system on it i found the Compaq wireless drivers install (not sure if its real or not).

Anyway and help would be appreciated I can get on line fine with an ethernet but that is inconvenient to me with the nearest hook up being a bridged network on my brother's computer or the home router which is 30 ft away. I am getting desperate as to just buy a usb wifi adapter but if I can avoid that it would be great.

Thanks in advance.



Matt

---

### Post by josephmills on 2011-06-09
> **mjc314 said:**
> Hi people who read this this is been an on going problem it started over 2 years ago when I had windows vista on this computer and my wifi went down for good. Well recently my girlfriend was having problems with her wireless and I put ubuntu on it yesterday and then it worked well that made me wonder so I installed ubuntu over my operating system on this computer.

I have not much experience in linux but I have tried most things I have read and when i went to the hardware drivers in the system's drop down a wireless driver doesn't show up I have no driver on here and of course after i wiped the drive and put this system on it i found the Compaq wireless drivers install (not sure if its real or not).

Anyway and help would be appreciated I can get on line fine with an ethernet but that is inconvenient to me with the nearest hook up being a bridged network on my brother's computer or the home router which is 30 ft away. I am getting desperate as to just buy a usb wifi adapter but if I can avoid that it would be great.

Thanks in advance.



Matt

could we please see from both puters a ```
lspci -nn
``` and a ```
rfkill list all
```thanks

---

### Post by mjc314 on 2011-06-09
I think I may have not been clear there is only 1 computer having trouble my gf's works fine just made me wonder why mine isn't.



00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [GeForce Go 6100] [10de:0247] (rev a2)
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


The second command nothing happens.

matthew@matthew-laptop:~$ rfkill list all
matthew@matthew-laptop:~$

---

### Post by mjc314 on 2011-06-20
bump

---

### Post by walt.smith1960 on 2011-06-20
This machine has an internal card?  I don't see any indication of a wireless network controller  in that "lspci" output. I assume this is your ethernet (wired) controller```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
``` I would expect to see something from RealTek or Ralink or Broadcom or somebody like that.  You wireless adapter isn't a USB, is it?  If so, the output of "lsusb" might shed some light.

---

### Post by mjc314 on 2011-06-21
No that computer has a built in wifi adapter I am getting to the point of buying a usb if it gets bad. But the computer worked fine for over a year when it was running vista then I had problems with the whole system so I just did a complete wipe of the hard drive put ubuntu 10.4 then I tried putting windows XP back on it to see if I could install the drivers. After that didn't work I put ubuntu 11.4 on it still no detecting of the drivers.

Right now I am on my school laptop but I was on ethernet adapter when I did the first commands but I am at a loss as to what I can do any suggestions or solutions.




Matt

---

### Post by walt.smith1960 on 2011-06-21
I'd almost think the built-in device has given up its silicon ghost if it's not recognized under XP either.  Did anything strange show up in device manager?    I assume you've checked for hardware wifi switches?  If you choose to get a USB device, I can give advice on the ones I've used. 2 N150 devices and one vintage but reliable G speed device that has been plug & play since Ubuntu 9.04 up and including 11.10.  Both my N150 devices required (simple) work in distros prior to 11.04.  All 3 of my WiFi  USB adapters are plug & play on 11.04.  Let me know if I can be of further assistance.  

Edit:  What release are you using?  I've played with Simply Mepis and Kubuntu.  My wireless  experience hasn't been as positive with the KDE versions as it has been with Gnome.  I have my ssid hidden which is a problem with KDE, it seems.

---

### Post by mjc314 on 2011-06-22
I am running the default GNOME on this distro. And as for the device manager I know a few things came up with a question mark but I don't recall exactly which ones they were. It could be possble my card is burned out cause that laptop had poor cooling (it was built horribly), at times the core would exceed 180F up to 200F+ averaging around 160F so thats an option but the weird thing is I had the laptop hidden away for about 6 months and when I pulled it out the wifi worked but then it got a load of updates then when I reset it the wifi broke again that was over 1 year ago that happened and the computer wouldn't charge my battery either (it does now on ubuntu but I don't know if it will stay that way) honestly this computer is a wreck but I wanted to see if i could get it going again.



Matt

---

### Post by walt.smith1960 on 2011-06-22
That does indeed sound like something could have gotten cooked.

---

