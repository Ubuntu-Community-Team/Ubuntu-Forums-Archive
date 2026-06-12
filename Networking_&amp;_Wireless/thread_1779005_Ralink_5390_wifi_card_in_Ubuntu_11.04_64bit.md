---
title: "Ralink 5390 wifi card in Ubuntu 11.04 64bit"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by thegrooviest1 on 2011-06-09
Ok I am totally new, I haven't got the foggiest idea how to install the driver **Ralink 5390 wifi card in Ubuntu.  I have it downloaded but I have no idea what to do or how to use terminal. I have done a few things in terminal but really I'm lost and want to really learn as much as I can about Linux and how to use it. I need step by step instructions, I'm real sorry if I sound stupid I just don't know how to install the driver. Thanks for understanding.****Ok I am totally new, I haven't got the foggiest idea how to install the driver ****[B]Ralink 5390 wifi card in Ubuntu.  ****I  have it downloaded but I have no idea what to do or how to use  terminal. I have done a few things in terminal but really Im lost and  want to really learn as much as I can about linux and how to use it. I  need sttep by step instructions, im real sorry if I sound stupid I just  don't know how to install the driver. Thanks for understanding.**[/B]
[B]
I downloaded it and extracted the driver in documents folder, im used to windows having a exe but this is all new to me. Like I said I need step by step as far as terminal I have a hp G62x  64bit.

Thanks again for anyone's help or could point me in the right direction of some website for new people to understand more about linux.
[/B]

---

### Post by chili555 on 2011-06-10
**EDIT! EDIT! EDIT!**
[COLOR="Red"]There is now a later version of the RT5390 driver called 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO. The patches discussed below are no longer required and you may skip those steps. Please see post #58 below. [/COLOR]
**EDIT! EDIT! EDIT!**

Mr. Stepbystep is here to help. I assume you have downloaded the driver file in the folder called Documents. If you haven't extracted it already, the open the Documents folder and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed. Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' Make these changes: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' Proofread carefully, save and close leafpad.

