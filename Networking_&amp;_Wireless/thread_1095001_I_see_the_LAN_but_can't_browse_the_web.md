---
title: "I see the LAN but can't browse the web"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by mastroragnatela on 2009-03-13
I have Ubuntu 8.10 installed on a pc I use as a test web server. Everything was fine but I changed from DHCP to static IP because I had problems to reach the apache server from the other PCs. I am not 100% sure, but I think that everything was still working.

Then I modified the network domain in the Samba config file. And another thing I noticed is that while making network configurations I deleted by mistake the default cabled connection and since I created a new one there isn't a MAC address anymore.

Morale: the LAN works fine, but I can't browse the web anymore.

any ideas?

Thanks

---

### Post by madverb on 2009-03-13
Don't use Network Manager to setup a Static IP, it's just pathetic.

Anyway, you will just need to do it all manually. Don't forget to add a DNS to resolv.conf.

---

### Post by issih on 2009-03-13
Intrepid appears to have issues with static ip's and network manager. Actually though, the solution, often, is to do as you have done and delete the default connection and create one from scratch.

grab you mac address from runing 
```
ifconfig -a
```

in a terminal. Most likely your ethernet connection will be eth0, grab the mac address associated with that (it'll look something like this  00:1b:61:b5:cd:f3)

Once you have that, just create a new connection.

Hope that helps

---

### Post by mastroragnatela on 2009-03-13
I did find the MAC address but nothing changed.

Regarding setting the network configuration manually unfortunatelly I have no clue on how to do it. Can you help?

One additional note: I also tried to switch back to DHCP but I still can't browse the web.

---

### Post by issih on 2009-03-13
It really should work with dhcp, try deleting the connection and making a new one using dhcp, and the mac address of your card.

As for doing it manually:

[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

you need to edit /etc/network/interfaces and make sure that it contains something like:

```

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254

```

using your relevant ip addresses obviously. if you have the line:

```
iface eth0 inet dhcp
```

you need to replace it with this block of code, otherwise just add it to the file.

Make sure that you do not delete the lo interface or anything else in there :)

Hope that helps

---

### Post by mastroragnatela on 2009-03-13
It works!

Actually it has been enough to delete the connection and create a new one with the same details and MAC address.

Thanks a lot for your help and the incredibly quick replies. This forum rocks!!!:D

---

### Post by issih on 2009-03-13
Glad to have helped :)

---

