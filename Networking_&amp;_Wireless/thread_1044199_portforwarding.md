---
title: "portforwarding"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by edmwer on 2009-01-19
how do i portforward and set up static ip address for ubuntun 8.1 
thanks

---

### Post by edmwer on 2009-01-19
i want to speed u pthe download for ktorrent how do i portforward and set up a static ip for it

---

### Post by rickyjones on 2009-01-19
We're talking about 2 separate things here. I can help out with one but the other one I can only give a general idea about.

Set Static IP: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

You will basically edit the /etc/network/interfaces file to configure the interface. This will set a static IP on your internal interface.

As for port forwarding this will depend on how you have your internet configured. If it is high speed w/ a standard router then you should be able to do this from the web interface. Consult the manual for your router.

Thanks,
Richard

---

### Post by superprash2003 on 2009-01-19
post your modem/router model no .. you should find port forwarding guides at [www.portforward.com](www.portforward.com)

---

### Post by edmwer on 2009-01-19
but how do i set up static ip, i cant run the cmd menu as in window right?also i cant acess the router admin page why?

---

### Post by rickyjones on 2009-01-20
> **edmwer said:**
> but how do i set up static ip, i cant run the cmd menu as in window right?also i cant acess the router admin page why?

1. Are you using the server or desktop version of Ubuntu? If server then you should already be in the terminal. If desktop then click Application -> Accessories -> Terminal.

2. Are you currently connected to the network properly? Can you access internet web pages? Do you know the IP address of your router? 

Thanks,
Richard

---

### Post by Iowan on 2009-01-20
[Here]("http://codesnippets.joyent.com/posts/show/319") is a How-To on Static address. To address router config page, you'll need to be in the same subnet... which means you'll need to know the address of the router and your machine (server?).

---

