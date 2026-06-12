---
title: "2 wireless networks - routing Q"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2010-11-10
Running 9.10

1 PCI wireless card - wlan0
1 USB wireless stick (using ndiswrapper) - wlan1
1 wired interface - eth0

Scenario is when either wireless interface is connected - machine works fine. However when *both* are running, then they both try to connect to the SAME wireless network. When they do, the machine falls off the network. Logging in locally I can see both connections, but the machine can't access anything.

I am guessing I have hit a routing issue here - presumably the machine is confused as to which interface should be the default, as they are both the same[1].

Now in reality, I want all iinternet traffic to go via wlan0. wlan1 and eth0 will be used for internal network traffic.

Can anyone advise me on how to setup this route so all traffic from eth0 and wlan1 go through wlan0 ?

[1] I'd actually like wlan1 to use a different wireless network, but an afternoon of trying has hit the "keeps asking for password and won't connect" issue, so let's not go there ....

---

### Post by ankith13 on 2010-11-10
just try and use the route table. manipulate it using the route command...


$sudo route add default gw <ip address of wlan1> -dev wlan1


this will make sure that the internet traffic goes through wlan1....

Now also make sure that the route to the wireless network through wlan0 is above the entry of that to the wlan1....This can be checked through 

$route -n

Please let me know if there are further problems....

---

