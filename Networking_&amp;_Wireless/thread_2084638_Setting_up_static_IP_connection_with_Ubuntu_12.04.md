---
title: "Setting up static IP connection with Ubuntu 12.04"
date: 2012-11-16
forum: Networking &amp; Wireless
---

### Post by lololol123 on 2012-11-16
Hey guys,
I installed Ubuntu 12.04 64 bit on my laptop yesterday and bear in mind I am a COMPLETE newbie when it comes to Ubuntu or even computing in general so please keep that in mind when your posting solutions :-).

Okay so we use a static IP, and after installing Ubuntu I tried to set the static IP using the network manager but the save option was greyed out. After googling for about an hour I managed to change the <inactive></inactive> bit of the following file freedesktop.org.NetworkManager.policy from no to yes. I changed all of them logged out and logged on again but, lo and behold, no change. After banging my head on the wall for about 5 minutes I tried again. This time, after another hour, I changed the /etc/Network/interfaces file to 
auto lo etho
iface lo net loopback
iface lo net static
     address 192.168.1.155
     netmask 255.255.255.0
     gateway 192.168.1.1

and after restarting using this

sudo /etc/init.d/networking restart

and logging out and in again, I managed to connect to the Internet

However, when I turned on my PC this morning, the Internet doesn't seem to be working. Help please :-(

---

### Post by chili555 on 2012-11-16
> I changed the /etc/Network/interfaces file to
auto lo etho
iface lo net loopback
iface lo net static
address 192.168.1.155
netmask 255.255.255.0
gateway 192.168.1.1Yikes!! Please try:```

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.155
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```I assume you have some typographical errors in there. Spelling, terminology, etc. are crucial. Ubuntu won't guess what you want. It will simply not perform. Reboot and let us have your report.

---

### Post by oldfred on 2012-11-16
If manually configuring in networking interfaces file you need to un-install the gui network manager as they conflict. 

Also most routers have DHCP ranges starting at 100 and either the next 50 or 100 are already allocated. You cannot use any of those addresses without conflicts. So check what ranges is used by your router.

---

