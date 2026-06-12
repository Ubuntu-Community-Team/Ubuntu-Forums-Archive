---
title: "An easy way to change from DHCP to static IP address?"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by Emporata on 2010-11-14
Does anyone know an easy way to do this?  I can't seem to figure it out.  Thanks.  :confused:

---

### Post by puppywhacker on 2010-11-14
right click the network icon on the right top (arrow up+down) "edit connections" "IPv4 Settings" "Method" "Manual"

---

### Post by lisati on 2010-11-14
My preference is, where possible and in the interests of not causing problems if I need to hook up my machine(s) to another network, to let my router hand out IP addresses on my local network. Both my routers have options to set static IP addresses. The method varies according to make and model, but usually means logging into the router's web based control panel.

---

### Post by Morbius1 on 2010-11-14
The biggest advantage of the method described by lisati above is that once set it's set forever for that machine. Install another OS and it has the same ip address. Have a multiboot with several OS's and they all have the same ip address. 

If you look through your documentation search for something like this: 

"DHCP Address Reservation" 
"Static DHCP"
"Reserved DHCP"
"Reserved leases"
"Pre-assigned DHCP" .

All it's doing is attaching a specific ip address to the specific MAC address of the network adapter.

---

### Post by Iowan on 2010-11-14
I also like the method mentioned... but Network Manager should also let you configure a static address. One trick is to use the [ENTER] key in appropriate places. [Here]("http://www.howtogeek.com/howto/19541/how-to-assign-a-static-ip-to-an-ubuntu-10.04-desktop-computer/") is a guide that might also help...

---

### Post by Emporata on 2010-11-23
Thanks everyone.  

In the end I got the router configured correctly but it just wouldn't play nicely with the modem I got from my ISP.  I purchased a modem-router combo from them (for which they provide support) and, so far, all is going well.

---

### Post by pricetech on 2010-11-23
Glad you got it working.  I've used that method exclusively for some time.  Haven't changed my printers / printservers yet, but that's only because I'm too lazy.

---

