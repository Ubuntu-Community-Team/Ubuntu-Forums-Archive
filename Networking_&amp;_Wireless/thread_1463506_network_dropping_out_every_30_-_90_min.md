---
title: "network dropping out every 30 - 90 min"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by austclint on 2010-04-27
Hi

I am running ubuntu 9.10 server and last night i was fiddling with proftpd and ended up uninstalling it and installing vsftpd and i also installed acpid so I could shut down the box by the power button.

And now the box is dropping off the network every 30 - 90 min, could someone tell me why this is?

---

### Post by computer13137 on 2010-04-27
You could check your router configuration and see what the DHCP lease renewal time is.  When I first installed my new linux router, I left it set to 10 minutes because I wanted new computers to get the new "static" IPs I was assigning them in DHCP as quickly as possible.  Then I left it set that way by accident, and I ended up with an issue where sometimes the computer would momentarily lose connectivity every 20s minutes or so, when it 'missed' its renewal for some reason.  (I think the system clock on the server was wrong too, which caused this to happen).

My situation was probably unusual, but you could still take a look and see if maybe your DHCP lease renewal time is set to 30 minutes.

Cheers
Kirk

---

### Post by austclint on 2010-04-27
I will have a play around with the rougher but the server has been up for 3 weeks until last night, with nothing changed to the rougher

---

### Post by Iowan on 2010-04-27
Does the server get DHCP address? If not, the lease shouldn't come into play - but if the server _ever_ had a DHCP address, you might check/flush */var/lib/dhcp3/dhclient.eth0.leases* and/or */var/lib/dhcp3/dhclient.leases *

---

### Post by austclint on 2010-05-04
How do i go about checking them or flushing?

sorry, fairly new to linux

---

### Post by Iowan on 2010-05-05
```
less /var/lib/dhcp3/dhclient.eth0.leases
```or you could use```
cat /var/lib/dhcp3/dhclient.leases 
``` (either command will work with either file. You could edit the file(s) with either ```
sudo nano /var/lib/dhcp3/dhclient.eth0.leases
``` or if you'd prefer a graphical editor ```
gksudo gedit /var/lib/dhcp3/dhclient.leases 
```I haven't tried editing or removing the files...

---

### Post by austclint on 2010-05-11
This didn't seem to work, still dropping off the wireless network

---

### Post by austclint on 2010-05-14
Should I just do a reload of the system?

I have had this problem before and a reload solved it, but it happened again 5 weeks after... Just would be nice to know how to solve it without doing a reload

---

