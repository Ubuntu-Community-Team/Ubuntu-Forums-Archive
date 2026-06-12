---
title: "Can't connect to web server on access point from wifi device"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by kcsc on 2011-08-06
Hi folks
 
I am running Maverick as a home theatre pc with mythtv. This PC sits on a LAN with various other devices.
 
The Ubuntu PC also acts as a wireless access point for laptops, phones, tablets, etc. I had lots of issues getting this to work but eventually firestarter did the trick. 
 
One thing will NOT work: I can't connect to my mythweb web interface from devices connected with wifi.
 
To be clear, I can connect to the mythweb web interface from other device on the wired LAN. Devices connected by wifi through the Ubuntu PC can access the LAN router and internet address beyond.
 
I assume all traffic from the wifi devices is being routed straight out onto the LAN bypassing the ability to make any local connections to the web server on the Ubuntu PC. I've looked at iptables and the routing tables but I'm not confident enough to try making changes. I've found it difficult to formulate a google search describing this issue that shows anything useful....
 
Thanks
 
Steven

---

### Post by gordintoronto on 2011-08-06
If you set up a shared folder on the Ubuntu PC (right-click on a folder and select Sharing Options), then select the network "place" on one of the wireless computer, does it see the Ubuntu PC?

What is the IP address of the Ubuntu PC on the wireless network? What happens when you enter this into the address bar of a browser on a wireless PC?

---

### Post by kcsc on 2011-08-07
> **gordintoronto said:**
> If you set up a shared folder on the Ubuntu PC (right-click on a folder and select Sharing Options), then select the network "place" on one of the wireless computer, does it see the Ubuntu PC?
 
What is the IP address of the Ubuntu PC on the wireless network? What happens when you enter this into the address bar of a browser on a wireless PC?
 
I downloaded an app on to my Android tablet that can detect various services available on a network. With this tablet connected to the Ubuntu PC by wifi I can see the http service on my router's IP address, and the windows shares available on my laptop connected to the wired LAn. Searching for services on either the internal or external IP address of the Ubuntu PC times out. Trying both these IP addresses in the browser also times out.
 
Network setup
 
Router = 192.168.1.1
Laptop = 192.168.1.2
htpc = 192.168.1.3 and it's wifi interface = 192.168.100.1
Tablet = 192.168.100.2
 
The tablet can see services connected to the first two IP addresses but none on either IP address of the Ubuntu htpc.
 
Thanks for your help gordintoronto.
 
kcsc

---

### Post by gordintoronto on 2011-08-07
There is a lot here that I don't know, but I have some prejudices. I would make the laptop 192.168.1.20 and the HTPC 192.168.1.30, and its wi-fi 10.10.1.1, with the tablet getting 10.10.1.something. I don't know if that would make any difference.

I assume the router's http service is the admin console?

---

