---
title: "Broadcom Issue (well researched before posting) :)"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by jermanbdogg on 2011-02-14
First off I have scoured the i-net/ubuntuforums for a solution and have yet to find one that works (or that I have tried correctly...I am sorta-new).

Hardware: HP Mini 1119nr with broadcom 4312 chip (on PCI-ID: 14e4-4315).

When I did a clean install, I didn't have either ethernet or wireless. I have been trying to find a solution with either using the install media (via usb) or transfer/compile via thumbdrive.

I am looking for some hands-on troubleshooting with this (in case I was actually doing it wrong and bypassed the problem).

Anything is greatly appriciated.
-Thanks. :p

Some of the links that I have researched:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)
[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)
[http://ubuntuforums.org/showthread.php?t=1586366](http://ubuntuforums.org/showthread.php?t=1586366)

---

### Post by jermanbdogg on 2011-02-14
[B]Install B43 Broadcom Wireless Driver on HP Mini 1119nr 
Ubuntu 10.10 Desktop edition &#8211; from clean install (no wired or wireless connection at start up)
PCI-ID: 14e4:4315
Driver needed: BCM4312  LP-PHY[/B]

My install guide was made from 2 sources:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)
[http://fedoraforum.org/showthread.php?t=218303](http://fedoraforum.org/showthread.php?t=218303)

In order to find out what the PCI-ID and driver that you need type:

lspci -vnn | grep 14e4
The result will look something like this (just an example from website source)

0001:01:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

In the example PCI-ID is 14e4-4318 and the Driver chip is BCM4318
	-If in running this command you receive a different PCI-ID or different Driver chip please refer to the first link in my sources to determine what version of the files you will need to obtain

**Before starting make sure that the power and ethernet cable is plugged in**

From a working internet computer download b43-fwcutter (version 13 at time of posting) from:
[http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)

and

Download broadcom-wl-4.178.10.4.tar.bz2  (incorrectly labeled) should be 4.174.64.19 (label not important though) from:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)

Put them in a folder called drivers and put it on a thumb drive and move it to the problem computer on the desktop.

