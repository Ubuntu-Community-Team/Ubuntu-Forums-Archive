---
title: "Cannot connect to LAN from recovery mode"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by Wise Ferret on 2011-11-25
Hello! 11.10 user here.

I played with a ppa I shouldn't have played with, and broke my system (lightdm loads and re-loads in an endless loop). I want to clean my mess up with ppa-purge, but I do not have a liveCD or means to make one for chroot.

No problem, right? I can still go to recovery mode from grub and connect to the internet from there! But, alas, my network is not working. After choosing recovery mode from grub I chose fsck, passed it, chose "root terminal with networking", and nada. apt-get gives me unresolved domains. The LAN works from windows (I use dual boot).

I tried using "ifconfig eth0 up" and "dhclient" (without really understanding what I am doing) and got no errors, but no network either.

What can I do to get connected again?

---

### Post by SeijiSensei on 2011-11-25
If you're using an Ethernet cable, you can configure the network card manually with ifconfig.  You'll need to give the machine an IP address in the same subnet as the router.  If your router assigns addresses in the common 192.168.1.0/24 subnet, and the router has 192.168.1.1 as its address, you can try this:

```
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ip route add default via 192.168.1.1
```

Now you should be able to ping the router at 192.168.1.1  If the router also provides DNS name resolution for you, then edit /etc/resolv.conf by running "sudo nano /etc/resolv.conf" and add these two lines:

```

nameserver 192.168.1.1
nameserver 8.8.8.8

```

The second entry is one of the public DNS servers that Google provides.  It will use that if there's not a working nameserver at 192.168.1.1.

---

### Post by Wise Ferret on 2011-11-26
Thank you very much, SeijiSensei. I found a more simple but far weirder solution: just log in as my user, using the "login" command. Then the network suddenly starts working. I have no idea why it is so.

---

### Post by kasmanit on 2011-12-01
Thans a lot SenjiSensei

You were more than very useful :)

---

