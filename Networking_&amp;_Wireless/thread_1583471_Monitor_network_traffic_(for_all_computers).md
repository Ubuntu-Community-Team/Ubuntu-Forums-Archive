---
title: "Monitor network traffic (for all computers)"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by drewsus on 2010-09-27
Hello all,

I am a student, living with other students, and was wondering how I might go about monitoring network usage. I am not interested in WHAT people are looking at, just how much of our shared bandwidth people are using. And what I want to achieve is just to be able to say to who ever is killing our relatively fast connect that they aren't the only person using the network. Everyone just says "I hardly download anything." which is obviously untruthful as normally I can download at 1.5 MB/s but now loading even google.com takes way too long (same with pinging and all other sites). 
Once I do this, I can determine whether or not I need to call my ISP and do the long 'on hold' dance and "have you tried rebooting the router" BS. 

So... any help?

Drew

---

### Post by cj.surrusco on 2010-09-27
What are all of the computers that you want to monitor connected to? Is it a router or a server?

---

### Post by drewsus on 2010-09-27
It is a wireless router/modem (2701HG-G Gateway) provided by my ISP (Bell Canada).

---

### Post by drewsus on 2010-09-30
Bump. Please, anyone?

---

### Post by cj.surrusco on 2010-09-30
It's kinda hard to manage the bandwidth of another computer. There are a bunch of tools to monitor bandwith here:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html)

Maybe you can get them to agree to run these programs on their computers, or ssh into their computers and run them.

---

### Post by SeijiSensei on 2010-10-01
[ntop]("http://www.ntop.org/overview.html") is a good option, but I believe it needs to run on a gateway not just any host on the network.  That said, it's a cinch to get up and running, so it might be worth a try.

If this doesn't work for you, you'd need to install a Linux box with routing between the Internet and your local network and run ntop on it.  Unless you're fairly well acquainted with routing and Linux, that may be more effort than it's worth.  I have a Linux router that interconnects my LAN and the Internet and run ntop there.

---

### Post by SlugSlug on 2010-10-01
chances are it's a P2P program running and is zapping your upload -- you could just go round each pc and check the upload setting on the like of torrents,

---

### Post by FatherDale on 2010-10-01
> **drewsus said:**
> Hello all,

I am a student, living with other students, and was wondering how I might go about monitoring network usage. I am not interested in WHAT people are looking at, just how much of our shared bandwidth people are using. And what I want to achieve is just to be able to say to who ever is killing our relatively fast connect that they aren't the only person using the network.  

So... any help?

Drew

sudo apt-get install etherape.  Once you've done that, run EtherApe as root and note which IP/machine names are sucking up the most bandwidth. I fire it up whenever my network slows to a crawl. Usually some jerk watching cartoons or porn. We have a chat or I disconnect him.

---

### Post by dmizer on 2010-10-01
The only way you can reliably monitor network usage is to control the gateway. If you do not have access to the router that everyone connects to, and cannot insert a QOS capable gateway between the router and the internet, then you can only guess.

---

