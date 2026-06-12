---
title: "How do I connect my laptop to an ethernet router?"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Klasanov on 2009-09-22
I am running Ubuntu (either 8.04 or 8.1, not sure which... how do I check?) on a Toshiba Laptop that originally had Vista. Networking was fine in Vista, and networking in Linux was fine when I was at the college taking classes. But at home I can't get it to connect.

I ran pppoeconf once and just hit enter through all the prompts, and that allowed me to connect to the internet until I had turned off the computer. Subsequent runs through pppoeconf had no effect.

I don't know a lot about networking. I know the ip address of my router is 192.168.1.101, but what do I need to do to get connectivity to my laptop through my router?

If you need more info let me know. Not too familiar with networking, as I said, so not sure what you guys need or don't need.

---

### Post by i.r.id10t on 2009-09-22
If your router is handling your PPPoE connection, you probably just need to run dhclient (the dhcp client command) on the laptop for it to get an IP.

---

### Post by badger_fruit on 2009-09-22
if you're connecting to an ETHERNET router, then you need an ETHERNET cable ...
you shouldn't need to pppoe unless the laptop connects to the unternet directly (ie via a USB ADSL modem)

I presume that your setup is ...


INTERNET --- MODEM --- ROUTER --- LAPTOP

If that's the case, then just plugging in an ethernet cable to your laptop and the other end into the router will get you online, if DHCP is enabled on the router then you don't need to do anything else .... other than what [i.r.id10t]("http://ubuntuforums.org/member.php?u=478834") said

---

### Post by Iowan on 2009-09-22
> **Klasanov said:**
> I am running Ubuntu (either 8.04 or 8.1, not sure which... how do I check?)System>About Ubuntu.
Might need to look through */etc/network/interfaces* to see if something got left there by **pppoeconf**

---

### Post by Klasanov on 2009-09-22
I ran dhclient and this is what I got

Listening on LPF/pan0/d6:e6:af:e9:90:5b
Sending on   LPF/pan0/d6:e6:af:e9:90:5b
Listening on LPF/eth0/00:1e:33:3a:f9:a6
Sending on   LPF/eth0/00:1e:33:3a:f9:a6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

What do I do now?

---

### Post by Iowan on 2009-09-22
Check [this]("http://ubuntuforums.org/showthread.php?t=1156441") one.

---

### Post by Klasanov on 2009-09-23
I did.

I don't see any line that says "rfc3442" in /etc/dhcp3/dhclient.conf

:confused:

---

### Post by Klasanov on 2009-09-23
> **Iowan said:**
> System>About Ubuntu.
Might need to look through */etc/network/interfaces* to see if something got left there by **pppoeconf**

/etc/network/interfaces says

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auth eth0
iface etho inet manual

---

### Post by Iowan on 2009-09-23
> **Klasanov said:**
> I did.

I don't see any line that says "rfc3442" in /etc/dhcp3/dhclient.conf

:confused:
Sorry - brain slipped out of gear.  I DID notice you mentioned running 8.04 or 8.10 - I think the rfc3442 arrived with 9.04. 
Try commenting out (#) everything but the two lines about "lo" (the first two lines). Restart networking ( **sudo /etc/init.d/networking restart**) and see what happens.

---

### Post by Klasanov on 2009-09-24
Thanks, it works now.

This is what I did.

Commented out like you said. Didn't work. Said something about ignoring unknown devices.

Deleted all but the two lines. Got a message saying it had reconfigured the connection. Still no connection.

Restarted linux and opened firefox, and it worked.

So, thank you. A lot. I can start programming again :)

---

