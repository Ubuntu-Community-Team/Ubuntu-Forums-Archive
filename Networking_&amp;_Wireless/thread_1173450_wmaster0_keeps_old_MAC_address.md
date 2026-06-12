---
title: "wmaster0 keeps old MAC address"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by jakslev on 2009-05-29
Dear Everybody, 

Following a paranoid streak, I wanted to be sure that the evil people at HP are not tracking me and gathering a file on my dodgy internet habits and location, based on my MAC address. 

In other words I wanted to investigate how to change the MAC address on NICs, and found a good solution that works perfectly under Ubuntu 9.04, posted by Bluestreek:

sudo gedit /etc/rc.local

Add the lines

ifconfig eth0 down
ifconfig eth0 hw ether 00:00:00:00:00:01
ifconfig eth0 up

ifconfig wlan0 down
ifconfig wlan0 hw ether 00:00:00:00:00:02
ifconfig wlan0 up

ifconfig wmaster0 down
ifconfig wmaster0 hw ether 00:00:00:00:00:03
ifconfig wmaster0 up

This works like a charm on my computer as for the 2 first interfaces. 

As for the changing of the wmaster0, it does not have any effect, and in fact the MAC address of this master virtual device remains the ORIGINAL even though it is changed on the wlan0. 

I am aware that the nice trusting people behind Ubuntu are saying that wmaster0 is only needed in some strange cases with old hardware and salt in the eye; however - speaking for the paranoids - I would like to hear how I can kill the MAC address on this one. 

I would prefer not having to solder anything!!

Cheers, 

jakslev

---

### Post by pytheas22 on 2009-05-29
I think the MAC address for wmaster0 is arbitrarily generated--I've never seen it correspond to a real MAC on any of my systems.  The address of wlan0 is the one that reflects the physical address of your wireless card.  Moreover, the MAC that people would see if they sniffed the packets coming from your computer would be the one associated with wlan0; there's no way for people without access to your computer to know the address of wmaster0, as far as I know.  But I'm no expert.

That said, which kind of wireless card do you have?  If you don't know, post the output of:
```

lspci -nn
```

For some devices there are utilities available to change the MAC hard-coded into the chip; this is possible with Broadcom devices using [ssb-prom]("http://linuxwireless.org/en/users/Drivers/b43#relatedtools"), for example.

---

