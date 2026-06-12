---
title: "Ibex - Tried to get static IP, now no network"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by britlion on 2010-08-03
I have an Ibex machine - it's key (for the moment - new server coming) - so I don't wont to upgrade.

It was on DHCP, which was a continuous pain if I wanted to connect directly - the IP was changing all the time.

So I tried to make it static.

I tried:

1> Edit /etc/network/interfaces to read:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.6
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1


Which didn't do anything, and rebooting put me back on DHCP.
So I did 

sudo update-rc.d -f NetworkManager remove

as advised by [http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)


After a reboot, I have no network at all. I don't know how to un-remove the network manager and even get it back to the DHCP PITA that it was. 

One would think that getting a linux box to network statically would be trivially easy... apparently it isn't.

Any ideas, folks?

---

### Post by lisati on 2010-08-03
As an alternative to setting a static IP from Ubuntu's end, I'd suggest that doing it within your router might be a better option. That way, if you move a computer to a different network there'll be less risk of a conflict.

---

### Post by britlion on 2010-08-03
And now it seems to work... Hmm.

The on-desktop gnome applet says it's not connected though, which is worrying - I can however, ping to the internet. Very weird.

---

### Post by Iowan on 2010-08-03
Interfaces defined in */etc/network/interfaces* aren't controlled by Network Manager. I don't remember if Intrepid could change that (I habitually forget which file needs edited...). I remember some articles on converting from DHCP to static address - but will need to search for them.
I'm also a fan of setting up a "static lease" in the DHCP server(router?). then the client (server) can stay set for DHCP.

---

