---
title: "Where can i find and download wireless driver (.INF) file?"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by razorboy5 on 2009-07-08
Hi

sorry for the constant problems however i spent about 4 hours so far researching and trying to get my wireless working and getting VERY frustrated.

I downloaded the ndisgtk from Synaptic Package or Manager however i do not have the windows.INF file for my driver. 

been following this guide

[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

so where can i find the .inf driver and download it?

thx

---

### Post by ddrichardson on 2009-07-08
From the manufacturer of your hardware.  This might have been given on a CD or be available from the recovery partition of your hardware.  What device is it?

BTW I wrote that guide, has it helped?

---

### Post by razorboy5 on 2009-07-08
yes it was quite helpful

the troubleshooting guide was step by step and was easy to follow (even for a computer noob like me :P)

however when i installed Ubuntu i believe i deleted everything off my harddrive (including backup) and do not have the CDs from the original package either.

---

### Post by ddrichardson on 2009-07-08
I'm glad it helped, the troubleshooting guide wasn't a popular addition.

You should be able to get the drivers from either the hardware manufacturer or the computer manufacturer - which device is it, if you open a terminal and type:```
sudo lshw -C network
```Post the output here and we can see the device and revision.

---

### Post by razorboy5 on 2009-07-08
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:4c:51:84
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.36 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:9f:98:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:15:15:6a:02:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




also i found a few .INF files from the Intel Site and installed it using the Windows Wireless Drivers however it reads "Invalid Driver!"

---

### Post by razorboy5 on 2009-07-08
when i run 

iwconfig

it reads

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"TP-LINK_E7DF1C"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


is that what u meant by ESSID=  in your tutorial?

thx again

---

### Post by ddrichardson on 2009-07-08
You need the entire driver, not just the .inf file - are you expanding the entire archives?

Can you post the output of:```
iwconfig
```

---

### Post by ddrichardson on 2009-07-08
You shouldn't need a windows driver because the device is associated.  When you attempt to connect from network manager, does it show any available connections?

---

### Post by razorboy5 on 2009-07-08
running 9.04 (jaunty) and didn't see a network manager

however i saw a network tools (System -> Administrator -> Network Tools)

and i dont see any networks i can connect to

---

### Post by razorboy5 on 2009-07-08
also nothing in System -> Preferences -> Network Connections that i can connect to

---

### Post by ddrichardson on 2009-07-08
Network manager should have an icon in the notification area that looks like two overlapping computers.

---

### Post by razorboy5 on 2009-07-08
ok 
i had wireless working for a minutes by doing
alt+fn then using
[B]nm-applet --sm-disable

however after i rebooted it was no longer working then
the "enable wireless" button beneath the "enable networking" no longer shows either

i uninstalled some stuff thinking i didn't need them anymore
could this be the problem?
[/B]

---

### Post by ddrichardson on 2009-07-08
The driver is associated and iwconfig looks correct.  It depends on what you uninstalled and I'm not sure what the options do as I didn't think nm-applet too options.  In fact, this chipset should work off of the Live CD.

---

### Post by razorboy5 on 2009-07-08
well thx for all the help

mainly got to the solution thx to ur replies and ur wonderful tutorial ^^

gonna try to figure out what i uninstalled and how to auto connect to wireless everytime i sign on

if u got any more tips i'd appretiate it :P

thx

---

### Post by ddrichardson on 2009-07-09
> **razorboy5 said:**
> gonna try to figure out what i uninstalled and how to auto connect to wireless everytime i sign on

if u got any more tips i'd appretiate it :P
Do you mean you have to connect manually every time or that you're asked for a password to unlock the keyring?

---

