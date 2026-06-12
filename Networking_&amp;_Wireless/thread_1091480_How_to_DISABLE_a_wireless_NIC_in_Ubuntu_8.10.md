---
title: "How to DISABLE a wireless NIC in Ubuntu 8.10"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by hamster-moon on 2009-03-09
Hello all.

This is my first post in these forums, so please excuse me if I've made a faux-pas. I'm also an Ubuntu newb, so I apologise once again if I come across a little confused.

The problem:

I have two wireless NICs installed on my computer, and Ubuntu appears to be connecting to my network with both of them. However, one wireless NIC is obviously enough, and I would like to know how to disable one of them.

Basically I need to know if Ubuntu IS CONNECTING to the Internet using both of these NICs, and if it is, how do I disable one of them? If it's only connecting with one of them, how do I disable the other one, anyway?

(The screen shot is of my wireless, I've blanked out my SSID because it's my more common online alias)

---

### Post by hamster-moon on 2009-03-10
I presume there is no way of disabling hardware in Ubuntu? Any help at all will be much appreciated. Thank you.

---

### Post by Adina on 2009-03-10
open a terminal and try this: sudo ifconfig wlan0 down 

this assumes your network card is called wlan0, change this to wlan1 or whatever your wireless interface is called.

to check if both nic is connected you could try : ifconfig (this shows all interfaces and if they ave an ip address)

if both nic have ip adress you could try to ping something on the internet from each nic.

try this: ping -I wlan0 [www.google.com](www.google.com)

and then you try the other nic.

to disable one of them try : sudo ifconfig wlan0 down

hope this was any helpful.

---

### Post by hamster-moon on 2009-03-10
Excellent, thank you very much.

Although I'm still having trouble maintaining full radio silence for my wlan1 connection. "sudo ifconfig wlan1 down" isn't disabling it completely, as I would like, but I'm happy with the fact wlan1 isn't connecting to the 'net.

If you know of a way to completely disable it, I would be even more grateful.

---

### Post by eldragon on 2009-03-10
> **hamster-moon said:**
> Excellent, thank you very much.

Although I'm still having trouble maintaining full radio silence for my wlan1 connection. "sudo ifconfig wlan1 down" isn't disabling it completely, as I would like, but I'm happy with the fact wlan1 isn't connecting to the 'net.

If you know of a way to completely disable it, I would be even more grateful.

you need to remove the kernel module concerning your wireless chipset.

```

sudo rmmod <module>

```
where <module> is the name of your card's module.

---