Now go here:  [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patch files. Check carefully because you need every one. Wherever they get downloaded, drag and drop them into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder inside your Documents folder. 

Now we will work in the terminal. Open a terminal and we will change directories to where all our files are located:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```Now, we will apply all the patches:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patch -p0 < rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```If, at any time, you get stuck or have a question, post back. If you get warnings in the 'make' stage, that's acceptable, errors are not. Any time you get an error, stop and ask me. I will be watching the forum actively for your replies.

EDIT: Note to searchers. When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:
```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su 
make clean 
make
make install
modprobe rt5390sta
exit
```

As always, post back if we can help you further.

---

### Post by thegrooviest1 on 2011-06-10
So Far so good, I did get warnings but no errors this time. Is this all I need to do or is there more steps to take? I guess what I'm asking is what next, should I see if it worked?

---

### Post by chili555 on 2011-06-10
When you click the Network Manager icon, do you see networks? Can you click yours and connect?

---

### Post by thegrooviest1 on 2011-06-10
I haven't tried, when I try to close terminal it says this terminal has a process still running and are you sure you want to close, will it kill all the stuff I patched or is there something I should do to exit and have it all saved?

---

### Post by chili555 on 2011-06-10
> **thegrooviest1 said:**
> I haven't tried, when I try to close terminal it says this terminal has a process still running and are you sure you want to close, will it kill all the stuff I patched or is there something I should do to exit and have it all saved?Tsk, tsk! Did you forget the last command?```
exit
```Then you can close the terminal with ease and the confidence of a newly hardened Linux geek.

---

### Post by thegrooviest1 on 2011-06-10
I did forget to exit, It still doesn't show any wireless connections and only shows for wired network, theres not option for wireless at all.

---

### Post by thegrooviest1 on 2011-06-10
Now I might be wrong but after following your instructions did that install the driver or just the patches and was there more I should have done? Is there a way to see if the driver installed?

I appreciate your patient's.

---

### Post by chili555 on 2011-06-10
Let's go back to basics. Do you actually have a 5390 card? Please run and post:```
lspci -nn
```

EDIT: Sorry for the mis-step.

---

### Post by thegrooviest1 on 2011-06-10
~$ lsusb
Bus 002 Device 004: ID 04f2:b1aa Chicony Electronics Co., Ltd Webcam-101
Bus 002 Device 003: ID 125f:0000 A-DATA Technology Co., Ltd. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

But this shows after _sudo ifconfig_

eth0      Link encap:Ethernet  HWaddr 98:4b:e1:b9:1b:37  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9a4b:e1ff:feb9:1b37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5055312 (5.0 MB)  TX bytes:817643 (817.6 KB)
          Interrupt:40 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85292 (85.2 KB)  TX bytes:85292 (85.2 KB)

---

### Post by chili555 on 2011-06-10
Sorry about that! I meant:```
lspci -nn
```

---

### Post by thegrooviest1 on 2011-06-10
sorry I didn't get the nn last time


:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

---

### Post by thegrooviest1 on 2011-06-10
Darn, I did what you said all over and this time it worked and awareness of my card and network was instant. I couldn't have done it without you Chili555. These are nothing to the problems I have faced with windows, I'm beginning to really like Linux and I really do appreciate all your help. Thanks again!

---

### Post by chili555 on 2011-06-10
Deleted.

---

### Post by chili555 on 2011-06-10
> **thegrooviest1 said:**
> Darn, I did what you said all over and this time it worked and awareness of my card and network was instant. I couldn't have done it without you Chili555. These are nothing to the problems I have faced with windows, I'm beginning to really like Linux and I really do appreciate all your help. Thanks again!Oh, well, great! Getting the wireless going is generally the highest hurdle new users face. It's all pretty simple from here on.

Have fun!

---

### Post by thegrooviest1 on 2011-06-10
I think I messed up when it asked for my password, thats when I exited..I'm a real goof! I love when things work out, and again, thanks chili  :D

---

### Post by ratibars on 2011-06-10
[SIZE=4]**chili555**[/SIZE], I badly need your help. I have been struggling with wireless disconnection problem for a long time. It will randomly disconnect particularly while I'm watching youtube videos. Got a MSI PC60G card.


Looking at your other replies I have added a these items to the blacklist.conf file. But it still doesn't seem to solve the issue:

blacklist rt2800pci
blacklist rt2x00usb
blacklist rt3390sta
blacklist rt2860sta
blacklist rt2800lib

And here are some commands' results:

[SIZE=3]**lspci -v | less**[/SIZE]

03:07.0 Network controller: RaLink RT2561/RT61 802.11g PCI
        Subsystem: Micro-Star International Co., Ltd. Device b834
        Flags: bus master, slow devsel, latency 32, IRQ 21
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci


**[SIZE=3]sudo lshw -C network[/SIZE]**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:dd:20:a1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:8c:53:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.0.101 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcf7fff

[SIZE=3]**sudo lshw -C network**[/SIZE]
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:dd:20:a1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdae0000-fdaeffff memory:fda00000-fda0ffff
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 00
       serial: 00:24:21:8c:53:f2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.38-8-generic firmware=0.8 ip=192.168.0.101 latency=32 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:fdcf0000-fdcf7fff

**[SIZE=3]lsmod | grep rt2[/SIZE]**
rt2x00pci              13986  1 rt61pci
rt2x00lib              39075  2 rt61pci,rt2x00pci
mac80211              257001  2 rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

[SIZE=3]**iwconfig**[/SIZE]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"kanini"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:BF:0E:6D   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:287   Missed beacon:0

---

### Post by chili555 on 2011-06-10
@ratibars--

You have a completely different device from the subject of this thread. Please start a new thread and reference rt61pci. If I don't catch it right away, send me a private message by clicking my user name and selecting 'Send PMS to chili555' or whatever it says.> blacklist rt2800pci
blacklist rt2x00usb
blacklist rt3390sta
blacklist rt2860sta
blacklist rt2800libMan! You blacklisted everything in sight!

---

### Post by snsfene on 2011-06-20
im not sure you check this anymore, but i jus wanted to say thank you soooooooooooooo much for helping me!!!!! countless hours on this issue and this is the only solution that has helped! you truly are a life saver!!!! much appreciation! new to linux and loving it!:KS

---

### Post by chili555 on 2011-06-20
I check. I appreciate your kind comments. Have fun!

---

### Post by JimmyI on 2011-06-23
chili555 I'm afraid I need your help too. The link you have given for the patches doesn't seem to work for me. 

I use the follwing link but only get a 500 internal server error.

[https://build.opensuse.org/package/files?package=rt5390shttps://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awirelessta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390shttps://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awirelessta&project=driver%3Awireless)

---

### Post by chili555 on 2011-06-23
> **JimmyI said:**
> chili555 I'm afraid I need your help too. The link you have given for the patches doesn't seem to work for me. 

I use the follwing link but only get a 500 internal server error.

[https://build.opensuse.org/package/files?package=rt5390shttps://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awirelessta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390shttps://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awirelessta&project=driver%3Awireless)It works for me. Are you in the USA or ... where? I'd think if I can get it in the backwoods of South Cackalacky, you could get it anywhere. Our internet runs on burning corncobs!

Be sure to get and use the x86_64 patch only if you have an x86_64 kernel.

If you still can't get it, PM me your email address and we'll see what we can do.

---

### Post by JimmyI on 2011-06-23
Im in the UK, but I've just tried it again and it has worked. I'll have to try your fix tomorrow. Thanks for getting back so quickly!!!!

---

### Post by chili555 on 2011-06-23
Post back if you need some additional help. I guess their site was not running Ubuntu and so it was on and off!

---

### Post by JimmyI on 2011-06-25
It worked a treat! Thank you very much Chilli. I've been on ubuntu for 4 years now but a simple step by step guide makes life so much easier. For anyone who is interested I'm on a HP G62 laptop. The general wireless card for this laptop seems to be a Broadcom one so just beware that they also ship with ralink cards.[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10973667](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10973667)

---

### Post by smithees on 2011-06-25
all the files that i need is in this link right?
[https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

then after that, i just have to follow chilli's steps? :D thanks

---

### Post by chili555 on 2011-06-25
> **smithees said:**
> all the files that i need is in this link right?
[https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

then after that, i just have to follow chilli's steps? :D thanksRight. Post back if you get stuck; I'm subscribed to the thread and will see your replies.

---

### Post by smithees on 2011-06-25
thanks man! i got it working flawlessly. i've been finding solutions since yesterday. lol. anyways thanks!

i really didn't check if i had the Ralink 5390 wifi card, but i actually remembered looking in Device Managers in Windows a while ago, so the thread title just struck me. anyway, just for peace of mind, would you mind checking if i have the same card, and if i did the correct thing by following this thread? (well, the internet is running, so it did work. but this is just for the a peace of mind. :D)
> 
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6740]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
0d:00.0 Network controller [0280]: Ralink corp. Device [1814:539f]
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
19:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

---

### Post by chili555 on 2011-06-25
> i really didn't check if i had the Ralink 5390 wifi card,Call me irresponsible, but I feel that it's always good to check first.> 0d:00.0 Network controller [0280]: Ralink corp. Device [[COLOR="Red"]1814:539f[/COLOR]]In fact, your device is claimed by rt5390sta:```
$ modinfo rt5390sta | grep -i 539f
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]539F[/COLOR]sv*sd*bc*sc*i*
```So I say, go for it! Hammer down! Mat it!

---

### Post by smithees on 2011-06-25
ahh thanks! so i was looking at the correct line. :KS haha i was comparing mine and thegrooviest1's network controller, and his said:

> 
02:00.0 Network controller [0280]: Ralink corp. Device [1814:[COLOR=Red]5390[COLOR=Black]][/COLOR][/COLOR]

and mine said:

			 				> 0d:00.0 Network controller [0280]: Ralink corp. Device [[COLOR=Red][COLOR=Black]1814:[/COLOR]539f[/COLOR]] 			 		

so i was assuming it was the wrong card or something. thanks for checking and for the clear step by step instruction. it really helped me. (just started using ubuntu. i just installed 11.04 yesterday) :)

---

### Post by chili555 on 2011-06-25
> **smithees said:**
> ahh thanks! so i was looking at the correct line. :KS haha i was comparing mine and thegrooviest1's network controller, and his said:



and mine said:

			 				

so i was assuming it was the wrong card or something. thanks for checking and for the clear step by step instruction. it really helped me. (just started using ubuntu. i just installed 11.04 yesterday) :)There are several different devices with the same chipset; they all should work with the same driver. I have been dragged out to lunch with Mrs. Chili; back in a few...```
$ modinfo rt5390sta 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt5390sta.ko
description:    RT5390 Wireless Lan Linux Driver
license:        GPL
version:        2.4.0.4
srcversion:     898106B377DB27C956ED4B8
alias:          pci:v00001814d0000[COLOR="Red"]5392[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001814d0000[COLOR="Red"]539F[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001814d0000[COLOR="Red"]5390[/COLOR]sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```

---

### Post by tomihau on 2011-06-26
> **chili555 said:**
> Mr. Stepbystep is here to help. I assume you have downloaded the driver file in the folder called Documents. If you haven't extracted it already, the open the Documents folder and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed. Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' Make these changes: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' Proofread carefully, save and close leafpad.

Now go here:  [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patch files. Check carefully because you need every one. Wherever they get downloaded, drag and drop them into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder inside your Documents folder. 

Now we will work in the terminal. Open a terminal and we will change directories to where all our files are located:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```Now, we will apply all the patches:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patch -p0 < rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```If, at any time, you get stuck or have a question, post back. If you get warnings in the 'make' stage, that's acceptable, errors are not. Any time you get an error, stop and ask me. I will be watching the forum actively for your replies.

I fight 2 days in my CQ56 and wireless problem, then I found this and this solve my problem. 

Many thanks for You chili555 - "Natty" RULES !!!

---
Tomi

---

### Post by admaris on 2011-06-26
:KS> **chili555 said:**
> Mr. Stepbystep is here to help. 

The only solution that worked on my HP Pavilion 6g with Ubuntu 11.04 (in parallel wih Windows 7) and the network device: Ralink Corp Device 539f.

I had to do one extra step to get an active network: restart after configuring a new Wireless Device.

With many, many thanks!

---

### Post by chareen on 2011-06-28
Hi chili555,

I followed the steps you suggested and now my HP works too. Thanks alot.

cheers
chareen

> **chili555 said:**
> Oh, well, great! Getting the wireless going is generally the highest hurdle new users face. It's all pretty simple from here on.

Have fun!

---

### Post by chili555 on 2011-06-28
@chareen, admaris, tomihau and smithees--

Thanks to you all for your very kind comments. You make my day! I hope you are all enjoying your Ubuntu experience.

---

### Post by joebuirski on 2011-06-29
thanks chili555  from me too!! awesome stuff.

---

### Post by RochJer on 2011-06-29
Hello Chili555 - I have posted in several threads regarding my wireless connection issue - I did the rfkill unblock all, and now no more blocks but on my top right for network applet or what I call it - network lists - it doesn't even show wireless devices in sight, only eth0 wired connection. How do I get wireless to show up again ? 

Thanks.

---

### Post by chili555 on 2011-06-29
> **RochJer said:**
> Hello Chili555 - I have posted in several threads regarding my wireless connection issue - I did the rfkill unblock all, and now no more blocks but on my top right for network applet or what I call it - network lists - it doesn't even show wireless devices in sight, only eth0 wired connection. How do I get wireless to show up again ? 

Thanks.Do you have a Ralink 5390? Did you compile and patch and all above? If not, please start a new thread.

---

### Post by MotherMonster on 2011-07-01
Oh my god thankyou so much it literally took me 7 hours to get to this thread

---

### Post by utamore on 2011-07-01
chili--I am having a similar problem with different hardware.  If you would be so kind as to lend me your help on this, I would be forever grateful:

[http://ubuntuforums.org/showthread.php?t=1794360](http://ubuntuforums.org/showthread.php?t=1794360)

---

### Post by talal88 on 2011-07-02
Got my dm1z today and the fist thing I did was delete Windows 7 and install Ubuntu 11.04. Was a little sad when the wireless wasn't working, but this fix worked like a charm! In fact, I'm posting this using the wireless!

Thanks! I really appreciate all the hard work you guys do.

---

### Post by tuckernet on 2011-07-07
Thank you for posting this help.

Unfortunately, I did not succeed.  I have confirmed 5390 is present.
Followed your instructions, and found some differences.

"Please open the folder os and then linux and right-click the file  config.mk. Select 'Open with Leafpad.' Make these changes: set  'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'  Proofread carefully, save and close leafpad."

I open the config.mk with "Text Editor", as "Leafpad" is not available.
The "HAS....." lines are as you suggest, so I did not edit.  

Later, after entering "sudo su", it asks for user password.  I enter password,
although I do not see any characters appear.  I hit enter.  "PO#" is displayed.
I was not expecting this, but continued with your instructions, all the way to "Exit".

Wireless does not work.  Any thoughts?

---

### Post by chili555 on 2011-07-07
Let's do some diagnostics. Please run:```
lsmod | grep rt5 > tuckernet.txt
dmesg | grep -i rt5 >> tuckernet.txt
rfkill list all >> tuckernet.txt
```The pipe symbol | is on the right side of my US keyboard on the same key with \. You will find the text file tuckernet.txt in your user directory. Transfer it on a USB key or, if possible, hook up an ethernet connection and post it here.

---

### Post by tuckernet on 2011-07-07
im@ubuntu:~$ lsmod | grep rt5
rt5390sta            1047040  0 
im@ubuntu:~$ dmesg | grep -i rt5
[   16.911990] rt5390 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.912036] rt5390 0000:02:00.0: setting latency timer to 64
im@ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
im@ubuntu:~$

---

### Post by chili555 on 2011-07-07
How about:```
lspci -nn | grep 0280
```Thanks.

---

### Post by TubaDaddy8 on 2011-07-08
I am in a similar situation in that I am new to Linux.  I am also trying to install a wireless driver, but mine is for the Ralink 5370 USB wireless adapter.  Do you have some patches for that driver, and could you show me how to install the driver?  Thanks!

---

### Post by theDunkel on 2011-07-08
> **chili555 said:**
> Mr. Stepbystep is here to help. I assume you have downloaded the driver file in the folder called Documents. If you haven't extracted it already, the open the Documents folder and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed. Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' Make these changes: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' Proofread carefully, save and close leafpad.

Now go here:  [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patch files. Check carefully because you need every one. Wherever they get downloaded, drag and drop them into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder inside your Documents folder. 

Now we will work in the terminal. Open a terminal and we will change directories to where all our files are located:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```Now, we will apply all the patches:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patch -p0 < rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```If, at any time, you get stuck or have a question, post back. If you get warnings in the 'make' stage, that's acceptable, errors are not. Any time you get an error, stop and ask me. I will be watching the forum actively for your replies.

EDIT: Note to searchers. When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:
```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su 
make clean 
make
make install
modprobe rt5390sta
exit
```

As always, post back if we can help you further.

i've follow it step by step, but i get errors:
```
make[1]: Entering directory `/lib/modules/2.6.38-8-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-8-generic-pae/build'
make: *** [LINUX] Error 2

```

---

### Post by chili555 on 2011-07-08
> **theDunkel said:**
> i've follow it step by step, but i get errors:
```
make[1]: Entering directory `/lib/modules/2.6.38-8-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-8-generic-pae/build'
make: *** [LINUX] Error 2

```Before you started, did you install build-essential and linux-headers-generic?

---

### Post by chili555 on 2011-07-08
> **TubaDaddy8 said:**
> I am in a similar situation in that I am new to Linux.  I am also trying to install a wireless driver, but mine is for the Ralink 5370 USB wireless adapter.  Do you have some patches for that driver, and could you show me how to install the driver?  Thanks!Happy to help. Please start a new thread and reference rt5370sta in the title and include the results of these terminal commands in your post:```
lsusb
uname -r
```Be sure you also install build-essential and linux-headers-generic in Synaptic. Leave a link here and I'll be right there.

---

### Post by tuckernet on 2011-07-08
> **chili555 said:**
> How about:```
lspci -nn | grep 0280
```Thanks.


02:00.0 Network controller [0380]: Ralink corp. device[1814: 5390]

---

### Post by TubaDaddy8 on 2011-07-08
Ok I made a new thread.  Here is the link: [http://ubuntuforums.org/showthread.php?p=11027446#post11027446](http://ubuntuforums.org/showthread.php?p=11027446#post11027446)

---

### Post by beercz on 2011-07-09
> **chili555 said:**
> Mr. Stepbystep is here to help. I assume you have downloaded the driver file in the folder called Documents. If you haven't extracted it already, the open the Documents folder and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed. Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' Make these changes: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' Proofread carefully, save and close leafpad.

Now go here:  [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patch files. Check carefully because you need every one. Wherever they get downloaded, drag and drop them into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder inside your Documents folder. 

Now we will work in the terminal. Open a terminal and we will change directories to where all our files are located:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```Now, we will apply all the patches:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patch -p0 < rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```If, at any time, you get stuck or have a question, post back. If you get warnings in the 'make' stage, that's acceptable, errors are not. Any time you get an error, stop and ask me. I will be watching the forum actively for your replies.

EDIT: Note to searchers. When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:
```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su 
make clean 
make
make install
modprobe rt5390sta
exit
```As always, post back if we can help you further.

Thanks for this chili555 - your solution worked like a charm on my brand new HP Pavillion cv6-6004sa laptop, which has the RALink Corp 539f Wireless Device.

Much appreciated!

---

### Post by RiverHorse64 on 2011-07-19
Dr. Chilli555; a great [SIZE=4]BIG[/SIZE] [SIZE=4]THANK YOU! [/SIZE]

After four days of wandering around dazed and confused, weeding through incomplete and confusing non-working "fixes" for my deadbeat Ralink wireless card, you have once again cured what's ailing my enjoyment of newly discovered Ubu!  I can now see at least seven WiFi networks...only one is mine though.   I am gleefully pushing that other OS deep into the murky sludge from which it came.  :lolflag:

Thank you again.  If it weren't for you, I'd still be wandering around tethered to an Ethernet outlet.

Stay cool, I know those S.C. summer days can be brutal.

Drew

---

### Post by chili555 on 2011-07-19
I appreciate your kind comments. I'm very glad it's working. Your appreciation and *two* big AC units sucking down that pure Duke nuclear energy make summer pretty nice!

---

### Post by ATMOS_SKY on 2011-08-05
Ubuntu 10.04.3 (fresh install) with one synaptic-pack manager update complete. (the update did install the latest kernel)

I have read this thread thoroughly and am impressed with Chili

My hardware is:
01:00.0 Network controller [0280]: RaLink Device [1814:5390]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

So I hope this thread applies to me

I have followed Chili's instructions to the letter and now I am getting a response I do not know what to do with.

Please assist:

```
~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ la -la
total 952
drwxr-xr-x 8 myusername myusername   4096 2011-08-05 09:36 .
drwx------ 3 myusername myusername   4096 2011-08-05 09:41 ..
-rw-r--r-- 1 myusername myusername 620292 2011-08-05 09:20 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.tar.xz
drwxr-xr-x 2 myusername myusername   4096 2011-06-22 03:32 chips
drwxr-xr-x 2 myusername myusername   4096 2011-06-22 03:32 common
drwxr-xr-x 5 myusername myusername  12288 2011-06-22 03:28 include
-rw-r--r-- 1 myusername myusername  14819 2011-06-22 03:28 iwpriv_usage.txt
-rw-r--r-- 1 myusername myusername  13637 2011-08-05 09:28 Makefile
-rw-r--r-- 1 myusername myusername  13637 2011-08-05 09:28 Makefile.orig
-rw-r--r-- 1 myusername myusername   3179 2011-08-05 09:36 Makefile.rej
drwxr-xr-x 3 myusername myusername   4096 2011-06-21 14:42 os
-rw-r--r-- 1 myusername myusername    104 2011-08-05 09:19 preamble
-rw-r--r-- 1 myusername myusername  13366 2011-06-22 03:28 README_STA_pci
-rw-r--r-- 1 myusername myusername    613 2011-06-22 03:28 RT2860STACard.dat
-rw-r--r-- 1 myusername myusername   1124 2011-06-22 03:28 RT2860STA.dat
-rw-r--r-- 1 myusername myusername   3811 2011-08-05 09:19 rt5390sta-2.5.0.3-config.patch
-rw-r--r-- 1 myusername myusername    504 2011-08-05 09:19 rt5390sta-2.5.0.3-convert-devicename-to-wlanX.patch
-rw-r--r-- 1 myusername myusername    582 2011-08-05 09:19 rt5390sta-2.5.0.3-gcc-warnings-x86_64.patch
-rw-r--r-- 1 myusername myusername    540 2011-08-05 09:19 rt5390sta-2.5.0.3-reduce_debug_output.patch
-rw-r--r-- 1 myusername myusername    589 2011-08-05 09:18 rt5390sta-2.5.0.3-remove_date_time.patch
-rw-r--r-- 1 myusername myusername   2766 2011-08-05 09:18 rt5390sta-2.5.0.3-remove-potential-conflicts-with-rt2860sta.patch
-rw-r--r-- 1 myusername myusername    382 2011-08-05 09:18 rt5390sta-2.5.0.3-return_nonvoid_function.patch
-rw-r--r-- 1 myusername myusername    623 2011-08-05 09:18 rt5390sta-2.5.0.3-WPA-mixed.patch
-rw-r--r-- 1 myusername myusername   1158 2011-08-05 09:18 rt5390sta.changes
-rw-r--r-- 1 myusername myusername   4521 2011-08-05 09:18 rt5390sta.spec
drwxr-xr-x 2 myusername myusername   4096 2011-06-22 03:32 sta
-rw-r--r-- 1 myusername myusername  14253 2011-06-22 03:28 sta_ate_iwpriv_usage.txt
drwxr-xr-x 2 myusername myusername   4096 2011-06-22 03:30 tools
myusername@myusername-lap:~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ patch -p0 < rt5390sta-2.4.0.4-config.patch 
bash: rt5390sta-2.4.0.4-config.patch: No such file or directory
myusername@myusername-lap:~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ patch -p0 < rt5390sta-2.5.0.3-config.patch 
patching file Makefile
Reversed (or previously applied) patch detected!  Assume -R? [n] 
```

as you can see I updated the patch name to the latest revision

What do I do with the ```
Reversed (or previously applied) patch detected!  Assume -R? [n]
``` prompt?

---

### Post by ATMOS_SKY on 2011-08-05
Hello Chili!

Really appreciate your time in supporting this forum!

I am encountering errors.

I pushed ahead and I think I need feedback before I proceed further...

```
~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ patch -p0 < rt5390sta-2.5.0.3-config.patch
patching file Makefile
patching file os/linux/config.mk
Reversed (or previously applied) patch detected!  Assume -R? [n] -R
Apply anyway? [n] n
Skipping patch.
2 out of 2 hunks ignored -- saving rejects to file os/linux/config.mk.rej
myusername@myusername-lap:~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ patch -p0 < rt5390sta-2.5.0.3-config.patch
patching file Makefile
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] y
Hunk #1 FAILED at 323.
Hunk #2 FAILED at 370.
2 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file os/linux/config.mk
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] y
Hunk #1 FAILED at 54.
1 out of 2 hunks FAILED -- saving rejects to file os/linux/config.mk.rej
myusername@myusername-lap:~/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO$ 

