---
title: "How to connect to internet, so complicated."
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by giorgiomartini on 2009-03-18
How in the world do i conect to the internet in ubuntu ?


I have the cable conected to my computer but i just cant get oline.



what do i have to do ?


where do i get the mac adress and how to set up all those complicated things i show in the screen shot.

please help , ubuntu is so comlicated for me.:(

---

### Post by issih on 2009-03-18
Unless you messed about with it, it should have set up a dhcp connection by default, anyway..

Your ethernet ports mac address is the HWaddress of eth0 from ifconfig, i.e. from your screenshot it is:

```
00:18:f3:bb:d3:11
```

As for the rest, assuming you have a router that is set up correctly and has dhcp, do the folowing.

1)Enter that as the mac address
2)Leave the mtu as automatic
3)ignore the 802.1x tab completely
4)go to the ipv4 tab and select method from the drop down as "Automatic(DHCP)"

That should be all you need.

Hope that helps

---

### Post by giorgiomartini on 2009-03-19
> **issih said:**
> Unless you messed about with it, it should have set up a dhcp connection by default, anyway..

Your ethernet ports mac address is the HWaddress of eth0 from ifconfig, i.e. from your screenshot it is:

```
00:18:f3:bb:d3:11
```

As for the rest, assuming you have a router that is set up correctly and has dhcp, do the folowing.

1)Enter that as the mac address
2)Leave the mtu as automatic
3)ignore the 802.1x tab completely
4)go to the ipv4 tab and select method from the drop down as "Automatic(DHCP)"

That should be all you need.

Hope that helps

Thanx man , i tried thtat, but when i clik ok the tab just closes and im still without internet, the router works in vista,  how do i know if i have a dhcp ?

---

### Post by mcla0203 on 2009-03-19
> **giorgiomartini said:**
> Thanx man , i tried thtat, but when i clik ok the tab just closes and im still without internet, the router works in vista,  how do i know if i have a dhcp ?

You were very close in your screen shot to being able to tell if you have DHCP on.  If you go to edit your network settings, as in your screen shot, you have to click the IPv4 tab.  In there if it says "Method: Automatic (DHCP)" then you know it is DHCP.  It should be by default though.  I am guessing you cannot connect to the internet a driver failed in Ubuntu for your wireless card, but Vista had it installed right off the bat.  Do you know what kind of networking card you have?

---

### Post by issih on 2009-03-19
Dhcp is something your router will either have turned on or it won't. I can't tell you how to find that out. In esence dhcp automatically assigns an ip address (required for networking) to any computer connecting to the router. If dhcp is off then you have to use static ip assignment.

if in the output of "ifconfig -a" the eth0 interface doesnt have an inet address then its still not working. If it does have one (and it doesn't start with 169 then you should at least have the local networking up and running.

Either way to really diagnose things we really need to know a bit about your router. What is its ip address?, it is probably something like:

192.168.0.1, 192.168.1.1, 192.168.100.1 or 10.0.0.1, but there is no real guarantee here and it varies from manufacturer to manufacturer, so if you don't know you will have to dig out your manual.

---

