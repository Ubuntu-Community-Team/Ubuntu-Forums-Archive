---
title: "Vbox guests on 2 different hosts need to connect"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by varelov on 2011-07-15
In my home network I have two ubuntu desktops that are connected to a router. On each pc I have installed Virtual Box 3.2 and various OSes. I need to sometimes run multiple vm's at the same time which is very RAM intensive so I was wondering if there is any way to connect VM's on different hosts so that they appear they are in the same network? Various articles that show up as search results hardly pertain to what I want to do.
 Basically, I would like to make vm's visible in the network but on different hosts and with ip addresses that would reflect that those vm's are on a same network.
Like ubuntu 1 has vm's a and b and ubuntu 2 has c and d. When I start all of the vm's, I would like them to connect to each other just like they are in the same network without "knowing" they are on different hosts.

---

### Post by jmoorse on 2011-07-15
Set their network adapters to 'bridged' in Vitualbox and they will grab DHCP from your LAN.

---

### Post by varelov on 2011-07-15
I have their nics set to "Bridged" but when I start up the vm and inspect for ip address, there is none. No ip address, just hardware address after ifconfig.
Is it a wrong type of adapter that I choose for the virtual nic? I took the default offered, Intel PRO/1000 MT Desktop.
So how do I get the LAN's dhcp to give address to the bridged adapter? I am using virtualbox ose 3.2.8

---

### Post by varelov on 2011-07-15
In a moment of panic I reached for Synaptic and got me the bridge-utils. And then, in a "light-bulb" moment I reached for some networking config files on the guest and set its NIC's to turn on when booting and ask dhcp for an address.
The lightbulb moment came while working on the guest with a GUI. I guess you have to see to believe ](*,)
I don't know if bridge-utils played a part in solving this.
Thank you jmoorse for your kind nudge.

---

