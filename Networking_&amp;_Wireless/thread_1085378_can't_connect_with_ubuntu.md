---
title: "can't connect with ubuntu"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by phillip1882 on 2009-03-03
i have a wireless connection, that is, i have a primary pc that its directly connected and distributes a wireless connection to the other pcs in my home. windows is able to automatically detect and connect to this wireless conection without a problem, but for some odd reason i can't get ubuntu to connect using the same pc, same wireless router.  here's what i get when i run ifconfig
eth0 link encap: Ethernet Hwaddr:00:13:d3:cb:f4:a9
     up broadcast multicast mtu:1500 metric: 1
     rx packets:0 errors:0 dropped:0 overruns:0 frame:0
     tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     rx bytes: 0 (0.0 B) tx bytes: 0 (0.0 B)
lo   link encapL local loopback
     inet addr: 1270.0.1 mask:255.0.0.0
     up loopback running mtu:16436 metric: 1
     rx packets: 216 (rest same as above)
     tx packets: 216 (same)
     collisions: 0 txqueuelen: 0
     rx bytes: 13536 (13.5 KB) tx bytes 13536 (13.5 KB)
and what i get when i run iwconfig
  lo no wireless extentions
  eth0 no wireless extentions
  pan0 no wireless extentions
i've tried going through the standard help under ubuntu without success.

---

### Post by ugm6hr on 2009-03-03
Look at the wifi help link below, and provide more detail as requested.

Also - use the CODE and /CODE markers (click the # sign) for terminal output - since it is hard to read otherwise.

---

### Post by phillip1882 on 2009-03-04
alright, i'm running ubuntu 8.10
heres what i get from the remaining commands in your request.
ubuntu@ubuntu:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 005: ID 0930:6545 Toshiba Corp.
Bus 002 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 001 Device 003: ID 13b1:000b Linksys WUSB11 v4.0 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 56:f5:40:6d:4a:e5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by ugm6hr on 2009-03-04
This might help: [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

---

### Post by phillip1882 on 2009-03-04
well, i looked through the steps, and did everything up to step 4, but i'm stuck there. i don't have an internet connection under ubuntu, so i cant go to the neesicary website to download the driver under ubuntu. i can get the driver in windows, but i also can't access the hard drive under ubuntu.

---

### Post by ugm6hr on 2009-03-04
If you have no wired connection, this will be harder.

Are you using 32- or 64-bit Ubuntu?

---

### Post by phillip1882 on 2009-03-04
32. and no, i dont have a wired connection

---

### Post by phillip1882 on 2009-03-04
well i was able to make a lttle progress on my own. i saved the driver to a flash drive, loaded ubuntu, then put the driver in ubuntu. unfortunately, the driver is version 1.54, and the make commands didnt work with it. does anyone know the nessicary commands for this version?

---

### Post by ugm6hr on 2009-03-04
The make commands wont work without build-essential.

apt-get build-essential won't work without internet.

Try a different approach:

Follow steps 1 & 2.

Skip 3 (it won't do any harm, but won't work either).

Instead of 4: use USB stick to download files from (pick nearest mirror site)
1. [http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download](http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download)
2. [http://packages.ubuntu.com/intrepid/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/intrepid/i386/ndiswrapper-utils-1.9/download)
3. [http://packages.ubuntu.com/intrepid/i386/unzip/download](http://packages.ubuntu.com/intrepid/i386/unzip/download)

[ Probably worthwhile downloading the driver itself at this stage: [ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe](ftp://ftp.linksys.com/pub/network/WUSB11v4_08272004.exe) ]

Transfer above 4 files to Ubuntu (to Home Folder directory) from USB stick.

Double-click on the 3 .deb files in order.

Skip start of step 5 - follow advice from:
> You can now check the ndiswrapper to see that it is installed correctly...

Hopefully the rest will work.

To explain: this installs ndiswrapper v1.52 from the repository rather than the latest 1.54 from source.  By doing this, you do not need build-essential.

---

### Post by phillip1882 on 2009-03-04
well, even after clicking all three in order, no ndiswrapper folder was even created, co i couldn't check to see if it installed correctly (which i'm guessing it didnt.)

---

### Post by phillip1882 on 2009-03-04
Okay, got it. Yeah, I tried skipping the check to see if it was installed and was able to get up to step 7 without a problem. after that it was just a matter of right clicking network connections and clicking on the appropriate network to get my wireless up and running. I am posting this from inside Ubuntu! (hugs everyone!) I'm sorry if a came off as rude or impatient before but I've been trying to fix this for like 3 days now, and no offence but this seems like a fairly difficult fix.

---

### Post by ugm6hr on 2009-03-05
> **phillip1882 said:**
> I've been trying to fix this for like 3 days now, and no offence but this seems like a fairly difficult fix.

You're welcome.

Unfortunately, this was difficult because you have a USB wifi card that is not supported (due to the chipset manufacturers unwillingness to provide a linux driver or open the hardware details to allow community to create one).  Honestly, you should be impressed that it works at all (compare this to using unsupported hardware with Apple OSX).

You're particular situation was complicated by lack of wired connection.

In any case, I'm glad it worked out.  Welcome to the community!

---

