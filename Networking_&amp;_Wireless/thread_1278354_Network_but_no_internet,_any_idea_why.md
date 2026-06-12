---
title: "Network but no internet, any idea why?"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by Nubnut on 2009-09-29
Hi,
I've configured an eeepc 100 ha with UNR 9.04 and followed the instructions linked below to get everything wotking:
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/")

Although wireless is working and wired can see the windows network, the wired network cannot access the internet - any idea why this would be? I suspect it may be a DNS problem but dont know how to fix this.

I can see from another machine what DNS server I should be using, but where do i set this, or ascertain what dns is currently being used.

The output from route -n is:

Destination     	Gateway         Genmask         Flags Metric Ref    Use Iface

87.37.60.0      	0.0.0.0         	255.255.252.0   U     1     	 0       	 0 eth0

0.0.0.0         	87.37.60.1      0.0.0.0         UG   	 0      	0       	0 eth0

I can ping the default gateway successfully.

I'm at a loss as to what to do next. I'm sure it must be a simple setting since the network card is obviously working.

Nubnut

---

### Post by chili555 on 2009-09-29
> but where do i set this, or ascertain what dns is currently being used.You can ascertain what is being used with a terminal command:```
cat /etc/resolv.conf
```If you know the DNS nameservers you want, please do:```
sudo gedit /etc/resolv.conf
```Use your favorite text editor if you don't have *gedit*. Add the nameservers thus:```
nameserver 123.45.6.789
nameserver 123.45.6.890
```Proofread, save and close *gedit*, or your favorite text editor. Then do:```
ping -c3 www.google.com
```If Google is resolved into an IP address and you get ping returns, you should be all set.

---

### Post by Nubnut on 2009-09-29
Output of less /etc/network/interfaces is:

auto lo
iface lo inet loopback

shouldn't there also be a listing for the ethernet card?:

auto eth0
iface eth0 inet dhcp

What would happenif I added that line to that file?

Nubnut

---

### Post by Nubnut on 2009-09-29
Well that didn't work, editing the interfaces file I mean.
I pinged google successfully and the nameservers and resolv.conf look okay.
Is there a setting somewhere that I need to change to allow the ethernet card to use http? 
I reedited interfaces back to the original and can now see the local network again but still no internet.

---

### Post by Nubnut on 2009-09-29
Thanks for your help chilli555, any other ideas as to what it could be?
nn

---

### Post by mikehenson on 2009-09-29
see 
[http://ubuntuforums.org/showthread.php?t=1275362](http://ubuntuforums.org/showthread.php?t=1275362)

I was having a gateway problem.

---

