---
title: "Newbie - Cannot find Network - wifi"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by jmauster on 2008-12-02
Hi, I hope this is enough information to find some help. I cannot find any way of making a wireless connection. 

When I run lshw -C network I get this result:

  *-network DISABLED      
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:a6:6f:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:bf:23:51:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 92:88:7e:4b:f6:de
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



And when I run lspci I can tell that I am running: 

Network controller [0280]: broadcom corporation BCM4318 [Airforce One 54g] 802.11 Wireless LAN controller [14e:4318] (rev 02) 
Subsystem: Linksys Device [1737:0049]


Any ideas on how I can get this working? 


Many thanks,

---

### Post by jmauster on 2008-12-02
also, I think this information might be helpful. 


```
evan@evan-laptop:~$ iwconfig
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
```

---

### Post by akira86 on 2008-12-02
hello

post the answer of the command line :
sudo iwlist wlan0 scan

---

### Post by transverse_wave on 2008-12-02
I'm not the OP but I have the exact same problem in terms of my lshw says that my wireless device is disabled...

 sudo iwlist wlan0 scan 
returns the following:

wlan0     Interface doesn't support scanning : Network is down

---

### Post by Cenotaph on 2008-12-03
You need to install the firmware for your card, BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller.

run

```
sudo apt-get install b43-fwcutter
```

in the terminal and when asked to obtain the firmware say yes.

Of course you'll need a wired connection to do this, if that isn't an option you should get the firmware file from here:

[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

extract this file and get the wl_apsta_mimo.o file in the driver folder and get it into ur pc using a USB flash drive or something similar.

then you should install b43-fwcutter from the ubuntu installation CD with the same command i pasted above

and run

```
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

assuming your in the same directory as the .o file, if not just point to the file's path.

I should mention that the **Restricted Drivers Manager** included in Ubuntu will also do everything for you, provided you have a working wired connection. And it's probably the **easiest way** for a newbie to get the card working. Just update your Ubuntu with the wired connection and it should be there to activate.

---

### Post by jmauster on 2008-12-03
Thanks for the help! I think I'm getting close. 

I ran the stuff you said, and now when I go to Hardware Drivers I see Broadcom B43 wireless driver, however when I try to activate it, a progress bar pops up and disappears after 50% through the download step. (obviously, since I'm not able to get online, it's not downloading anything)

Any ideas? 

Here is how things look now: 

```
evan@evan-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16336 (16.3 KB)  TX bytes:16336 (16.3 KB)

evan@evan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

evan@evan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:0f:1f:a6:6f:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:4d:ad:8b:6e:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:bf:23:51:f6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
evan@evan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

evan@evan-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for evan: 
wlan0     Interface doesn't support scanning : Network is down


```

---

### Post by Cenotaph on 2008-12-03
Can't you use a ethernet cable to make you laptop go online and run the Hardware Drivers then?

Maybe you have a desktop who uses a wired connection with a cable you can use or something?

I pretty much already said everything regarding firmware installation. If you managed to install b43-fwcutter, then all you need is that wl_apsta_mimo.o file and run the second command i wrote.

You can find more information on this here:
[http://www.linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://www.linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

---

### Post by jmauster on 2008-12-04
First, thanks again for all you help. 

Okay, I plugged the onboard ethernet card into my router. 

Do I need to do anything for it to show up? When I run lshw I get the same results as posted above. Do I need to fire off anything to the connection detected?

---

### Post by Cenotaph on 2008-12-04
NetworkManager should set up your wired connection automatically if you plugged the cable to your router. Now it's pretty much just opening the Hardware Drivers in System -> Administration and activate the Broadcom wireless adapter.

---

