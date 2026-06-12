---
title: "Wireless not recognized...Ubuntu 9.04"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by mudman00 on 2009-05-29
Hello, I upgraded from 8.10 to 9.04 hoping that my machine would miraculously recognize the wireless network and save my Linux challenged backside from another several hours of messing around. Well, it didn't...sigh

I am however, committed to hanging in there with Ubuntu. Even if I actually have to really learn something about the operating system and be able to enter command line script. No more evil empire for me.....regardless of what my spousal unit has to say about my snail like learning curve...bear with me please...I am not all that savvy with computers, especially on the soft ware end of things.

Anyway, I am using a Linksys WIreless G PCI Adapter2.4 gig card, Model:WMP54G.....

I have not ever tried to connect the machine via the wireless, though we have two laptops with that viral code from Washington that connect quite well at this very moment.

What do I need to install, extract and direct in order to use the wireless connectivity in 9.04? 

The system does not seem to recognize any wireless network(s) at this time. The router is only a few feet away. 

Do I need to put the ndswrapper on the machine and go from there. Is it self explanatory? I am able to follow a procedure if someone will point me to one that applies to 9.04

Any and all help is greatly appreciated!
Thank you,
Craig

---

### Post by Iowan on 2009-05-29
Post results of **lshw -C network**. You could also post results if **iwconfig** and **ifconfig**, but I suspect they'll report no IP address for wireless.

---

### Post by mudman00 on 2009-05-31
Iowan....thank you for the help. Here is the result of entering the commands in a terminal....I am very new to this.

craig@benedictisanass:~$ Ishw -C network
bash: Ishw: command not found
craig@benedictisanass:~$ Iwconfig
bash: Iwconfig: command not found
craig@benedictisanass:~$ Ifconfig
bash: Ifconfig: command not found
craig@benedictisanass:~$ 

Craig

---

### Post by snideatlondon on 2009-05-31
Craig, don't use capitals for iwconfig and ifconfig mate. and spell the first command with l (as in lima)... cheers

---

### Post by mudman00 on 2009-06-02
Thank you for the reply....here is what I got with the first command

Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

Thank you again....I can't say that I know what this means though.
Craig

---

### Post by mudman00 on 2009-06-02
And here is what I get with the lower case ifconfig and iwconfig

craig@benedictisanass:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:5b:13:1d  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe5b:131d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16609256 (16.6 MB)  TX bytes:3369522 (3.3 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

craig@benedictisanass:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Craig

---

### Post by uupreti on 2009-06-02
> **mudman00 said:**
> Thank you for the reply....here is what I got with the first command

Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.13)



I think you put C in lower case. That's why it is giving you help menu instead of output. it is 
**lshw -C network**     Only C is uppercase.

Also try command **dmesg** and **lspci** to see if there is any entry for wireless device.

As per output of iwconfig, it seems you dont' have wireless card's driver installed or ubuntu couldn't recognize your wireless driver.

Which card you are using?

---

### Post by mudman00 on 2009-06-03
> **uupreti said:**
> I think you put C in lower case. That's why it is giving you help menu instead of output. it is 
**lshw -C network**     Only C is uppercase.

Also try command **dmesg** and **lspci** to see if there is any entry for wireless device.

As per output of iwconfig, it seems you dont' have wireless card's driver installed or ubuntu couldn't recognize your wireless driver.

Which card you are using?
Thank you for your reply.......I am using a Linksys WIreless G PCI Adapter2.4 gig card, Model:WMP54G............I do not think that it is being recognized. I suspect that it is the problem. The system does not seem to be recognizing any wireless networks and I know that there are two others that are recognized by my spousal units laptop which still has that viral code from washington on it.....

I do not know what to do to install the necessary driver for the wireless card to work. If possible, I want to use whatever Ubuntu open source for Jaunty that is available. Is there a specific application that I should download?

Alternatively, I could just get another wireless card that Ubuntu is happier with. I don't have to use the old card that I put in the box. Trading out is not a problem.
Thank you again,
Craig

---

### Post by uupreti on 2009-06-03
I have not used Linksys with Ubuntu but I saw couple of forums point about linksys. I use Broadcom Wireless card which worked right out of the box for me with Jaunty. 

