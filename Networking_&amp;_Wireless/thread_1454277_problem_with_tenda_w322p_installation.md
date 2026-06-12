---
title: "problem with tenda w322p installation"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by LordAro on 2010-04-14
Hello,

I'm trying to install the Tenda Wireless N PCI adapter
I have installed *ndisgtk* with its dependencies. 
(as suggested by [http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/](http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/))
When i try to access the *.inf* files i get the error message:
***Unable to see if hardware is present.***

Any ideas please?

Thanks

---

### Post by chili555 on 2010-04-14
Did you install the .inf file that came on the driver CD that came with the device? The XP .inf?

---

### Post by LordAro on 2010-04-15
i couldn't because it was locked up in a .exe

---

### Post by chili555 on 2010-04-15
Please post:```
lspci -nn
```We may have a native driver.

Note to Chili: rt2860sta

---

### Post by LordAro on 2010-04-15
hope you wanted all of it...

```
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 02)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] [1039:0964] (rev 36)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] [1039:0180] (rev 01)
00:08.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
00:09.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)
00:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)

```

---

### Post by LordAro on 2010-05-01
i apologise for bumping this topic, but i really would like an answer...:-?

---

### Post by nyarnon on 2010-05-01
There is no answer, you will just have to wait till a fix is released. Canonical threw an unfinished release at you to make the deadline. Thats what bloody edge obviously means.

---

### Post by chili555 on 2010-05-01
Please open a terminal and do:```
sudo modprobe rt2860sta
iwconfig
dmesg | grep rt2
```Thanks.

---

### Post by d0gleg on 2010-05-02
Hello, I'm also having troubles with a tenda w322p installation. I was running server 9.10 (kernel 2.6.31.20) until yesterday when I installed the w322p card. It worked fully straight out the box, and I did not have any problems until I upgraded ubuntu to 10.04 (kernel 2.6.32.21) later that day. The w322p card will now no longer connect to my lan. If I revert back to 2.6.31.20 then the w322p card works perfectly.
 
I understand that a fix is just a matter of time, but is there any simple way to install the 2.6.31.20 driver into 2.6.32.21, or should I just wait for the fix?

---

### Post by d0gleg on 2010-05-02
I did what chili555 suggested:
 
> **chili555 said:**
> Please open a terminal and do:```
sudo modprobe rt2860sta
iwconfig
dmesg | grep rt2
```Thanks.
 
This is what I got back:
- Ubuntu 9.10
 
```
 
$ sudo modprobe rt2860sta
[sudo] password for x: 
$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
ra0       RT2860 Wireless  ESSID:"xxxxxxx"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ dmesg | grep rt2
[   45.792821] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   45.797839] rt2860 0000:05:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
 

```
 
- Ubuntu 10.04
 
```
 
$ sudo modprobe rt2860sta
[sudo] password for x: 
$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.452 GHz  Access Point: 00:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-56 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ dmesg | grep rt2
[   27.882780] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   28.127927] rt2860 0000:05:07.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
 

```
 
I don't see much of a difference. The w322p card works with 9.10 but not with 10.04 :confused:

---

### Post by chili555 on 2010-05-02
What is the result of:```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate 54M
sudo iwlist wlan0 scan

```Thanks.

---

### Post by d0gleg on 2010-05-03
Hi chili555,
 
I ran the commands on both versions of Ubuntu
 
> **chili555 said:**
> What is the result of:```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 rate 54M
sudo iwlist wlan0 scan

```Thanks.
 
On 9.10 I had to substitute ra0 for wlan0, I got:
 
```
 
$ sudo iwconfig ra0 mode managed
$ sudo iwconfig ra0 rate 54M
$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:xx:xx:xx:xx:xx
                    ESSID:"XXXXXXXX"
                    Mode:Managed
                    Channel:9
                    Quality:100/100  Signal level:-49 dBm  Noise level:-71 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```
 
On 10.04, I got:
 
