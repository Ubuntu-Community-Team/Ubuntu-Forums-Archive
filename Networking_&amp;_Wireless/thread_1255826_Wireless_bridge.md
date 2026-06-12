---
title: "Wireless bridge"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Kayos02 on 2009-09-01
So I put Xubuntu 9.0.4 on my Inspiron 1300. It's a note taking device for school and a part time access point :P.


[SIZE="4"]**Previous Setup:**[/SIZE]
Laptop receives wireless connection from main router, eth is hooked up to a switch, Windows XP bridges these two connections, computers in room that are hooked up to switch get static IPs, it's all good. Any computer that I chose to use DHCP could be managed by the main router.

*Note that if I recall correctly I had to enable a forced mode when I was in XP for the bridging to work. I don't remember what it is, I'll look up and edit later.*


[SIZE="4"]**Now:**[/SIZE]
I need to set up the same thing in the new OS. So what I need to do I suppose is connect to wlan and eth0 and then bridge them, this was ridiculously easy in XP, but after googling and reading and making attempts I cannot seem to pull it off now.

If it works like the old setup did, I don't need a DHCP server on the lappy, because it was pulling DHCP from the main router.


Bottom line: How the poopsmith do I bridge connections for ICS properly in *ubuntu?

---

### Post by Kayos02 on 2009-09-02
This is an extremely important part of my network setup and I don't have an access point to replace it with. Help?

---

### Post by Zodiac69 on 2009-09-02
Edit /etc/network/interfaces
This is my setup and work as follow:

eth1 is static - connected to router
eth0 is connected to switch
all pc's connect to switch and is assigned address from router


#This is to Bridge two network cards
#Lose local internet connection
#
auto eth0
iface eth0 inet manual
#
auto eth1
iface eth1 inet static
    address    xxx.xxx.1.100
    network    xxx.xxx.1.0
    netmask    255.255.255.0
    broadcast xxx.xxx.1.255
    gateway    xxx.xxx.1.1
#
auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
#
#The loopback network interface
auto lo
iface lo inet loopback

---

### Post by Kayos02 on 2009-09-03
ARGH.

```
auto eth0
iface eth0 inet manual
auto wlan0
iface wlan0 inet static
address 192.168.1.10
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

auto lo
iface lo inet loopback
```



PC connected to switch with static IP cannot ping the lappy, the router, or anything outside.

---

### Post by Kayos02 on 2009-09-03
Anyone...? I may have to reinstall XP, and that would make me a sad panda.

---

### Post by superprash2003 on 2009-09-04
i presume you mean internet connection sharing ?

---

### Post by Kayos02 on 2009-09-05
> **superprash2003 said:**
> i presume you mean internet connection sharing ?

Yes

---

### Post by Kayos02 on 2009-09-06
I heard you like it when I bump like this.

---

### Post by 3rdalbum on 2009-09-06
There are two programs that can reportedly set up Internet Connection Sharing for you.

The first is the Network Manager applet that ships with Ubuntu. There should be a HOWTO about it somewhere online; check with Google.

The second program that can set up ICS is Firestarter, which is actually a firewall configuration program.

I didn't have any success when I tried those, but then I was attempting to share a flakey mobile broadband connection across a wired network. And it was late at night. You might have more luck.

---

### Post by Kayos02 on 2009-09-06
I tried Firestarter with 0 luck a while back. Couldn't quite seem to find out how to do it with the network manager app.

---

### Post by superprash2003 on 2009-09-16
tried this? [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

