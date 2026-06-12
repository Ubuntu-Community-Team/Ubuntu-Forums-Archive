---
title: "Network over FireWire IEEE 1394"
date: 2006-01-26
forum: Networking &amp; Wireless
---

### Post by cracker on 2006-01-26
I have two laptops, one with Breezy, and one with XP Professional. Before I installed Breezy, I could connect them with a firewire cable and transfer files at 400mbps. I want to know how I can set up Breezy to work the same way. I've searched the forums, and firewire is hardly even mentioned. Here is the relevant portion of lspci:

0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)

---

### Post by Lambert on 2006-01-26
Try this. (and I'm not sure if this will work as I don't have set up to test on)

```
sudo modprobe eth1394
```
I'm not sure if breezy comes with this module and I can not check at the moment.

then check to see if module is running

```
lsmod | grep eth
```


You should have an interface that you can configure now.

```
sudo ifconfig ethx xxx.xxx.x.x up
```

try to ping the interface you just set up and if that goes good then try to ping the second box.

You may also need to set up a route and nameservers.

```
sudo route add default gw xxx.xxx.x.x dev ethx
```

name server would be in /etc/resolv.conf

note: all xxx's need to be replaced with actual data.
ifconfig command = ip you're setting for your device
route command = ip of windows interface you're connected to

note:
There is a preliminary eth1394 driver. It is neither stable nor fully standards (RFC 2734) compliant--but getting close! Please test out with another Linux machine and submit bug reports and patches to the linux1394-devel mailing list.

You might look here for more help.
[http://www.linux1394.org/index.php](http://www.linux1394.org/index.php)

---

### Post by cracker on 2006-01-26
Thanks, that worked great.

---

