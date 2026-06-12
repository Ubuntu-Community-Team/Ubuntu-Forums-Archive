---
title: "FireWire (IEEE 1394) networking with Windows XP and Mac OS X Tiger/Leopard"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by ergosteur on 2009-01-04
I'm trying to figure out how to get my Ubuntu laptop to connect to my iMac G3 (Mac OS X 10.4.11) and Windows desktop (Windows XP SP3) via FireWire. I found this archived thread: [http://ubuntuforums.org/showthread.php?t=305493](http://ubuntuforums.org/showthread.php?t=305493), but in 8.10 the network configuration options seem to have changed. I have modprobe'd eth1394; should I be seeing a new interface in ifconfig?

Has anyone got Firewire networking working in Intrepid? Or can someone tell me if Networkmanager supports firewire or if I have to configure it by some other means?

thanks

---

### Post by inxygnuu on 2009-01-04
Well, Firewire works for external hard drives, but I am not sure about networking. Try plugging the cord into the computers to see if they detect one another. Other than that, you might have some configuration to do on all platforms. Oh, and congratulations, you got all 3 main platforms.

---

### Post by ergosteur on 2009-01-04
> **inxygnuu said:**
> Oh, and congratulations, you got all 3 main platforms.

Thanks. I actually have all three on my Inspiron 640m right now :p.

I tried connecting the Inspiron running Ubuntu to my iMac, but the iMac says that the Firewire network has a "cable unplugged". 

As for the Ubuntu box, it says:
$ ip link show eth2
6: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ieee1394 46:4f:c0:00:18:2c:51:41 brd ff:ff:ff:ff:ff:ff:ff:ff
$

I don't know what that means...

what's odd is that if I boot OS 10.5.5 on my Inspiron and connect it to the iMac's FireWire port, they both detect that the cable has been connected and are able to communicate with each other using mDNS (Apple Bonjour). But under ubuntu, ,no dice.

---

### Post by inxygnuu on 2009-01-04
> **ergosteur said:**
> Thanks. I actually have all three on my Inspiron 640m right now :p.

I tried connecting the Inspiron running Ubuntu to my iMac, but the iMac says that the Firewire network has a "cable unplugged". 

As for the Ubuntu box, it says:
$ ip link show eth2
6: eth2: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ieee1394 46:4f:c0:00:18:2c:51:41 brd ff:ff:ff:ff:ff:ff:ff:ff
$

I don't know what that means...

what's odd is that if I boot OS 10.5.5 on my Inspiron and connect it to the iMac's FireWire port, they both detect that the cable has been connected and are able to communicate with each other using mDNS (Apple Bonjour). But under ubuntu, ,no dice.

well, I don't know much about OS X x86, but you are one lucky person/kid to be having all 3 on one system. Considering they are both Mac OS X, I would imagine that it would work. but both Mac and Windows try to but a curtain over Linux, by not adding features for it. I am a beginner, (one step from noob) so I can't help you much, but Googling about networking mac and Ubuntu, but it could be that the Macs port and the PCs port are not compatible when using different OS's. All I know is that "46:4f:c0:00:18:2c:51:41 brd ff:ff:ff:ff:ff:ff:ff:ff $" is pointing to a hardware address, but from there, I don't know :(.

Good Luck,
3v4n=P~

---

