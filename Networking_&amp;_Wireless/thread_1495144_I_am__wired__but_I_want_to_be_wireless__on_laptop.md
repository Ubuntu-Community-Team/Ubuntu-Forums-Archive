---
title: "I am  wired  but I want to be wireless  on laptop"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by henry cow on 2010-05-27
This nice new laptop has great native wireless under Windows 7 but can't connect under Ubuntu

thanks for your help.

harry@harry-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
harry@harry-laptop:~$

---

### Post by Iowan on 2010-05-27
**sudo lshw -C network** should provide some information on chipset and driver.
 I presume you've tried with cable unplugged...

---

### Post by henry cow on 2010-05-27
I have tried at least a dozen "solutions" that have been suggested to me here such as ndiswrapper, blacklists, backports, and done everything I can find under Synaptic Package Manager, Ubuntu Software Center, apt-get update, etc, etc,

netrtx64.inf and rt64win7.sys report "Hardware Found" 

The hardware is good because it works great under Windows. 
This is obviously a driver issue of some sort. The laptop is new and the OS installs are clean and new and updated scrupulously.

harry@harry-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f1100000-f110ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:51:d6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=172.16.0.88 latency=0 multicast=yes
       resources: irq:28 ioport:2000(size=256) memory:f1010000-f1010fff(prefetchable) memory:f1000000-f100ffff(prefetchable) memory:f1020000-f102ffff(prefetchable)
harry@harry-laptop:~$ 


does this tell you anything?

---

### Post by v1ad on 2010-05-27
ifconfig 

please post results.

also try the xp .inf file at times the windows vista and 7 does not work great.

---

### Post by henry cow on 2010-05-27
Where can I find an XP driver? The laptop came with everything built in and Windows 7 pre-installed.

What kind of freak puts up junk messages about dead girls?


harry@harry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:51:d6:00  
          inet addr:172.16.0.88  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::226:22ff:fe51:d600/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19156447 (19.1 MB)  TX bytes:1113422 (1.1 MB)
          Interrupt:28 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

harry@harry-laptop:~$

---

### Post by Iowan on 2010-05-27
> **henry cow said:**
> What kind of freak puts up junk messages about dead girls? The kind that end up with jailed posts and/or banned ;)

---

### Post by v1ad on 2010-05-27
Don't know if you tried this. i had a problem with a similar wifi card.
ill look for other solutions post back if it works or not with it. 

```
 sudo apt-get install linux-backports-modules-wireless-lucid-generic 
```

---

### Post by v1ad on 2010-05-27
also do 

```
 sudo apt-get dist-upgrade 
```

newer kernels sometimes support newer wifi cards.

---

### Post by henry cow on 2010-05-27
Vlad - 

thank you for your reply. 

I update regularly, and both of these commands reported that I already have the most recent versions.

All of these techniques have already been tried.

It is perplexing to me that this is so difficult on a clean new machine, I expect problems when running ancient obsolete hardware and software.

---

### Post by v1ad on 2010-05-27
yea that is weird because with the newer builds that wireless type is supported ill keep looking and hopefully by the end of today we can have it up.

---

### Post by v1ad on 2010-05-27
before you do those commands do

```
 sudo apt-get update 
```

---

### Post by v1ad on 2010-05-27
also went to their website and it says this wireless driver is supported for linux.

download link [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

if you need help installing that file let me know and ill walk you through.

just in case check the wifi button :].

also one time i had an issue where i had to literally right click on my network connections and select enable.

also after all this do (ifconfig wlan0 up)

---

### Post by henry cow on 2010-05-28
400 Bad Request

I tried your link, then went to Source Forge (great stuff, used it before) and swam around until I found it myself, then, 400 Bad Request

Is this my box blocking it, or something? I spent a lot of time a few weeks ago trying to get Madwifi and getting it work, and it never did.

---

### Post by v1ad on 2010-05-28
hmm you download the source code for it? big green button. extract it? make ? make install?

[http://sourceforge.net/projects/madwifi/files/madwifi/0.9.4/madwifi-0.9.4.tar.gz/download](http://sourceforge.net/projects/madwifi/files/madwifi/0.9.4/madwifi-0.9.4.tar.gz/download)

---

### Post by henry cow on 2010-05-28
Also, whenever I install linux-backports-modules......

it kills my hard-wired ethernet connection too, besides not working

---

### Post by henry cow on 2010-05-28
Vlad - 

Thanks, I was now able to download Madwifi (via Windows of course, backports killed my ethernet connection in Ubuntu).

I moved the .tar file into my Ubuntu partition and extracted it, to about a dozen files in its own folder.

Now what? How do I access, install, and run what I have?

Thank you for your patience, I am still swimming in water over my head here.

---

### Post by v1ad on 2010-05-28
lol we all where there before.

open up a terminal

now if the folder is in downloads do
```
 cd Downloads 
```
then u find the folder name where the files are extracted
and do
cd thatfoldername

then do
```
 ./configure 
```
if that makes an error just move on to the next step
then do
```
 make 
```
then
```
 sudo make install 
```

and that should compile and insall your drivers

last but not least 
```
 sudo ifconfig wlan0 up 
```

btw did u upgrade to 10.04 instead of a new install? i've seen a lot of wireless issues come that way.

---

