---
title: "private browsing"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by topbayder on 2010-12-22
is there a way to prevent a network admin from knowing what sites your viewing? i know there are proxy's to use but they are slow. can a change be made in firefox somehow that doesn't leave traces? or that leaves traces that cant be identified or even that would be hard to or take ages to identify?

---

### Post by spiky001 on 2010-12-22
There is a selection in Firefox tools private browsing is this what you are looking for?

---

### Post by topbayder on 2010-12-22
i dont think so. basically i am using a friends network and i dont want them to know what i have been looking at if they check there logs on their router.

---

### Post by Joe of loath on 2010-12-22
You'll need a way to encrypt your traffic, then. A proxy, a VPN or a tunnelled connection is your best bet.

---

### Post by endotherm on 2010-12-22
if you are worried about your  stream being logged from a device in the middle (router, websense appliance, etc)  then there is nothing you can do on the client to bypass that, except to either route around, or obfuscate. since they only have the one router, and all internet traffic passes through it, there is nothing you can do to route around the surveliance. that leaves obfuscation, by means of proxying, encrypting, or disgusing your datastream. of these, proxies are simplest, and encryption is the most bullet proof (though they may wonder what all this encrypted traffic is carrying).

in the long run, I've never yet seen a free anonymizing system that wasnt slooooooooooow. just the nature of the beast. most commercial services however are pretty quick.

---

### Post by Boondoklife on 2010-12-22
VPN would be the best option as if you just use a proxy, that still leaves the data open for packet sniffing. You could do encryption, but then as [endotherm]("http://ubuntuforums.org/member.php?u=1103144") mentioned it could be a little suspicious.

---

### Post by topbayder on 2010-12-23
how do you do encryption surfing? would it be quicker then proxy?

---

### Post by Boondoklife on 2010-12-23
https, but then the server has to support it and big brother can still see the ip that you are connecting to. As far as speed that would depend on the server and what proxy. If it is a paid proxy then it should be snappy, if it is free then you get what you "don't" pay for.

---

### Post by Joe of loath on 2010-12-23
Either that or use a *nix server and tunnel to that using ssh, that way your browsing is encrypted until it gets to the server.

---

### Post by endotherm on 2010-12-23
> **Joe of loath said:**
> Either that or use a *nix server and tunnel to that using ssh, that way your browsing is encrypted until it gets to the server.

indeed, thought they will wonder what all this ssh traffic is. you can tunnel ssh over port 443 (ssl/https) to tunnel through some equipment, but more advanced routers can tell the difference between an ssh header and an ssl one, if it monitors the ssl handshake, or just applies strict compliance to the ssl specification. depends on the sophistication of router and its admin.

---

### Post by Boondoklife on 2010-12-23
Bottom line is either pay for a good proxy or figure out a way to game a server that you have ssh/proxy access to and never tell anyone. Oh and don't abuse it or go crazy saturating the bandwidth, nothing will get you bounced or caught faster.

---

### Post by ottosykora on 2010-12-24
just for surfing, you can use TOR network, simply install all from repository and start.

You can also grab full budled TOR browser package from [http://www.torproject.org/](http://www.torproject.org/)

and have fun

---

