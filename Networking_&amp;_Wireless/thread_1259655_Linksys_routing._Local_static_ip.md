---
title: "Linksys routing. Local static ip?"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by dragos240 on 2009-09-06
Hi,

Some of you here may know about my server, it has a static IP on the outside, but not the inside. Most of the time dhcpcd will assign 192.168.1.104, but it will change from time to time, meaning I have to change the port forwarding each time. How can I fix this?

---

### Post by falconindy on 2009-09-06
Unless I'm mistaken, dhcpcd is a dhcp client, not a server. It's the server (presumably the Linksys router you reference?) that assigns and maintains the table of local IP addresses. There exists such a thing as a DHCP reservation. You provide a MAC address to the DHCP server and assign an IP to that MAC address. Every time that MAC address appears on the network and requests an IP from the DHCP server, it will be recognized and assigned that particular IP.

In short, look on your DHCP server. If that's your router, check your router.

---

### Post by puppywhacker on 2009-09-06
you can set the local ip address, dns name server and default gateway in the network manager (little network icon in the right top)

the dhcp server in a linksys is optional, you can assign addresses, preferably with the same prefix, but not in the dhcp-range. 

assuming your linksys uses 192.168.1.1 ... your server can use the static address 192.168.1.2 ... the dhcp server is probably using 192.168.1.100 and higher.

---

### Post by dragos240 on 2009-09-06
> **falconindy said:**
> Unless I'm mistaken, dhcpcd is a dhcp client, not a server. It's the server (presumably the Linksys router you reference?) that assigns and maintains the table of local IP addresses. There exists such a thing as a DHCP reservation. You provide a MAC address to the DHCP server and assign an IP to that MAC address. Every time that MAC address appears on the network and requests an IP from the DHCP server, it will be recognized and assigned that particular IP.

In short, look on your DHCP server. If that's your router, check your router.


I know dhcpcd is a client. I have a webserver. I was saying that I use it to connect to my network.

---

### Post by falconindy on 2009-09-06
> **dragos240 said:**
> I know dhcpcd is a client. I have a webserver. I was saying that I use it to connect to my network.
That doesn't really make any sense. Regardless, if my solution of creating a DHCP reservation or puppywhacker's solution to set a static IP doesn't work, then you need to reword your OP.

---

### Post by dragos240 on 2009-09-06
> **falconindy said:**
> That doesn't really make any sense. Regardless, if my solution of creating a DHCP reservation or puppywhacker's solution to set a static IP doesn't work, then you need to reword your OP.

It doesn't?

I use dhcpcd to connect to my linksys router?

ifconfig up
iwconfig wlan0 essid "linksys"
iwconfig wlan0 mode Managed
dhcpcd wlan0

Okay. That's what I mean.

---

### Post by Whiffle on 2009-09-06
2 ways to do it:  

set a static ip on your comptuer in /etc/networking/interfaces (i think thats it), such as 192.168.1.2 [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

or, if your router supports it, you can tell it to assign the same IP address to your computer: [http://www.dd-wrt.com/wiki/index.php/Static_DHCP](http://www.dd-wrt.com/wiki/index.php/Static_DHCP)

---

