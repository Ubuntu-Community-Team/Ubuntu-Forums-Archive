---
title: "wireless can only access local network"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by louislepperd on 2008-12-14
hello
I recently purchased an air live usb wireless adapter(wt-2000)
before i bought it I found linux drivers somewhere online.
when i plugged it in ubuntu recognized it automatically but when I put my ip address settings in and connected to my home network I was only able to access my local network and possibly only ip addresses(that means that I can use a local php proxy on my webserver(but its slower than usual)).
I am using the same dns servers as one of my computers that is connected(wired)to the network.
as well as gnome I also have kde xfce and fluxbox and I dont know if any of their tools is doing anything.
Any ideas?
Louis

---

### Post by razy60 on 2008-12-14
Maybe your running to many progs and its getting confused,

One of the things i've found is you have to ensure that any usb wireless device needs to be compatible with the router.
My house mate bought a belkin wireless usb which was ok, until i changed to sky, they then sent there router at which point his wireless refused to work until he changed to a sweex usb. and that was him using vista.(which is really rubbish on wireless)

Raz

---

### Post by joebeasley on 2008-12-17
Did you add a default gateway and add your dns servers to /etc/resolv.conf?

---