If you still try to make your existing device to work, you may probably play with **ndiswrapper** ( which is a free software driver wrapper that enables the use of Microsoft Windows drivers for wireless network devices on Unix/Linux operating systems.

Take a look at this.

[http://ubuntuforums.org/showthread.php?p=40016](http://ubuntuforums.org/showthread.php?p=40016)

---

### Post by DavidFourer on 2009-06-03
mudman00 and iowan,

I have the same problem, So I'd like to piggyback here.  Wireless Networks is "greyed out in NetworkManager.  I had wifi roaming reporting many routers in the neighborhood, and a good connection, with Intrepid Ibix.  My card is Broadcom 4318 (Dell 1370 internal wireless).  The broadcom B43 wireless driver is "installed and in use" after the recent install.  That's what I used with the Intrepid, when wifi roaming worked in NetworkManager.

Here's all the output from
lshw -C network
ifconfig
iwconfig
lspci
dmesg (file)

Any basic information you care to share is appreciated.  I've been trying to learn more about this for a long time now.

Thanks,
David
> david@david-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:da:6f:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.101 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:37:aa:84
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: b2:b0:45:67:0b:e1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
david@david-laptop:~$ 
> david@david-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

david@david-laptop:~$ 
> david@david-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:da:6f:e2  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feda:6fe2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63950 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70752906 (70.7 MB)  TX bytes:9633072 (9.6 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14276 (14.2 KB)  TX bytes:14276 (14.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:37:aa:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A4-37-AA-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

david@david-laptop:~$ 
> david@david-laptop:~$ lspci
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
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
david@david-laptop:~$ 

for dmesg output, I'll have to link to a file.  I don't know how to attach it.
[https://home.comcast.net/~dfourer/misc/dmesg.txt](https://home.comcast.net/~dfourer/misc/dmesg.txt)

Thanks,
David
Chicago, IL

---

### Post by uupreti on 2009-06-04
Hello David!
You outlook looks pretty close towards getting connected. I can see your wireless card is not getting ip address from our router. Are you able to scan your network (SSID)? 

when I see output from your system, it seems your card is recognized by Ubuntu. So I will suggest you trying to configure DHCP for wlan0 from network manager..

---

### Post by DavidFourer on 2009-06-04
> **uupreti said:**
> I can see your wireless card is not getting ip address from your router. Are you able to scan your network (SSID)?I have a wired network connection with NetworkManager.  I don't know what you mean my scan my network.  Normally, when it worked, the roaming picks up a long list of wifi signals--from the neighbors.  Now there is no list, no signals listed.  I have an ssid and password and wep-128 key for my own wireless.  I've tried using NetworkManager applet/edit connections, to manually make connection to my own wifi.  I'm not sure I'm doing it right.   
> when I see output from your system, it seems your card is recognized by Ubuntu. So I will suggest you trying to configure DHCP for wlan0 from network manager..So far I don't know how to do this.  Later I can try to figure it out.

David

---

### Post by uupreti on 2009-06-04
As far as I understand you are concern about your wireless device to be connected to any of avialbale SSID right? SO my question is if you have wireless access point of your own or your neighbor, Can you try to scan this by using following command..

```
 iwlist wlan0 scanning 
```

And please post the output also..Thanks

---

### Post by DavidFourer on 2009-06-04
```
david@david-laptop:~$ sudo iwlist wlan0 scanning
[sudo] password for david: 
wlan0     No scan results

david@david-laptop:~$ 

```
I checked to make sure I have "enable wireless" checked in NM, and also that my hardware light is on indicating the wifi card turned on.  I just have this feeling that it's some simple little thing that's holding it up.  

David

---

### Post by uupreti on 2009-06-04
If you hardware light is not showing your wireless is enabled then may be first thing is you want to make sure everything is good from that part. In my case orange light will show wifi is off and blue light shows wifi is on. 

Then after try to scan again. Even if you turn on your button and light is still same then may be it's turn to re-install or reactivate your driver from System->Administration->Hardware Drivers.

---

### Post by adrock1942 on 2009-06-17
I also have the WMP54G, and it is recognized using "lspci". However, after using the command "iwlist wlan0 scanning", the output is "wlan0     Failed to read scan data : Resource temporarily unavailable". Not sure what to do about that.

---

### Post by Jahendo on 2009-06-17
Hey guys,

Fairly new to the forum, and am finally getting to a hurdle I can't quite fix.  If this is in the wrong place, I apologize, but it seemed fitting.

I am using an IBM Thinkpad T42 with Ubuntu 8.10.  I just moved into a new place with wireless, and I can't connect to the router!  

The router is a NetGear WNR2000. My PC card is a Cisco Aironet wireless 802.11b.  It's internal, and the only pictures and info I found was on an adapter.  Mine is built in.

  I know the router is working, because I set it up on this computer.  Also, tested the connection with my Wii.  My PC wireless is working, because I can pick up other networks in the area.  I know it's a simple question, but I can't find the answer in all my searching.

Is the problem a compatibility issue between my portable and the router?

Will upgrading to 9.04 fix the issue?  

Thanks, guys.

David, good luck.  You seem to handle yourself well with a computer.

---

### Post by Ayuthia on 2009-06-18
> **DavidFourer said:**
> ```
david@david-laptop:~$ sudo iwlist wlan0 scanning
[sudo] password for david: 
wlan0     No scan results

david@david-laptop:~$ 

```
I checked to make sure I have "enable wireless" checked in NM, and also that my hardware light is on indicating the wifi card turned on.  I just have this feeling that it's some simple little thing that's holding it up.  

David

I am guessing that the firmware has not been installed for the b43 module (the wireless module that makes your card work).  As mentioned earlier, please check System->Administration->Hardware Drivers to see if the Broadcom wireless option is available.  However, I have read in some posts that the 4318 card does not always get recognized.  If that is the case for you and you have a working connection in Ubuntu, please try the following:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
You will then need to reboot or do the following:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe b43
sudo modprobe b44
sudo ifconfig eth0 up
sudo ifconfig wlan0 up
sudo iwlist scan
```
Most of those commands will not return anything.  However the last one hopefully will return a list of wireles sites.

Hope that helps.

---

### Post by Ayuthia on 2009-06-18
> **Jahendo said:**
> Hey guys,

Fairly new to the forum, and am finally getting to a hurdle I can't quite fix.  If this is in the wrong place, I apologize, but it seemed fitting.

I am using an IBM Thinkpad T42 with Ubuntu 8.10.  I just moved into a new place with wireless, and I can't connect to the router!  

The router is a NetGear WNR2000. My PC card is a Cisco Aironet wireless 802.11b.  It's internal, and the only pictures and info I found was on an adapter.  Mine is built in.

  I know the router is working, because I set it up on this computer.  Also, tested the connection with my Wii.  My PC wireless is working, because I can pick up other networks in the area.  I know it's a simple question, but I can't find the answer in all my searching.

Is the problem a compatibility issue between my portable and the router?

Will upgrading to 9.04 fix the issue?  

Thanks, guys.

David, good luck.  You seem to handle yourself well with a computer.

You have a different card than the original poster.  You will be better off creating another thread.  Please include the results of:
```
lspci -nn
lshw -C network
```They will help us see the wireless card information and what module it is trying to use.

---

