---
title: "hp mini 1035nr wifi help"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by giuseppe321 on 2011-06-02
Hello im a noob to ubuntu havnt been on it since karmic wich ran horrible i just installed ubuntu 11.04 lts on my hp mini 1035nr netbook and wireless doesnt work ive tried installing bf43 still no luck.
not even my ethernet connection works so this is going to be a pain since i cant use sudo apt. all the tools i have right now is a 128mb flash drive and another laptop running windows. btw i have a 55gig hard drive and windows 7 runs horribly on my netbook so i switched to ubuntu its really nice and fast love it so far but my other question is that can i format the windows partition and merge it with ubuntu's giving me back 15 gigs

---

### Post by josephmills on 2011-06-02
hi there could you open your terminal and type in  ```
lspci -nn | grep Broadcom 
``` and a ```
rfkill list all 
``` then paste all here thanks

---

### Post by giuseppe321 on 2011-06-02
[LEFT]giuseppe@ubuntu:~$ lspci -nn | grep Broadcom
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
giuseppe@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
giuseppe@ubuntu:~$ 

here you go got it
[/LEFT]

---

### Post by josephmills on 2011-06-02
> **giuseppe321 said:**
> [LEFT]giuseppe@ubuntu:~$ lspci -nn | grep Broadcom
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

ok you need the b43-fwcutter and the firmware-b43lpphy-installer you still have no eth0 so lets work on that first give us a ```
sudo lshw -C network 
``` and a ```
 lspci -nn | grep Ethernet 

``` thanks again

---

### Post by giuseppe321 on 2011-06-02
both of those codes didnt work but  do have an auto etho connection on my edit list but it doesnt say im connected

---

### Post by josephmills on 2011-06-02
ok lets see if you are connected try 
```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
``` lets us know if it downloads the packages

---

### Post by giuseppe321 on 2011-06-02
giuseppe@ubuntu:~$ sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer
[sudo] password for giuseppe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
giuseppe@ubuntu:~$ 
                                                               still not working Whats up above was what i got in return for putting in the sudo command

---

### Post by josephmills on 2011-06-02
please go to ubuntu software center then go to **Edit-->software sources **then make sure all are ticked see attachments then close out of everything and then open your terminal and do a ```
sudo apt-get update && sudo apt-get upgrade 
``` do you get any errors? if so stop and say something but if not then type in ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot 
``` after reboot are you getting wireless ? if not let us see a ```
lsmod && dmesg | grep b43 
``` thanks

---

### Post by giuseppe321 on 2011-06-02
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
giuseppe@ubuntu:~$ sudo 1shw -C network

yup i got an error

---

### Post by josephmills on 2011-06-02
unplug the ethernet cable then plug it back in do you get connected? let us see a ```
ping google.com
``` then press **ctrl+c** then paste the results it sould look something like this ```
^C
--- google.com ping statistics ---
25 packets transmitted, 25 received, 0% packet loss, time 24039ms
rtt min/avg/max/mdev = 66.596/67.373/69.915/0.744 ms
``` what do you get?

---

### Post by giuseppe321 on 2011-06-02
it said command not found

---

### Post by josephmills on 2011-06-02
```
sudo apt-get install ping 
``` will it install ?

---

### Post by giuseppe321 on 2011-06-02
it sed i have the latest version 0 upgraded 0newly installed 0 to remove 0 not upgraded

---

### Post by josephmills on 2011-06-02
try ```
sudo apt-get remove --purge bcmwl-kernel-source && sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-lpphy-installer && sudo apt-get install bcmwl-kernel-source && sudo reboot

``` then after reboot anything? are you connected to the internet plug in the ethernet cable and then go to google or here can you do that? or do you get a connection timeout. Also what country do you live in?

---

### Post by giuseppe321 on 2011-06-02
it said unable to load package bcmwl-kernal- source  live in america  and still no connection to any website

---

### Post by josephmills on 2011-06-02
```
lspci -nn 
```

---

### Post by giuseppe321 on 2011-06-02
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]

---

### Post by josephmills on 2011-06-02
this one takes some time to load but it will ```
sudo lshw -C network
``` is the sky2 diver installed?

---

### Post by giuseppe321 on 2011-06-02
giuseppe@ubuntu:~$ sudo lshw -C network
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
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:feb00000-feb03fff ioport:e000(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2b:88:fb:a9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

did this do anything the output of the command is up there btw whats a sky 2 driver

---

### Post by josephmills on 2011-06-02
A sky 2 driver is the driver you need for your Ethernet. I am sorry but with out the net it is going to be real hard to set up the wireless just remember that you need the b43-fwcutter and the firmware-b43lpphy-installer  the lpphy is real important and it is for lower power cards if you use the firmware-b43-installer it will be to powerful and will not work

---

### Post by giuseppe321 on 2011-06-02
can u put up a link for the sky2 driver i cant find any same with the bf43

---

### Post by josephmills on 2011-06-02
for the b43 

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)



for the sky2 

just google it hope that you get it fixed up :p

---

### Post by giuseppe321 on 2011-06-02
yeah  i tried the link this just feels to impossible i need a walk through these those intructions either need internet or just hav commands that dont work

---

