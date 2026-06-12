---
title: "RaLink RT2561/RT61 wireless card installation"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by jpr0 on 2010-09-13
Hi, 

I'm having trouble installing my RaLink RT2561/RT61 wireless card. It seems that this driver causes problems for all ubuntu users, and I've tried a couple of work arounds, none of which work for me. 

Firstly I downloaded the most recent driver from here: 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661) is the driver I downloaded. Next I performed the following steps: 

```

robinsjp@home-desktop:~$ sudo apt-get install linux-headers-`uname -r` build-essential gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.32-24-generic is already the newest version.
build-essential is already the newest version.
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I extracted the contents of the download to a directory on the Dekstop. The drivers are in a "Module" subdirectory. I navigate to that folder and do the following: 

```

robinsjp@home-desktop:~/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module$ make all
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.o
/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c: In function ‘NICLoadFirmware’:
/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c:2919: error: implicit declaration of function ‘current_fsuid’
/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c:2920: error: implicit declaration of function ‘current_fsgid’
make[2]: *** [/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.o] Error 1
make[1]: *** [_module_/home/robinsjp/Desktop/2010_0825_RT61_Linux_STA_v1.1.2.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'

```

The source refuses to compile. I've tried creating a /module subdirectory in the linux headers folder, as per this page:

[http://www.physics.nmt.edu/~rsonnenf/linuxcontrib/ralink-2561-rt61/](http://www.physics.nmt.edu/~rsonnenf/linuxcontrib/ralink-2561-rt61/)

I've also tried 

```
sudo KBUILD_NOPEDANTIC=1 make all
```

as this page suggests [http://ubuntuforums.org/showthread.php?t=1274079](http://ubuntuforums.org/showthread.php?t=1274079) but neither of these things help. 

I'm using Ubuntu 10.04 32 bit. 

Any help is appreciated.

---

### Post by chili555 on 2010-09-13
I couldn't build it either, using all the power of the gray beard. What is going wrong with the built-in rt61pci?

---

### Post by jpr0 on 2010-09-13
Hi
Thanks for the quick reply.

The problem I'm having with rt61pci is that the wireless signal seems to be very weak. If I'm sat directly on top of the router, then it's fine, but if I move away a few metres the signal is lost completely. I don't have windows installed on this box so I can't do a direct comparison with the windows driver, but I have two laptops here that pick up several surrounding wireless networks, while the box using rt61pci is only picking up one network.

I've been googling this for the past couple of hours and several people have reported weak wireless signals with rt61pci, like this bug report for instance:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508882](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/508882)

I'm not sure if building the driving from RaLink will help, but as things stand the card is unusable. Just for reference:

```
lspci | grep Ra
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
```

```
lsmod | grep rt61
rt61pci                18920  0 
crc_itu_t               1371  1 rt61pci
rt2x00pci               5995  1 rt61pci
rt2x00lib              27509  2 rt61pci,rt2x00pci
eeprom_93cx6            1333  1 rt61pci
```

```
iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"eTec"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:64:3B:24:FF   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Thanks

---

### Post by chili555 on 2010-09-13
I'm not sure I have any viable answer. You might try:```
sudo rmmod -f rt61pci
sudo modprobe rt61pci nohwcrypt=1
```It's the only parameter available, according to *modinfo rt61pci* and I'm not sure how it could affect your issue, but it costs nothing to try.

If it works, we can write a conf file and make it permanent.

You might email the developer of the Ralink tarball and complain that the file won't make.

---

### Post by jpr0 on 2010-09-13
I tried adding this option, and it doesn't improve the signal as far as I can see, there is only one visible network. I'll try emailing RaLink and see if I get a reply from them.

Edit:

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6075](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6075)

This seems to cover the problem I'm facing. Maybe I'll jump on that thread and hope someone can help us out.

---

### Post by chili555 on 2010-09-13
Have you tried linux-backports-modules-wireless? There is evidently an updated rt61pci in there.

---

### Post by jpr0 on 2010-09-13
Okay it will take a while to download this. Just to be sure, uname -r gives: 2.6.32-24-generic

So I should install the following package? 

linux-backports-modules-wireless-2.6.32-24-generic-pae

(I initially installed the wrong one, for 2.6.35... should I remove this?)

---

### Post by chili555 on 2010-09-13
I don't think you want pae. You should find and install linux-backports-modules-wireless-2.6.32-24-generic as well as linux-backports-modules-wireless-lucid-generic. The latter is designed to keep installing the latest version when a newer kernel image is installed; 2.6.32-555, for example.

---

### Post by MaindotC on 2010-09-14
Btw - not to barge in on your thread chili but jpr0 I thought you should know PAE is "Physical Address Extension" and it's an ideal kernel for utilizing more than 3.2 GB of memory if you ever wanted to.

---

### Post by jpr0 on 2010-09-14
> **strAlan said:**
> Btw - not to barge in on your thread chili but jpr0 I thought you should know PAE is "Physical Address Extension" and it's an ideal kernel for utilizing more than 3.2 GB of memory if you ever wanted to.

Thanks, I wasn't aware of what it was exactly. It's handy to know though, because I want to put more than 3 Gb in my own computer (the one I'm on at the moment isn't mine) and I was thinking of switching to a 64 bit OS. They don't seem as thoroughly supported as the 32 bit versions though.

Anyway, chili I installed the wireless backports module, but I don't notice any difference in the rt61pci module: 

```
modinfo rt61pci 
filename:       /lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     A658F54642571F722E33A38
alias:          pci:v00001814d00000401sv*sd*bc*sc*i*
alias:          pci:v00001814d00000302sv*sd*bc*sc*i*
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
depends:        rt2x00pci,rt2x00lib,crc-itu-t,eeprom_93cx6
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```

It's late here so I'm going to sleep. I'll check back here tomorrow. Thanks for your help.

---

### Post by chili555 on 2010-09-14
As I said before, I'm not sure I have any concrete answer. Are you certain it's the driver and not the hardware? I'm generally not a fan of throwing money at a problem, but there are other reliable wireless cards out there. 

I will be interested in Ralink's response and will be glad to try to build a replacement file if I can be of help.

When you write to Ralink, I'd think it would be most helpful if you provided all the data in your initial post plus:```
uname -r
lspci -nn  <==trim all but the wireless card
cat /etc/lsb-release
```

---

### Post by jpr0 on 2010-09-14
Well I just emailed RaLink, so I guess I have to wait on their reply. In the meantime, if I see what modules I have running, 

```
lsmod | grep rt
[COLOR="Red"]rt61pci[/COLOR]                18355  0 
crc_itu_t               1371  1 rt61pci
[COLOR="Red"]rt2x00pci[/COLOR]               5921  1 rt61pci
[COLOR="Red"]rt2x00lib[/COLOR]              26858  2 rt61pci,rt2x00pci
led_class               2864  1 rt2x00lib
compat_firmware_class     6554  1 rt2x00lib
agpgart                31724  1 nvidia
mac80211              225491  2 rt2x00pci,rt2x00lib
cfg80211              144650  2 rt2x00lib,mac80211
eeprom_93cx6            1333  1 rt61pci
parport_pc             25962  1 
parport                32635  3 ppdev,parport_pc,lp

```

I notice that rt2x00pci and rt2x00lib are both running. I read in another thread (I can't find it now, but related to RaLink USB dongles) that these modules were conflicting with the wireless driver. I've tried blacklisting them, 

```
cat /etc/modprobe.d/blacklist.conf | grep rt2
blacklist rt2x00pci
blacklist rt2x00lib

```

but they always seem to be running whenever the RT61pci module is running. Is there any way I can force these modules to not start, seeing as the blacklist isn't working?

---

### Post by chili555 on 2010-09-14
> I read in another thread (I can't find it now, but related to RaLink USB dongles) that these modules were conflicting with the wireless driver. Not correct. These are **required** by rt61pci! From *modinfo rt61pci*:```
$ modinfo rt61pci
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
license:        GPL
firmware:       rt2661.bin
firmware:       rt2561s.bin
firmware:       rt2561.bin
description:    Ralink RT61 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     1F8ADC136D38ED1899F7174
--- snip ---
alias:          pci:v00001814d00000301sv*sd*bc*sc*i*
[COLOR="Red"]depends:        rt2x00pci,rt2x00lib,crc-itu-t,eeprom_93cx6[/COLOR]
vermagic:       2.6.32-22-generic SMP mod_unload modversions 586 
parm:           nohwcrypt:Disable hardware encryption. (bool)
```I would remove the blacklist, although it doesn't seem to have any effect.

---

### Post by noelferreira on 2010-10-23
Hi guys.

Please let me know if you find a solution to this driver problem.
I use this card since 5.10 kernel and it alwyas worked fine.
Now updating to kernel 2.6.32.25 anytime it crashes my laptop.
I will let you know if you find any solution.

Thanks,

noel

---

### Post by noelferreira on 2010-10-24
> **noelferreira said:**
> Hi guys.

Please let me know if you find a solution to this driver problem.
I use this card since 5.10 kernel and it alwyas worked fine.
Now updating to kernel 2.6.32.25 anytime it crashes my laptop.
I will let you know if you find any solution.

Thanks,

noel

By the way i tried this option:

sudo modprobe rt61pci nohwcrypt=1,

from the previous thread and it improves my wireless signal from 30/70 to 50/70. And now wireless is ok. But only in the older kernels. 2.6.32.25 still craches my PC when i turn on wireless.

noel

---

### Post by jpr0 on 2010-10-24
I don't have access to that computer any more so I can no longer test it. But up until that last post, the signal was very weak, and the card was unusable with the kernel drivers. I also couldn't get ndiswrapper to work.

---

### Post by foundatron on 2010-11-17
Hi,

I'm using 10.10 AMD64, and my RaLink RT2561 based card works fine for about 40 minutes then websites start taking longer and longer to resolve. Till after an hour I restart the computer because sites start timing out.  Disconnecting from my wireless network and reconnecting seems to resolve the issue for a few minutes, but then reverts right back to being slow.  I've been looking through the forums and I haven't see anyone else who sited this same problem, but maybe this falls under the category of "unstable"?

---

### Post by jogi.nayak on 2011-02-25
View the readme in the driver directory it has very clear instructions!

---

### Post by hisho on 2011-08-16
Hello guys,

I am trying to build the rt61pci driver but I keep getting the same build errors mentioned in the first post of this discussion. Does anyone know what is the solution for it? Thanks

halshaebi@HeshamLinuxMachine:~/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module$ make all
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.o
/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c: In function ‘NICLoadFirmware’:
/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c:2919:2: error: implicit declaration of function ‘current_fsuid’
/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.c:2920:2: error: implicit declaration of function ‘current_fsgid’
make[2]: *** [/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rtmp_init.o] Error 1
make[1]: *** [_module_/home/halshaebi/Desktop/rt61DriverFirmware/2010_0825_RT61_Linux_STA_v1.1.2.6/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [all] Error 2

Hesham

---

### Post by jpr0 on 2011-08-16
Have you tried ndiswrapper with the windows driver? I tried this but couldn't get it to work, maybe you will have more luck.

---

### Post by cvgaviao on 2011-11-10
I had the same problem with ubuntu 11.10 64bits. But when I tried with a 32bits distribution, the drivers worked perfectly.

cheers

---

### Post by dunbar on 2012-03-07
To  "error: implicit declaration of function ‘current_fsuid’" this worked for me (Linux dunbar-desktop 2.6.32-38-generic):

diff Module/rt_config.h ../2010_0825_RT61_Linux_STA_v1.1.2.6/Module/rt_config.h
90a91,92
> #include <linux/sched.h>
> #include <linux/cred.h>

---

### Post by tcalbrecht on 2012-04-05
I just put this adapter into an old Dell Dimension 8200 running Ubuntu 10.10 and I cannot get it to hook up to my router.  

Any help would be appreciated.

Here's all the gory details:


```
tom@topcat:~$ sudo lshw -C network 
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: wlan1
       version: 00
       serial: 00:23:14:00:24:80
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci driverversion=2.6.35-32-generic-pae firmware=N/A latency=64 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe1f0000-fe1f7fff
  *-network:1
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Davicom Semiconductor, Inc.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 31
       serial: 00:08:a1:05:0f:82
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=64 link=no maxlatency=40 mingnt=20 multicast=yes
       resources: irq:18 ioport:ec00(size=256) memory:fe1fd800-fe1fd8ff memory:fe200000-fe23ffff

tom@topcat:~$ rfkill list 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

tom@topcat:~$ sudo iwlist scanning 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: E0:91:F5:A8:42:DE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"sorce"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b2c33dbe
                    Extra: Last beacon: 1016ms ago
                    IE: Unknown: 0005736F726365
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34010D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD8E0050F204104A0001101044000102103B0001031047001000000000000010000000E091F5A842DE1021000D4E6574676561722C20496E632E10230009574E523130303076321024000456324831104200046E6F6E651054000800060050F20400011011001E574E523130303076322D564328576972656C6573732041502D322E344729100800020086103C000103
          Cell 02 - Address: 00:14:BF:39:D2:F8
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:off
                    ESSID:"hondo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000009151ce95
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0005686F6E646F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020601
          Cell 03 - Address: 00:1C:10:36:AA:D0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Bluewater"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029451044ef
                    Extra: Last beacon: 764ms ago
                    IE: Unknown: 0009426C75657761746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020014000000
          Cell 04 - Address: 00:11:50:0A:AD:4D
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000271a3034184
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010200

tom@topcat:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
     wireless-ssid Hondo
     pre-up wpa_supplicant -B -Dwext -iwlan1 -c/etc/wpa_supplicant.conf
     post-down killall -q wpa_supplicant


tom@topcat:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

tom@topcat:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) [8086:2530] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 04)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 04)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 04)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 MX 420] [10de:0172] (rev a3)
02:07.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
02:08.0 Network controller [0280]: RaLink RT2561/RT61 802.11g PCI [1814:0301]
02:09.0 Ethernet controller [0200]: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet [1282:9102] (rev 31)

