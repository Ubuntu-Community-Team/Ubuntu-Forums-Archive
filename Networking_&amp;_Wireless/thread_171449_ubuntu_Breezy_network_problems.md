---
title: "ubuntu Breezy network problems"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by TwistesdTexan on 2006-05-06
I have 2 ubuntu Breezy computers ethernet wired to a Linksys router/gateway with wireless G capability. Both computers can access the internet great. I can not see from one computer to the other. I can't send or share files from on to the other. The thing is, I have had network capabilities but only intermittantly, and then only for about 24 hours. I can only print from the computer that is connected to the printer, unless it is the golden 24 hour period when I have network. I have set my router to use Auto DHCP internet addresses and as a DHCP server. The internet seems to work best there. When the network is working, I cam click on Network Servers an see both computers and the Windows Network. When the network isn't working (which is most of the time), I only see the Windows Network. Any sugestions?


Here are some of the reading from my inquiries thru the terminal.
Blank:~$ lsmod | grep mii
mii                     5760  2 8139too,8139cp

Blank:~$ lspci | grep Eth
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Blank:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:11:5B:4F:52:02
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7258581 (6.9 MiB)  TX bytes:1210349 (1.1 MiB)
          Interrupt:21 Base address:0xa400

Also I can ping inside my network with no problem. I think most of my problem is actualy with the recognition software.

Again any help would be appreciated.

---

### Post by mips on 2006-05-07
Quite a few people seem to be have hassles with the RTL8139 cards. Looks like 2 modules are being loaded for this card and it should only be one if I'm not mistaken.

Could I sugget you search here for RTL8139 and see what others have found.

---

### Post by TwistesdTexan on 2006-05-09
I tryed to rename the driver and it still loaded on boot-up. I went thru all the conf files and removed the incorrect driver from the listed  drivers to be loaded. (Files search for all file with 8139cp and removed from all files listed and deleated the driver also) then I went to System---->Preferences---->Sessions---->Startup Progerams---->+Add    and typed in 'Rmmod 8139cp'. I did the for each of the users on this computer. I now have only 1 driver loaded after login. I don't know if th effect is what I needed but I thought I would Post this so someone else could have a try at it if needed. I think the second driver is loaded by the other driver. I noticed it (8139too) was listed in my search parameter.  Any further help in this would bee appreciated.

---

