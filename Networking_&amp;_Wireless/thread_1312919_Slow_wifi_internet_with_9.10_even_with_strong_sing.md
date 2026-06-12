---
title: "Slow wifi internet with 9.10 even with strong singal"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by Maxepr on 2009-11-03
I am some what of a "newb" to Linux but I have a small problem since upgrading to 9.10. When I first installed 9.04, my internet was slow as it is now.It is not my provider. It is not my signal strength or some interference from anything. It is not my hardware. It is not the browser. I have tried all of them (except internet explorer from microcrap) 

 When using 9.04, I went "System/Administration/hardware driver" and found a proprietary driver for my wireless card. After I changed to it, my internet was great. I just put in 9.10 and it is as slow as 9.04 was when I fist installed it except now there are no propietary drivers listed.

I have been through all the forums that I care too. I have spent a week trying to fix this. I have been through all the (so called EASY) driver installs and all I have succeed in doing is having to reload the entire system, twice. As I have said, I'm a newb but not an idiot.

My question is this. Are there going to be any other drivers, Proprietary or otherwise,through the normal upgrade process? If not, Then I will reluctantly have to go back to 9.04.

help
maxepr

---

### Post by dajare on 2009-11-03
I first tried Ubuntu from the 9.04 live disk, and have now installed 9.10 on an older Toshiba laptop. I have precisely your symptoms, but no idea about how to solve them.

I guess this is just to let you know you're not alone -- and I am extremely interested to hear if there are any (other) solutions.

David.

---

### Post by arjuntank on 2009-11-03
i saw this problem on my dad's laptop where i just installed 9.10. but it was not only the wireless that was working slow. wired connection also showed significant slow speeds.
according to my estimate its like 3 times slower.
there is also xp dual booted in the same machine. speeds were good there.

