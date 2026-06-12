---
title: "Wired connection makes wifi fail"
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2013-08-02
I get to the internet via wifi. I share it with my neighbour (his idea). I'm trying to install LAMP and have a server for my .com. I'm trying to get MythTV to work.

I have set a static IP address using NM

mark@Lexington:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:06:56:14  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe06:5614/64 Scope:Link


wlan0     Link encap:Ethernet  HWaddr 90:f6:52:0c:2d:a4  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0

when the eth0 is connected, I have no internet access. What do I have to do to not lose internet access? Does the WiFi have to drive through the router? How do I do this? Please point me towards a Tutorial or How-To.

By the bye: As I write this, the eth0 is disconnected.

---

### Post by praseodym on 2013-08-02
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by Mark_in_Hollywood on 2013-08-02
Here is the ubuntu pastebin of those terminal responses:


[http://paste.ubuntu.com/5941173/](http://paste.ubuntu.com/5941173/)

---

### Post by praseodym on 2013-08-02
Check the IP addresses, other subsystems:

```
eth0 Link encap:Ethernet HWaddr 40:61:86:06:56:14
inet addr:[COLOR="#FF0000"]192.168.0.101[/COLOR] Bcast:192.168.0.255 Mask:255.255.255.0

wlan0 Link encap:Ethernet HWaddr 90:f6:52:0c:2d:a4
inet addr:[COLOR="#FF0000"]192.168.1.73[/COLOR] Bcast:192.168.1.255 Mask:255.255.255.0
```
Sure this is right?

---

### Post by Mark_in_Hollywood on 2013-08-02
It is the info in the "Connection Information" of the panel's Connection Manager. I've attached screenshots of the two (eth0 and wlan0) devices.

I'm trying to clarify here. I have access to the internet via wifi. It's a uverse motorola ATT modem. I have a wifi router connected to the ethernet port of my computer. I want to use this router connected to the computer's ethernet port to send the MythTV signal to a "smart" tv's ethernet port. It is not for internet access, except as a way to pass through the 'net to the "smart" tv.

But one thing at a time, first.

---

### Post by Mark_in_Hollywood on 2013-08-03
Following this post:


[http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/](http://www.sudo-juice.com/how-to-a-set-static-ip-in-ubuntu/)

I am able to have some ethernet-working and wifi connectivity for internet access, simultaneously.

I can see the following by changing the last octet's digit or digits: example: 192.168.0.1 or 2 or 268 or 10

I can see the control panel pages for

My ISP's modem

My wifi router connected via an ethernet cable

and

SiliconDust's tv tuner

whether I can send the TV signal out from the MythTV through the ethernet cable to the TV's ethernet port remains to be solved.

---

