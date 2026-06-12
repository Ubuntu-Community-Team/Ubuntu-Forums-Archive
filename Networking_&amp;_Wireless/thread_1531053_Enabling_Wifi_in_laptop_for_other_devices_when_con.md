---
title: "Enabling Wifi in laptop for other devices when connected to Wired Network"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by samalex on 2010-07-14
This may be more suited for the networking forums, but I figured Community Cafe would be well rounded enough for someone to tell me if this is even possible (with minimal configuration that is).

There are a few places I travel where I only have a wired connection to the Internet (no wifi), but when this happens is there a simple way to create an adhoc network so wireless devices can route through my computer and to the network?  Reason I'm asking is I'm thinking of getting an iPad or iPod Touch which have wireless connections, but in the cases where my laptop is using a wired ethernet connection and the wireless card isn't used, I'd like to create an adhoc wireless network that'll let such wireless devices work.

Thanks for any suggestions on how to make this work.  And again I don't want something that's too crazy to setup since most of the time my laptop will be using the wireless network so i need the configurations interchangeable.

Thanks --

Sam

---

### Post by blueturtl on 2010-07-14
Should be possible if your Wi-Fi supports operation in AP (Access Point) mode. I wonder though if you can accomplish this using the GUI... haven't seen any indicative checkboxes or other settings in NetworkManager.

edit: You'll probably want to install a package called dnsmasq which will allow you to create a NAT for the device(s) connected to your wireless interface. I've used it succesfully with wired connections, but have not tried wireless...

edit 2: Ok, so basically it goes something like this:

1) Enable AP mode for your Wi-Fi
2) sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
3) sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
4) sudo apt-get install dnsmasq

---

### Post by Austin25 on 2010-07-14
This probably belongs in one of the support forums, but I would like to know as well. Specifically, it would be nice to have a shell script to enable it. I'm thinking iwconfig, but not sure quite what to do.

---

### Post by cariboo on 2010-07-14
The Cafe is not a support forum. Move to networking & Wireless.

You may want to have a look at this [page]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

---

