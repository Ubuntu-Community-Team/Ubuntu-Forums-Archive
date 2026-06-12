---
title: "route configuration"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by goodfella on 2006-06-13
I just recently upgraded to 6.06.  I have an ethernet card and a wireless card installed on my pc.  The wireless card works fine.  When I had 5.10 installed I disabled the ethernet card,  but now since I upgraded I have to issue 'ifconfig eth0 down' in the terminal after every boot.  My interfaces file does not bring up this device, so I don't know how it gets started at every boot.  Also when I use the route command after boot I do not have a default gateway which forces me to issue 'route add default gw' at the terminal with the ip address of my router so I can have internet access.  How do I set up the routing table correctly for every boot and how do I stop my ethernet card from starting at every boot?

---

### Post by Joeb on 2006-06-13
If you go to the network settings under System==>Administration==>Networking, you should be able to deactivate your ethernet nic there and also set your default gateway for your wireless.  The settings should stick the next time you reboot.

---

### Post by goodfella on 2006-06-13
My ethernet card under System==>Administration==>Networking is already deactivated; that was the first place I checked.

---

### Post by goodfella on 2006-06-14
Also my wireless card is shown to be the default gateway device yet still at reboot I have to issue the commands I stated earlier to be able to access the internet.

---

