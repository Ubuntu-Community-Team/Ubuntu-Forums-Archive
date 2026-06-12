---
title: "eth0 network suddenly stopped working in 8.10"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by Gris on 2009-06-02
Hello

My networking on eth0 (only one I use) suddenly stopped working on my 8.10 installation.

The system log shows messages like:

Device 'eth0' DHCP transaction took too long (>45s), stopping it.
...
(eth0): deactivating device (reason 0).

Can anyone help? The system is totally isolated now!

Cheers

Gris

---

### Post by Crafty Kisses on 2009-06-02
What are the results of the following:
```
ifconfig
```

---

### Post by Gris on 2009-06-02
Hello

Output of ifconfig:

[IMG]http://i41.tinypic.com/igd94w.png[/IMG]

Thanks

Gris

---

### Post by Gris on 2009-06-03
Anyone got any thoughts on what I can look at to determine the cause?

---

### Post by superprash2003 on 2009-06-03
post output of** sudo dhclient eth0**  , your eth0 doesnt seem to be getting an ip address

---

### Post by Gris on 2009-06-03
Here is the output of sudo dhclient eth0:

[IMG]http://i39.tinypic.com/cq7wn.png[/IMG]

Thanks

Gris

---

### Post by superprash2003 on 2009-06-04
post contents of /etc/dhcp3/dhclient.conf

---

### Post by Gris on 2009-06-04
Here it is!

[IMG]http://i42.tinypic.com/2mw8679.png[/IMG]

Thanks for the help, hoping that it is something simple...

---

### Post by Gris on 2009-06-04
The DCPDISCOVER requests on 255.255.255.255 look strange to my (admittedly ignorant) eye. Shouldn't they go to my router?

---

### Post by Gris on 2009-06-04
Any suggestions for where I might read up about DHCP on Ubuntu so that I can try and get this system on to the network again? I am starting to tear out what little hair remains :D

---

### Post by jonobr on 2009-06-04
Where are you getting your IP addresses from?

Is it from your own home setup?

Looks like the device that responds to the offer has no leases left?

Are you in a large network where a lot of devices are getting addresses?

---

### Post by Gris on 2009-06-04
Hi jonobr

The system is at home, 3 systems (Mac, Win XP/Ubuntu 8.10, iPhone) that need an IP. The Mac and iPhone work fine. If I start Windows XP, it comes up fine - gets an IP and everything is normal. But if I start Ubuntu 8.10, then no IP is acquired. It used to work fine, but it seemed to stop working around about the last set of updates that were installed.

Thanks for your interest in helping me.

Gris

---

### Post by mackerman on 2009-06-04
Bump.  I applied the latest updates and am experiencing the same issue.  I tried applying a static IP in the subnet of my home router, but I may have done that incorrectly.  

I also recently installed vmware before the reboot (as well as system updates).

---

### Post by Gris on 2009-06-04
I managed to get things working by running a vmware virtual machine, for some reason that allowed the network to connect? Wish I knew why it stopped working in the first place... thanks everyone for trying to help me.

---

### Post by mackerman on 2009-06-04
I also managed to get it to work by following:
[http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

This didn't work at first, but after a couple reboots (while fixing some xorg settings) the networking started working again.

---