tom@topcat:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

tom@topcat:~$ sudo lshw -short 
H/W path             Device      Class       Description
========================================================
                                 system      Dimension 8200
/0                               bus         Dimension 8200
/0/0                             memory      64KiB BIOS
/0/400                           processor   Intel(R) Pentium(R) 4 CPU 2.40GHz
/0/400/700                       memory      8KiB L1 cache
/0/400/701                       memory      512KiB L2 cache
/0/1000                          memory      768MiB System Memory
/0/1000/0                        memory      128MiB RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
/0/1000/1                        memory      128MiB RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
/0/1000/2                        memory      256MiB RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
/0/1000/3                        memory      256MiB RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
/0/100                           bridge      82850 850 (Tehama) Chipset Host Bridge (MCH)
/0/100/1                         bridge      82850 850 (Tehama) Chipset AGP Bridge
/0/100/1/0                       display     NV17 [GeForce4 MX 420]
/0/100/1e                        bridge      82801 PCI Bridge
/0/100/1e/7                      bus         USB
/0/100/1e/7.1                    bus         USB
/0/100/1e/7.2                    bus         USB 2.0
/0/100/1e/8          wlan1       network     RT2561/RT61 802.11g PCI
/0/100/1e/9          eth0        network     21x4x DEC-Tulip compatible 10/100 Ethernet
/0/100/1f                        bridge      82801BA ISA Bridge (LPC)
/0/100/1f.1          scsi0       storage     82801BA IDE U100 Controller
/0/100/1f.1/0        /dev/sda    disk        40GB MAXTOR 6L040J2
/0/100/1f.1/0/1      /dev/sda1   volume      243MiB Linux filesystem partition
/0/100/1f.1/0/2      /dev/sda2   volume      37GiB Extended partition
/0/100/1f.1/0/2/5    /dev/sda5   volume      37GiB Linux LVM Physical Volume partition
/0/100/1f.1/0.1.0    /dev/sdb    disk        160GB ST3160023A
/0/100/1f.1/0.1.0/1  /dev/sdb1   volume      127GiB Windows NTFS volume
/0/100/1f.1/0.1.0/2  /dev/sdb2   volume      21GiB Windows NTFS volume
/0/100/1f.1/1        /dev/cdrom  disk        ODD-DVD SD-R5272
/0/100/1f.2                      bus         82801BA/BAM USB Controller #1
/0/100/1f.3                      bus         82801BA/BAM SMBus Controller
/0/100/1f.4                      bus         82801BA/BAM USB Controller #1
/0/100/1f.5                      multimedia  82801BA/BAM AC'97 Audio Controller

