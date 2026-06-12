---
title: "Wired works, wireless does not work. Need help."
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by gmf64 on 2010-01-10
I am quite new to Linux, but I have decided to use it actively this year (2010) and hopefully become familiar with it. I have recently bought a new laptop for this purpose. It is a Toshiba L555D-103. It was pre installed with Windows 7 (64 bit). I have now installed Ubuntu 9.10 (32 bit). 

It works perfectly when wired. But it does not when I try it wireless. It did work wirelessly with Windows 7, and I have many more both stationary and laptops working through the router, so I do not think the router is the problem.

I am guessing that there are no drivers for the wireless to function, but I am not sure. And I am not sure what information you would need from me.

With the "ifconfig" command, I get this:

gaute@backtrack:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:37:03:61  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe37:361/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7781638 (7.7 MB)  TX bytes:833896 (833.8 KB)
          Interrupt:29 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

With the "lspci" command, I get this:

gaute@backtrack:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

I am guessing that there are no drivers for the Ethernet card ?

gmf64

---

### Post by chili555 on 2010-01-10
This may help. Although you don't have a Thinkpad, the wireless device and driver are the same.  [http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II](http://www.thinkwiki.org/wiki/ThinkPad_11b/g/n_Wireless_LAN_Mini-PCI_Express_Adapter_II)

Especially see:> You need to download RTL8192SE driver if your card is identified (by running 'lspci -v') as 'Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)'. 

---

### Post by chandika on 2010-01-10
Try the following link. It may not be the direct answer to your problem but I guess you'll find good information to adapt to your machine.
[https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)

---

### Post by gmf64 on 2010-01-11
Ok. Thanks to both of you. Being new to Linux, a lot of what I  am reading is a little "Greek". But as far as I can see, the Network Card is RTL8172. But what I want is RTL8169 ??? Because this is for the Ethernet Card RTL8101E/RTL8102E ?

Now, if I can find the drivers for this through Linux, I do not have to go through NDIS wrapper. Correct ? Because this is only a way for Windows drivers to comply with Linux.

Am I going to download the RTL8101E/RTL8102E or just the RTL8169 ? Or is the RTL8169 a name for RTL8101E/RTL8102E ? Many questions from my side, but good to know, so I will remember until next time.

Apart from my computer being a Toshiba L555D-103, here is some information I have got through using the terminal. I have taken away everything not having to do with Network and Ethernet Card.

gaute@backtrack:~$ lspci

0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
gaute@backtrack:~$

gaute@backtrack:~$ lspci -nn

0e:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
14:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

gaute@backtrack:~$ sudo lshw -C network
[sudo] password for gaute: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:a000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:37:03:61
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:b000(size=256) memory:f0410000-f0410fff(prefetchable) memory:f0400000-f040ffff(prefetchable) memory:f0420000-f043ffff(prefetchable)

gaute@backtrack:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
    Link detected: yes

gaute@backtrack:~$ lspci -v

0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at a000 [size=256]
    Memory at f0200000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff00
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at b000 [size=256]
    Memory at f0410000 (64-bit, prefetchable) [size=4K]
    Memory at f0400000 (64-bit, prefetchable) [size=64K]
    [virtual] Expansion ROM at f0420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by chili555 on 2010-01-11
Your ethernet has a driver attached and is running and has an IP address:> *-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast [COLOR="Blue"]Ethernet[/COLOR] controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:14:00.0
logical name: [COLOR="Blue"]eth0[/COLOR]
version: 02
serial: 00:26:22:37:03:61
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes [COLOR="Blue"]driver=r8169[/COLOR] driverversion=2.3LK-NAPI duplex=full [COLOR="Blue"]ip=192.168.1.7[/COLOR] latency=0 [COLOR="Blue"][COLOR="Blue"]link=yes [/COLOR][/COLOR]multicast=yes port=MII speed=100MB/sI thought you were trying to get your wireless going...

Your wireless card is an RTL8172:> 0e:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)The link I gave you suggests it works with the Realtek RTL8192SE driver. I am fairly certain it will also work with ndiswrapper. I have heard no feedback yet as to which is preferable. Each method has its complexities, so which do you prefer?

---

### Post by qrazydutch on 2010-01-11
just wondering why install a 32 bit system on a 64 bit platform?
also I am sort of piggybacking on this discussion since I purchased Toshiba Satellite M505D (64 bit) with Win7 (just works fine, however I want to dual or triple boot on my 160 GIG hard drive, plenty of space), so far no wireless driver (s) found, however I appreciate these discussions, great learning for an old mainframe () (that is real BIG computer)) operator  ...still at it.:p

