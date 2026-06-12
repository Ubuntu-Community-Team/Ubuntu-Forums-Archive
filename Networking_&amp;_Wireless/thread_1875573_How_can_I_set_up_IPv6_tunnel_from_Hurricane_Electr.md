---
title: "How can I set up IPv6 tunnel from Hurricane Electric ?"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by yangjiangnan on 2011-11-05
I access Internet by a Netgear Router through Timewarner Cable. I have set my router to forward port 41 to the internal IP address of my PC with Ubuntu 10.10 installed. I have registered an account on Hurricane Electric (HE). I set up a tunnel a long time ago but it wasn't working. My router only gets a dynamic IP address. So, my IP has changed since I registered on HE. Now, when I try to change my "Client IPv4 Address" on the website to my current Internet IPv4 address, they show me an error message: 

"IP is not ICMP pingable.  Please make sure ICMP is not blocked.  If you  are blocking ICMP, please allow 66.220.2.74 through your firewall."

So, what can I do now? I definitely want to have IPv6 access. Any help would be greatly appreciated. I am not very good at network, so please tell me the detailed steps as well[.]("http://www.sitance.com/")
Thanks a lot.

---

### Post by tomski on 2011-11-05
looks like HE are trying to ping you so
login to router change rules to allow ICMP ping
go back to HE & re-check

also consider getting a static IP for your connection otherwise ipv6 will drop off when your ip changes therefore you will have to keep changing your settings for the tunnel 

fyi /sugestion:
once you have the tunnel all good to go on HE use the lil drop down box which will give you all the commands you need to setup your tunnel on many popular OS's

consider using m0n0wall as this integrates with he ipv6 tunnels nicly & will also advertise the address range so all devices will pick up a working address

gluck

---

### Post by yangjiangnan on 2011-11-05
> **tomski said:**
> looks like HE are trying to ping you so
login to router change rules to allow ICMP ping
go back to HE & re-check

also consider getting a static IP for your connection otherwise ipv6 will drop off when your ip changes therefore you will have to keep changing your settings for the tunnel 

fyi /sugestion:
once you have the tunnel all good to go on HE use the lil drop down box which will give you all the commands you need to setup your tunnel on many popular OS's

consider using m0n0wall as this integrates with he ipv6 tunnels nicly & will also advertise the address range so all devices will pick up a working address

gluck

Thanks a lot for your reply. I have set up my router to enable Internet ping, and the tunnel has been set up. However, I still cannot get the ipv6 working.

Under "Example Configuration", I first chose Linux-net-tools. I typed "sudo bash" in a terminal and get the root privilege, and then copy and paste the commands to the terminal. However, this does not seem to be working. I cannot connect to ipv6.google.com. Then I chose Linux-route2,  replaced my Internet address with my LAN address in their web box,and then copy and paste to terminal. But this does not work either. So, I don't know what else to do. I cannot find m0n0wall on their web either. So I don't know what it means.

---

### Post by tomski on 2011-11-06
check out the following links for references on setting up a HE tunnel in linux:

[https://wiki.ubuntu.com/IPv6](https://wiki.ubuntu.com/IPv6)

[http://duxklr.blogspot.com/2011/01/setup-he-ipv6-tunnel-in-ubuntu-linux.html](http://duxklr.blogspot.com/2011/01/setup-he-ipv6-tunnel-in-ubuntu-linux.html)

[http://blog.geekgonecrazy.com/2011/03/ipv6-connectivity-in-ubuntu-setting-up.html](http://blog.geekgonecrazy.com/2011/03/ipv6-connectivity-in-ubuntu-setting-up.html)

the following uses a free6 tunnel but may yield some good points to try:
[http://www.cyberciti.biz/faq/tspc-debian-ubuntu-linux-configure-ipv6-tunnel/](http://www.cyberciti.biz/faq/tspc-debian-ubuntu-linux-configure-ipv6-tunnel/)

m0n0wall is nothing to do with HE at all BUT it is a bsd based firewall which i use & find works very well for many many situations all you need is a old pc or mini pc to install it on & it will work right out the box with ipv6 HE tunnels too
[http://m0n0wall.ch](http://m0n0wall.ch)

---

### Post by lemming465 on 2011-11-07
First, congratulations on experimenting with IPv6 and choosing a point-to-point tunnel with a tunnel broker while waiting for your ISP to get around to offering you native IPv6.  These are good decisions.

Could we please see the output *with the tunnel up* from```

ip address show
ip -4 route show
ip -6 route show
```
Note that 6in4 v6 encapsulation depends on passing IP protocol 41 (IP in IP; see /etc/protocols, not port 41 (see /etc/services).  That is, the tunneled traffic is the native IPv6 packet with an IPv4 header addressed to the tunnel relay tacked in  front.  Not all wifi routers and cable modems will pass protocol 41 traffic, though sometime using a "gaming" mode which passes all unspecified traffic to a specific IP can help.  Firmware upgrades on the wifi/broadband gear can sometimes help.

---