```
 
$ sudo iwconfig wlan0 mode managed
$ sudo iwconfig wlan0 rate 54M
$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:xx:xx:xx:xx:xx
                    Protocol:802.11b/g
                    ESSID:"XXXXXXXX"
                    Mode:Managed
                    Channel:9
                    Quality:91/100  Signal level:-54 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```
 
Thanks for your help :)

---

### Post by chili555 on 2010-05-03
The card and driver are working correctly. Does Network Manager see your network? What happens when you try to connect? Does it ask for your WPA-PSK password?

---

### Post by d0gleg on 2010-05-03
> **chili555 said:**
> The card and driver are working correctly. Does Network Manager see your network? What happens when you try to connect? Does it ask for your WPA-PSK password?
 
Hi chili, By 'Network Manager' I assume you mean the radio icon on the right side of the top panel (near the speaker icon). The radio icon is indicating that it is scanning, however it is not making a connection. If I left click on it I see my network. If I select my network, it then just continues to indicate that it is scanning. I also recreated a new wireless network with the correct WPA password etc, but no luck. :confused: 
 
On the other hand the w322p works perfectly with 9.10 :confused:
 
I've since tried an old wg311 card with both versions of Ubuntu, and it works perfectly with either version, however the wg311 belongs to a windows XP PC. It's also odd that the w322p doesn't install properly on the windows XP PC. It kept installing more and more copies of the driver until I eventually pulled the plug. :confused:

---

