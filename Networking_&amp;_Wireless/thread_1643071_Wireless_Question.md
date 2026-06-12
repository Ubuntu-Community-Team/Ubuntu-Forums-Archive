---
title: "Wireless Question"
date: 2010-12-11
forum: Networking &amp; Wireless
---

### Post by CiSC0kid on 2010-12-11
I am attempting to connect to my wireless router. When I click on NetworkManager It says Wireless: Disconnected. I then tried to add the connection manually as if it were hidded (even though it should broadcast SSID). 

I have tried with WPA2 and with no security what so-ever. It hangs, tries to connect for a minute or so, then fails. 

I have the Alfa AWUS036nh USB card. Here are my iwconfig and ifconfig ouputs:

```
wlan1     Link encap:Ethernet  HWaddr 00:c0:ca:4a:69:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

god@cisco-tosh:~$ sudo iwconfig wlan1
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=6 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
```

---

### Post by pytheas22 on 2010-12-11
Please post the output of these commands so we'll have more information:
```

lspci -nn
lsusb
sudo iwlist scan
uname -a
lshw -C Network
dmesg | grep wlan
```

Please also let me know the name of the network you're trying to connect to.

---

### Post by CiSC0kid on 2010-12-11
**lspci -nn**


```
root@cisco-tosh:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
04:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
04:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
```

**lsusb**

```
root@cisco-tosh:~# lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:d104 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**sudo iwlist sca**n

```
root@cisco-tosh:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results
```

**uname -a**

```
root@cisco-tosh:~# uname -a
Linux cisco-tosh 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
```

**lshw -C Network**


```
root@cisco-tosh:~# lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:fe:82:a9
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.169.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:5000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d6700000-d6703fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:c0:ca:4a:69:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```


**dmesg | grep wlan**

```
root@cisco-tosh:~# dmesg | grep wlan
[   20.537402] udev: renamed network interface wlan0 to wlan1
[   21.171020] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1580.647521] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1602.056571] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2450.605606] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2488.682695] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 2573.884796] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3348.985998] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3685.489452] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3685.933451] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3789.945564] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 4783.672623] udev: renamed network interface wlan0 to wlan1
[ 4783.997562] ADDRCONF(NETDEV_UP): wlan1: link is not ready
```


The name of the network is wifu. I have tried with no security and WPA2 no luck. When I add it manually, the network manager icon looks like its attempting to connect. I have tried static IPs and DHCP...Thanks for the reply.

---

### Post by pytheas22 on 2010-12-11
Thanks for the information.  Do you have two wireless cards attached to this computer?  From your output, it looks like you have a Ralink-based USB card and an internal card with a Realtek chipset.  The Realtek device is not working at all, probably because you'd need to install a driver for it, which I could help you to do if you'd rather use the internal card than the external one.

As for the external card, it seems not to be able to detect any other wireless networks.  This could potentially be a driver problem, but it could also be an issue with the way your wireless network is configured.  Do you know which channel your router is operating on, and which mode it's in?  Of course, if you'd rather just work on getting the internal card running, you can ignore these questions.

---

### Post by CiSC0kid on 2010-12-11
The external card is the one i rather use at the moment. Especially since I just paid $40 for it since I found my internal card is not listed in the supported cards list.

My router is on channel 6. It is a g router. I am a networking student so I have tried various IP addressing schemes such as DHCP with no security / with security and Static IPs as well. 

The nm-tool command shows me the driver for the device as ***rt2800usb ***and lists the status as ***disconnected***.

---

### Post by pytheas22 on 2010-12-11
I think the issue might come down to two different drivers trying to claim your device, as outlined in [this thread]("http://ubuntuforums.org/archive/index.php/t-1378782.html") (you have the same chipset as the poster there).

Please try running these commands:

```
sudo rmmod rt2800usb
sudo rmmod rt2870sta
sudo modprobe rt2870sta
sudo ifconfig wlan1 up
```

Now wait a few seconds and see if the command "sudo iwlist scan" shows you a list of wireless networks.  If it does, try connecting.

If this doesn't work, what happens with the commands:

```
sudo rmmod rt7870sta
sudo rmmod rt2800usb
sudo modprobe rt2800usb
sudo ifconfig wlan1 up
```

If either of these sets of commands does the trick for you, we can fix the problem so the card will automatically work from now on (without having to type any commands).

---

### Post by CiSC0kid on 2010-12-11
Results from first set of commands:

```
god@cisco-tosh:~$ sudo rmmod rt2800usb
[sudo] password for god: 
god@cisco-tosh:~$ sudo rmmod rt2870sta
god@cisco-tosh:~$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```


And the second:

```
god@cisco-tosh:~$ sudo rmmod rt7870sta
ERROR: Module rt7870sta does not exist in /proc/modules
god@cisco-tosh:~$ sudo rmmod rt2800usb
ERROR: Module rt2800usb does not exist in /proc/modules
```

Thanks for the help. I looked at the article, couldn't make much sense of it.


EDIT:  I removed ndiswrappe, went through the commands again and noticed that the rt2870sta module was loaded. I removed my lan cable and noticed I could finally see wireless networks.

When I attempt to login to mine, it asks for encryption key, I put it in, then it doesn't connect, it just keeps asking for password over and over.

***_EDIT EDIT_***: So I removed my WPA2 and made it an open network and it connected fine. I must need to look into making WPA2 work better with Ubuntu. I have heard of a WPA supplicant.

Thank you Pytheas for your help.



This is the code that worked:

```
god@cisco-tosh:~$ sudo rmmod rt2800usb
[sudo] password for god: 
god@cisco-tosh:~$ sudo rmmod rt2870sta
god@cisco-tosh:~$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

