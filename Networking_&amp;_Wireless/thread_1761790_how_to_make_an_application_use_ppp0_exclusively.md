---
title: "how to make an application use ppp0 exclusively"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by scopper on 2011-05-18
Hey all, thanks for your time in advance. I'm running 10.10 64 bit.
I have a vpn service and I'd like to configure my bittorrent client to use only the vpn link (and NOT continue through my plain-old ISP service if the vpn drops). 

I imagine there are a few possible approaches to this:

1.have a script that checks if ppp0 is up an terminates the bt client if not

2.configure the bt client to use only ppp0 (though I tried this with qtorrent and it switches over to eth0 if vpn drops...)

3.?

thanks again!

---

### Post by scopper on 2011-05-29
alright, I've found out that the solution is to add an appropriate script in the /etc/Networkmanager/dispatcher.d directory. I in particular am having trouble with that part and am about to post another thread dealing with it....

---

