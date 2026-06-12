---
title: "PCI wifi card wg311v3(Marvell) + lubuntu 12.10 PROBLEM"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by tubester on 2013-01-15
PCI wifi card wg311v3(Marvell) + lubuntu 12.10

Hello there,

I just installed lubuntu 12.10 on a P4 machine with 1GB RAM.
Installation went smoothly and all work ok but the wifi card.
Connection through wired ethernet (lan cable to router) works fine.

uname -m returns i686, so I installed the 32bit version of OS.

I then tried to build the driver for the card following the instructions from 
[http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/](http://www.cyberciti.biz/faq/marvell-88w8335-chipset-netgear-wg311-pcicard-driver/)
as per their instructions:

Step # 1: Install Ndiswrapper utilities

Open the terminal and type the following command:
$ sudo apt-get update
$ apt-cache search ndiswrapper-utils
$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

	It installed with no visible errors.

Step # 2: Download Windows Driver for Marvell 88w8335 PCI chipset

$ cd /tmp/
$ wget [ftp://downloads.netgear.com/files/wg311v3_1_0.zip](ftp://downloads.netgear.com/files/wg311v3_1_0.zip)
$ unzip wg311v3_1_0.zip

	OK no problem.

Step # 3: Install Driver

To install driver, enter:
$ cd "/tmp/WG311v3 V1.0/Driver/Windows XP/"
$ sudo ndiswrapper -i WG311v3.INF

	It worked fine.

Verify that driver was installed:
$ ndiswrapper -l

Output:

mrv8335 : driver installed
        device (11AB:1FAA) present

	I got similar message.

wg311v3 : driver installed
        device (11AB:1FAA) present

Finally, install ndiswrapper driver itself:
$ sudo modprobe ndiswrapper

	That did not work, producing the following message:

FATAL: module ndiswrapper not found.

I got a problem here.
Following your ndiswrapper troubleshooting tutorial, I did the following:

$ lshw -c network
	
	That got me the following response:

$ sudo lshw -c network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:ea000000-ea00ffff memory:ea010000-ea01ffff
  *-network:1
       description: Ethernet interface
       product: SMC2-1211TX
       vendor: Accton Technology Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:10:b5:09:ac:7c
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:d000(size=256) memory:ea020000-ea0200ff

I then tried

$ lspci -nn

	and got the following response:

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8753 [P4X266 AGP] [1106:3128] (rev 01)
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
00:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
00:0d.0 Ethernet controller [0200]: Accton Technology Corporation SMC2-1211TX [1113:1211] (rev 10)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233A ISA Bridge [1106:3147]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.3 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 40)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)
01:00.1 Display controller [0380]: Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (Secondary) [1002:5940] (rev 01)

I tried to locate the issue with $sudo modprobe ndiswrapper following some of your guidelines.

$locate ndiswrapper.ko       

	returned nothing!

$lsmod | grep ndis

	returned nothing!

$echo 'ndiswrapper' | sudo tee -a /etc/modules

	returned ndiswrapper.

$ dmesg |grep -e ndis -e wlan

	returned nothing!

Following your instructions I removed ndiswrapper and reinstalled it again.
I then run the same tests and got the same results.

Apparently the action:

Run iwconfig to see wlan0 interface:
$ iwconfig

	produced the following message:

lo        no wireless extensions.

eth0      no wireless extensions.


I stopped at this point and thought to seek some help.
Any ideas to solve my 	$ sudo modprobe ndiswrapper
 			FATAL: Module ndiswrapper not found.
issue would be welcomed.
Thanking in advance,

Konstantinos

---

### Post by chili555 on 2013-01-16
> Open the terminal and type the following command:
$ sudo apt-get update
$ apt-cache search ndiswrapper-utils
$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
With a temporary internet connection, try:```
sudo apt-get install ndiswrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```Now does it work? If not, you'll probably need to compile ndiswrapper -1.58rc1 here: [http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper](http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper)

---

### Post by Trinity1976 on 2013-01-16
I'm having similar issues. Since I upgraded to Precise Pangolin, I can no longer get internet. I ran happily using ndiswrapper since Jaunty.

If I follow the instructions on this page: [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

I get to the bit where I run the command 'ndiswrapper -l'. This brings up a message "WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release." followed by the correct output of:   

Wg311v3 : driver installed
                  Device (11AB:1FAA) present


On typing 'sudo modprobe ndiswrapper', I get the same warning, followed by 'FATAL: Module ndiswrapper not found'.


So I tried following the instructions on this page:


[http://justanyone.blogspot.co.uk/2012/07/solved-how-to-install-netgear-wg311.html](http://justanyone.blogspot.co.uk/2012/07/solved-how-to-install-netgear-wg311.html)


Alas, on running the command 'sudo apt-get install dkms ndiswrapper-dkms', I get:



  Err [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe ndiswrapper-dkms all 1.57-1ubuntu1
  Could not resolve ‘gb.archive.ubuntu.com’
  Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.57-1ubuntu1_all.deb Could not resolve ‘gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper/ndiswrapper-dkms_1.57-1ubuntu1_all.deb%20Could%20not%20resolve%20'gb.archive.ubuntu.com")’
  E: Unable to fetch some archives, maybe run apt-get update or try with –fix-missing?


Is this because I need to actually be connected to the internet in order to do this bit, and if so, does anyone know another way? Reason being, I'm a lodger in someone else's house and I don't think it would go down too well if I carted my huge desktop PC and monitor etc...  into the dining room to connect with an ethernet cable.


Any advice greatly appreciated.

---

### Post by chili555 on 2013-01-16
> Is this because I need to actually be connected to the internet in order to do this bit, Yes, exactly. You could download the package here: [http://packages.ubuntu.com/precise/ndiswrapper-dkms](http://packages.ubuntu.com/precise/ndiswrapper-dkms)

Download it on some other computer, transfer it on a USB key or similar and get it to your desktop. Then open a terminal and do:```
cd Desktop
sudo dpkg -i ndiswrapper-dkms*.deb
sudo modprobe ndiswrapper
```

---

### Post by Trinity1976 on 2013-01-17
You star, that worked. Thanks :)

---

