---
title: "SSH Login Help"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by rowbird on 2010-08-30
Hi all, I am trying to connect to my home server from the internet. I don't know the proper syntax. I have a dynamic IP address from my ISP but a static home IP. I was using Places/"Connect to server" menu from the panel. I tried STATIC_HOME_IP@DYNAMIC_IP_FROM_SERVICE_PROVIDER in the server field. Any help would be appreciated. Thanks

---

### Post by rawlins02 on 2010-08-30
Can you ping your home server?  Open a terminal window and enter this command:

> ping XXX.XXX.XX.XX

where XXX.XXX.XX.XX is your home server IP address. If you have secure shell running on the local host machine, try:

> ssh XXX.XXX.XX.XX

---

### Post by pricetech on 2010-08-30
Begin by making sure SSH is set up and working internally.  Once it is, forward the port you want to use (default is 22) through your router to the computer you want to connect to.

Connect using "username@IP_adress_provided_by_ISP" (leave off the quotes of course)

You'll need to be able to keep track of this IP to make this work.  I use Dynamic DNS, but their are other entities that provide the same service.

Have fun.

---

### Post by rowbird on 2010-09-02
I have tried to ping my computer with 192.xxx.xxx.xxx@ISP_address and it says the address cannot be found. I can ping my username using blahblah.local, and I can ping using my ISP address, but I still cannot ping over WAN.

---

### Post by BkkBonanza on 2010-09-02
Trying to ping 192.xxx.xxx.xxx@ISP_address makes no sense anyway. You can ping an address, not "something@something", which is not an address (well, it could be an email address but that's a different animal). If you can **ping ISP_address** then that means you can get to your router. Now you need to make sure your router is set to forward port 22 to your local 192... address. 

You cannot ping to your local address from outside the router unless your router is forwarding ICMP packets somewhere which is not usually setup for home gateways, though a DMZ setting may allow that.

In your case, once you have port 22 forwarded you should then try **ssh user@ISP_address** to get to your home server.

---

### Post by rowbird on 2010-09-02
I Have a Siemans Gigaset modem that I set up port forwarding tcp port 5500,5800, and 5900, now I get a black screen using in VNC using ISP_Address.

---

### Post by pricetech on 2010-09-02
Unless you've set SSH to use one of those ports, it's not going to work.

For security's sake, don't use VNC over the Internet.

---

### Post by rowbird on 2010-09-02
I Quite agree. It seems better to not use VNC over the Internet. Thank you.

---

