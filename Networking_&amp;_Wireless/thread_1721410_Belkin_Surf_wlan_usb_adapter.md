---
title: "Belkin Surf wlan usb adapter"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by lovo on 2011-04-04
hello
I have bought a Belkin wlan usb adapter and I can't get it working whereas I have read many topics around.
It looks like this product : [http://www.belkin.com/IWCatProductPage.process?Product_Id=509945#](http://www.belkin.com/IWCatProductPage.process?Product_Id=509945#)

The key is recognize when I plug it:
```
$ lsusb 
Bus 008 Device 003: ID 05af:0310 Jing-Mold Enterprise Co., Ltd 
Bus 008 Device 002: ID 045e:00f0 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:945a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


I manage to have information on the wifi device by following some advices here: #2 [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)
So it partially activated my device as shown here:
```
$ iwconfig                   
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

But it is not exactly the same device (given by lsusb 050d:945a) and I cannot search for a wifi network to connect to.
When I click on the network icon, the *Wireless Networks* is marked as *Disconnected*.

Do you have any idea ?

---

### Post by lovo on 2011-04-05
Hey, I still have this problem, any ideas?

---

### Post by walt.smith1960 on 2011-04-05
After doing some googling, it looks like your device might use the RealTek 8192SU chip.  The PCI version seems to use the 8192SE chip.  If your device does indeed use the 8192SU chip, here's an easy way to enable it. My TrendNet TEW-649 uses the same chip. Here's a link:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)  

If the firmware file doesn't work, you can download the latest file from RealTek, extract the individual folders & files and in one of the resulting folders is the latest version of the rtl8192sfw.bin file.  You can then check the file version or creation dates to see if it's different than the one at the link.  You could also try 11.04 beta.  The kernel in 11.04 has built-in support for this and other recent chip sets.

---

### Post by lovo on 2011-04-05
> **walt.smith1960 said:**
> After doing some googling, it looks like your device might use the RealTek 8192SU chip.  The PCI version seems to use the 8192SE chip.  If your device does indeed use the 8192SU chip, here's an easy way to enable it. My TrendNet TEW-649 uses the same chip. Here's a link:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)  

If the firmware file doesn't work, you can download the latest file from RealTek, extract the individual folders & files and in one of the resulting folders is the latest version of the rtl8192sfw.bin file.  You can then check the file version or creation dates to see if it's different than the one at the link.  You could also try 11.04 beta.  The kernel in 11.04 has built-in support for this and other recent chip sets.

How do I know the chip I use ?

In the link you have posted, it says on ubuntu 10.10 a file is missing .. but I do have this file
```
$ la /lib/firmware/RTL8192SU/          
total 276K
drwxr-xr-x  2 root root 4.0K 2011-04-03 18:10 ./
drwxr-xr-x 53 root root  20K 2011-04-03 18:10 ../
-rw-r--r--  1 root root  75K 2010-12-13 21:01 rtl8192sfw492.bin
-rw-r--r--  1 root root  88K 2010-12-13 21:01 rtl8192sfw74.bin
**-rw-r--r--  1 root root  87K 2010-12-13 21:01 rtl8192sfw.bin**
```

---

### Post by walt.smith1960 on 2011-04-05
"How do I know the chip I use ?"  It looked from some google searches like it was a RealTek 8192SU.  After further searching I came across this from the Linux Kernel Driver Database:
vendor: 050d ("*Belkin Components*"), product: 945a ("*F7D1101 Basic Wireless USB Adapter v1000 [Realtek RTL8188SU]*") 

From appearances the same driver should work on both.  Here's another thread that may have some bearing on your situation.  I didn't have to do this but I have a slightly different chip

