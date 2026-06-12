---
title: "ubuntu / linux as a network switch or routher"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by pcmann2004 on 2009-05-31
Hey all!
any one experimented with making a pc with multiple NICs into a switch / router. i searched this as well as other forums. i cant find anything. this project might be a CISCO alternative for me. any and all help will be appreciated!

---

### Post by Phil Usher on 2009-05-31
Take a look at [http://www.untangle.com/](http://www.untangle.com/)

---

### Post by eentonig on 2009-05-31
1. **install ubuntu server.**
2. **Enable both NIC's**
3. **Enable ip forwarding **
by running the following (this works on the fly but isn't saved between reboots)
> echo 1 > /proc/sys/net/ipv4/ip_forward

There are better ways, but I automated this through /etc/interfaces when my external NIC comes up.
4. **Enter a default route** to the external network
> route add default gw 192.168.1.254 eth0
Again, this is automated through my /etc/interfaces setup

Et Voila, my spare HW became a router for my home network.

It's not the cleanest setup, but this was fast and easy. I also enabled NAT anhd firewalling through iptables.

---

### Post by eentonig on 2009-05-31
Oh, and 2" of Google:

[http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_Linux_router_or_firewall_distributions)

---

### Post by pcmann2004 on 2009-05-31
thanks for everyone's input this quickly, anyone have tried out these method with 4 NICs. i am setting up VLANs also (eg 192.168.1.0/24 192.168.2.0/24 192.168.3.0/24 192.168.4.0/24 etc) i found [http://www.gibraltar.at/](http://www.gibraltar.at/)   hopefully i can combine it to this homebrew switch \ router \ NAT

---

### Post by t0mppa on 2009-05-31
Easiest bet by far is picking something off the list of those specific distributions designed to handle this. Myself, I had an old 486 box lying around, went and bought some extra NIC's, downloaded IpCop and it was real simple to set up.

During the install, you pick what you want out of it. Lots of options and it supports up to 4 different networks, full fledged firewall and lots of other stuff. And there are plenty of add-ons for it, so that you can for instance cache any larger downloads, so you only need to download system updates once for all the machines that use the same OS.

Since the OS doesn't have any extra fluff, it runs perfectly on an older box and still gives a fairly thorough web UI, so you don't even need a display, mouse or keyboard for it, just configure it through a browser from another machine.

If you insist, most of these things are doable through Ubuntu as well, but getting a specific distro WILL save you a lot of time and effort.

---

