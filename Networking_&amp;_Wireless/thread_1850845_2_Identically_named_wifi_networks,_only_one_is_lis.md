---
title: "2 Identically named wifi networks, only one is listed"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by josvanr on 2011-09-27
here there are 2 wifi networks with the same name, (I can see them on my phone) but only 1 of them shows in the network manager. What can I do about this?

josvanr

---

### Post by kurt18947 on 2011-09-27
I wonder if the same network is showing up twice? It seems unlikely to me that having two networks with identical SSIDs would work. Seems like that would be like two devices having the same I.P. address.

---

### Post by aeiah on 2011-09-27
try scanning via the command line. perhaps ubuntu assumes they are part of the same network and just displays the strongest one (although this isn't very secure)

```

iwlist <interface name> scan
```

---

### Post by josvanr on 2011-10-01
thnx.. 

iwlist wlan0 scan

shows the two with a separate 'Adress'. They are indeed 2 
separate access points (one has encryption, the other doesn't)
Just only 1 appears in the scan of the network manager. Bug...?


josvanr

---

### Post by josvanr on 2011-10-12
I now entered the ip address of the network in the
network manager (manually add) but it doesn't seem to 
want to connect. On my phone I can connect with no trouble.
Definitely some bug. Need to find another way to 
connect from the command line...

---

### Post by matt_symes on 2011-10-12
Hi

Can't you manually create a new connection, and edit it to add the mac address of the router you want to connect to ?

That way you can give them separate names, use the same ssid but have different MAC addresses. 

I'm not sure of that will work but it's worth a try.

Kind regards

---

### Post by josvanr on 2011-10-16
hi, thnx,but that is exactly what I did...

---

