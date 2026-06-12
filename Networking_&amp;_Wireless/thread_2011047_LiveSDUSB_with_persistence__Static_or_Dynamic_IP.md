---
title: "LiveSD/USB with persistence / Static or Dynamic IP"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by Jahragon on 2012-06-26
Hey ladies/and gents, hope you can help me out here.

I am going to have alot of pcs running ubuntu off of a liveusb or live sd card. my problem is that for some sites i will use static ips and need to be able to customize this if needed, Ive tried remastersys and did a backup of ubuntu 11.10 and tried to just go to /etc/network/interfaces and change it there but it does not persist. 
So All in all, what would be the easiest method of being able to mass produce Ubuntu 11.10 on usb/sd (no hard drive in the computers, so they have to run off the usb or sd card), where i can choose to have a static ip, that will persist.

Thanks in advance for your help or any suggestions.

---

### Post by TheFu on 2012-06-26
> **Jahragon said:**
>  so they have to run off the usb or sd card), where i can choose to have a static ip, that will persist.
Thanks in advance for your help or any suggestions.

The easiest way is to use DHCP Reservations to assign specific static IPs based on the MAC address of the network card inside the computer.

[http://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again](http://lifehacker.com/5822605/how-to-set-up-dhcp-reservations-so-you-never-have-to-check-an-ip-address-again)

This method only works where you control the network, but that's where these static IPs matter most, right?

It also means that any network device that supports DHCP can use this method without changing the OS settings.

Anyway, I hope this is what you need.

---

### Post by Jahragon on 2012-06-27
Yeah unfortunately this isn't an option, it has to be set static on our side.

---

### Post by Jahragon on 2012-06-29
ok found a solution;

1) create a liveusb with persistence
2) create a custom_script that will assign the ipnumber and subnet at startup

for my sample i used ubuntu 11.10 desktop and my custom script is as follows
ifconfig eth0 127.0.0.1 netmask 255.255.255.0 broadcast 127.0.0.1
route add default gw 127.0.0.1 eth0

---

