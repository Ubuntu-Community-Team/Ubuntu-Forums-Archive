---
title: "cant connect wireless"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by lil_kid1333 on 2009-02-17
My laptop doesn't detect my modem :( im currently using the ethernet cable any help?

---

### Post by gletob on 2009-02-17
Could you please post the outputs of the commands

```
lspci
```
and
```
lsusb
```

---

### Post by lil_kid1333 on 2009-02-17
```
fello@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

```

```
fello@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

their you go dude thanks for your help :)

---

### Post by gletob on 2009-02-17
I'm sorry I kind of forgot you in my many firefox tabs (Mobile World Congress, interesting stuff)

Could you go to System>Administration>Hardware Drivers and see if there is anything like "BCM4318", "Broadcom 4318", or "Wireless Adapter"

---

### Post by lil_kid1333 on 2009-02-17
>_> lol its ok I understand!!

Nah that's what I checked before you posted (weird) it's empty...

---

### Post by gletob on 2009-02-17
I actually used to have a card with the same chipset and it worked in fiesty but I can't remember for the life of me how I fixed it.  I'm actually researching your card right now.

---

### Post by lil_kid1333 on 2009-02-17
yey thanks I would research if I knew where O.O

---

### Post by gletob on 2009-02-17
Could I ask if your running Hardy or Intrepid?
and
Have you tried updating your system just to make sure there are no drivers available?

---

### Post by lil_kid1333 on 2009-02-17
Intrepid and about the updates.................................... no xD I jsut barely installed it in this laptop but will do :) oh yeah I got Wubi...

---

### Post by 2scott on 2009-02-17
I have just installed 8.10 (x386 desktop)on a wiped 7G hard drive but cannot get the Network manager to connect to the internet.

Here are the answers to the "general" questions - if you need more info - I will try to get it.

Thanks for your help.

For internet-related help, make sure you include the following details:

1. How were you trying to get online? WIRELESS ROUTER

2. What hardware are you using? Seimens, SpeedStream Residential Gateway Model 6520 ([http://homesurewest.net/ajf/DSL/6520manual.pdf](http://homesurewest.net/ajf/DSL/6520manual.pdf)), Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) - also have an ethernet card installed - but don't want to use it: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

3. Who is your Internet Service Provider (and in which country)?  FRONTIERNET.NET - USA

4. Which version of Ubuntu are you using? e.g. Ubuntu 8.10 x386 - ON A SEPARATE DRIVE

5. Can you get online with any other method? HAVE NOT TRIED ANY OTHER METHOD - ROUTER IS DIFFICULT TO ACCESS.

6. How are you getting online to post on this forum? I LOGOUT OF UBUNTU AND START WINDOWS ON A SEPARATE DRVIVE

7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.
Code:

lspci
lsusb
lshw -class network
ifconfig
iwconfig

lspci
ubuntu@ubuntu-NASCAR:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

lsusb
ubuntu@ubuntu-NASCAR:~$ lsusb
Bus 005 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 047d:1032 Kensington 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:17:31:1c:fd:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:4e:33:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 7e:81:36:7e:69:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:1c:fd:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15316 (15.3 KB)  TX bytes:15316 (15.3 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

8. For wifi - what encryption are you using? - NONE
Have you tried an open network? YES

9. Do you dual-boot with Windows? NO

---

### Post by lil_kid1333 on 2009-02-17
> **2scott said:**
> I have just installed 8.10 (x386 desktop)on a wiped 7G hard drive but cannot get the Network manager to connect to the internet.

Here are the answers to the "general" questions - if you need more info - I will try to get it.

Thanks for your help.

For internet-related help, make sure you include the following details:

1. How were you trying to get online? WIRELESS ROUTER

2. What hardware are you using? Seimens, SpeedStream Residential Gateway Model 6520 ([http://homesurewest.net/ajf/DSL/6520manual.pdf](http://homesurewest.net/ajf/DSL/6520manual.pdf)), Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) - also have an ethernet card installed - but don't want to use it: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

3. Who is your Internet Service Provider (and in which country)?  FRONTIERNET.NET - USA

4. Which version of Ubuntu are you using? e.g. Ubuntu 8.10 x386 - ON A SEPARATE DRIVE

5. Can you get online with any other method? HAVE NOT TRIED ANY OTHER METHOD - ROUTER IS DIFFICULT TO ACCESS.

6. How are you getting online to post on this forum? I LOGOUT OF UBUNTU AND START WINDOWS ON A SEPARATE DRVIVE

7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.
Code:

lspci
lsusb
lshw -class network
ifconfig
iwconfig

lspci
ubuntu@ubuntu-NASCAR:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

lsusb
ubuntu@ubuntu-NASCAR:~$ lsusb
Bus 005 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 047d:1032 Kensington 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:17:31:1c:fd:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1c:df:4e:33:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 7e:81:36:7e:69:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:1c:fd:65  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15316 (15.3 KB)  TX bytes:15316 (15.3 KB)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

8. For wifi - what encryption are you using? - NONE
Have you tried an open network? YES

9. Do you dual-boot with Windows? NO

what?? O.o

---

### Post by gletob on 2009-02-17
Ok I may have a solution
1. Right click this link and save this file to your home folder
[http://ubuntu.cafuego.net/cafuego.gpg](http://ubuntu.cafuego.net/cafuego.gpg)
2. Open Software Sources in the Administration menu
3. Click in to the authentication tab click import key file then find the file you downloaded earlier
4. Click in to the Third Party Software tab and hit add
5. In the box that show up paste this and hit Add Source
deb     [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) intrepid-cafuego all
6. Then do the same for this address
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) intrepid-cafuego all
7. Now hit close and close again
8. Open a terminal and run
sudo apt-get update
sudo apt-get install b43-firmware
9. Reboot and see if Wi-Fi works.

I'm hoping this will work if it doesn't work don't get discouraged I might have messed something up.

---

### Post by Crafty Kisses on 2009-02-17
It would appear you have this wireless card:
```
Broadcom Corporation BCM4318
```
To make sure, I'd recommend you run this command, and see the results:
```
lspci | grep Broadcom\ Corporation
```
You can get the Broadcom driver right [here.]("ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe") Once you have the drivers, you want to use ndiswrapper to actually install the drivers, if you don't have ndiswrapper install it from the Terminal:
```
sudo apt-get install ndiswrapper
```
Once you have ndiswrapper, run the following command in Terminal:
```
sudo ndiswrapper -i bcmwl5.inf
```
What you want to do next is check and see if ndiswrapper is currently using the drivers, so run the following:
```
sudo ndiswrapper -l
```
If you see the driver, then good, but you're not quite done yet, let's handle the proper dependencies and what not, so run the following:
```
sudo depmod -a
```Then add the ndiswrapper module by running the following:
```
sudo modprobe ndiswrapper
```
Once you've done that make sure that module will start after every boot:
```
sudo ndiswrapper -m
```
In some cases the BCM module is installed by default, so what you need to do is blacklist that module, so do the following:
```
sudo nano /etc/modprobe.d/blacklist
```
You should now see like a text file. So what you want to do now, is at the bottom of the file, add the following line:
```
blacklist bcm43xx
```
After all this, run the following and see if the drivers are present:
```
ndiswrapper -l
```
If the ndiswrapper install went well, you should get something similar to this:
```
bcmwl5 driver installed, hardware present
```

---

### Post by lil_kid1333 on 2009-02-17
Ok so which do I try out first?? Codename or gletob?? 

oh wow... I just tried to open some program on my desktop computer and said someone might be eavesdropping me............... im paranoid now... :s

EDIT: WTF it said doing administrative something on the bottom O.O

---

### Post by gletob on 2009-02-17
> **lil_kid1333 said:**
> Ok so which do I try out first?? Codename or gletob?? 

oh wow... I just tried to open some program on my desktop computer and said someone might be eavesdropping me............... im paranoid now... :s

EDIT: WTF it said doing administrative something on the bottom O.O

I don't know the other dude has more experience but I thought of Ndiswrapper way earlier and try to stay away from it if necessary.

---

### Post by lil_kid1333 on 2009-02-17
aight so ill try his solution then thanks!!

but im scared for my desktop PC :'(

---

### Post by lil_kid1333 on 2009-02-17
I was doing the updates on the laptop and it froze when it was installing and I reboot it and went back to install and says
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

E: _cache->ope() failed, please report

I ran the command it said and says,

dpkg: requested operation requires superuser privilege

so what do I do guys?

damn it man so much trouble just for a damn wireless connection >_<

---

### Post by Crafty Kisses on 2009-02-17
Run the following command:
```
sudo dpkg --configure -a
```

---

### Post by lil_kid1333 on 2009-02-17
> **Codename said:**
> Run the following command:
```
sudo dpkg --configure -a
```

OMFG imma shoot myself i forgot to type in the sudo part >_< imma cry of anger >_< >_< >_<

---

### Post by lil_kid1333 on 2009-02-17
aight did the update and the driver was found but now how do I detect the wireless signal??

---

### Post by Crafty Kisses on 2009-02-17
You should be able to right click on Network Manager and select "Enable Wireless" and then you can scan for networks.

---

### Post by lil_kid1333 on 2009-02-18
> **Codename said:**
> You should be able to right click on Network Manager and select "Enable Wireless" and then you can scan for networks.

yeah I got it thanks :D

---

### Post by Crafty Kisses on 2009-02-18
I'm glad I could help.

---