### Post by chili555 on 2010-05-03
> It's also odd that the w322p doesn't install properly on the windows XP PC. It kept installing more and more copies of the driver until I eventually pulled the plug. I really hate to say this and my old computers 101 (you probably don't remember punchcards) instructor will scorn me, but is the card defective?

---

### Post by d0gleg on 2010-05-03
> **chili555 said:**
> I really hate to say this and my old computers 101 (you probably don't remember punchcards) instructor will scorn me, but is the card defective?
 
Yeh, I was wondering that as well. I'm going to have to take it back and replace it. I'll let you know how it goes. :)

---

### Post by dafrostyone on 2010-05-03
Hi guys, the card is not defective as i an having exactly the same problem with the same card. Again it worked perfectly on ubuntu 9, now it appears to work perfectly on 10, but won't connect. I'm dual booting windows 7 where it also works perfectly.

---

### Post by chili555 on 2010-05-03
@ d0gleg--

May I please see:```
lsusb
```I am trying to work out an experiment. You have been selected to be my test pilot!

---

### Post by d0gleg on 2010-05-04
Well, I went back to the computer store today with the intention of replacing the card with one that worked. I was convinced it was faulty. Anyway the owner took back the card and promptly inserted it into a PC running windows 7, to show me that the card was not faulty. According to him, there are driver issues with windows XP, but the card works OK with 7.
 
The owner then exchanged the card for a TP-LINK TL-WN851N. Evidently this card works OK with windows XP but it has issues with 7. I plugged it into my Ubuntu 10.04 box and it worked immediately without further effort.
 
Based on what I have seen so far with help from chili555, I believe that the w322p is not faulty, and the card has (temporary) issues with 10.04. I would also take a stab in the dark, and guess that the issues with 10.04 might be related to the issues with XP.
 
Thanks anyway, and good luck with the w322p.:D

---

### Post by dafrostyone on 2010-05-04
My w322p worked fine under XP 32 bit, XP 64bit, Ubuntu 9 32 bit, Ubuntu 9 64 bit, but does not work under Ubuntu 10 64bit.

```
lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:b0:8c:06:04:cb  
          inet6 addr: xxxxxxxxxxxxxxxxxxxx/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2089558 (2.0 MB)  TX bytes:0 (0.0 B)
          Interrupt:21 
```

---

### Post by udippel on 2010-05-04
You all might have the same problem that you could find a dozen times in the last 12 hours (could any of the mods make this one finally sticky, please, it is high time!).

Uwe

---

### Post by glennbolton on 2010-05-10
Hello,

I ran into the exact same problem after upgrading to 10.04. Here how I got my Tenda W322P V2.0 working:


[LIST=1]
[*]From a terminal run **lspci** to determine the chipset your card uses. In my case I had the following entry:
*Network controller: RaLink Device 3062*
(if you have a different version of the W322P card the chipset may differ, these exact instructions may not work in that case, use your common sense here)
[*]Go to RaLink's website and check their Linux Support page:
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
[*]Find your device name and download the corresponding driver. The "**RT3062PCI**/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790)" driver seemed like the best choice for rather obvious reasons.
**Tip:** on the driver download page you don't need to enter your name or email address, just click accept.
[*]Extract the download to a location of your choice
[*]Open the .../os/linux/config.mk file in your favourite text editor
[*]Change HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y
[*]Change HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
[*]Open your terminal again and navigate to the location of the extracted files
[*]Type **sudo make** and wait a moment or two
[*]Type **sudo make install** and wait another moment
[*]Reboot your computer
[/LIST]
- Glenn

---

### Post by LordAro on 2010-05-25
thanks glennbolton i'm sure thats very useful
i just can't find:
[QUOTE="glennbolton"].../os/linux/config.mk file[/QUOTE]
i'm on ubuntu 9.10 still - do i need to upgrade?

---

### Post by glennbolton on 2010-05-27
> **LordAro said:**
> thanks glennbolton i'm sure thats very useful
i just can't find:

i'm on ubuntu 9.10 still - do i need to upgrade?

Hey LordAro!

Sorry, I should have been more specific, re-read step 5 as:

5. Open the <path to wherever you extracted the download from step 4>/os/linux/config.mk file in your favourite text editor

---

### Post by LordAro on 2010-05-27
ah
i see what the problem is
because mine is: RaLink RT2800 802.11n [1814:0601] there isn't an actual driver available, just firmware 
(i picked [Firmware RT28XX/RT30XX PCI/mPCI/PCIe/CardBus series (RT2760/RT2790/RT2860/RT2890/RT3060/RT3062/RT3562/RT2860/RT2760/RT2890/RT2790/RT3090)]("http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWTBNamsyTVRBNE1pNTZhWEE5UFQxU1ZESTROakJmUm1seWJYZGhjbVZmVmpJMkM%3D") because it seemed right)

---

### Post by Rogue Soul on 2010-06-11
I have the RT2800 version too.  I followed glennbolton's instructions exactly, except I had to use the "**RT2860PCI**/mPCI/CB/PCIe(RT2760/RT2790/RT2860/RT2890)" driver to get the W322P card working and connecting to my network properly. 

Works a treat now.  Thanks glenn!

---

### Post by LordAro on 2010-06-13
ok, i have installed both drivers mentioned above but IT STILL DOESN'T WORK!:-(
here is more info:
```
the_overlord@Toby-Linux:~$ sudo lspci -nn
[sudo] password for the_overlord: 
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 02)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] [1039:0964] (rev 36)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)
00:05.0 IDE interface [0101]: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] [1039:0180] (rev 01)
00:08.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
00:09.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)
00:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)

``````

the_overlord@Toby-Linux:~$ sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:11:2f:94:18:75
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:c800(size=256) memory:e7012000-e7012fff memory:40000000-4001ffff(prefetchable)
  *-network:1 UNCLAIMED
       description: Network controller
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:e7000000-e700ffff

``````

the_overlord@Toby-Linux:~$ uname -rm
2.6.32-22-generic i686

``````

the_overlord@Toby-Linux:~$ dmesg | grep -e iwl -e wlan
the_overlord@Toby-Linux:~$
(nothing shown)
```

---

### Post by chili555 on 2010-06-13
Please do:```
sudo modprobe rt2860sta
dmesg | grep -i rt2
```Thanks.

---

### Post by LordAro on 2010-06-13
```
the_overlord@Toby-Linux:~$ sudo modprobe rt2860sta
[sudo] password for the_overlord: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
the_overlord@Toby-Linux:~$ dmesg | grep -i rt2
[26238.016781] [COLOR=Red]rt2[/COLOR]860sta: module is from the staging directory, the quality is unknown, you have been warned.
[26238.026484] [COLOR=Red]rt2[/COLOR]860 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
the_overlord@Toby-Linux:~$
```

---

### Post by chili555 on 2010-06-13
> rt2860 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Looks promising! Did an interface get created?```
iwconfig
```Does the Network Manager icon see networks?

---

### Post by LordAro on 2010-06-13
So we're getting somewhere then?
depends what you meant by interface - no window appeared or anything
```
the_overlord@Toby-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

the_overlord@Toby-Linux:~$ 

```
i think this is good, yes?

---

### Post by chili555 on 2010-06-13
It is good! Now click the Network Manager icon at the upper right and see if you see networks and can connect. In my example attached, my network is GBR1. If you do not, post:```
dmesg | grep RT2
```

---

### Post by LordAro on 2010-06-14
:confused:
multiple new problems...
i look on the network manager, and see that there are no connections visible (internet.png)
thinking it is hidden i i fill in the hidden network form thing (internet2.png)
it then spends some time connecting asking me for the passkey ~5 times before giving up completely (internet3.png)
i have checked the connection details - it seems it just can't see the network :(
(and yes, the network it functioning correctly - i'm typing this wirelessly on the family laptop)
```
the_overlord@Toby-Linux:~$ dmesg | grep RT2
the_overlord@Toby-Linux:~$
```(shows nothing again)

---

### Post by chili555 on 2010-06-15
That's troubling! Let's do a full diagnostic work-up. Please do:```
lsmod > aro.txt
sudo iwlist wlan0 scan >> aro.txt
dmesg >> aro.txt
zip aro.zip aro.txt
```You will find a zip file in your Home directory called aro.zip. Please attach it to your reply. Hopefully we can see what's going wrong.

---

### Post by LordAro on 2010-06-15
okay... here goes...
i have since discovered on startup from complete shut down (turned off at wall) there appears to be no wireless active (see internet.png but without the wirless section) until i type in terminal:
```
sudo modprobe rt2860sta
```then the wireless networks section appears
aro.zip is before i "modprobed"
aro2.zip is after

---

### Post by chili555 on 2010-06-15
I noticed this:> [   12.240933] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)What explains that? Did you try and fail to get ndiswrapper going? Please do:```
sudo rmmod -f ndiswrapper
sudo rmmod -f rt2860sta
sudo modprobe rt2860sta
```Now are there networks available?

Your scan doesn't complain or error. > wlan0     No scan resultsAre you certain there are wireless access points in range?

---

### Post by LordAro on 2010-06-16
> **chili555 said:**
>  Did you try and fail to get ndiswrapper going? 
? 
all i had done since start up was follow your instructions and what i said below IN PREVIOUS POSTS
```
the_overlord@Toby-Linux:~$ sudo rmmod -f ndiswrapper
[sudo] password for the_overlord: 
the_overlord@Toby-Linux:~$ sudo rmmod -f rt2860sta
ERROR: Removing 'rt2860sta': Resource temporarily unavailable
the_overlord@Toby-Linux:~$ sudo modprobe rt2860sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
the_overlord@Toby-Linux:~$ 

```> **chili555 said:**
> Are you certain there are wireless access points in range?
yes, i've connected with the laptop (which i'm on) from furthur away and through more walls

