---
title: "Trouble connecting to wireless network, adpator keeps getting wrong IP?"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by flatland2d on 2009-08-30
I first noticed this problem a couple nights ago when I was trying to install ZoneMinder.  I had to install about a dozen other libraries as it was installing to try to get it to work.  I don't know exactly what happened, but my wireless didn't work after that.  Could have been just coincidence though.

My wireless card thinks it's connected to a my network (says connection established) but shows zero bars and is not actually connected.  I've tried setting the wireless for DHCP and static IP, but can't seem to get that to work.

Tried reinstalling and on the first boot had the exact same problem before.  I know that Ubuntu wireless works out of the box on this computer.  Only formatted and installed /, and kept the same /home partition.  I did manage to get the wireless working breifly by editing some files in /etc/network, but now it's gone back to not working.  Could there be something in my /home directory screwing it up?  I would have thought a full reinstall would have made it work again.  It's never been an issue before.

Here is ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:23:5a:4a:1f:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:23:40:97  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe23:4097/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6181 (6.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-23-40-97-30-39-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Notice the 10.42.43.1 address on wlan0.  My home network is on 192.168.1.*.  I have no idea where this IP is coming from.

Laptop is an Acer One 10", which has an Atheros AR242x wireless card.  Let me know if there is any more information I can provide.  Thanks for any help!

---

### Post by flatland2d on 2009-08-30
I can add that when starting from live CD (USB drive), wireless works like it used to.

---

### Post by uylug on 2009-08-30
If you've gotten it to work using a complete different environment but you couldn't if you kept your home folder, why don't you do it without your settings?

Create a new user and check if it works!

---

### Post by Iowan on 2009-08-31
Any static configuration left in */etc/network/interfaces*?

---

### Post by flatland2d on 2009-08-31
> **Iowan said:**
> Any static configuration left in */etc/network/interfaces*?

Yes there was.  Deleted this, changed back to DHCP and it worked perfect.  Thanks for the help.

---

