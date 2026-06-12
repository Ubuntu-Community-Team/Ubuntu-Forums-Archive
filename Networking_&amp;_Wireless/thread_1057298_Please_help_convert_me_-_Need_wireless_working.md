---
title: "Please help convert me - Need wireless working"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by LoyalWannabe on 2009-02-01
Hi guys, 

I installed Ubuntu for the first time in my life today, no problems and I'm liking the speed on an old laptop. The only thing I need to work now to become fully converted and start preaching to others is to get my wireless sorted.

I tell you this because please understand I've never used Linux before so please keep your answers basic.

I have a Vista PC that is connected to my tiscali wireless internet connection, all is working fine that end. On my new ubuntu install I click on the 2 little black computers on the top panel and see the name of my internet connection. I click it, enter my correct WEP key and it does just not connect. 

**Some points I want to note...**

I went through the troubleshooting sections before posting this so just want to say:

I don't have the 'network' option in system > administration - only network tools

When I run the command 'sudo lshq -C network' I get the error message that it is disabled

Any help would be appreciated

---

### Post by mikewhatever on 2009-02-01
Please post the outputs of the following:
sudo lshw -C network
ifconfig

q is just next to w on the keyboard, yet lshw is not the same as lshq.

---

### Post by LoyalWannabe on 2009-02-01
Any idea how i can do this easily? I can't put in my external hard drive to copy output, I get a mount error. When i try to run the code to force to use the hard drive it says i must be an admin

Here is some of the code from the first command:
Product: Atheros AR5001X+ Wireless Adaptor Network
Vendor: Atheros Communications Inc
Logical Name: wifi0

Can you tell me what you need specifically or should i just type it all?

---

### Post by mikewhatever on 2009-02-01
You could try pumping the output into a file since it's usually easier to copy. The mount error is probably solvable, what does it say?
> sudo lshw -C network > ~/Desktop/wireless
ifconfig >> ~/Desktop/wireless

The first command provides the info about the hardware in use. Atheros and Broadcom usually have very poor Linux support, some can be made work, others not.
The second command shows if the wireless interface is recognized and if you get an IP.

---

### Post by enebre on 2009-02-02
it work fine with atheros ath5k
here is the solution 
get this working backport from synaptic

Solution recommandée : Le module ath5k

Le module ath5k a été désactivé avec la version finale d'Intrepid car il créait des problèmes (voir changelog).

À la place, une version plus récente du module est disponible dans le paquet linux-backports-modules-intrepid.

---

### Post by mikewhatever on 2009-02-02
Very nice, thanks for the update.

---

### Post by vnzjunk on 2009-02-03
****** PLEASE IGNORE THIS POST, WRONG FORUM *******  THANKS



You guys are good.  Now that I am past the buttering up part......same problem here.  Toshiba Satellite A-215 laptop with apparently the Atheros wireless onboard. Here is the output from the scan........

custom@custom:~$ sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:06:1f:97
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.113 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0 



I have done several searches for relevant info trying to figure it out on my own but got to the point where I just feel that I am chasing my tail in circles.

Any help is appreciated in advance.

vnz

---

