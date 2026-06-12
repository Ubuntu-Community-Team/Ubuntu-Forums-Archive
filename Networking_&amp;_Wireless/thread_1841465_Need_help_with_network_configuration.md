---
title: "Need help with network configuration"
date: 2011-09-09
forum: Networking &amp; Wireless
---

### Post by n8af on 2011-09-09
Hey all
 
I'm trying to setup my home network using Ubuntu Server has the main thouroughfare for network and internet connection traffic to all computers connected on the network. I have some questions on how to configure the server, and network devices to allow me to accomplish this. So far here is my network setup:
 
Internet -> Cable Modem -> eth0 on Ubuntu Server.
eth1 on Ubuntu Server -> 5port switch
 
5 Port switch has 3 devices connected: PC (Windows 7) (used for TV), Xbox, and WiFi Access Point
 
The WiFi access point connects 2 desktop PCs (Windows 7), 2 laptops (1 Windows 7, 1 Ubuntu Desktop), 2 smartphones(android) and a tablet (android).
 
Now from what I understand so far, i want to configure the Ubuntu Server (eth0) to use a static IP and config DNS to forward to either my ISP or Googles DNS. At this point, the Ubuntu server should be configured for internet.
 
Now here is where I start having questions:
Do I need to configure the eth0 to "share" the internet connection? If so, how can I do that via the terminal?
 
How would I configure eth1 so the PCs on the network can access the server and internet?
 
Would I need to enable DHCP on the WiFi Access Point to automatically assign IP addresses for the wireless devices, or do I need to use static?
 
I'm relatively new to Ubuntu (been tinkering around with if for a few months) and I would love to be able to make this setup work. 
 
Thanks in advance.

---

### Post by Doug S on 2011-09-09
The set up that you want to end up with sounds very similar to mine.
I think you have a lot of studying and reading to do.
I would suggest that you get the 11.04 server guide and read it thoroughly. The pdf: [https://help.ubuntu.com/11.04/serverguide/C/serverguide.pdf](https://help.ubuntu.com/11.04/serverguide/C/serverguide.pdf) or the html: [https://help.ubuntu.com/11.04/serverguide/C/index.html](https://help.ubuntu.com/11.04/serverguide/C/index.html) 
Myself, I prefer the PDF version as it is easier to print pages and add notes about my specific implementation. The guide is also filled with useful references.
> Do I need to configure the eth0 to "share" the internet connection? If so, how can I do that via the terminal?
How would I configure eth1 so the PCs on the network can access the server and internet?
See server guide chapter 4- Networking and Chapter 8 - Security - Sub-chapter 3 Firewall - 3.3 IP Masquerading. Your server will act as router. You will need to design your network details.
> Would I need to enable DHCP on the WiFi Access Point to automatically assign IP addresses for the wireless devices, or do I need to use static?
It depends on what you want. On my network, I have my wireless router configured as a switch because I wanted the wireless devices to be on the same sub-net as the wired devices. My wireless devices get their IP address from my server via DHCP. My wireless router also gets an IP address (even though it is acting as a switch) the same way.

---

### Post by tava0002 on 2011-09-09
wireless - switch - eth1 Ububtu eth0 - modem - Internet

For home use you'll probably configure eth0 as a dhcp client unless you have a static Internet routable address from your ISP. I would configure eth1 as a dhcp server, that would take care of the devices wired to the switch.  

With wireless, it depends on what you want to do and the type of device you have, but I'd create a bridge if possible, with your wireless router and your wireless devices can grab addresses from your dhcp server.

As the previous poster mentioned read about networking and security.  Since Ubuntu is your router you probably don't want to allow all inbound traffic to your devices so you need to find out how to configure that correctly.

---

### Post by n8af on 2011-09-10
So far, I have it setup just like you mentioned:
eht0 DHCP
eth1 Static

I didn't have to do anything with the wifi AP.  Once I configured the NICs on Linux, the other PC detected the gateway instantly.  All computers have access.  However, now that you mentioned the security issue, i'm concerned I have left the door wide open.

I'll be spending the weekend and longer if need be, reading the networking section of the Ubuntu PDF.

Thanks for your advice and comments!

---

### Post by n8af on 2011-09-10
Ah, i feel much better now.  I have enabled Firestarter and checked its stealth mode with ShieldsUP.  Everything looks great!

---

### Post by rodrigr2006 on 2011-09-14
How do you put Firestarter in stealth mode or is that how it works by default?

---

### Post by n8af on 2011-09-15
> **rodrigr2006 said:**
> How do you put Firestarter in stealth mode or is that how it works by default?

stealth mode just means that it doesn't respond to to ip requests, it just drops the connection.  I believe firestarter is launched from the beginning in this configuration.

---