```

---

### Post by chili555 on 2011-08-05
It very much looks to me like the require patches have already been applied to version 2.5.0.3. I'd make a new folder called, for instance, *test1* and then drag and drop everything except 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.tar.xz into it. Extract 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO.tar.xz again and start again without the patches. Make the needed changes in config,mk and then:```
cd setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO
sudo su
make
make install
modprobe rt5390sta
exit
```Since I don't have the device and cannot test it, you will need to tell us how it works.

---

### Post by ATMOS_SKY on 2011-08-05
after running ```
 make 
```
I had these *warnings*
```

/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c: In function ‘rt2860_probe’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../os/linux/pci_main_dev.c:326: warning: assignment discards qualifiers from pointer target type
  CC [M]  /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.o
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘DefaultATEAsicSwitchChannel’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1248: warning: comparison of distinct pointer types lacks a cast
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:1034: warning: unused variable ‘RFValue2’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘ATETxPwrHandler’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:5162: warning: unused variable ‘CfgOfTxPwrCtrlOverMAC’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TX_FREQOFFSET_Proc’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:7623: warning: comparison of distinct pointer types lacks a cast
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_EX_Proc’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9373: warning: unused variable ‘CurrentChannel’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9372: warning: unused variable ‘BSSID_ADDR’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9371: warning: unused variable ‘ChannelPower’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9370: warning: unused variable ‘EEPData’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369: warning: unused variable ‘TssiDeltaPerChannel’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9369: warning: unused variable ‘TssiRefPerChannel’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368: warning: unused variable ‘BBP49Value’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368: warning: unused variable ‘RF28Value’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368: warning: unused variable ‘RF27Value’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368: warning: unused variable ‘RFValue’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9368: warning: unused variable ‘BbpData’
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9376: warning: control reaches end of non-void function
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c: In function ‘Set_ATE_TSSI_CALIBRATION_Proc’:
/home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/rt_ate.c:9360: warning: control reaches end of non-void function
  LD [M]  /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.o
