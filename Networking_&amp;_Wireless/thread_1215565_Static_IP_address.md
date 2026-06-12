---
title: "Static IP address"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by vaslat29 on 2009-07-17
I am trying to set up Ekiga and when I open the application I get this message (refer attached). I am using router SpeedStream 6520. The message as you can see in the attachment says that Ekiga could not configure network settings automatically. So I am trying to set it up manually. One of the requirements is to enter a static IP address - now where do I get that from and how do I configure?

---

### Post by mhgsys on 2009-07-17
you can configure your network manually in System>Administration>Network

If it's not there
```

sudo apt-get install gnome-network-admin

```

---

### Post by vaslat29 on 2009-07-17
My question is actually where can I get the static IP address.

---

### Post by mhgsys on 2009-07-17
Well, you don't get a static ip adres, you assign one.


borrowed From wikipedia:
```

 Static IP addresses are manually assigned to a computer by an administrator.
 The exact procedure varies according to platform. 
This contrasts with dynamic IP addresses, which are assigned either by the 
computer interface or host software itself, 
as in Zeroconf, or assigned by a server using Dynamic Host Configuration Protocol (DHCP). 
Even though IP addresses assigned using DHCP may stay the same for long periods of time
, they can generally change.


```
To make it easier;
In the menu we spoke of before; Or right click your connection and edit it;


You assign a ip address ; f.e 192.168.1.10

You assign the primary and secondary DNS.

To find the DNS settings , you could look it up in your router settings .
 
If you are connected to that router now ,its even easier; all you have to then then is to right click the connection> connection information.
Your dns settings will be there, copy them/ write them down, and assign the ip address and dns manually.

---

### Post by Abe T on 2009-09-05
Where can I find my router

---

### Post by Abe T on 2009-09-05
How to find my router settings?

---

### Post by cariboo on 2009-09-05
It depends on what make of router you have, you usually access the router management interface from you web browserm for example if you have a Linksys router you would enter:

```
http://192.168.1.1
```

---

### Post by mhgsys on 2009-09-10
btw, you can open up a terminal and type;
```

route

```

This will show your router address.

---

### Post by Iowan on 2009-09-10
Be forewarned - if you change to a static address, you'll need to pick one that is *outside* your DHCP server's range.  If the router is also the DHCP server, you can *probably* have it issue a static lease based on MAC address... but that adds another layer of complexity to your system (how much experience did you want to gain with this project :) )?

---

