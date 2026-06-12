---
title: "Android discoverable wifi network with proxy support"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by topgun_tapan on 2010-10-26
Curently i see 2 major drawbacks with my android phone .. 1. it can't detect ad hoc wifi networks
2. There is no proxy support for wifi

I use internet on my laptop through the university proxy server. What i would like to do is setup a wifi network which is discoverable by my android phone since it doesn't detect the default network created through the network manager. I use a proxy server on my laptop to connect to the internet. What i want to do is that connection requests by any devices that connect to my network are automatically forwarded through the proxy server(which requires authentication as well) by my laptop. This will get around the 2nd drawback that i mentioned. Any suggestions about how I could go about achieving this ?

I'm using ubuntu 10.10 and my network adapter is Intel Wifi Link 5100 AGN

---

### Post by carl.davis on 2010-10-26
Hello,

You could start here:

[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

I don't think that there is any easy way to do this through nm-applet, hopefully someone will post a correction if I am wrong.

---

### Post by topgun_tapan on 2010-10-26
thanks for the answer. The link certainly helps me get around drawback #1. I would prefer something simpler, but i guess if no other option turns up i would go ahead with this. Drawback #2 is still a pain though.

---

