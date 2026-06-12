---
title: "pulseaudio[8390]: sap.c: sendmsg() failed: Operation not permitted"
date: 2009-01-05
forum: Multimedia Software
---

### Post by dunno on 2009-01-05
Hi all,
I have a server running Hardy with all the latest updates and in the syslog is:
```
Jan  4 17:38:45 mymachinename pulseaudio[8390]: sap.c: sendmsg() failed: Operation not permitted
```
followed by many:
```
Jan  4 22:45:33 mymachinename last message repeated 12 times
```
To configure pulseaudio I followed the instructions at [http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
pulseaudio appears to be functioning correctly (i can hear sounds and pa daemon is running), so I'm wondering if the "pulse" user should be added to some group to allow it to use sendmsg()?  Or perhaps its some other issue?

I have another machine running Intrepid that doesn't have this message.

Google-ing around I did see the bug where sendmsg() fails due to "invalid argument", but this is different.

Thanks in advance.

---

### Post by impensj on 2009-02-08
Try checking your firewall settings on 8.04.

On my system I get these exact errors when my firewall software (iptables) blocks OUTPUT to multicast address 224.0.0.56 UDP port 9875.

Good luck.

---

### Post by onno-itmaze on 2009-08-20
If you don't need network access to or from your audio server you can disable it like this:

Pulse Audio Applet -> Configure Local Sound Server ... -> Muticast/RTP

Disable both Multicast Sender and Receiver.

---

### Post by afrodeity on 2010-11-02
> **impensj said:**
> Try checking your firewall settings on 8.04.

On my system I get these exact errors when my firewall software (iptables) blocks OUTPUT to multicast address 224.0.0.56 UDP port 9875.

Good luck.

I don't have any firewall software installed, how does one find out which address is being blocked, if any in maverick?

---

### Post by warrenc5 on 2011-08-28
did you enable multicast traffic on your interface?

route -n
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 lo

/etc/network/interfaces
up route add -net 224.0.0.0 netmask 240.0.0.0 lo
down route del -net 224.0.0.0 netmask 240.0.0.0 lo

---