---

### Post by gmf64 on 2010-01-12
I have just got home from my nightshift and will look into it when I wake up. I know I will make mistakes, just trying to prevent the big ones from happening.
 
chili555: I will download the driver. I have looked into the ndiswrapper just incase. There must be thousands of howto manuals. Just haven't found one I am satisfied with yet. I will keep you and others informed.
 
qrazydutch: First of all I am a "Windows person". Being 45, I really don't like learning new things. This includes Linux which I know little about. But I have my Bachelor Project in computers this whole semester which in part involves how "easy or NOT" is it to discover unsecured networks (wardriving), how easy or NOT is it to break the code in WEP and WPA and what does it take to "take" out a bussiness for 5 minutes. The media states anyone can do it. My thesis is to prove them right or wrong.
 
Using Backtrack (at least in the start) and knowing most of these for me still unknown programs work best on Linux, that's why the Linux and computer purchase. I downloaded the Ubuntu version 9.10 and did not see a 64 bit version available. I did see the 64 bit version available with older versions. At the same time, I am not sure the programs I want to use or drivers are all "there" for the Linux 64-bit version.
 
The reason I bought a computer with 64 bit, is that after my Bachelor Project, my wife (there's always a wife taking over your newest goodies) will take over the computer. And she is a photographer and uses the Adobe CS4 package. So the Toshibas's 17 inch screen is not the brightest idea for wardriving, but it will be great for her working on a 17 inch when at the cabin where we have no stationary. She will off course turn
the computer over to Windows 7 again (were the wireless works perfectly).

---

### Post by chili555 on 2010-01-12
This could be very interesting! I don't think we have learned yet if the 8192SE goes into monitor mode and does injection! We will all learn together.

---

### Post by prodigal on 2010-01-14
Well I'm not entirely sure exactly what is causing this, but it may well be what chili555 just said. I've followed the couple of tutorials around for this, on a not so fresh install (A few days old with some updates using a CAT5 cable, then trying to install wireless) and now on a fresh install (Brand new 64bit install with the CD, first boot make and make install etc, then reboot) after rebooting, I run apt-get update, it works on wireless, I run apt-get dist-upgrade and it freezes during the get part of the process and flakes out, wireless does not come back until a reboot.

I'm currently updating the machine with a cable installed and the driver pre-compiled and hopefully will get re-compiled/update with the kernel upgrade that is about to happen via apt-get dist-upgrade, we will see how it goes, but I am not holding out much hope, as this is basically what happened before.

---

### Post by prodigal on 2010-01-15
This did not help, and in fact on booting up it threw a kernel panic instead and now just won't boot. I know I can rectify this by logging in with a livecd, mounting the partition and deleting the module, but I have done this before and until the problem is solved, this laptop is going to have to run Vista or 7, which upsets me VERY much, so has anyone else got a possible solution?

The laptop is a Toshiba Satelite L500D with a Realtek 8172 Wireless adapter in it. The procedure for the 8192 works, then half way through the wireless connection just plain dies, then on reboot, kernel panic, and I know if I removed the module using a livecd, knetworkmanager will bug out on every boot, because that happened last time.

Please someone give me an idea here so I don't have to reload this with Vista or 7, because we HATE windows, this is my partners laptop, she's had enough of XP, doesn't want Vista, and we don't feel much love for 7 either.

---

### Post by chili555 on 2010-01-15
Can you confirm that you built the 64-bit driver, and not the 32-bit? Did 'make' proceed without any errors? 'make install' as well?

Before I installed Windows, I'd try re-installing Ubuntu first, updating the install fully via ethernet and then do the 8192 compile. Be sure you get the latest 64-bit file.

---

### Post by prodigal on 2010-01-16
Yup can definitely confirm that it was the 64bit driver and not 32. make and make install went flawlessly, there is no error during install, simply a wireless crash after about 2 - 3 minutes of first usage, then a complete refusal to boot after that, with a Kernel Panic around the time of the automatic Module Loading for Wireless.

Unfortunately this is my partners laptop, she wants it back and working, like NOW, I can't stand the thought of having to use Windows on that laptop, while trying to dual boot with Ubuntu and fix the Wireless issue, while giving her my laptop to use in the mean time, I'd rather just stick Win 7 90 day trial on it until we get back to England (We're flying from NZ to England for good on Feb 13th) then hopefully in a month or two's time this driver will be working a little better, then she can use Windows (Which she's not happy about, but not as unhappy as I'd be using Win 7 or Vista) and I can continue to use my Linux only HP nx9420.

If we weren't flying soon, and still had a desktop etc then none of this would be a problem, the laptop could be useless for another couple of months while trying to sort this out, but for the next couple of months, our laptops are the only systems we have.

---

### Post by nathanieldouglas on 2010-01-16
Yeah we should be careful not to hijack anything, but I've got some really similar reports from those commands and am having very similar problems.  The only thing is that for the command sudo ethtool eth0 I am getting "Link detected: no" where yours is "yes" and "Duplex:Half" where your is "Full" ... 

I can't get the wired to connect at all so it's sort of stranded ... 

How do we get a driver in to support the UNCLAIMED Broadcom controller - I noticed that for yours too actually, the Realtek driver sounds like a good fix, but it's the Broadcom Network Controller that needs the driver (hence the UNCLAIMED that it reports).  So I doubt the Realtek thing is worth the hassle.  Am I wrong?

---

### Post by chili555 on 2010-01-16
> **nathanieldouglas said:**
> Yeah we should be careful not to hijack anything, but I've got some really similar reports from those commands and am having very similar problems.  The only thing is that for the command sudo ethtool eth0 I am getting "Link detected: no" where yours is "yes" and "Duplex:Half" where your is "Full" ... 

I can't get the wired to connect at all so it's sort of stranded ... 

How do we get a driver in to support the UNCLAIMED Broadcom controller - I noticed that for yours too actually, the Realtek driver sounds like a good fix, but it's the Broadcom Network Controller that needs the driver (hence the UNCLAIMED that it reports).  So I doubt the Realtek thing is worth the hassle.  Am I wrong?Please start a new thread. You evidently have a Broadcom wireless and he has a Realtek. His fix, when it comes, will probably be inapplicable to your Broadcom. In your new thread, please post:```
sudo lshw -C network
```

---

### Post by chili555 on 2010-01-16
> simply a wireless crash after about 2 - 3 minutes of first usage, then a complete refusal to boot after that, with a Kernel Panic around the time of the automatic Module Loading for Wireless.Very weird! Please let us see:```
sudo cat /var/log/messages | grep 8192
sudo cat /var/log/messages | grep wlan0
```Substitute your wireless interface, if it's not wlan0. Find out with:```
iwconfig
```Thanks.

---

### Post by gmf64 on 2010-01-17
I wish I could say that I know how to solve the problem. But I don't. What I can say is that the problem is resolved. Someone I know which does know Linux pretty well fixed my wireless. What he did is hard to say and it wasn't very easy to follow along.

Device 8172 is correct. And RTL8101E/RTL8102E are both correct. He did download the drivers from the Realtek page. One more thing I can say is this. NDISwrapper is not needed. And if NDISwrapper is installed on the laptop, it has to be uninstalled before the drivers are downloaded. Do not ask me why.

Next time I talk to him, I will have him go through it with me, and maybe I can come up with a recepy on how it is done. Now it is time to go on the Ubuntu forum and ask my next question.

---

### Post by prodigal on 2010-01-20
Hi Chilli, I'll have to wait until I get back to England now, the machine was re-installed with Win 7 so my partner could use it and get some work done in the next week or so. Once we get back to the UK (Feb 13th), we won't have to worry about the STUPID 3GB download limit we have in this house (NZ Sucks for bandwidth limits) nor the 50Kbps download speeds we get here either.

I'll re-install 9.10 when we get back, download the stuff I need to and go from there. Thanks for your help so far.

---

### Post by chili555 on 2010-01-20
I will look forward to helping you get going! Have a safe trip.

---

### Post by prodigal on 2010-01-21
Well now, I've found the driver for 8192, as gmf64 suggested on the realtek website. Unfortunately as the machine is currently running Windows 7 and we have limited bandwidth here I'm not going to get time to check it out now :( 

I'm also a little unsure about the compatibility, the only driver available says nothing about whether it is 32 or 64bit, can anyone else confirm this works with 64bit Linux, before I waste more time installing it later on?

---

### Post by chili555 on 2010-01-21
I believe the 64-bit version is clearly identified; for example: rtl8192se_linux_2.6.0010.1012.2009_[COLOR="Red"]64bit[/COLOR].tar.gz or similar.

---

### Post by mr clark25 on 2010-01-21
have you tried checking out the BIOS on the laptop?
you should be able to press a key to enter setup when you first turn it on.

you must have the wireless (WLAN) turned on or enabled. windows has some sneaky way around it (or so i hear), nut Ubuntu doesn't. i had the same problem with a desktop computer when i put in a new wireless card. i fixed it by changing some functions in the bios,

when in the BIOS, dont change things if you dont know what they are.

---

### Post by prodigal on 2010-01-21
Well, if I didn't know what a bios option was I'd be worried, I'm paid to know, but thanks for the suggestion Mr Clark.

As for the driver, I assumed they would be different, for 32 and 64 and be clearly marked, but these days, even 32 bit drivers are usually marked in the readme file, the name of the zip file, or on the website you download it from, this has absolutely no mention of either 32 or 64 bit anywhere, in any document.

I guess I'll just have to wait and see. Things will be much much easier once we're home and back in our own house again, with decent internet and therefore more resources available to try and fix the issue.

EDIT:

I just had a dig around and found this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all)

it seems this series of drivers from realtek directly are multi-arch, so, odd as that seems, I'll give it a try, see if it will compile and load in a live cd, then see what happens from there.

RE-EDIT:

I got bored, booted the Toshiba Satelite L500-D with the Realtek 8172 Wireless card into Kubuntu 64bit Karmic, plugged in a USB stick that had the latest Linux driver for the wireless card, provided by Realtek themselves, on their download site, simply search for 8192 and you'll get the driver. It is not labelled as 32 or 64 bit specific, but it definitely works on 64bit, so I'd assume, since it isn't labelled 64bit, it should work on 32 bit systems as well.

I now have to convince my partner to let me re-install this laptop with Kubuntu Karmic 64 bit again, but I doubt she'll let me until we get back to the UK because of the pathetic download limit we have here in NZ. All is well though, I now know for sure, the laptop CAN run Karmic and Wireless and work perfectly.

Cheers

---

### Post by soad6 on 2011-03-09
was wondering if someone could help get my rtl8192SE wifi card into monitor mode. When I run the command sudo airmon-ng start wlan0 i get this: 
needlez@needlez-Satellite-A505:~$ sudo airmon-ng start wlan0
[sudo] password for needlez: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID  Name
1029  avahi-daemon
1030  avahi-daemon
1179  NetworkManager
1218  wpa_supplicant
16302  dhclient
Process with PID 16302 (dhclient) is running on interface wlan0


Interface  Chipset    Driver

wlan0    Unknown   rtl819xSE - [phy0]mon0: ERROR while getting interface flags: No such device

        (monitor mode enabled on mon0)

----------------------------
Im open to trying anyway to get this to do monitor mode, then if maybe it could injection that'd be perfect. Any help apperciated. thanks

---

### Post by soad6 on 2011-03-09
ok, so i got it to go into monitor mode, by doing this. Kill all process that are giving issues, dhclient, network-manager, wpa_supplicant, avahi-daemon. then sudo iwconfig wlan0 mode monitor
sudo airodump-ng wlan0
---------------------------
however after this is done it shows its in monitor mode, just it shows 0 pwr so not sure what thats about? or if I can fix this card to support injection. Any ideas would be helpful. thanx

---

### Post by qrazydutch on 2011-09-19
> **gmf64 said:**
> I have just got home from my nightshift and will look into it when I wake up. I know I will make mistakes, just trying to prevent the big ones from happening.
 
chili555: I will download the driver. I have looked into the ndiswrapper just incase. There must be thousands of howto manuals. Just haven't found one I am satisfied with yet. I will keep you and others informed.
 
qrazydutch: First of all I am a "Windows person". Being 45, I really don't like learning new things. This includes Linux which I know little about. But I have my Bachelor Project in computers this whole semester which in part involves how "easy or NOT" is it to discover unsecured networks (wardriving), how easy or NOT is it to break the code in WEP and WPA and what does it take to "take" out a bussiness for 5 minutes. The media states anyone can do it. My thesis is to prove them right or wrong.
 
Using Backtrack (at least in the start) and knowing most of these for me still unknown programs work best on Linux, that's why the Linux and computer purchase. I downloaded the Ubuntu version 9.10 and did not see a 64 bit version available. I did see the 64 bit version available with older versions. At the same time, I am not sure the programs I want to use or drivers are all "there" for the Linux 64-bit version.
 
The reason I bought a computer with 64 bit, is that after my Bachelor Project, my wife (there's always a wife taking over your newest goodies) will take over the computer. And she is a photographer and uses the Adobe CS4 package. So the Toshibas's 17 inch screen is not the brightest idea for wardriving, but it will be great for her working on a 17 inch when at the cabin where we have no stationary. She will off course turn
the computer over to Windows 7 again (were the wireless works perfectly).

Appreciate that whoever claims to be qrazydutch, to stop. next violation will be reported...your age is wrong and all the other things of a personal nature are totally off...

---

