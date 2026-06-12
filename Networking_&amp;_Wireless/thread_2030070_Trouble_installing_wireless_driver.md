---
title: "Trouble installing wireless driver"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by Lateralus138 on 2012-07-20
Hello all, I have had Ubuntu as a dual boot with Windows for about 2 years and the whole time I have had trouble with the wifi connection cutting out the whole time. Sometimes it will be fine for days and other times it cuts out within a few seconds of of turning my computer on. Never had I had a problem with Windows so I thought maybe it was something to do with the Linux driver. I didn't use to use Ubuntu that much, only for fixing Windows problems and just checking it out, but the more familiar I become with Linux (I install many distros in Windows VMware) the more I want to be in it and I wanted to solve my problem so I have done a lot of searching and none of any other solution has worked. I finally figured out how to tell what wifi driver I have and I realized it's probably the driver because the wireless adapter is really rtl8192e and I found out that the Linux driver installed is r8169. I have followed instructions on this site and others to install the right driver and every time I go to make or sudo make there is always an error. I have actually tried to compile other software with make and there is an error there too so am I too assume that it is a problem compiling? I am not even 100%  sure it is the driver taht is the main problem, but I want to rule that out before moving on to something else. This is the error I receive in the terminal when I run make:
```

ian@Hell:~/Downloads/rtl8192e_linux_2.6.0015.1013.2010$ sudo make
[sudo] password for ian: 
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
gcc: error: /lib/modules/3.2.0-26-generic-pae/build/include/linux/autoconf.h: No such file or directory
gcc: fatal error: no input files
compilation terminated.
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ian/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192/Makefile". Fix it to use ccflags-y.  Stop.
make[1]: *** [_module_/home/ian/Downloads/rtl8192e_linux_2.6.0015.1013.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
make: *** [all] Error 2


```

Here's info on my laptop:
Laptop: Toshiba Satellite m505-4940s

lspci:
 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

ifconfig wlan0:
wlan0     802.11bg  ESSID:"K8S-PUTER_Network"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 68:7F:74:36:07:A2   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=87/100  Signal level=-56 dBm  Noise level=-113 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Here's something I just found that was interesting in lsmod:
rtlwifi                95804  1 rtl8192se

I know for a fact that it is supposed to be rtl8192e and not se.

Network config:
  *-network
       description: Wireless interface
       product: RTL8192E/RTL8192SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:c4:48:a8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xE driverversion=0014.0401.2010 ip=192.168.1.104 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:c800(size=256) memory:fdffc000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:7c:41:ff
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:e800(size=256) memory:fcfff000-fcffffff memory:fcfe0000-fcfeffff memory:febe0000-febfffff

---

