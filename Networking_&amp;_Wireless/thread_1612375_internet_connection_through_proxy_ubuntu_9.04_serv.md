---
title: "internet connection through proxy ubuntu 9.04 server"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by abhijeetdesai on 2010-11-03
hi 

i am working from a network behind a proxy 

the settings given to me by my system admin are : 
 
ip       172.16.90.127
subnet   255.255.0.0
gateway  172.16.16.1

dns 121.242.190.180 / 211

proxy 172.16.16.1 port 3128

ping & trace route commands are block @ my gateway 

i am using $sudo apt-get update command to test my connection
& $sudo ntpdate npt.server.name  both  commands don't work 

in need of urgent help

thanking you in anticipation

---

### Post by P4man on 2010-11-03
[http://www.techmetica.com/howto/setup-a-proxy-in-ubuntu/](http://www.techmetica.com/howto/setup-a-proxy-in-ubuntu/)

Im not entirely sure if apt uses that now, if it doesnt, you can configure the proxy for apt using the instructions here:
[https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting%20up%20apt-get%20to%20use%20a%20http-proxy)

---

