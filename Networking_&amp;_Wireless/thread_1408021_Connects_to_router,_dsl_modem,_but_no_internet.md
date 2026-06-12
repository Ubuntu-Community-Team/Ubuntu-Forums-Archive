---
title: "Connects to router, dsl modem, but no internet"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by j.biddy on 2010-02-15
I recently installed Ubuntu Netbook Remix 9.10 on a Dell Inspiron Mini. I'm having trouble getting any sort of networking working on the system, however. I can access my router and DSL modem through ethernet, however, when I try to access a website it times out very quickly in Firefox. 

Also, I'm having trouble getting the Wireless to activate as well. It wants me to use the proprietary Broadcom drivers, except when I enter my password and click authenticate it doesn't actually turn them on, it just puts me back at the Hardware Drivers screen, without actually activating the drivers.

---

### Post by Iowan on 2010-02-15
What are results of **route -n** and contents of */etc/resolv.conf*?

---

### Post by j.biddy on 2010-02-15
> **Iowan said:**
> What are results of **route -n** and contents of */etc/resolv.conf*?

route -n:
Kernel IP routing table
Destination  Gateway     Genmask       Flags Metric  Ref  Use Iface
192.168,1.0  0.0.0.0     255.255.255.0 U      1       0    0  eth0
169.254.0.0  0.0.0.0     255.255.0.0   U      1000    0    0  eth0
0.0.0.0      192.168.1.1 0.0.0.0       UG     0       0    0  eth0

/etc/resolv.conf:
namserver  192.168.1.1

---

### Post by j.biddy on 2010-02-16
I'm sorry that I do not know how to make that look better.

---

### Post by Iowan on 2010-02-16
That looks fine...
Can you ping internet by IP address (74.125.95.103)? by name (google.com)?
I presume 192.168.1.1 is the router - You can reach (ping) the modem through the router?

---

### Post by j.biddy on 2010-02-17
> **Iowan said:**
> That looks fine...
Can you ping internet by IP address (74.125.95.103)? by name (google.com)?
I presume 192.168.1.1 is the router - You can reach (ping) the modem through the router?

I can indeed ping the modem, google.com, as well as the IP address.

---

### Post by j.biddy on 2010-02-17
I believe the wireless chip being used is the BCM 4322 (PCI-ID 0x432B) and according to linuxwireless.org is unsupported. Bummer.

As for the wired being able to ping everything but not load any websites through the browser, that is indeed still a mystery.

---

### Post by j.biddy on 2010-02-17
I've managed to get everything limping along. Ethernet is working like a charm, pulling down as fast as the DSL can dish it. The wireless on the other hand is performing sub-par. After removing and reinstalling b43-fwcutter several times through Synaptic, it seems to be working, though downloads are excruciatingly slow, being measured in the thousands of bytes/s.

---

### Post by animelogger on 2011-07-02
I have an ASUS EEE PC 1005. I installed Ubuntu Netbook Remix 10.04 in it(dual boot with windows). I'm not able to connect to the internet even though the I'm using a LAN cable. But it works fine when I boot to Windows. Will anyone please help me? 

[IMG]http://i1094.photobucket.com/albums/i452/animelover0081/Screenshot.png[/IMG]

---

