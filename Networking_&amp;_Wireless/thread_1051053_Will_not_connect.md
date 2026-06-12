---
title: "Will not connect"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by vjp38 on 2009-01-26
First let me start by saying this is a long post.  I am not even a novice in the Linux environment. I have been a brain dead MS Windows for years. I know absolutely nothing about Linux or Ubuntu. For me its like living in another country without knowing the language, but I am interested and willing to learn.  

I ran this same question on the Absolute Beginner Guide forum.  I tried everything suggested, but no sucess.  The right information was in AuthO, but it would never connect.  I did however get it to connect one time, but I have no idea how. I never changed anything.  I did reboot my router and I thought that may have solved the problem, but when I repeated the boot up after re-boot, no connection.  So I wrote it off as a quirk.  

My current OS is Windows XP (SP3). Quite honestly its running fine, but I was looking for a challenge and possibly a more secure environment. I downloaded Ubunto 8.10 ISO without any problems. Played around working off the CD then decided to install it on my hard drive and dual boot. 

Everything during installation went fine. I like the look and feel of the desktop. I think I can figure out most of the applications I need to use in the short term. My problem or challenge is connecting to my network. Again, remember I am a novice at best. 

I am not a network guru, by the grace of God I am able to do simple network adimintrative tasks only because WinXP does most of the thinking for you.  I have a Verizon provided (actiontec) wired router which connects me to (via coax) my Verizon FIOS. The router is based to my computer via a CAT 5 cable.  This router has a wireless capability which connects to another computer (client?)in the house.  This set up works fine.  My desktop is the base and the one which ubuntu (and MS WinXP) is installed on. My WinXP security suite is McAfee total protection, virus, firewall, etc. I have not turned off anything.

I think I have all the settings I need from windows. I ran ifconfig in windows and it gave me my network settings.

jimp@ubuntu:~$ -C
bash: -C: command not found
jimp@ubuntu:~$ c
bash: c: command not found
jimp@ubuntu:~$ cd\
> iwconfig
bash: cdiwconfig: command not found
jimp@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

jimp@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0e:a6:33:e3:f6 
inet6 addr: fe80::20e:a6ff:fe33:e3f6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:19 Base address:0xb400 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:240 errors:0 dropped:0 overruns:0 frame:0
TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:15040 (15.0 KB) TX bytes:15040 (15.0 KB)

jimp@ubuntu:~$ sudo iwlist scan
[sudo] password for jimp: 
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

pan0 Interface doesn't support scanning.

jimp@ubuntu:~$ sudo lshw -C network
*-network 
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: f
bus info: pci@0000:02:0f.0
logical name: eth0
version: 10
serial: 00:0e:a6:33:e3:f6
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 4e:af:a5:24:5d:5f
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
jimp@ubuntu:~$
 
I just can figure out where they go or if they are the ones needed. I also ran lspci | grep -i net as recommended and got: 02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

So here is the problem.  When Ubuntu boots up and the desktop appears the network icon initiates and looks for a network to connect to. Each time it fails. I check the connection box, but I am not able to edit the MAC address. Sometimes its there sometimes its blank. Regardless, I am not able to connect no matter what edits I try.

I do notice that when i reboot and go from the windows environment to Ubuntu, the ethernet socket I have my cat5 cable plugged into no longer lights up. But when I go back to windows, it comes back fine.  No sure that is an issue.  The router works fine in the WinXP environment.

I really want to give Ubuntu a go but without being able to connect to the network and internet really restricts my evaluation. I know the internet is the internet, but bouncing back and forth between OS is counterproductive.

I really reached a point of terminal frustation and un-installed Ubuntu from my hard drive. I am more than willing to give it another try. I am sure its something very simple.  So can anyone walk me through this and get me connected (and stay connected)? Remember I am less than a novice so you have to type real slow.

Cheers,
Jim

---

### Post by puppywhacker on 2009-01-26
Hi,

you have an Verizon FiOS connection with an actiontec modem and your network card is an Realtec RTL-8139, the driver 8139too is loaded and the logical interface is named eth0 and it is UP. 

The bad news is that it has no ip address, nor did it run any incoming or outgoing traffic. nor do you see a light indicating you have a link

Lets start with a few easy steps to determine what does work.

1. check if the lowest level link is up
**sudo mii-tool eth0**

2. assign eth0 an ipaddress (it is only temporary for testing, until you reboot)
**sudo ifconfig eth0 192.168.1.2**

3. try to browse to the modem with firefox
[http://192.168.1.1/]("http://192.168.1.1/")

4. check which mac-addresses you computer has learned
**arp -a**

5. try to receive an ip-address 
**sudo dhclient eth0**

6. show your ifconfig again
**ifconfig eth0**

show us the results and eitherway welcome to ubuntu and goodluck with your learning curve

---

### Post by vjp38 on 2009-01-26
> **puppywhacker said:**
> Hi,

you have an Verizon FiOS connection with an actiontec modem and your network card is an Realtec RTL-8139, the driver 8139too is loaded and the logical interface is named eth0 and it is UP. 

The bad news is that it has no ip address, nor did it run any incoming or outgoing traffic. nor do you see a light indicating you have a link

Lets start with a few easy steps to determine what does work.

1. check if the lowest level link is up
**sudo mii-tool eth0**

2. assign eth0 an ipaddress (it is only temporary for testing, until you reboot)
**sudo ifconfig eth0 192.168.1.2**

3. try to browse to the modem with firefox
[http://192.168.1.1/]("http://192.168.1.1/")

4. check which mac-addresses you computer has learned
**arp -a**

5. try to receive an ip-address 
**sudo dhclient eth0**

6. show your ifconfig again
**ifconfig eth0**

show us the results and eitherway welcome to ubuntu and goodluck with your learning curve
OK here is what I got.  It don't look good:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mii-tool eth0
eth0: link ok
ubuntu@ubuntu:~$ sudo ifconfig eth) 192.168.1.2
bash: syntax error near unexpected token `)'
ubuntu@ubuntu:~$ sudo ifconfig eth0 192.168.1.2
ubuntu@ubuntu:~$ arp -a
su? (192.168.1.1) at <incomplete> on eth0
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0e:a6:33:e3:f6
Sending on   LPF/eth0/00:0e:a6:33:e3:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

iubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:33:e3:f6  
          inet6 addr: fe80::20e:a6ff:fe33:e3f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xb400

---