### Post by chili555 on 2012-07-20
>  I realized it's probably the driver because the wireless adapter is really rtl8192e and I found out that the Linux driver installed is r8169.r8169 is for wired ethernet and has nothing to do with wireless.> I know for a fact that it is supposed to be rtl8192e and not se.How is that? What is the pci.id?```
lspci -nn | grep 0280
```> so am I too assume that it is a problem compiling? Yes, indeed. However, before we compile this old-timer on your shiny new 3.2.xx kernel, let's dig deeper as above:> rtl8192e_linux_2.6.0015.1013.[COLOR="Red"]2010[/COLOR]We are mystified because the wireless seems to be working just fine:> *-network
description: Wireless interface
product: RTL8192E/RTL8192SE Wireless LAN Controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 00:24:d2:c4:48:a8
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xE driverversion=0014.0401.2010 [COLOR="Red"]ip=192.168.1.104[/COLOR] latency=0 [COLOR="Red"]link=yes[/COLOR] multicast=yes wireless=802.11bg
resources: irq:17 ioport:c800(size=256) memory:fdffc000-fdffffff

---

### Post by Lateralus138 on 2012-07-20
> **chili555 said:**
> r8169 is for wired ethernet and has nothing to do with wireless.How is that? What is the pci.id?```
lspci -nn | grep 0280
```Yes, indeed. However, before we compile this old-timer on your shiny new 3.2.xx kernel, let's dig deeper as above:We are mystified because the wireless seems to be working just fine:

Ok I know I was wrong, I went into Windows and the device is named rtl8192e, but the driver there is rtl819xp. 

Here's the output of your query:
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)

Hmm, It doesn't always work though, like I said it cuts in and out and at the same moment the wireless works fine on my phone and on my xbox which I did not have running when it disconnected, but checked right away when it does disconnect. It keeps popping up asking for the password when this happens and of course it's the right password. I used to think it only happened when I *was downloading at my max speed because that's when I noticed it, but it has happened when doing nothing at all, and like I said I always check my other devices rigth away to see if they work and they do.*

---

### Post by chili555 on 2012-07-20
The module rtl8192se says it wants your device:>  Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [[COLOR="Red"]10ec:8192[/COLOR]] (rev 01)> $ modinfo rtl8192se | grep 8192
filename:       /lib/modules/3.2.0-26-generic-pae/updates/cw-3.3/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
alias:          pci:v0000[COLOR="Red"]10EC[/COLOR]d0000[COLOR="Red"]8192[/COLOR]sv*sd*bc*sc*i*
Let's see if we can tweak it a bit:```
sudo modprobe -r rtl8192se
sudo modprobe rtl8192se swenc=1
```If it helps, we can write a file and make it persistent.

I used to have a bit of instability and found some improvement setting the router to WPA2 only and channel 11. You might try some alternate settings in the router. You might also try without N speeds in the router.

---

### Post by Lateralus138 on 2012-07-20
> **chili555 said:**
> The module rtl8192se says it wants your device:Let's see if we can tweak it a bit:```
sudo modprobe -r rtl8192se
sudo modprobe rtl8192se swenc=1
```If it helps, we can write a file and make it persistent.

I used to have a bit of instability and found some improvement setting the router to WPA2 only and channel 11. You might try some alternate settings in the router. You might also try without N speeds in the router.
Ok thanx, how will I know if it helps? I have had a good connection today. Do I just leave my computer running for days and see if it stays on? I have run  the commands.

---

### Post by chili555 on 2012-07-20
> **Lateralus138 said:**
> Ok thanx, how will I know if it helps? I have had a good connection today. Do I just leave my computer running for days and see if it stays on? I have run  the commands.You can reboot at any time, just run the commands again after you start. If it seems to help, we'll make it persistent. You can always come back a few days from now and report your results. I'm not going anywhere!

---

### Post by Lateralus138 on 2012-07-22
Hey I just thought I'd let you know I have purposely been downloading a lot of stuff (around 40 gbs so far) in the last couple of days and it seems to be working just fine so I think your fix is working great. I'd appreciate that file if you don't mind whenever you get a chance.

---

### Post by chili555 on 2012-07-22
> it seems to be working just fine Awesome!

Please do:```
sudo gedit /etc/modprobe.d/rtl8192se.conf
```Add one line:```
options rtl8192se swenc=1
```Proofread carefully, save and close gedit.

Use leafpad, kate, vim or any text editor if you don't have gedit.

You should be all set. Please use thread tools at the top to mark Solved.

---

### Post by Lateralus138 on 2012-07-22
> **chili555 said:**
> Awesome!

Please do:```
sudo gedit /etc/modprobe.d/rtl8192se.conf
```Add one line:```
options rtl8192se swenc=1
```Proofread carefully, save and close gedit.

Use leafpad, kate, vim or any text editor if you don't have gedit.

You should be all set. Please use thread tools at the top to mark Solved.
Yep, thanx I try to triple check everything I do and always backup every file I edit. Sheldons my idol by the way lol. One of the few shows I watch on tv anymore, that and Breaking bad.

Did that file not exist to begin with?

---

### Post by chili555 on 2012-07-22
> Did that file not exist to begin with?That's correct, you created an /etc file from scratch.

Glad it's working now.

---

