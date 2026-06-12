---
title: "I can connect to every router except one."
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by Scooter_X on 2009-11-30
I've got Karmic on my laptop, and can connect at home, at my in-laws' house and at school. I just can't connect at work. The routers are the same at work as well as the in-laws' house. I've been trying to resolve this weird issue for a few weeks. I can't get any headway. Also, I can connect that laptop when running windows to the router at work. (dual boot, windows 7 and Karmic) Does anyone have any ideas or suggestions? I would appreciate the help. Thanks!

---

### Post by jdstunner on 2009-11-30
Are you getting an IP address? Try running *ifconfig *or clicking the network icon, in the menu bar, and clicking connection information. 

Your wired ethernet connection is most likely eth0. 

In order for the internet to work, you must have:

IP Address
Subnet Mask
Gateway
DNS Server

These are usually provided by a DHCP server, which would be those routers you are connecting to. 

You can try restarting the network service after booting into Karmic.

```
sudo /etc/init.d/networking restart
```

You can also boot into windows, check out your IP information using *ipconfig /all* and assigning those values into Ubuntu statically. 

Good luck!

---

### Post by Scooter_X on 2009-11-30
Boot into windows and do it statically? That's a good idea. I'll give it a whirl.

And as far as the reset goes, I typed: ```
sudo /etc/init.d/networking restart
```

and got:```
 * reconfiguring network interfaces...
 Ignoring unknown interface wlan0=wlan0
                                                [OK]
```

Is that supposed to mean it got reset? Nothing happened.

---