Go into the drivers folder on the desktop and double click on b43-fwcutter.deb to install it. (it will open software center &#8594; click on install. Once it is installed close software center.

Back in Nautilus, right click on broadcom-wl-4.178.10.4.tar.bz2. Left click on extract here.

In the Ubuntu menu click on Applications &#8594; Accessories &#8594; Terminal

Type:  
cd Desktop/drivers/broadcom-wl-4.178.10.4.tar.bz2/linux

Then type: 
sudo b43-fwcutter -w /lib/firmware wl_apsta.o
(this is going to build the driver in the firmware folder)

Reboot the computer

After logging in you should have a wired connection. (check Firefox for internet connection) Also check to see if the blue light is on the front of the laptop. (if not flip the switch to see if it comes on)
	-if light is on, check the network connection icon to see if a list of wireless networks come up.
	
*****this is where everything was goofy*****
At this point I was not able to connect to anything but I saw a list of networks. I turned off all my router encryption settings and was still not able to wirelessly connect even after another reboot. (with or without the ethernet plugged.)

Run update manager (on menu System &#8594; Administration &#8594; Update Manager)
	click the &#8220;Check&#8221; button to find a list of updates and once done click &#8220;Install Updates&#8221;
	*this is going to take a while as a new kernel is also going to be loaded*

(I also received an error when checking for updates stating that I didn't have an internet connection but the updates downloaded and installed without error as I did, in fact, have an internet connection even.)	-not sure what happened on this part

Reboot Computer after updates complete

From here I had ethernet connection, however, I still was not able to connect to a wireless network, however, I am able to see the wireless networks in the area.
	- not sure as to what to do here

***Could someone help me out to work on this***
I am going to reply again to show outputs on network commands.

---

### Post by jermanbdogg on 2011-02-14
**Here is the output for sudo rfkill list**

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


**Here is the output for ifconfig**

jerry@jerry-netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:46:a3:bd  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe46:a3bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1556026 (1.5 MB)  TX bytes:208806 (208.8 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:bd:4e:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**Here is the output for lshw -C network**

jerry@jerry-netbook:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:24:81:46:a3:bd
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.2.7 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:febfc000-febfffff ioport:ec00(size=256)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2b:bd:4e:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-25-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by PRC09 on 2011-02-14
Just read on another post that the b43 documents didnt help you.According to your network card info "product: BCM4312 802.11b/g LP-PHY" you may need the LP-PHY part installed.I just stumbled on this while trying to install a broadcom card in Natty(another story).If you can go into System > Admin > Synaptic and search for b43.You should see 4 entries there.Check if the Firmware-b43-lpphy-installer is installed and if not try installing it and see if it works then......

---

### Post by jermanbdogg on 2011-02-14
It's funny that you mentioned that. That was the last thing I tried. I have it already installed and it didn't work. oi vey.

*scratches head

---

### Post by PRC09 on 2011-02-14
Assuming you have tried reboot....

---

### Post by jermanbdogg on 2011-02-14
Yeah. Reboot x 5. I wish it were that simple. :)

---

### Post by PRC09 on 2011-02-14
What else is installed under the search for b43?I have the standard b43 installer, and b43 fwcutter.Also if you search broadcom my install has the bcmwl-modaliases installed.I did not install this seperately.,so it must have installed when I activated the driver altho I use a b43 card...maybe....

---

### Post by jermanbdogg on 2011-02-14
I have two installed. The b43-LPPHY and fwcutter.

The other two that aren't installed is the standard b43 and legacy b43.

[edit]: under the search for bcmwl I also have modaliases installed.  Will try uninstalling and see if that does the trick.
[edit x2]: It didn't work. But it didn't make it worse either. Same as before. I get a network listing but cannot connect to it.

---

### Post by PRC09 on 2011-02-15
OOPS!!! I assumed you couldnt see any networks,so if you can see them and try to connect what does it say or do......

---

### Post by jermanbdogg on 2011-02-15
I can't. When I try to connect to a wireless network through the list the wifi meter goes up and down like it is trying to connect but ends up disconnected (it times out). I also tried to delete the auto connect in the "Edit Connections" option and try to reconnect but it just does the same thing.

---

### Post by PRC09 on 2011-02-15
Hmmmmmmm......

---

### Post by jermanbdogg on 2011-02-15
lol that is what I have been saying for 4 days.

---

### Post by PRC09 on 2011-02-15
I guess you could try the STA driver instead as it is listed as supported by that driver but it conflicts with the b43 version.See the attached link.I am no expert at this.....Happy reading....

[http://wireless.kernel.org/en/users/Drivers/b43#Known_issues](http://wireless.kernel.org/en/users/Drivers/b43#Known_issues)

---

### Post by jermanbdogg on 2011-02-15
Well. I think I am at witts end with this. Asside from compiling the kernel from source with the drivers included and turning on the PIO module, there is no way to get my netbook up and running with ubuntu (at least for now). 

I am going turncoat and putting XP back on it if it isn't solved by the end of the week.

Please help me change my mind ANYONE!!!!!! I miss my conky script!!!! :)


HELP!!!!

---

### Post by JBAlaska on 2011-02-15
Were you able to connect with a Ethernet cable?, if so connect with Ethernet and do:
```
sudo apt-get update
```
Then:
```
sudo apt-get install bcmwl-kernel-source
```
Now reboot and select the **BroadcomSTA** driver in **System, Administration, Hardware Drivers** Reboot again and your wireless should work.

If you can't connect with the cable, you'll have to d/l bcmwl-kernel-source for your distro with another computer and use a thumb drive to install it on your Mini.

---

### Post by jermanbdogg on 2011-02-15
I already have it installed and enabled, however, I rebooted and got the same result. I can see the list of active wireless networks but cannot connect with them

---

### Post by JBAlaska on 2011-02-15
Have you tried with your router open (Unencrypted)?

Also please post the output from ```
sudo lsmod | grep b43
```

---

### Post by jermanbdogg on 2011-02-15
lol. i just logged on here to to state that I am THAT retard. I tried to connect to my wifi with my phone to manage my xbmc. I wasn't able to. After that it just clicked. I went into the router settings and fiddling with them to see what was the problem. )Turns out that I added every computer that I owned to the wireless mac address filter (like I said,,,,,THAT retard). Turned that off and everything is working. I was so focused on the driver issue that I forgot that it could be anything else. Thanks to all that helped me. It is much appriciated and sorry for the wasted time.

):P

---

### Post by PRC09 on 2011-02-15
Lol...](*,)

---

### Post by JBAlaska on 2011-02-16
Great to here your connected! And don't feel bad, I've been "That" retard many times lol.

---

