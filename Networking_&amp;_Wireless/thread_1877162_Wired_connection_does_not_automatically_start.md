---
title: "Wired connection does not automatically start"
date: 2011-11-07
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2011-11-07
Hi, after changing some settings to remove wireless on my Ubuntu 10.04 machine I now only have a wired connection, which was what I wanted.  

However, the initial wired connection does not work - If I click on the network manager icon, under "Wired Networks" it automatically boots into "ifupdown (eth0)".  I then have to manually select "Wired connection 1" to be able to use the internet.  

If I right click the network manager icon and select "Edit connections", under the Wired tab I can see the two connections ("ifupdown (eth0)" AND "Wired connection 1").  

So I though I could just delete the" ifupdown (eth0)" option, but it doesn't allow me to do this.  I can delete the "Wired connection 1" but I don't want to do this as this is the one that works.  

Is there any way to get the working "Wired connection 1" to be the default when I login?

Cheers

---

### Post by praseodym on 2011-11-07
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
```
Checkbox all (at least network -but better all-) rights in "USERS&GROUPS", remove the profile in the NM-applet and reboot.

---

### Post by SnoopFogg on 2011-11-14
Hi, when I saw the /etc/network/interfaces I realised the problem.  At the time I was having issues setting up a fixed IP address too and the solution was to add the following which I have now "#" out.  

auto eth0
iface eth0 inet static
address 192.168.0.21
netmask 255.255.255.0
gateway 192.168.0.1

All working and I have reset a static IP address via the router which at the time I didn't know how to do. 

Thanks for you help.

---

