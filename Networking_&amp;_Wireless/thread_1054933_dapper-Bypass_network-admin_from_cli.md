---
title: "dapper-Bypass network-admin from cli"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by vector on 2009-01-30
HI all
Is there a way to renable network from the cli after it has been disabled using the gnome network-admin gui. dapper

I am in a world of trouble.

I have lost gnome gui. some problem with bonobo. But my main hassle now is that I have no network access. The last thing i did was to disable the network using the network settings. On reboot I suddenly have bonobo problems stopping the gui and no network with which to try and reinstall config things.

I have tried the simple ifconfig eth1 up (which is the wireless card) but it doesnt seem to grab an IP from the router.

---

### Post by vector on 2009-01-30
ok  i added
auto eth0
auto eth1
to the /etc/network/interface file
sudo /etc/init.d/networking restart

then restarted the gdm

and we have it back to working

now I just have to fix the bonobo problem

---