tom@topcat:~$ uname -a 
Linux topcat 2.6.35-32-generic-pae #67-Ubuntu SMP Mon Mar 5 21:23:19 UTC 2012 i686 GNU/Linux

tom@topcat:~$ dmesg | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt6|rt7|usb|witch|wl';
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.005887] SMP alternatives: switching to UP code
[    0.165553] ACPI: No dock devices found.
[    0.238799] HEST: Table is not found!
[    0.239349] usbcore: registered new interface driver usbfs
[    0.239369] usbcore: registered new interface driver hub
[    0.239410] usbcore: registered new device driver usb
[    0.239926] Switching to clocksource tsc
[    0.273434] pnp: PnP ACPI: found 12 devices
[    0.791121] ERST: Table is not found!
[    0.932956] hub 1-0:1.0: USB hub found
[    1.181497] isapnp: No Plug & Play device found
[    1.182080] hub 2-0:1.0: USB hub found
[    1.266852] hub 3-0:1.0: USB hub found
[    1.267335] hub 4-0:1.0: USB hub found
[    1.267711] hub 5-0:1.0: USB hub found
[    1.271577] device-mapper: multipath: version 1.1.1 loaded
[    1.271581] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.274066] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.683869] net eth0: Davicom DM9102 at pci0000:02:09.0, 00:08:a1:05:0f:82, irq 18
[   12.064075] [drm] nouveau 0000:01:00.0: BMP BIOS found
[   12.064088] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 2.0
[   12.528231] Console: switching to colour frame buffer device 128x48
[   14.592098] rt61pci 0000:02:08.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.096998] Registered led device: rt61pci-phy0::radio
[   15.097028] Registered led device: rt61pci-phy0::assoc
[   15.116138] udev[295]: renamed network interface wlan0 to wlan1
[   16.389586] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   16.391529] ADDRCONF(NETDEV_UP): eth0: link is not ready

