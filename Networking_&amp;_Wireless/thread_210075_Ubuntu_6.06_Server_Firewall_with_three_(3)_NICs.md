---
title: "Ubuntu 6.06 Server Firewall with three (3) NICs"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by gant1979 on 2006-07-06
Hi all.

I have installed Ubuntu Server with Ubuntu-desktop (Gnome) and I did this in order to use firestarter. The role of this server is firewall and internet connection sharing and it has 3 NICs. The first belongs to the outside network that communicates with the adsl router and the other two belong to two different subnetworks: 192.168.123.0/24 and 192.168.125.0/24.

No matter how much I have searched I can't seem to fine a quide for having a NAT with two sub networks. Every guide has as an example of an Ubuntu machine with two NICs (external and internal). 

My problem is that in Firestarter in the Preferences \ Networking options where it gives you the option to choose the "Local Network Connected Device" which is the Internal NIC, I can choose only one of the two which means that Internet Connection Sharing is used only by the selected NIC and the other does not have Internet... Is there anyother way of making it understand that I want the internet to be shared into two (2) NICs and not one (1)...

I hope someone can help me because I can't seem to find my way out of this for the last two days...

---

### Post by hda on 2006-07-06
Have a look at shorewall: [http://www.shorewall.net/]("http://www.shorewall.net/")
It's in the repos.

_hda_

---

### Post by gant1979 on 2006-07-06
So this is the only solution? The good thing about Firestarter is that you can watch the network activity, requests and ports made by the clients in real time and then easily create rules. Shorewall has no GUI to monitor network activity.

---

### Post by hda on 2006-07-06
[quote=gant1979]So this is the only solution? The good thing about Firestarter is that you can watch the network activity, requests and ports made by the clients in real time and then easily create rules. Shorewall has no GUI to monitor network activity.[/quote]

On **server** systems, you usually don't have a GUI. To monitor network activity you would use tools like **mrtg**, etc.

---

