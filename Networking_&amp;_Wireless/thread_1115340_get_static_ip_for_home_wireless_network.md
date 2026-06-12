---
title: "get static ip for home wireless network"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by raedbenz on 2009-04-03
hi,,
i have managed to make a USB wireless adapter to run using ndiswrapper on ubuntu8.04.
the IPs are assigned by the home router. i wanna give the PC a static ip like 192.168.2.11.

i do this:

```
sudo ifconfig wlan0 down
ifconfig wlan0 192.168.2.11 netmask 255.255.255.0 broadcast 192.168.1.255 up

```

output of ifconfig for wlan0 is
```
inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
```

it doesnt work,the network stops to work completely. why?
cheers

---

### Post by aragorn2909 on 2009-04-04
> **raedbenz said:**
> 
...the IPs are assigned by the home router. i wanna give the PC a static ip like 192.168.2.11.


You've sort of solved your own problem here.  Your *router* assigns IP addresses.  Make the *router* hand out a static IP.

---

### Post by Ericyzfr1 on 2009-04-04
The router set-up screen allows you to reserve IP address, not need to set anything on your PC.

---

### Post by raedbenz on 2009-04-04
lol,,i know that the IPs are assigned by the router..but i want to have fix one. i did that on another PC running WinXp.
i am asking what is the procedure to do it.
more over could i know how many PCs are connected to the router(what IPs are used) ?

cheers

---

### Post by mocoloco on 2009-04-04
I know the GUI way in 8.10's NetworkManager.  Right click it in the systray, go to the "wireless" tab, select your connection, edit, under the IPv4 tab change method to "manual", then put in the ip, netmask, and gateway.
CLI is probably easy too but I don't know offhand how to :)

---

### Post by igoddard on 2009-04-04
> **raedbenz said:**
> lol,,i know that the IPs are assigned by the router..but i want to have fix one. i did that on another PC running WinXp.
i am asking what is the procedure to do it.
more over could i know how many PCs are connected to the router(what IPs are used) ?

cheers

You need to log into your router.  Typically you will have a web interface at the same address as the gateway address.  If you haven't changed the password RTFM for the default password; if you've changed it & forgotten it RTFM for how to reset the router to its defaults - and be prepared to set it up again.

Once logged it you may have an option to view DHCP leases currently handed out.  You should also have an option to set the range of addresses it hands out.  For a home network you'll probably only need a few.  Set it up for, say, 10 or 20 and then set your static IP to something within the subnet range but outside the the range you've assigned to DHCP.

Ian

---

### Post by raedbenz on 2009-04-04
thanx for the reply..
still what about changing IP settings using CLI on wlan0 PC.??

---

