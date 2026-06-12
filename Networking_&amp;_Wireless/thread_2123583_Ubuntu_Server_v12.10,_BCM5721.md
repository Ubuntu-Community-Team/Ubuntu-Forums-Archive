---
title: "Ubuntu Server v12.10, BCM5721"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by MAFoElffen on 2013-03-08
Okay. I'm not a noob, but this is humbling.

Box is a IBM XSeries 346. Has 2 onboard Broadcom NetXtreme BCM5721 Server NIC's. This server is a new addition to my test bank. (64bit sys, 2 Xeon dual-core processors, 16GB RAM, RAID5EE)

When I install 13.04, I put a usb thumbdrive with linux-firmware-nonfree in while installing and have no troubles... They come right up, gets dhcp from my router, connects to time server and away it goes.

But, I want to play with Xen... So I deleted everything to install 12.10. Install gets to detecting network devices, syslog says it see's the card and uses tga... then when it tries to go dhcp, it says it can't get an address. If I repeat on that error, it finally says it got an dhcp address, but not a nameserver, it fails. If I try static, it fails. Funny about that, is that I didn't show in my router's dhcp assignment tables, so I know it lied. 

If I install without configuring the network settings, it installs... but starting as an island on it's own (now current status) it fails. It says it's coming up hardware wise, but I can't get a link.

I have some extra 64bit IBM server NIC's and a fiber NIC (somewhere) that I could throw in there to temporarily get it connected so it isn't isolated / to work it out... But when I did, it complained that it couldn't address eth2 as eth2???

I thought that Linux kernel 3.0 brought in internal support for bcm5720 series cards, since bcm drivers went opensource with tga?

Okay. It's now an adventure and challenge. If you answer, remember that server has no GUI and is commandline. Like I said- now humbled and asking for ideas and help.

---

### Post by MAFoElffen on 2013-03-08
Update-
Tried to reinstall 13.04 to see if that shed any light. I get a link. It starts dhcp discover, but said it did not get a lease. Says that dhcp protocol may not be in use. My router dhcp clients table shows "ET00200010A184" as a new client with an assigned IP address of 192.168.2.106... And this box was on 13.04 with no troubles previously... ?

---

### Post by chili555 on 2013-03-08
I love a mystery! > syslog says it see's the card and uses tga.I think it's tg3. Confirm:```
sudo lshw -C network
```What, if anything, resides in /etc/network/interfaces? I suggest, at a minimum:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp
```Then get the system to re-read the file:```
sudo ifdown eth0 && sudo ifup -v eth0
```This assumes the ethernet cable is attached to eth0. You should be able to see in lshw which interface has the cable with 'link detected.'

It should be clear if you connected or not and give some clues to troubleshoot if you did not. Confirm:```
ifconfig
ping -c3 www.google.com
```

---

### Post by MAFoElffen on 2013-03-08
Wait one... while trying a 64bit Netgears card, it got an NMI error, then one of the drives faulted in RAID. Rebuilt the array and now rebuilding the spare... Then have to add the riser cards back in to see what "that" problem was.

---

### Post by MAFoElffen on 2013-03-08
I reinstalled v12.10 again. Actually, more than a few again. 

I had bounced my router and modem to hard reset both. Then this server started getting dchp without any problems. Although Xen was another story. Each time I installed Xen on this box, after a reboot, networking would go away and then It would get an NMI machine check error... which would then just loop in reboots because of the NMI error.

During that NMI error, my router would have that network port locked out/not working... Then I would have to reset it again.

I search in IBM support and did see that this server seems to not like Xen 4.1. They don't play well together. There is a reported bug that this server gets NMI's under Xen 4.1.

So the last fresh install of 12.10 without Xen and everything is running fine, even networking. No problems with it all afteroon!

---