i am eager to know what is wrong with 9.10. many folks are already switching back to 9.04. :(

---

### Post by Fire_Chief on 2009-11-03
Maxepr,
Can you give us info on your wireless card make/model?
```
lspci
```

---

### Post by BertOlton on 2009-11-03
Fire Chief - I'm seeing the same thing with my hardwire broadband connection.  Huge slow down of Mozilla Browser and Email.  In fact, with both running my machine's locking up repeated.  Also locks up if I run a second tab in browser.  "lspci" output on my machine is:


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

Bert

---

### Post by james_xxx on 2009-11-03
It might be worthwhile to take a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757")

This appears to be affecting a lot of *ubuntu users, and it would appear that little or nothing is being done about it.

---

### Post by olichka on 2009-11-03
Same here, it takes ages to load a page, both wireless and wired.

---

### Post by soupowl on 2009-11-03
I'm having exactly the same problem since upgrading to 9.10 - it has been a good upgrade apart from this.  My other computer, which I haven't upgraded, is working fine.  The upgraded one shows my wireless network connection working at 38%, whereas before it was 100%, so I assume it's something to do with this.   Has any wizard out there got the answer?

---

### Post by Maxepr on 2009-11-04
> **Fire_Chief said:**
> Maxepr,
Can you give us info on your wireless card make/model?
```
lspci
```
Here the info. 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:0b.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

Maxepr

---

### Post by arjuntank on 2009-11-04
i dont have any such issues.
according to the bug at lauchpad, its a dns resolver issue. so i think it should affect every system. 
this is strange.
here is my lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by darco on 2009-11-04
Whats the output of 
```
iwconfig
```



darco

---

### Post by arjuntank on 2009-11-04
> **darco said:**
> Whats the output of 
```
iwconfig
```



darco

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"My_Adhoc_Network"  
          Mode:Ad-Hoc  Frequency:2.422 GHz  Cell: EA:06:20:75:D2:34   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.


```

P.S.
I dont use wireless. I have a DSL wired connection.

---

### Post by amorangi on 2009-11-04
Try Wicd. Network Manager has been broken since 8.04

---

### Post by QwUo173Hy on 2009-11-04
What results are you getting for this command: 

time host localhost

---

### Post by arjuntank on 2009-11-05
> **jarlath said:**
> What results are you getting for this command: 

time host localhost

localhost has address 127.0.0.1
localhost has IPv6 address ::1

---

### Post by Fire_Chief on 2009-11-05
> **Maxepr said:**
> 
00:0b.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
Maxepr

So this chipset is not directly supported in 9.10 as it is older. The madwifi package which would normally be available for this is now removed because it heavily depends on HAL (HAL is now depreciated in favor of udev for hardware detection). I did a quick google about it and found another thread which may offer help.
See here [http://ubuntuforums.org/showthread.php?t=1309072]("http://ubuntuforums.org/showthread.php?t=1309072")

Hope this helps!

---

### Post by Maxepr on 2009-11-06
To all with this same problem. I find it amazing that someone hasn't issued a (real) fix for such a high profile and important part of using a computer. The only certain fix that I have discovered is to move backwards. I have personally surrendered and put 9.04 back on my laptop. Things are good again. 

Maxepr

---

### Post by Phillip Spencer on 2009-11-07
> **james_xxx said:**
> It might be worthwhile to take a look at this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

This appears to be affecting a lot of *ubuntu users, and it would appear that little or nothing is being done about it.

I came to this forum thread - and others about slow internet on Unbuntu 9.10 - having been pointed at bug #417727.  I certainly having been having problems since upgrade earlier this week with three different machines but not just on wireless also on wired connection.  This bug report appears to cover most of the problems I having been having and I recommend anyone having internet delay problems to check it out if you have not already looked at it.

I agree with James_xxx that not enough is being done about the problem... I am not sufficiently technically competent to do the hack work-arounds and I am a) surprised that as this was a known issue in beta testing 9.10 was formally released without a fix given the internet is a major part of the average user's requirement from their system; b) that the bug report is now only "high" not "critical" for the same reason. Ubuntu will never break out of its niche and become a mainstream OS that the average person could use "off the shelf".

---

### Post by mdshaver on 2009-11-08
Although I am still not thrilled with my wifi internet with Karmic, I have found that switching to OpenDNS servers in NetworkManager has vastly improved my internet speed. I have also disabled iPV6 in firefox but not on the system as as whole.

---

### Post by Maxepr on 2009-11-08
To anyone that's reading all this C**P about slow wifi in 9.10. I have followed this link to a thread that has help me:

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

It installs the madwifi drivers for atheros wireless cards. My internet speed had improved considerably. It is still not quite a good as 9.04 was but I can live with it. I was going back to 9.04 but I thought I'd try this first. I had nothing to lose anyway. I will stick with 9.10 for now and hope that whoever realised 9.10 too early will fix it soon. If you don't like the new driver, I have found that you can activate/deactivate them in 'system/administration/hardware drivers.

---

### Post by laerub18 on 2010-02-21
so still no failproof solution ?

---

### Post by QwUo173Hy on 2010-02-22
In my wireless network settings I change 'Automatic DHCP' to 'Automatic (Addresses only) and used googles dns 8.8.8.8 and 8.8.4.4

I think I'm at full speed again.

---

### Post by viper250 on 2010-02-22
strong signal has nothing to do with the speed of a connection.
over the past month due to weather problems connection speeds were slow on many systems.
even in my area we may have had good weather but the site servers may have had poor weather in their areas
while you are surfing the net you are connecting through thousands of server networks.
and all it takes is one poor connection and the systems have to route through another network. all this network searching can slow things down a bit (even more if there is a bottleneck in the network traffic)
changing to a proprietary driver may indeed increase speed a bit because the driver was written specifically for that hardware. 
data compression is the method used for higher speed network communication. for the simple fact of smaller package faster throughput.
consider also network traffic for example: bit torrent when you use bit torrent to download a large file you basically set your computer up as the top of the pyramid and cascade (seed) the same file out to other networks. this can create a tremendous amount of network traffic

---

