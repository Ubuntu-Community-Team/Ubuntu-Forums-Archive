---
title: "Internet  access via Ubuntu 9.04"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Zodiac69 on 2009-07-13
I am completely new to Ubuntu and I have tried many setups the past 4 weeks and was not able to get this working
  I have the following setup – see attached pdf. The IP’s is what want to happen, not what is there now.
  1st let me say what I was able to do.
  All home PC’s were assigned IP’s from Ubuntu – via eth0, 10.42.43.10 and upwards - when I set eth0 to “Share with other PC’s”, they are able to browse the internet.
  Eth1 set as 192.168.1.100 fixed IP, ADSL modem setup as static IP and will assign IP’s based on the MAC address.
   
  I want the ADSL to assign IP’s to the desktops via Ubuntu. The ADSL must see the remote desktops and auto assign the IP as per the “Static” table.
   The next step is to implement bandwidth limiting to the internet, some grab the whole cap and then the rest have problems with timeouts.
   
  Can someone please assist me?

---

### Post by nhanquy on 2009-07-13
I think that configuration is wrong.
You have to have the ubuntu box 2nd interface with **a different segment**, i.e. instead of 192.168.**1**.101 it should be something like 192.168.**2**.100.
Good luck!

---

### Post by Zodiac69 on 2009-07-13
If i do this, how will the Router be able to assign the remote IP's on a diff. sub?

---

### Post by nhanquy on 2009-07-13
> **Zodiac69 said:**
> If i do this, how will the Router be able to assign the remote IP's on a diff. sub?

No. You just go in and configure the computers behind the switch with fixed IP: 192.1.2.102, 103,.....

---

### Post by Zodiac69 on 2009-07-13
Is there any way that i can get this to work and leave the IP's to Auto assign from the router. That is the whole idea.
Or do i need to get Ubuntu to start assigning IP's as i need this to be non static on the remote PC's? We have laptops that move between networks and i dont want to set the IP's the whole time.

Thanks

---

### Post by cariboo on 2009-07-13
I would set the connection betwwent the modem and the Ubuntu desktop computer to dhcp and then set a static ip addresses for the other computers on the network. You will have to set the static ip address on each computer manually.

Have a look at the Ubuntu [Connection Sharing]("http://https://help.ubuntu.com/community/Internet/ConnectionSharing") howto.

---