see include/linux/module.h for more information
  CC      /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.mod.o
  LD [M]  /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic'
cp -f /home/myusername/setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/rt5390sta.ko /tftpboot

```

but seems to be operating and downloading fine, I went to a speed test site (through wireless) and it needed flash, 
So through synaptic package manager I went to download adobe's flash and it was just as fast as my LAN cable at 312kB/s (i know but its cheap internet).

I did skip the speed test as my downloading I figured was speed test enough for me.

I am very pleased!

Thank you CHILI555! You Rock!

So What I did:

I downloaded my respective driver setup @ Ralink's website
[http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2")  ** for me I selected RT539xPCIe**

I extracted the downloaded file from ralinktech (*twice btw to get to the directory*)
I followed mostly the original directions.  I repeated them for ease:
> **chili555 said:**
> 

1) If you haven't extracted it already, open the folder where you downloaded it to *(possibly home/Downloads) * and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed.

2.A) Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' or 'Open with gedit' 
2.B)Make these changes: set **'HAS_WPA_SUPPLICANT=y'** and **'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'** Proofread carefully, save and close leafpad.

EDIT: Note to searchers. When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:
```
cd setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO * *Note this is the directory that was created through extracting**
sudo su
make
make install
modprobe rt5390sta
exit
```

As always, post back if we can help you further.

---

### Post by chili555 on 2011-08-05
Great work! I'm glad it's working. I will amend my post above to tell the searchers that the new package doesn't require patches. Thanks for helping us understand the evolution of the 5390 family.

---

### Post by Redblade20XX on 2011-08-08
Just an update!! _**[COLOR=Red]Kernel 3.01 officially has native support for the RT5390 chipse[/COLOR]**_t also RaLink has new drivers for the chipset if anyone doesn't want to upgrade the kernel.

:D

---

### Post by xxmzzkat on 2011-08-15
Ahh okay so I've done the above procedures, everything went pretty smoothly except my kernel release is 2.6.38-10-generic-pae so I rewrote the symlink in the Makefile to /lib/modules/2.6.38-10-generic/build

And then when I type in modprobe rt5390sta I get:
FATAL: Error inserting rt5390sta (/lib/modules/2.6.38-10-generic-pae/kernel/drivers/net/wireless/rt5390sta.ko): Invalid module format

:(

---

### Post by chili555 on 2011-08-15
> **xxmzzkat said:**
> Ahh okay so I've done the above procedures, everything went pretty smoothly except my kernel release is 2.6.38-10-generic-pae so I rewrote the symlink in the Makefile to /lib/modules/2.6.38-10-generic/build

And then when I type in modprobe rt5390sta I get:
FATAL: Error inserting rt5390sta (/lib/modules/2.6.38-10-generic-pae/kernel/drivers/net/wireless/rt5390sta.ko): Invalid module format

:(

:( :( indeed!

You shouldn't have to modify the Makefile in any respect. What happened in the 'make' process that caused you to do that? Can you confirm that you have linux-headers-2.6.38-10-generic-pae and build-essential installed.

Don't take me wrong; I don't know everything about this process. Is there something different about PAE?

---

### Post by ronaldoff on 2011-08-15
SUPER !! So long I didn't hope anymore making this @x!! wireless card working

THX a lot.

---

### Post by xxmzzkat on 2011-08-15
> **chili555 said:**
> :( :( indeed!

You shouldn't have to modify the Makefile in any respect. What happened in the 'make' process that caused you to do that? Can you confirm that you have linux-headers-2.6.38-10-generic-pae and build-essential installed.

Don't take me wrong; I don't know everything about this process. Is there something different about PAE?

Well in /lib/modules there's a 2.6.38-10-generic directory and a 2.6.38-10-generic-pae directory, and in the Makefile the path is /lib/modules/$(uname -r)/build, but the build is only in the 2.6.38-10-generic.  Aaand my kernel release is 2.6.38-10-generic-pae, so when i tried to compile everything it said that /lib/modules/2.6.38-10-generic-pae/build didn't exist.  And then I just put in 2.6.38-10-generic in place.

And yeah I did download and install the linux headers and such, not much changed I don't think.

Thanks again xD

---

### Post by xxmzzkat on 2011-08-15
> **chili555 said:**
> :( :( indeed!

You shouldn't have to modify the Makefile in any respect. What happened in the 'make' process that caused you to do that? Can you confirm that you have linux-headers-2.6.38-10-generic-pae and build-essential installed.

Don't take me wrong; I don't know everything about this process. Is there something different about PAE?

Well in /lib/modules there's a 2.6.38-10-generic directory and a 2.6.38-10-generic-pae directory, and in the Makefile the path is /lib/modules/$(uname -r)/build, but the build is only in the 2.6.38-10-generic.  Aaand my kernel release is 2.6.38-10-generic-pae, so when i tried to compile everything it said that /lib/modules/2.6.38-10-generic-pae/build didn't exist.  And then I just put in 2.6.38-10-generic in place.

And yeah I did download and install the linux headers and such, not much changed I don't think.  I also searched "pae" in the synaptics package manager and downloaded relevant items haha.

Thanks again xD

---

### Post by chili555 on 2011-08-15
> so I rewrote the symlink in the Makefile to /lib/modules/2.6.38-10-generic/buildI'm still confused. I doubt you can just change the symlink to any old /build file. Please change it back to:$(uname -r). Then please show me:```
uname -r
sudo dpkg -s linux-headers-`uname -r`
```Now, let's check the 'make':```
cd Desktop/2011_wherever_5390
sudo su
make clean
make
```Thanks.

---

### Post by xxmzzkat on 2011-08-16
Ahh that worked :) Thank you so much!  You're seriously amazing.
  Just out of curiosity, cause I've seen it a few times before, why the dpkg instead of apt-get?

---

### Post by chili555 on 2011-08-16
> why the dpkg instead of apt-get?dpkg -s checks the status of a package; we hoped we were going to see:> Package: linux-headers-2.6.38-10-generic
[COLOR="Red"]Status: install ok installed[/COLOR]
Priority: optional
Section: devel
Installed-Size: 10500
etc., etc.
apt-get goes out on the internet and finds the correct version on the Ubuntu repositories and installs it, if not already. They are two different, but related operations.

I'm glad it's working.

---

### Post by Rocaphilla on 2011-08-29
Chilli if you're there, I'm an extreme noob and could sure use your help - even a step-by-step walkthrough- to help me get this issue sorted out. Thanks

---

### Post by Rocaphilla on 2011-08-29
I guess I should explain, I don't know how to get the make command to work. I've (I think) downloaded the patches, made what I think are the appropriate changes to the config.mk file (although I was not given the option for HAS_ANTENNA_DIVERSITY_SUPPORT (?)) and now don't really know where to go from there. I've tried following some of the instructions on other threads, but like I said I am an extreme noob (yesterday was my first attempt at Linux, ever) and seem to get stuck alot of the time. I kind of just want to start this whole process over to make sure I'm doing it properly. Thank you

---

### Post by chili555 on 2011-08-29
> **Rocaphilla said:**
> Chilli if you're there, I'm an extreme noob and could sure use your help - even a step-by-step walkthrough- to help me get this issue sorted out. ThanksSee private messages at the top, please.

---

### Post by lb520fr on 2011-08-30
> **chili555 said:**
> **EDIT! EDIT! EDIT!**
There is now a later version of the RT5390 driver called 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO. The patches discussed below are no longer required and you may skip those steps. Please see post #58 below. 
**EDIT! EDIT! EDIT!**

Mr. Stepbystep is here to help. I assume you have downloaded the driver file in the folder called Documents. If you haven't extracted it already, the open the Documents folder and right click the file and select 'Extract Here.' A folder will appear called 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO. Double-click it to open it. We will make a few changes before we proceed. Please open the folder os and then linux and right-click the file config.mk. Select 'Open with Leafpad.' Make these changes: set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y' Proofread carefully, save and close leafpad.

Now go here:  [https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless](https://build.opensuse.org/package/files?package=rt5390sta&project=driver%3Awireless)

Download all the patch files. Check carefully because you need every one. Wherever they get downloaded, drag and drop them into the 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO folder inside your Documents folder. 

Now we will work in the terminal. Open a terminal and we will change directories to where all our files are located:```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
```Now, we will apply all the patches:```
patch -p0 < rt5390sta-2.4.0.4-config.patch 
patch -p0 < rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch 
patch -p0 < rt5390sta-2.4.0.4-reduce_debug_output.patch 
patch -p0 < rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch 
patch -p0 < rt5390sta-2.4.0.4-return_nonvoid_function.patch 
patch -p0 < rt5390sta-2.4.0.4-WPA-mixed.patch 
patch -p0 < rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch
sudo su 
cp RT2860STA.dat RT5390STA.dat
mkdir -p /etc/Wireless/RT5390STA
cp RT5390STA.dat /etc/Wireless/RT5390STA
make clean
make
make install
modprobe rt5390sta
exit
```If, at any time, you get stuck or have a question, post back. If you get warnings in the 'make' stage, that's acceptable, errors are not. Any time you get an error, stop and ask me. I will be watching the forum actively for your replies.

EDIT: Note to searchers. When Update Manager gives us a later kernel version, known as linux-image in Ubuntu-land, you'll need to rebuild the module agaimst the later kernel:
```
cd Documents/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
sudo su 
make clean 
make
make install
modprobe rt5390sta
exit
```

As always, post back if we can help you further.
Sorry for re-raise  the problem , I am   green-had.  If there is a R5390  driver programs for kernel 2.6.35-30 in Ubuntu,i meet the same  wireless-card problem ,and How can I solve it ,maybe there is no driver  programs in my PC.Many thx for yr any suggestion!

---

### Post by chili555 on 2011-08-30
> **lb520fr said:**
> Sorry for re-raise  the problem , I am   green-had.  If there is a R5390  driver programs for kernel 2.6.35-30 in Ubuntu,i meet the same  wireless-card problem ,and How can I solve it ,maybe there is no driver  programs in my PC.Many thx for yr any suggestion!The fix is exactly the same as you quoted except the latest driver version 2.5.0.3 doesn't need the patches. Please proceed.

---

### Post by effay on 2011-08-30
I am not able to get this to work.

Today I downloaded the 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2 file, which is apparently the current RT539xPCIe driver. I downloaded it to my /home/user/Downloads folder. I then did extract here. I then opened the config.mk file in the extracted package (i.e., the Tar archive called 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL in my /home/user/Downloads folder) and made these two edits: HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y. I saved and closed.

I then opened the terminal and tried a bunch of stuff that is not seeming to work:

user@user-dm1z-u:~$ cd setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO
bash: cd: setup_wireless/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO: No such file or directory
user@user-dm1z-u:~$ cd setup_wireless/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO
bash: cd: setup_wireless/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO: No such file or directory
user@user-dm1z-u:~$ cd home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO
bash: cd: home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO: No such file or directory

What am I doing wrong!?

---

### Post by chili555 on 2011-08-30
Please try:```
cd Downloads/2011*
```

---

### Post by effay on 2011-08-30
Thank you for the response chilli! Unfortunately:

user@user-dm1z-u:~$ cd Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO
bash: cd: Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPO: No such file or directory

It's there though! I promise!

2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL

That's the name of the Tar archive I'm staring at in my Downloads folder right now...

---

### Post by chili555 on 2011-08-30
> user@user-dm1z-u:~$ cd Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPODid you try what I suggested?```
cd Downloads/2011*
```Use of the asterisk will fill in all the extra bits automagically. In any event:> user@user-dm1z-u:~$ cd Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GP[COLOR="Red"]O[/COLOR]But it's actually:> 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GP[COLOR="RoyalBlue"]L[/COLOR]

---

### Post by effay on 2011-08-30
Oh, sorry, didn't know that about asterisks. Tried this:

user@user-dm1z-u:~$ cd Downloads/2011*
bash: cd: Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL: Not a directory

---

### Post by chili555 on 2011-08-31
Let's see:```
cd Downloads
```Now let's list the contents of the directory:```
ls
```If you have extracted the tar.bz2, you will have both the directory *AND* the original tar.bz2. You did extract, didn't you??> I downloaded it to my /home/user/Downloads folder. ***I then did extract here***.

---

### Post by effay on 2011-08-31
```
user@user-dm1z-u:~$ cd Downloads
user@user-dm1z-u:~/Downloads$ ls
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2
user@user-dm1z-u:~/Downloads$
```

The file I downloaded is called: 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2

I right-clicked it and selected "Extract Here," then another file pops out called: 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL

I made the two edits to the extracted file (i.e., the file without the .bz2).

Then I did/got:

```
user@user-dm1z-u:~$ cd Downloads/2011*
bash: cd: Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL: Not a directory
```

Sorry to be so much trouble!

---

### Post by chili555 on 2011-08-31
> user@user-dm1z-u:~/Downloads$ ls
*[COLOR="Red"]2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL[/COLOR]*
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL.bz2Ahhh! I had to download it again to figure this out! The file I highlighted above is ***also*** a .tar archive that needs to be extracted. Right click it and select Extract Here. Now check os/linux/config.mk and be sure to change:> ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.Save and close the text editor.

Now you can do:```
cd Downloads/2011*
etc., etc.
```

---

### Post by effay on 2011-08-31
Hah!!

Went to [Ralink-->Software-->Linux]("http://www.ralinktech.com/support.php?s=2") and downloaded the RT539xPCIe driver (which is 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL .bz2) to home/user/Downloads. Right-clicked it and selected "Extract Here." Out pops a new file called 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL. Right-clicked that file and selected "Extract Here." Out pops another new file. Opened os/linux/config.mk in that file (i.e., the file produced by the second extraction) and set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. Saved and closed config.mk.

Then opened terminal and did the following:

```
cd Downloads/2011*
sudo su
make
make install
modprobe rt5390sta
exit
```

And...success!!!! Many thanks chili!!

Oh, and, for the record, this was on a HP dm1z.

---

### Post by JoshuaRL on 2011-09-21
I've got a new DM1 I'd like to get wireless running on. I saw that a newer kernel has support baked in. Has that kernel hit the main update channel, or is this compiling still necessary?

---

### Post by chili555 on 2011-09-21
> Has that kernel hit the main update channel,Not as of the version of 2.6.38-11 that hit today so, unless you are running a beta of Ubuntu 11.10, compiling is still necessary.

---

### Post by wahwahwah on 2011-09-22
Hi,

I've been following the steps from post 58 - I had the same problem as effay, as it said the file or directory didn't exist when it did. I extracted twice and made the appropriate changes, but when I tried running the commands in Terminal, this happened: 

```
user@ubuntu:~$ cd Downloads/2011*
user@ubuntu:~/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL$ 
user@ubuntu:~/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL$ sudo su
[sudo] password for user: 
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# make
make: *** No targets specified and no makefile found. Stop.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# make install
make: *** No rule to make target `install'. Stop.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# modprobe rf5390sta
FATAL: Module rf5390sta not found.
root@ubuntu:/home/user/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_GPL# exit
exit

```

