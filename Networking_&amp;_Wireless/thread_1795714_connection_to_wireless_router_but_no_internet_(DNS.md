---
title: "connection to wireless router but no internet (DNS?)"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by grw on 2011-07-03
Hi,

We just set up a password for our wireless router (D-link DIR-615). WPA personal.

After doing that, I can no longer connect to the internet. I can connect to the wireless router, however.

Same problem for the Apple Macs in the house. We called Dlink. The fix for a Mac was to add DNS servers (4.2.2.2) under TCP/IP

But there doesn't seem to be anywhere to specify a DNS server in Ubuntu.

Can anyone help?
Thanks
Gwyn

---

### Post by Iowan on 2011-07-03
I'm on wired connection - but Network Manager gives the option to specify DNS servers.

---

### Post by chili555 on 2011-07-03
In Network Manager, Edit Connections, select wired or wireless as appropriate, click the IPv4 settings tab and add DNS as per the attached.

---

### Post by grw on 2011-07-04
Thanks.
The problem is that I am connected to the wireless router via DHCP (the router itself has a static connection to our ISP). This means that the DNS servers box is greyed out. I can't enter anything.

I tried the two options described in this post (which says "The default setup of Ubuntu does not make it easy to use static DNS servers while using DHCP). Neither worked:
[https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)

If you follow the link above, the first option is to edit /etc/network/interfaces
On my computer this file says:
[INDENT]auto lo
iface lo inet loopback[/INDENT]
There is no wlan1 entry, (as I am guessing there should be).

Anyway, I have set up a manual rather than DHCP connection to the wireless router. I just copied the settings from another computer in the house (a Mac). I can now access the internet. My connection seems slow to me, however.

If anyone knows how I can connect via DHCP AND specify DNS servers, I would still be interested to learn.

Thanks

---

### Post by Iowan on 2011-07-04
There *should* be an option for **Automatic (DHCP) addresses only** that enables the DNS selection box.

---

### Post by chili555 on 2011-07-04
Get out your welding gloves, let's try old-school methods. Please do:```
sudo gedit /etc/resolv.conf
```Change the file to read like this; eliminate all other settings.```
nameserver 4.2.2.2
```Proofread, save and close gedit. Now, Network Manager will attempt to rewrite it, so let's make the file unwritable:```
sudo chmod -w /etc/resolv.conf
```Now, if it's unwritable, it's unwritable even by you, even by sudo you! If you need to change the file, reverse the chmod with +w.

Please try it and let us know.> The problem is that I am connected to the wireless router via DHCP Must you? Many of us have a mix of both static and DHCP addresses on the same router. As long as you select an address outside the range of the DHCP server, there is not any reason you can't have a static IP address. My wife's computer has a static address specifically so I can ssh into it to administer it and make it play funny noises without having to leave my chair.

---

### Post by Bucky Ball on 2011-07-04
Or how about in /etc/network/interfaces, something like:

```
iface wlan0 inet dhcp
dns-nameservers 4.2.2.2

auto wlan0
```

---

### Post by grw on 2011-07-05
Thank you everyone!

I followed Iowan's suggestion in the end. All working with 'Automatic (DHCP) addresses only' and DNS server entered.

---

### Post by Bucky Ball on 2011-07-05
Great news! Please mark as 'solved' from 'Thread Tools', top right. ;)

---

