---
title: "Another bcm4318 problem card."
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by elmore724 on 2009-02-10
Hi. New Linux user with wifi problem. I have the dreaded broadcom 4318 pos card and need help getting it installed. I've read tons of other threads with this same issue but the results I got with them did not work. So I'm here begging for help.  I just did another clean install with ubuntu 8.10.  My wired ethernet card does not work either (due to lighting) so I have to copy and paste stuff to get it here.  I do have ndiswrapper installed as well as fwcutter.  I've also downloaded the drivers file for the wireless card (per one of the threads but not even sure if its the right one).  The wireless card is brand new and works with *xp installed. **sorry to use foul language on your forum**.  I'll list a couple of command outputs below. If I could get one of you wise linux guru's help it would make my day. Thanks!

pedro@user:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:9a:33:77  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16464 (16.4 KB)  TX bytes:16464 (16.4 KB)

pedro@user:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

---

### Post by elmore724 on 2009-02-10
pedro@user:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:9a:33:77
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0e:9b:d1:a4:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:3a:c6:85:57:7b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Ayuthia on 2009-02-10
Is this an Acer?  I think that some Acer laptops need the acerhk module also.

For ndiswrapper, you might try:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
```

I did not restart your wired ethernet card since you said that it is no longer functional.

---

### Post by elmore724 on 2009-02-10
No sorry its a Dell inspiron 5100. I just put in all those commands and all were successful.  Card still is not working.  I have not loaded any other drivers yet that did not load when the system was installed btw.  If I open my system, administration, Hardware Drivers there are no proprietary drivers in use on my system.  I also have not blacklisted anything like other people that I've read in other posts. Not sure if that helps.

---

### Post by Ayuthia on 2009-02-10
> **elmore724 said:**
> No sorry its a Dell inspiron 5100. I just put in all those commands and all were successful.  Card still is not working.  I have not loaded any other drivers yet that did not load when the system was installed btw.  If I open my system, administration, Hardware Drivers there are no proprietary drivers in use on my system.  I also have not blacklisted anything like other people that I've read in other posts. Not sure if that helps.

Let's try out the b43 module.  Verify that the firmware has been installed by checking to see if there are files in /lib/firmware/b43.  You can do this through Nautilus or through the Terminal:
```
ls /lib/firmware/b43
```

If it is there, reload the b43 module:
```
sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe b43
sudo ifconfig wlan0 up
dmesg|grep b43
```
The dmesg command will return some information about the b43 module.  Please check and make sure that there are no messages about the firmware being too old and that the radio is not turned off.  If all looks fine, check and see if you can scan for wireless sites:
```
sudo iwlist scan
```

---

### Post by elmore724 on 2009-02-10
No b43 is not there. No such file or directory.  How should I load this?

---

### Post by elmore724 on 2009-02-10
bump

---

### Post by elmore724 on 2009-02-10
anyone? I'll be here a bit longer.

---

### Post by Ayuthia on 2009-02-10
You can try this link:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by elmore724 on 2009-02-11
YES! I didnt think that was going to work due to the last line being an error No wlan0 device found. But after I restarted the whole system (shutdown) I now have a connection! I now think that the driver I had was wrong before.  I have not used the files you linked before.  THANK YOU THANK YOU for your time and effort! Now I wont have to go back to microsoft!:KS:KS:KS


The only concern I have now is that I'm sitting 3 feet from my wireless router and only get a signal of 68%. I'll look for other suggestions on this on the forum unless you have any ideas.

---

