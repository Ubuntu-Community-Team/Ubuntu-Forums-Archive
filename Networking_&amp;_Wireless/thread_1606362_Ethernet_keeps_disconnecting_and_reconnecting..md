---
title: "Ethernet keeps disconnecting and reconnecting."
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by kjekse on 2010-10-26
Hey, there. 
I installed 10.10 for some days ago, networking was working smooth back then. I use a ethernet cable to connect to the internet.
But yesterday when I installed 10.10 on my brothers laptop(he connects through wireless), I began to get these disconnects and reconnects. 
They just seem to happen random. 

I don't know if it's his computer that does it, just the first thing that comes to mind. :)

---

### Post by grahammechanical on 2010-10-26
If I understand you correctly, it is your brother's laptop that connects and disconnects. It is using wireless to connect and not ethernet as you state in your heading? If I am correct, then please enter this code in a terminal:

```
ifconfig
```

Look for wlan0 and RX packets and TX packets. That information should tell you if there are any errors in the transmission and receiving of data. How strong is the wireless signal?

Regards

---

### Post by kjekse on 2010-10-26
No, it's mine. That's connected to the ethernet that is having troubles.
I think I should reset the router it's connected to. Just to check if that's the problem.

---

