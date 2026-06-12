---
title: "Connecting routers together"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by davidryder on 2009-03-08
I have 2 routers (one a mac airport and the other a linksys with dd-wrt) and they both have external IP addresses but are connected to the same cable modem. The IP address of the linksys is 10.0.4.1 and the airport is 10.0.1.1. 

Is there a way to make these two networks see each other but still maintain different external IP addresses? I would like to be able to locally browse computers connected to the airport through a computer connected though the linksys.

I hope that makes sense :)

---

### Post by Iowan on 2009-03-09
How do the two routers connect to the modem (switch?)

---

### Post by kestrel1 on 2009-03-09
The IP addresses that you are specifying are internal IP addresses.
The best way would probably be to make them both have similar IP addresses. i.e. change IP one from 10.0.4.1 to 10.0.1.2 & leave the other as it is. Make sure that they are both using the same subnet mask.

---

### Post by davidryder on 2009-03-09
I have 2 external IP addresses being assigned to the two routers from one modem. Both routers are connected to the modem via a switch. I have housemates and this configuration allows us to run completely independent servers on the same line. However, I would like to be able to locally share files between one another.

---

### Post by Iowan on 2009-03-10
I can't tell you how, but the routers should be able to route traffic for the companion subnet.

---

### Post by issih on 2009-03-10
Not certain here, but I think the only way is to have one machine with two network interfaces and connect one to each router, and set that machine up as a bridge between the two networks. I'd guess you'd also need to tell each router to forward traffic for the other subnet to the machine that connects to both.

I'm not sure about that, but its the only way I know of doing it.

---

### Post by davidryder on 2009-03-11
> **issih said:**
> Not certain here, but I think the only way is to have one machine with two network interfaces and connect one to each router, and set that machine up as a bridge between the two networks. I'd guess you'd also need to tell each router to forward traffic for the other subnet to the machine that connects to both.

I'm not sure about that, but its the only way I know of doing it.

I didn't think of this until last night! I have two ethernet ports in my room and two interfaces on my PC so that's exactly what I did. 

Thanks :D

---

