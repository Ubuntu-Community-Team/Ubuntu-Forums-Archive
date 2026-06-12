---
title: "Trying to understand network properties in ubuntu 10.04 LTS"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2011-07-06
[SIZE=3]I have just installed Ubuntu 10.04 LTS and still trying to understand its network properties. I connect to the internet through so called BSNL Broadband which uses a modem (wired connection). After failing to configure through system->preferences->network connection by editing auto etho, dsl, I did it by using commands:

sudo ifconfig eth0 192.168.1.2 network 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo pppoeconf

and then followed the blue screen isntructions.

Next time when I loaded ubuntu, I no longer found the auto eth0 icon to the right of sound preference. Why has this vanished?

second, why does the command ping 192.168.1.1 does not generate positive response? why am I unable to open this location in firefox? before using sudo commands, though I was unable to connect by editing dsl, auto eth0, I was able to get modem configurations etc by loading this location. Why is this change?

third, will I have to keep modem switched on at the time of booting or is it ok to switch on modem after booting ubuntu? actually after giving the last command above, I was asked if I wanted to connect to net at the tome of booting and I chose yes. In case I chose no, will I be able to connect the net even by switching on modem after booting?

May be I have asked very elementary questions, but clarifications will be very helpful. Thanks.[/SIZE]

---