The files are in my downloads file, too... It's probably something quite simple but can anyone help me out please?

---

### Post by wildmanne39 on 2011-09-22
Hi, I answered in the other post.
Thank you

---

### Post by Crazycraka208 on 2011-09-27
Tried everything to get this to work....and nothing. Finally found a solution.

Updated Kernel to 3.0 here:
[http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html](http://www.khattam.info/howto-install-linux-kernel-3-0-in-ubuntu-11-04-natty-narwhal-2011-06-03.html)

everything works perfect. the wifi led light blinks to show connectivity but works.

---

### Post by taichadow on 2012-04-27
> **theDunkel said:**
> i've follow it step by step, but i get errors:
```
make[1]: Entering directory `/lib/modules/2.6.38-8-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.38-8-generic-pae/build'
make: *** [LINUX] Error 2

```

I followed this guide and it worked perfectly with the exception of this^  if you've install linux-headers-$(uname -r) and build-essential and you still get this you have to change the Makefile

go to line 173 and replace
```
LINUX_SRC = /lib/modules/$(shell uname -r)/build
```with
```
LINUX_SRC = /usr/src/linux-headers-$(shell uname -r)
```this worked using ubuntu 10.04.3 with the 2.6.32.40 kernel on an HP Pavillion dv6 laptop

as a side note, every single thread I found while trying to fix this had chili555 posting on it trying to help.  pretty damn impressive.

---

### Post by chili555 on 2012-04-28
> as a side note, every single thread I found while trying to fix this had chili555 posting on it trying to help. pretty damn impressive.Somebody needs to get a real life!

---

### Post by roman5566 on 2012-12-07
i am using a ubuntu11.04 64bits and for whatever reason when i switch os's i have a problem with video and with the ralink wireless wifi card.

b.t.w. i'm using an HP model: p7-1054 with ralink rt5390

---

### Post by chili555 on 2012-12-08
> **roman5566 said:**
> i am using a ubuntu11.04 64bits and for whatever reason when i switch os's i have a problem with video and with the ralink wireless wifi card.

b.t.w. i'm using an HP model: p7-1054 with ralink rt5390Rather than add on to an old, long thread, please start a new thread and tell us more:```
lspci -nn | grep 0280
```And please tell us what problem you have. Does it not connect? Is it unstable? Does your computer freeze? Is there smoke, sparks, etc.?

---

