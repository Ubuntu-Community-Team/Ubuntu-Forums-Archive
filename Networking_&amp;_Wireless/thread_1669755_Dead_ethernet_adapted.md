---
title: "Dead ethernet adapted"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by alexbj on 2011-01-18
Hi,

This is my first post and I'm fairly new to Ubuntu.

I'm running 10.10 on an integrated mini-ITX board, the Asus at3iont-i deluxe. On my first install, everything worked out of the box, and I was able to setup all I wanted, with valuable help from [http://ubuntuforums.org/showthread.php?t=1458300](http://ubuntuforums.org/showthread.php?t=1458300) .

For various reasons, I did a complete reinstall of 10.10, and after that my onboard Ethernet adapter is completely unresponsive. When I plug it in, the little light on the router does not indicate a connection (but it does if I put my laptop on the same cable).

The Gnome NetworkManager does not show a connection. I'm not sure what to check, but ```
lspci | grep Ethernet
``` yields
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```
Also, ```
ifconfig
``` gives ```
eth0      Link encap:Ethernet  HWaddr 20:cf:30:bb:67:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

```
and both ```
ifdown eth0
``` and ```
ifup eth0
``` give error messages about eth0 being unknown or not configured.

Any help would be greatly appreciated. Oh and by the way, the onboard wlan works fine.

---

### Post by anubhavrocks on 2011-01-18
Can you post the output of:

/etc/network/interfaces

---

### Post by schalkefan on 2011-01-18
hello alexbj,

have you looked up /etc/network/interfaces ?
i believe the "ifconfig /-up/-down" program uses this file to check for interfaces and decide which to start up on booting.

i think it should have an entry like:

auto eth0
iface eth0 inet manual

hope it helps.

regards.

---

### Post by alexbj on 2011-01-18
Hi and thanks for the quick reply.

```
cat /etc/network/interfaces
```
only yields
```
auto lo
iface lo inet loopback

```

but I get the same output on my laptop, where the ethernet adapter is working fine, so I'm guessing this is not so relevant. Thanks though.

---

### Post by alexbj on 2011-01-18
> **schalkefan said:**
> hello alexbj,

have you looked up /etc/network/interfaces ?
i believe the "ifconfig /-up/-down" program uses this file to check for interfaces and decide which to start up on booting.

i think it should have an entry like:

auto eth0
iface eth0 inet manual

hope it helps.

regards.

Adding the suggested lines to /etc/network/interfaces seems to have as only effect that the Gnome NetworkManager says "device not managed" instead of "not connected" under Wired Network. So I removed these lines again.

---

### Post by alexbj on 2011-01-19
> **anubhavrocks said:**
> Can you post the output of:

/etc/network/interfaces

Do you think I should modify this file in some other manner to force the activation of the ethernet adapter?

Cheers
Alex

---

### Post by alexbj on 2011-01-19
> **anubhavrocks said:**
> Can you post the output of:

/etc/network/interfaces

Do you think I should modify this file in some other manner to force the activation of the ethernet adapter?

Cheers
Alex

EDIT: sorry about the double posting... didn't realize the first one had worked.
Alex

---

### Post by alexbj on 2011-01-19
Hi guys,

Found this thread [http://ubuntuforums.org/showthread.php?t=1525455](http://ubuntuforums.org/showthread.php?t=1525455), and its solution worked! 

Strange though, cause the card has never been anywhere near a windows installation, and as far as I can remember I've never put it to sleep from Ubuntu either.

So, it turned out the card was not dead, it was merely in a "deep sleep". Thanks for the help.

---