tom@topcat:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

tom@topcat:~$ cat /etc/modprobe.d/* | egrep 'acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl';
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb 
blacklist uart6850
blacklist twl4030_wdt
options iwlagn 11n_disable=1

tom@topcat:~$ sudo hwinfo --netcard  
> hal.1: read hal dataprocess 2386: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: PCI 208.0: 0282 WLAN controller                             
  [Created at pci.318]
  Unique ID: PL6s.gohsp1cSoiA
  Parent ID: 6NW+.eDbWAYN5SdB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:08.0
  SysFS BusID: 0000:02:08.0
  Hardware Class: network
  Model: "RaLink EW-7108PCg"
  Vendor: pci 0x1814 "RaLink"
  Device: pci 0x0301 "RT2561/RT61 802.11g PCI"
  SubVendor: pci 0x1814 "RaLink"
  SubDevice: pci 0x2561 "EW-7108PCg"
  Driver: "rt61pci"
  Driver Modules: "rt61pci"
  Device File: wlan1
  Features: WLAN
  Memory Range: 0xfe1f0000-0xfe1f7fff (rw,non-prefetchable)
  IRQ: 17 (5954 events)
  HW Address: 00:23:14:00:24:80
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00001814d00000301sv00001814sd00002561bc02sc80i00"
  Driver Info #0:
    Driver Status: rt61pci is active
    Driver Activation Cmd: "modprobe rt61pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

24: PCI 209.0: 0200 Ethernet controller
  [Created at pci.318]
  Unique ID: rBUF.0NgK5ZS9c0D
  Parent ID: 6NW+.eDbWAYN5SdB
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:09.0
  SysFS BusID: 0000:02:09.0
  Hardware Class: network
  Model: "Davicom 21x4x DEC-Tulip compatible 10/100 Ethernet"
  Vendor: pci 0x1282 "Davicom Semiconductor, Inc."
  Device: pci 0x9102 "21x4x DEC-Tulip compatible 10/100 Ethernet"
  SubVendor: pci 0x4554 
  SubDevice: pci 0x434e 
  Revision: 0x31
  Driver: "dmfe"
  Driver Modules: "dmfe"
  Device File: eth0
  I/O Ports: 0xec00-0xecff (rw)
  Memory Range: 0xfe1fd800-0xfe1fd8ff (rw,non-prefetchable)
  Memory Range: 0xfe200000-0xfe23ffff (ro,non-prefetchable,disabled)
  IRQ: 18 (7 events)
  HW Address: 00:08:a1:05:0f:82
  Link detected: no
  Module Alias: "pci:v00001282d00009102sv00004554sd0000434Ebc02sc00i00"
  Driver Info #0:
    Driver Status: dmfe is active
    Driver Activation Cmd: "modprobe dmfe"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

tom@topcat:~$ cat /var/lib/NetworkManager/NetworkManager.state 

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

tom@topcat:~$ sudo lsmod 
Module                  Size  Used by
joydev                  8767  0 
binfmt_misc             6599  1 
nls_cp437               4931  0 
cifs                  241903  0 
arc4                    1165  2 
rt61pci                19187  0 
crc_itu_t               1383  1 rt61pci
rt2x00pci               6029  1 rt61pci
rt2x00lib              27339  2 rt61pci,rt2x00pci
led_class               2633  1 rt2x00lib
snd_intel8x0           25664  2 
mac80211              231959  2 rt2x00pci,rt2x00lib
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71603  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
cfg80211              144758  2 rt2x00lib,mac80211
nouveau               518076  2 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ttm                    56825  1 nouveau
drm_kms_helper         30200  1 nouveau
drm                   168796  4 nouveau,ttm,drm_kms_helper
eeprom_93cx6            1345  1 rt61pci
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              26926  1 
i2c_algo_bit            5168  1 nouveau
lp                      7342  0 
snd                    49102  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 29982  0 
psmouse                59027  0 
serio_raw               4022  0 
ppdev                   5556  0 
intel_rng               2320  0 
agpgart                32075  3 ttm,drm,intel_agp
soundcore                880  1 snd
parport_pc             26378  1 
snd_page_alloc          7216  2 snd_intel8x0,snd_pcm
parport                31492  3 lp,ppdev,parport_pc
dcdbas                  5442  0 
floppy                 54343  0 
dmfe                   17289  0 


```

---

### Post by tcalbrecht on 2012-04-05
Found my problem.  Spelling error in /etc/network/interfaces.  I used some code I found online.  It should have been wireless-essid.  I had wireless-ssid.

---

