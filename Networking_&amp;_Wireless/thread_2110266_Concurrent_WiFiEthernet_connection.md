---
title: "Concurrent WiFi/Ethernet connection"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by Core2uu on 2013-01-29
I posted this in the Raspberry Pi Forums, however, since this issue pertains to the Operating System (Ubuntu), way more than the Pi, I feel like I'll get more help here.

Hi all,

BACKGROUND
I have my Raspberry Pi successfully connecting to my laptop over direct ethernet connection using this guide: [http://www.mccarroll.net/blog/rpi_netbook/index.html](http://www.mccarroll.net/blog/rpi_netbook/index.html)

THE PROBLEM
There is one problem, however; I'm supposed to stay connected to WiFi while I'm also connected with the Pi, however, **whenever I connect to the Pi, I lose my WiFi connection.**

THINGS TO NOTE
I followed the guide **exactly**, EXCEPT; a) I'm not using a crossover cable, just a regular cable but it seems to work fine (the RPi is supposed to have an auto-sensing port so it makes sense); b) In the section in the guide where it tells you to put the following code in **dhcp.conf**,

```
ddns-update-style   none;
default-lease-time 3600;
max-lease-time 7200;
authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
  option routers 192.168.1.1;
  range 192.168.1.100 192.168.1.200;
}
```

**I put it in dhpcd.conf as well** because I needed to to make it work.

Anyone have any ideas? I'm sure it's a simple fix but I'm no Linux wizard and as such, don't know how to approach this.

Thanks

---

### Post by elgordodude on 2013-01-29
Go to your Network Connections page Then click Wired connection 1 -> Edit -> IPv4 Settings -> Method: Shared to other computers

That will tell ubuntu to stop looking for an internet connection there and expect a device instead.

---

### Post by Core2uu on 2013-01-29
> **elgordodude said:**
> Go to your Network Connections page Then click Wired connection 1 -> Edit -> IPv4 Settings -> Method: Shared to other computers

That will tell ubuntu to stop looking for an internet connection there and expect a device instead.

Doing this, I do get my WiFi back... unfortunately, however, this kills the connection with the Raspberry Pi. :( (Probably because the connection to the Pi is set up with DHCP, or something like that).

Any other ideas?

---