---

### Post by david_1989 on 2010-12-28
I just wanted to say that I have the Tenda W322P V2 and it did not work out of the box with Ubuntu 10.10, however I have managed to get it working beautifully with great wireless N speeds and WPA2. I have the Tenda W322P V2 which has a Ralink 3062 chip.

Basically follow [these instructions]("http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/") to install the driver.

In addition you must also blacklist the following modules in /etc/modprobe.d/blacklist.conf by adding:
```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```

Also add the following modules in /etc/modules:
```
rt3562sta.ko
rt3562sta
```

Finally reboot after doing all this.


Someone please try this and then we can mark the thread as solved if this works. Please ask if you have problems as there may have been something I missed seeing as tried numerous things to get the card to work.

---

### Post by dannybro on 2010-12-29
I have installed the driver, i still cannot see any networks, is there anything extra i need to do to get it to work? :confused:
with regards
Danny

---

### Post by dannybro on 2010-12-30
> **LordAro said:**
> Hello,
 
I'm trying to install the Tenda Wireless N PCI adapter
I have installed *ndisgtk* with its dependencies. 
(as suggested by [http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/](http://www.alstevens.co.uk/how-to-install-wireless-usb-drivers-for-ubuntu/))
When i try to access the *.inf* files i get the error message:
***Unable to see if hardware is present.***
 
Any ideas please?
 
Thanks
 
I couldn't find the "administration ‘Manage Sources’" , where is it?:confused:

---

### Post by david_1989 on 2011-01-02
> **dannybro said:**
> I have installed the driver, i still cannot see any networks, is there anything extra i need to do to get it to work? :confused:
with regards
Danny

See my post. You must blacklist the modules specified and specify the right module to be loaded.

---

### Post by PatchesTheCaveman on 2011-01-02
> **dannybro said:**
> I couldn't find the "administration ‘Manage Sources’" , where is it?:confused:

On Maverick, *Manage Sources* isn't available in the Administration menu any more.  Run this command:
```
gksudo software-properties-gtk
```
from a terminal or by pressing ALT+F2 to access it.

---

### Post by Possum Films on 2011-01-20
Just want to say thanks to david_1989, I'd been looking for a solution on setting up my wireless cards for ages and yours was the first the actually worked out of about half a dozen different ones.

:popcorn:

---

### Post by david_1989 on 2011-01-23
> **Possum Films said:**
> Just want to say thanks to david_1989, I'd been looking for a solution on setting up my wireless cards for ages and yours was the first the actually worked out of about half a dozen different ones.

:popcorn:

Great! Good to know that the same solution worked for someone else.

Perhaps an admin or mod should mark this thread as solved?

---

### Post by Troy T on 2011-01-23
Got mine working too thanks to David_1989
Although have some connection difficulties - it all seems a bit unstable.
(Probably something to do with my being a Noob!!)

---

### Post by david_1989 on 2011-01-29
> **Troy T said:**
> Got mine working too thanks to David_1989
Although have some connection difficulties - it all seems a bit unstable.
(Probably something to do with my being a Noob!!)
I know what you mean, I have similar problems with an unstable connection, but I think it is just that the card doesn't get great reception and in my case my router is the otherside of 2 walls. 300Mbps wireless N helps a lot in terms of speed and stability. 

The card for me is just as unstable in Windows as it is in Ubuntu.

---

### Post by Fullmetal78 on 2011-02-14
Thank you for your help this was a great thread with the usual excellent support :)

---

### Post by Fullmetal78 on 2011-03-13
> **david_1989 said:**
> I just wanted to say that I have the Tenda W322P V2 and it did not work out of the box with Ubuntu 10.10, however I have managed to get it working beautifully with great wireless N speeds and WPA2. I have the Tenda W322P V2 which has a Ralink 3062 chip.

Basically follow [these instructions]("http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/") to install the driver.

In addition you must also blacklist the following modules in /etc/modprobe.d/blacklist.conf by adding:
```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```Also add the following modules in /etc/modules:
```
rt3562sta.ko
rt3562sta
```Finally reboot after doing all this.


Someone please try this and then we can mark the thread as solved if this works. Please ask if you have problems as there may have been something I missed seeing as tried numerous things to get the card to work.

Morning, this worked for 10.04, how ever when I upgraded to 10.10 I have problems getting it to work :( 

Can you help, hopefully the screenshots attached will help. I have noticed no ra0 when checking the iwconfig but I am sure I download the correct driver and firmware (I have followed the instructions to the letter and it did work until the upgrade).

Thank you , David

---

### Post by hexag on 2011-03-19
Just wanted to say, david1989, you're a star, works a treat, thanks mate! If you've got an issue at all with this card, I reckon this guy's got the goods ;)

---

### Post by david_1989 on 2011-03-20
> **Fullmetal78 said:**
> Morning, this worked for 10.04, how ever when I upgraded to 10.10 I have problems getting it to work :( 

Can you help, hopefully the screenshots attached will help. I have noticed no ra0 when checking the iwconfig but I am sure I download the correct driver and firmware (I have followed the instructions to the letter and it did work until the upgrade).

Thank you , David

Hi,

The one problem I have is that after any kernel update you have to reinstall the drivers. Thus, what I would suggest to people is that after they follow the install instructions for the first time they leave the folder where they extracted the drivers on their hard drive. This will mean whenever there is a kernel update, all you need to do is run make and then make install to reinstall the drivers. Then simply modprobe rt3562sta and the drivers should be back working. This is what I do anyway.

For example, in the terminal
```
cd 'the folder where the drivers were downloaded and compiled from before'
make
sudo make install
sudo modprobe rt3562sta
```

Your wireless should then be back up and running as it was before.

---

### Post by Fullmetal78 on 2011-03-23
> **david_1989 said:**
> Hi,

The one problem I have is that after any kernel update you have to reinstall the drivers. Thus, what I would suggest to people is that after they follow the install instructions for the first time they leave the folder where they extracted the drivers on their hard drive. This will mean whenever there is a kernel update, all you need to do is run make and then make install to reinstall the drivers. Then simply modprobe rt3562sta and the drivers should be back working. This is what I do anyway.

For example, in the terminal
```
cd 'the folder where the drivers were downloaded and compiled from before'
make
sudo make install
sudo modprobe rt3562sta
```Your wireless should then be back up and running as it was before.

Cheers Dave.

Still having issues (see screenshot)

The files are already in the correct folders and I can see it under 'connect to hidden wireless network' but after entering the network password it tries but comes back to log in screen.

Any help would be appreciated.
David

---

### Post by david_1989 on 2011-04-01
> **Fullmetal78 said:**
> Cheers Dave.

Still having issues (see screenshot)

The files are already in the correct folders and I can see it under 'connect to hidden wireless network' but after entering the network password it tries but comes back to log in screen.

Any help would be appreciated.
David

Hmm, Im not really sure what's going on. Try downloading the firmware again and copying it to the right folder, as per the instructions.

---

### Post by Fullmetal78 on 2011-04-03
> **david_1989 said:**
> Hmm, Im not really sure what's going on. Try downloading the firmware again and copying it to the right folder, as per the instructions.

Thanks David

I did that and still issues but I used the sudo command on everything such as modprobe and it did the trick :)

Thanks again for your help, I am learning about command lines..

David

---

### Post by david_1989 on 2011-04-03
> **Fullmetal78 said:**
> Thanks David

I did that and still issues but I used the sudo command on everything such as modprobe and it did the trick :)

Thanks again for your help, I am learning about command lines..

David
:D Great news to hear that you've managed to get it working!

---

### Post by david_1989 on 2011-04-03
> **david_1989 said:**
> I know what you mean, I have similar problems with an unstable connection, but I think it is just that the card doesn't get great reception and in my case my router is the otherside of 2 walls. 300Mbps wireless N helps a lot in terms of speed and stability. 

The card for me is just as unstable in Windows as it is in Ubuntu.

I've changed my mind about this. Wireless N works fine on Windows, but it is a bit unstable on Ubuntu. Wireless G works equally as perfect on both. In fact I now have my router running on G because Wireless N on this card in Ubuntu is irritatingly unstable. Hopefully there will be a driver update soon.

---

### Post by nikonicanicanon on 2011-04-08
hello
I really am very new to Ububtu and I could not install my card (tenda 322p) and I have followed several steps of which are mentioned here, but I think my problem is different ... when I run
sudo iwlist wlan0 scan
wlan0    No scan results

---

### Post by david_1989 on 2011-04-09
> **nikonicanicanon said:**
> hello
I really am very new to Ububtu and I could not install my card (tenda 322p) and I have followed several steps of which are mentioned here, but I think my problem is different ... when I run
sudo iwlist wlan0 scan
wlan0    No scan results

This card does not install as wlan0, instead it installs as ra0.

Try my instructions in this thread:
[http://ubuntuforums.org/showpost.php?p=10289943&postcount=38]("http://ubuntuforums.org/showpost.php?p=10289943&postcount=38")

Let me know how you get on.

---

### Post by nikonicanicanon on 2011-04-09
ok, perfect... so i have a problem, when i try to add in the blacklist.... i can´t, and i revise the tool of user privileges and supposedly I have all the permissions.

thanks for the support!!!

---

### Post by chili555 on 2011-04-09
What happens when you do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Can you add the text and save the file? What is the error message?

---

### Post by nikonicanicanon on 2011-04-09
fully operational .... david thank you very much and chilli ... do not have the support of people like you in the forums Hispanics ...

---

### Post by david_1989 on 2011-05-01
> **david_1989 said:**
> I just wanted to say that I have the Tenda W322P V2 and it did not work out of the box with Ubuntu 10.10, however I have managed to get it working beautifully with great wireless N speeds and WPA2. I have the Tenda W322P V2 which has a Ralink 3062 chip.

Basically follow [these instructions]("http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/") to install the driver.

In addition you must also blacklist the following modules in /etc/modprobe.d/blacklist.conf by adding:
```
blacklist rt2800pci
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2800lib
```

Also add the following modules in /etc/modules:
```
rt3562sta.ko
rt3562sta
```

Finally reboot after doing all this.


Someone please try this and then we can mark the thread as solved if this works. Please ask if you have problems as there may have been something I missed seeing as tried numerous things to get the card to work.

Just to say that these instructions still work in 11.04.

---

### Post by nikonicanicanon on 2011-05-06
yes, works 100 %.... just my imagination or firefox 4 is faster than chrome?

---

### Post by xgalexyx on 2011-06-04
[FONT="Arial"]I am having the same problem and i followed the instructions in davids link but i couldn't find the rt280.bin file. I have completed all other steps and ubuntu can now detect wireless networks but when i try to connect to my home router it never manages to connect. Windows 7 connects perfectly on the same computer. Is it because i couldn't find a rt280.bin file to but in the framework?[/FONT]

---

### Post by xgalexyx on 2011-06-04
[FONT="Verdana"]I have just found out that ubuntu can connect to unsecured networks but not wpa2 secured ones. I have a bt home hub and it has an openzone where you can connect without security and it works. Problem is if you leave the openzone page it tries to charge you. Am i missing something?[/FONT]

---

### Post by david_1989 on 2011-06-12
> **xgalexyx said:**
> [FONT="Verdana"]I have just found out that ubuntu can connect to unsecured networks but not wpa2 secured ones. I have a bt home hub and it has an openzone where you can connect without security and it works. Problem is if you leave the openzone page it tries to charge you. Am i missing something?[/FONT]

Sounds like wpa_supplicant is not enabled. I suggest that you follow all my instructions from the beginning again, including re-downloading the drivers and pay particular attention to point 5 in the instructions that are on the page to which I gave a link to.

---

### Post by moisea on 2011-12-09
Sorry for just bugging you all, i am having a slightly different problem with my tenda 322P wireless card.just got it, fit it in and all connected fine. ie.It shows the connected icon and also everything seems fine under the connection information and the driver being used is the RT2800 PCI but I JUST CANNOT BROWSE THE INTERNET. HELP PLEASE!

---

### Post by david_1989 on 2011-12-25
> **moisea said:**
> Sorry for just bugging you all, i am having a slightly different problem with my tenda 322P wireless card.just got it, fit it in and all connected fine. ie.It shows the connected icon and also everything seems fine under the connection information and the driver being used is the RT2800 PCI but I JUST CANNOT BROWSE THE INTERNET. HELP PLEASE!

Have you tried these instructions originally posted on page 4 of this thread?

[http://ubuntuforums.org/showpost.php?p=10289943&postcount=38]("http://ubuntuforums.org/showpost.php?p=10289943&postcount=38")

---

### Post by billypoke on 2012-03-13
> **david_1989 said:**
> Just to say that these instructions still work in 11.04.
And 11.10.  It was making me so angry that it wasn't working at first, but after editing the blacklist and modules, it works perfectly

---

### Post by nerderello on 2012-04-26
just to add some more observations.

I run a PC with both an old, continously upgraded partion which now has **11.10** (now using XFCE, but still with a lot of Gnome stuff and the usual kreft left over from years of use) and a **Xubutu 11.10** partition which is a fresh/clean install (on both I had a USB Dongle giving the wlan connection, and it is this that has now been successfully replaced by the Trenda W322P PCI card).

I got this card working with the Xububtu (11.10) by following the above instructions and getting the compiled rt3562sta module loaded (I couldn't find the bin file either - see earlier post - so couldn't copy that firmware file across, but that didn't cause any problems) I also found that I didn't need to do the bits to load the rt3562sta module, it happens automagically.

**HOWEVER** the old (been upgared amd upgrade over the years) partition was a [COLOR="Red"]pig[/COLOR]. I followed the instructions and could get iwconfig and ifconfig to show the card, but I couldn't get it to connect to my router.

First I went thru and cleared up some stuff left over in /etc/NetworkManager  to make it look like this:
> [main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Also cleaned up the other files that the above instructions tell you to edit.

But to no avail, then I did the usual "compare the working one with the non-working one file by file" (I really must get a life...) and changed [FONT="Arial"]/etc/network/interfaces[/FONT] to read:
> auto lo
iface lo inet loopback

#auto ra0
#iface ra0 inet dhcp

(ie. to get rid of/comment out the **ra0** stuff)
rebooted and it came straight up!!!!

---

### Post by nerderello on 2012-04-28
**_12.04 LTS_**
Further to the above post, I've just upgraded my Xbuntu partition from 11.10 to 12.04 LTS and had to do a 
[FONT="Courier New"]make clean
make
sudo make install[/FONT]
Which was as expected, everything else was left as above.

---

### Post by nerderello on 2012-04-29
**12.02 LTS update**
Since posting the above I realised that, thanks to blacklisting the rt2800/rt2x00 modules, I hadn't actually tried this card with the 12.02 versions of these modules, so...

They work (as in if you un-blacklist them and reboot), **[SIZE="4"]BUT[/SIZE]** there is a problem. The signal level (reported by the network manager plugin) is only about half what the rt3562sta module gives and when I ran a speed test (speedtest.net) the rt2800 modules gave about 0.6 meg recieve, while the rt3562sta gave about 5meg (big difference).

So, even though they work, the rt2800 modules don't work properly.

---

### Post by nerderello on 2012-05-01
another observation about the use of the rt3562sta driver with the W322P card, my syslog was filling up with loads of messages like these :
[FONT="Courier New"]> 
<--- rt28xx_get_wireless_stats
MediaState is connected
==>rt_ioctl_giwmode(mode=2)
==>rt_ioctl_giwfreq  11
[/FONT]

To get rid of a lot (but not all) of the messages from my syslog, I edited **/os/linux/config.mk** (the same file that you are advised to edit in the instructions shown in earlier posts) so that the line 

[FONT="Courier New"]WFLAGS += -DCONFIG_STA_SUPPORT -DDBG[/FONT] 

becomes 
[FONT="Courier New"]WFLAGS += -DCONFIG_STA_SUPPORT[/FONT] 
(ie. remove the -DDBG bit). 

Then I re-did the make (ie. [FONT="Courier New"]sudo make clean[/FONT], [FONT="Courier New"]sudo make[/FONT], [FONT="Courier New"]sudo make install[/FONT]) and bounced the module (stopped wireless networking with the network manager, then [FONT="Courier New"]sudo rmmod rt3562sta[/FONT] then [FONT="Courier New"]sudo modprobe rt3562sta[/FONT], then re-enabled wireless networking using the network manager).

There are now a lot fewer messages being put into my syslog.

---

