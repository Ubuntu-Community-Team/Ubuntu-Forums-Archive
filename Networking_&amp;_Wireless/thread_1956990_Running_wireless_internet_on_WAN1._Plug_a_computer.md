---
title: "Running wireless internet on WAN1. Plug a computer into ETH0, i loose my internet."
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by GoaTzaR on 2012-04-12
Hi everyone. I'm having this really annoying problem with my network connections. The interface i use to connect to the Internet is wireless USB WLAN1 (dynamic, but it's always the same) 192.168.1.100 which is all fine. When i plug another computer (static) 192.168.1.11 into my on-board NIC ETH0 (static) 192.168.1.10 i can no longer access the Internet. I tried pinging my router (static) 192.168.1.1 but it gives a response from ETH0 192.168.1.10 that host is unreachable. That's also wrong, it should be responding from WAN1 192.168.1.100 as far as i know. I'm guessing it's related to that. Anyway as soon as i unplug ETH0 everything is fine. I've set WLAN1 to be the default connection, doesn't fix it. Any ideas? Thanks in advance.

---

### Post by kurt18947 on 2012-04-12
I believe that when there is a wired connection available, the wireless network gets disabled.  If for whatever reason the wired connection is recognized but isn't working,  the wireless is still disabled and you could have no functioning network connection.

---

### Post by GoaTzaR on 2012-04-12
Hmm... Doesn't sound like good news. When ETH0 cable is plugged in i can ping WLAN1 192.168.1.100 and ETH0 192.168.1.10 and the XBOX 192.168.1.11 connected to ETH0. Everything except Router 192.168.1.1 which connects through WLAN1. Unplug ETH0 and Internet is restored.

---

### Post by loolooyyyy on 2012-04-14
> **GoaTzaR said:**
> Hmm... Doesn't sound like good news. When ETH0 cable is plugged in i can ping WLAN1 192.168.1.100 and ETH0 192.168.1.10 and the XBOX 192.168.1.11 connected to ETH0. Everything except Router 192.168.1.1 which connects through WLAN1. Unplug ETH0 and Internet is restored.

i guess you have to tell your OS how to use each interface
means set "iptables", so internet traffic will be routed to wlan1 ,  everything else ( or whatever you want, that's what iptables is about)  through eth0

talking about xbox, maybe you want your xbox access internet through your PC's wireless
well, that needs iptables too, that's what i'm looking for and got here!
it's a bit tricky since all the search result of "share internet from wlan to eth0" or "route wlan to eth" or .... will come up with this: ad-hoc! totally unrelated! so look for iptables, and wish me luck

also have a look at 
user@domain:~$ man iptables
for the first time it's confusing, for later use it's borring extracting what you need from man, so look for it on web!

---

### Post by GoaTzaR on 2012-04-16
Awesome, Thank you very much for your response. That "sounds" like it could be right from my vague memories of doing an IT diploma. I think i might have been drunk during that lesson :) Yeah, I'll look into that and post the results. Thanks again, Cheers.

---

### Post by loolooyyyy on 2012-04-16
> **GoaTzaR said:**
> Awesome, Thank you very much for your response. That "sounds" like it could be right from my vague memories of doing an IT diploma. I think i might have been drunk during that lesson :) Yeah, I'll look into that and post the results. Thanks again, Cheers.

and i should've been pretty much asleep or absent :D
I'd love to see the result, do post it please

---