---

### Post by pytheas22 on 2010-12-11
Glad to hear that did it.  As I understood the thread I linked to, the problem seems to be that there are two drivers built into Ubuntu that think they should work with that wireless card.  One of them, rt2800usb, doesn't actually work; the other, rt2870sta, works.  So the solution is to prevent rt2800usb from loading.

The commands you ran manually unloaded rt2800usb and replaced it with rt2870sta.  From here on out, however, it should be sufficient to blacklist the rt2800usb driver to prevent it from loading.  To do that, open the blacklist file by typing:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Add this line to the end of the file:

```
blacklist rt2800usb
```

Then save the file.  From now on, rt2800usb should never load (unless you load it explicitly using "modprobe"), and your wireless connection should work automatically.  If it doesn't, let me know.

As for the WPA, WPA supplicant shouldn't be the issue; that's built into Ubuntu (actually I don't think NetworkManager uses WPA supplicant *per se*, but it doesn't need to because it handles WPA on its own; in any case I doubt that's the issue).

But I would try experimenting with different WPA settings on your router to see if they make a difference.  Try WPA1 instead of WPA2, try using both in mixed mode, etc.

---

### Post by CiSC0kid on 2010-12-11
Thanks for the help. I will be blacklisting the module and will post the result of that here when I do it. 

I do appreciate the help and it has made me realize that this is a good community that I should visit more often. I will be paying it forward as they say.

---

### Post by CiSC0kid on 2010-12-12
I have blacklisted the driver and all seems to be working. Thanks again for all your help. If you do happen to visit this thread, does the *sta* part of the one driver mean staging? 

Thanks again for your help.

---

### Post by pytheas22 on 2010-12-12
Glad to hear it's working out as planned, and no problem for the help.

As for what sta means, I'm not actually sure.  It does seem to be in the "staging tree" (i.e., under /usr/src/linux-headers-2.6.35-22/drivers/staging), so that would make sense, but on the other hand there are other modules under the staging directory that don't have sta in their names.  Also, Broadcom's proprietary driver (used for some Broadcom-based chips, but not for either of your devices) is called the "Broadcom STA driver," and I've never been sure why, but as it's a proprietary driver provided by Broadcom directly, it's not part of the Linux kernel tree as far as I know.  So the STA there seems to refer to something else.

This is all to say that I'm not as informed as I wish I were about how Linux kernel development is organized.  I'm sure you could find someone who would provide a more definitive answer, and I'd love to hear it if you ever do.

Good luck going forward and hope to continue to see you around the forums :)

---

