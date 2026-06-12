---
title: "slow network speed - high packet loss"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by bulls_eye on 2010-04-22
hi,

I have problems with my network speed... when i ping my proxy server I end up getting a high packet loss .. generally more than 30%...

I have tried to use various network monitoring softwares like etherape, wireshark, tcpdump ... but I am not able to get to the bottom of the problem...

basically I am trying to find out where  the lost packets are going...

can someone help me???

---

### Post by dineshs on 2010-04-22
Checking MTU may help.
```
ifconfig -a
```

---

### Post by bulls_eye on 2010-04-22
well, i tried this code...

but in the output it shows 0 errors for all 3 interfaces !!!

---

### Post by bobyy on 2010-04-23
Hy
where is located the proxy .. LAN ? on internet ? on your machine?
If it`s on wan .. how many hop`s away?
if it`s on LAN(and they are direct connected) be sure the netw setings on netw card`s are the same .. i mean the speed and duplex
also check the cable

---

### Post by bulls_eye on 2010-04-23
I am using a LAN connection in hostels... large number of users are connected by passing on the connection from one hub to another...

and I guess that there is no problem with the network card settings because the network is never disconnected but its rather slow...

and the same goes for the cable...

---

### Post by bulls_eye on 2010-04-23
I think the problem doesn't lie in the hardware but the sofwares ...

some of the people might be using some softwares to extract maximum bandwidth for themselves leaving out little for others...

I just need a way to find these miscreants...

---

### Post by bobyy on 2010-04-23
If you areusing hub`s ..is clear why you have a slow network.

[HTML]I am using a LAN connection in hostels... large number of users are connected by passing on the connection from one hub to another..[/HTML]

That`s mean lot of  colision on lan ..to stop that you must use switches instead of hub`s 
.

---

### Post by bulls_eye on 2010-04-24
ohhh

i am sorry for using the term "hub" in a generalised manner...

in fact I am using a netgear fast ethernet switch...

---

