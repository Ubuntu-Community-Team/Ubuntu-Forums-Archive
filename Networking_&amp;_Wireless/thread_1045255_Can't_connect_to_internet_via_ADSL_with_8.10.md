---
title: "Can't connect to internet via ADSL with 8.10"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by LonelyTraveler on 2009-01-20
Hi guys.

I might have asked this question here before, but nobody could help me, so as this is about 2 and a half months later I figured I'd try again. Was actually hoping this would be sorted out via a update by now.

Since doing a fresh install to 8.10, my ADSL (wired, lan or whatever you wanna call it) does not work. When I plug the modem in, the network manager starts working and then connects to a connection it creates on its own called Auto eth0. Only problem is this is all it does. I can't open websites, ping Google, or even ping the router. My work computer running Windows XP is connected to the same router, so the router is fine. 

The machine is question is my personal laptop and it has a built-in 3G card which works perfectly with the network manager.

With 8.04, I could just plug the cable in and it worked perfectly. 

So I would really appreciate it if someone can help me as I need both connections here.

I can never remember what commands to run to get more information, like what kind of network card I have, so please let me know so I can post that information. (And make a note of the commands this time! ;) )

Thanks a lot.

---

### Post by all metro on 2009-01-20
I am having the same problem. I have a dual boot system. When I boot to XP my network works fine. When I boot to Ubuntu with the same setting it says I am connected but Firefox wont load.

When I run "sudo dhclient eth0" I get the following:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Not sure if that normal? 

Thanks Tim

---

### Post by LonelyTraveler on 2009-01-20
> **all metro said:**
> I am having the same problem. I have a dual boot system. When I boot to XP my network works fine. When I boot to Ubuntu with the same setting it says I am connected but Firefox wont load.

When I run "sudo dhclient eth0" I get the following:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Not sure if that normal? 

Thanks Tim

Hi.

I'm not at work at the moment so I can't check what response I get to that command. Will check tomorrow and let you know.

---

### Post by LonelyTraveler on 2009-01-21
> **all metro said:**
> I am having the same problem. I have a dual boot system. When I boot to XP my network works fine. When I boot to Ubuntu with the same setting it says I am connected but Firefox wont load.

When I run "sudo dhclient eth0" I get the following:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Not sure if that normal? 

Thanks Tim

I take it you only posted the last part of the output? This is what I get:

```
crownambassador@CrownAmbassador-Laptop:~$ sudo dhclient eth0
[sudo] password for crownambassador: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No buffer space available
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1c:23:18:d4:0d
Sending on   LPF/eth0/00:1c:23:18:d4:0d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Message too long
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by LonelyTraveler on 2009-01-21
Tim,

What card are you using? (Command: lspic)

I'm using a Broadcom Corporation NetXtreme BCM8755M Gigabit Ethernet PCI Express.

---

### Post by saygin on 2009-02-02
I am experiencing the sam problem too. I used to have internet connection with 8.04 but now, it can't connect to internet. I don't know what to do. Haven't yo found a solution yet?

---

### Post by LonelyTraveler on 2009-02-03
> **saygin said:**
> I am experiencing the sam problem too. I used to have internet connection with 8.04 but now, it can't connect to internet. I don't know what to do. Haven't yo found a solution yet?

Hi,

It has been resolved yes. Remove the words "interface-mtu" out of /etc/dhcp3/dhclient.conf

I also edit /etc/NetworkManager/nm-system-settings.conf and changed managed=false to managed=true. This is optional, but without it the network app will say you're disconnected.


Let me know if this worked for you!

---

### Post by saygin on 2009-02-04
It worked! thanks a lot for your help!

---

### Post by LonelyTraveler on 2009-02-05
> **saygin said:**
> It worked! thanks a lot for your help!

Great! Glad I could help!

---

### Post by dragonmojo on 2009-02-05
It did not seem to work for me.

---

### Post by LonelyTraveler on 2009-02-05
> **dragonmojo said:**
> It did not seem to work for me.

Are you still using Hardy or are you on Intrepid? I had this problem with Intrepid but not on Hardy.

When you run ifconfig eth0, do you get an ip address?

---

### Post by visibletrap on 2009-03-16
> **LonelyTraveler said:**
> Hi,

It has been resolved yes. Remove the words "interface-mtu" out of /etc/dhcp3/dhclient.conf

I also edit /etc/NetworkManager/nm-system-settings.conf and changed managed=false to managed=true. This is optional, but without it the network app will say you're disconnected.


Let me know if this worked for you!

This worked for me!! Thanks

---

