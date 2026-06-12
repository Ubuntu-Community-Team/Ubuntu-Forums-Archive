---
title: "I realize the magnitude of all the &quot;Can't Connect to Wireless&quot; threads, butttt...."
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by Nomad5150 on 2012-02-27
I am a complete Newbie to this stuff, but I have an HP Pavilion Dv7, and like everyone else who is having problems, I too, cannot connect to the internet through wireless or through a cable. I've done a bit of research and I can see that each computer has its own quirks.  I downloaded Ubuntu 11.04 from the "Windows Installer" and partitioned my drive. I know that my ethernet card isn't supported. Please help me. :D

---

### Post by Nomad5150 on 2012-02-28
Also, i have a realtek card.

---

### Post by nothingspecial on 2012-02-28
Well, you need to give some information.

Press Ctrl-Alt-T to open a terminal and type

```
sudo lshw -C network
```

Then post the resulting gobbldygook back here

**note** you will have to type your password which you will not see as you type.

---

### Post by Nomad5150 on 2012-02-28
```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9000000-d9003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:15:32:14
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:5000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 0c:60:76:40:69:c3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```

---

### Post by bkratz on 2012-02-28
You actually have a broadcom wireless card


product: Bcm4312 802.11b/g LP-PHY


You should be able to find what you need in post 3 of this thread

[http://ubuntuforums.org/showthread.php?t=1932922](http://ubuntuforums.org/showthread.php?t=1932922)

---

### Post by Nomad5150 on 2012-02-28
Awesome! Thank you. I'll try these methods out tonight. :)

---

### Post by ratcheer on 2012-02-28
Also, your Ethernet card can be made to work by installing a good, working driver, too.

Download driver r8168 version 8.028. It is pretty easy to find via Google.

Make sure you have packages build-essential and linux-headers-<your kernel version> installed on your system.

cd to the r8168-8.028.00 directory and run "sudo ./autorun.sh"

Your Ethernet connection should come up. Sometimes it helps to blacklist the r8169 driver.

Tim

---

### Post by bkratz on 2012-02-28
> **Nomad5150 said:**
> Awesome! Thank you. I'll try these methods out tonight. :)



Sorry, I didn't notice that you don't have ethernet either--you will need to get the wired connection working first since you will have to download the wireless drivers so do Ratcheer's suggestions first.

---

### Post by ratcheer on 2012-02-28
> **bkratz said:**
> Sorry, I didn't notice that you don't have ethernet either--you will need to get the wired connection working first since you will have to download the wireless drivers so do Ratcheer's suggestions first.

He needs to download the driver for Ethernet card, too. I hope he has sneakernet. :)

Tim

---

### Post by Nomad5150 on 2012-02-29
I guess I have 11.10 not 11.04. I also tried to download the packages and the linux header but probably did the wrong one or don't know how. Ill figure it out on the weekend I guess. Thanks though :)

---

### Post by TBABill on 2012-02-29
This is a really easy fix and you do not need ethernet to download the drivers or firmware. They're on the live CD/DVD. Since you have no ethernet it'll be easier to go into a live session, get the wireless going, then immediately install the OS while the wireless is working.
 
Open a terminal after you boot from the LIVECD and go to additional drivers. Select the STA driver. Once it activates, which it will right from the CD, it will prompt you to restart. DO NOT RESTART! Simply open a terminal and ```
sudo modprobe wl
``` Wait a few moments and then try to connect.
 
Once you connect, install the OS during that live session. Once it finishes you will have a live working wireless connection on your first boot into the newly installed OS.

---

### Post by varunendra on 2012-03-01
> **bkratz said:**
> 
You should be able to find what you need in post 3 of this thread
[http://ubuntuforums.org/showthread.php?t=1932922](http://ubuntuforums.org/showthread.php?t=1932922)Wow! How nice to see being quoted for a solution! (probably for the first time!):p

However, as already figured out, that post assumes a working ethernet connection which is not the case here (damn this r8169 bug!!). Accordingly, *TBABill's* method seems most straightforward. Another alternative method (for no-internet connection) is given in the community documentation: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)


As for the ethernet issue, this post should be all that is required: [http://ubuntuforums.org/showthread.php?p=11719747](http://ubuntuforums.org/showthread.php?p=11719747)

(the above linked post uses driver version 8.026... You might wish to get the latest one (currently 8.028..)from realtek's site: [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false) . The parts of commands that contain the driver/folder name would change accordingly.)

The downloaded driver file (.tar.bz2) contains its own installation instructions in a README file which is just running:
```
sudo ./autorun.sh
``` as *ratcheer* suggested. Normally, this should take care of everything, but some users have reported problems even after that, hence the alternate method I linked to above.

I'll eagerly wait to see which methods worked for you.

---

### Post by Nomad5150 on 2012-03-04
*TBABill's* method worked!  Thank you so much!  I'm so happy now haha.

---

### Post by bkratz on 2012-03-04
> **Nomad5150 said:**
> *TBABill's* method worked!  Thank you so much!  I'm so happy now haha.


Glad you got it going, congratulations!  I too will make note of that trick (never thought of it!).

---

### Post by ratcheer on 2012-03-04
So, you are going to do a new install just to get the wireless driver working?

Tim

---

### Post by Nomad5150 on 2012-03-07
Well it was a fresh install anyway so it didn't really matter.  Also, I thought it worked, but it turns out that I have a new problem with not being able to boot, so I can't even see if it worked or not...

Thanks anyway though. :)

---