[http://ubuntuforums.org/archive/index.php/t-1493253.html](http://ubuntuforums.org/archive/index.php/t-1493253.html)

Particularly this post:

```
I managed to get this adapter working under Ubuntu (lucid 64) with the  Belkin surf and share (F7D2101).  Pretty straightforward actually... I  got most of this from http://ubuntuforums.org/showthread.php?t=1522815 ,  although it required a some slight changes. 

Run this command:
sudo gedit /etc/udev/rules.d/network_drivers.rules 

And add this line to the file (which may be empty) and save:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"

Then run this command:
sudo gedit /etc/modprobe.d/network_drivers.conf 

And add this file (and save)
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb  $CMDLINE_OPTS; /bin/echo "050d 845a" >  /sys/bus/usb/drivers/rtl819xU/new_id

Finally, download this file:
http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin

and copy it to the directory /lib/firmware/RTL8192SU/ 

To summarize, the first two commands tell linux to load the correct  driver when that particular USB device is plugged in (which I figured  out with the lsusb command), and the firmware is used to load the  information the wireless chip needs to run.
```
I hope this will bring things to life for you.

---

### Post by lovo on 2011-04-05
Wowww it works!

I did this:

> Run this command:
sudo gedit /etc/udev/rules.d/network_drivers.rules 

And add this line to the file (which may be empty) and save:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb"

Then run this command:
sudo gedit /etc/modprobe.d/network_drivers.conf 

And add this file (and save)
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 945a" > /sys/bus/usb/drivers/rtl819xU/new_id

Finally, download this file:
[http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)

and copy it to the directory /lib/firmware/RTL8192SU/ 

With 050d 945a to be adapted with what you have in the "lsusb" command.

Thanks!

---

### Post by walt.smith1960 on 2011-04-05
Great!!

---

### Post by infinite143rd on 2011-09-22
ok im on 10.4.3 ive done exactly like you guys have said to do, why is it not working for me is beyond me... please help im a noob.... this is driving me crazy and im sick of windows i really need wifi lol

---

### Post by se_anderson on 2011-11-08
I am having similar problems, I have the Belkin F9L 1002v1 model wireless adaptor.
I have been using it successfully on my Ubuntu desktop (11.04).   I decided to upgrade my wifes old 2003 Medion box, it has ubuntu 9.10 and the Belkin adaptor worked with it also.  I installed the 10.04 upgrade from CD and rebooted.  No wireless device, no connection.

So I tried the methods on this page;

sudo gedit /etc/modprobe.d/network_drivers.conf
install r8192s_usb/sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a"> /sys/bus/usb/drivers/rtl819xU/new_id

sudo gedit /etc/udev/rules.d/network_drivers.rules
ACTION=="add",SUBSYSTEM=="usb",ATTR{idVendor}=="050d",ATTR{idProduct}=="845a",RUN+="/sbin/modprobe -qba r8192s_usb"
(the space between 05 and 0d seems to be an artifact of the post, it isnt in the file I created, I checked)

downloaded rt8192sfw.bin.gw (different link to the one on this page)
gunzip rtl8192sfw.bin.gw
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU

I created the directory and copied the file
rtl8192sfw.bin, this worked, a RTL8192SU folder was created with ftl8192sfw.bin inside. I noticed there is an existing RTL8192SE folder with 3 files;
rtl8192sfw.bin, rtl8192sfw74.bin, rtl8192sfw492.bin,

rebooted, no connection;

diagnosis;

 stuart@stuart-shed:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0db0:6982 Micro Star International Medion Flash XL Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:845a Belkin Components 
Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo lshw -c network
[sudo] password for stuart: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=28 mingnt=10
       resources: memory:f3400000-f3401fff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 8b
       serial: 00:0c:76:67:21:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:9000(size=256) memory:f3403000-f34030ff

stuart@stuart-shed:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


modinfo 845a | grep 8192
ERROR: modinfo: could not find module 845a

dmesg
[    0.874163] usb 1-4: configuration #1 chosen from 1 choice
[    0.983448] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.108311] scsi 1:0:0:0: CD-ROM            PIONEER  DVD RW  DVR-106D 1.07 PQ: 0 ANSI: 5
[    1.117986] usb 1-6: configuration #1 chosen from 1 choice
....
11.770103] Linux kernel driver for RTL8192 based WLAN cards
[   11.770107] Copyright (c) 2007-2008, Realsil Wlan
[   11.770182] usbcore: registered new interface driver rtl819xU
...

However on my Ubuntu 11.04 system, it installs and connects immediately;

lsusb
Bus 002 Device 005: ID 050d:845a Belkin Components F7D2101deSH [rtl8192su]

dmesg
[25983.316027] usb 2-2: new high speed USB device number 5 using ehci_hcd
[25983.450988] r8712u: DriverVersion: v7_0.20100831
[25983.451006] r8712u: register rtl8712_netdev_ops to netdev_ops
[25983.451009] r8712u: USB_SPEED_HIGH with 4 endpoints
[25983.451699] r8712u: Boot from EFUSE: Autoload OK
[25983.854816] r8712u: CustomerID = 0x0000
[25983.854820] r8712u: MAC Address from efuse = 08:86:3b:57:cb:2a
[25983.982938] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[25984.636444] r8712u: 1 RCR=0x153f00e
[25984.637189] r8712u: 2 RCR=0x553f00e
[25984.744511] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[25995.474517] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[25995.482945] r8712u: [r8712_got_addbareq_event_callback] mac = 54:e6:fc:bf:63:b1, seq = 0, tid = 0
[26006.264008] wlan0: no IPv6 routers present

Any ideas on how I get the wireless back on the Medion?  Would copying the driver over help?

Stuart

---

### Post by se_anderson on 2011-11-08
Correction, I have Ubuntu 11.10 on my desktop.

---

