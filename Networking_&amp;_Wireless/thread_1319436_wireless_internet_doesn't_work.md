---
title: "wireless internet doesn't work"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by chuckberry26 on 2009-11-08
Hi all, i have installed ubuntu 9.10 and i have an Intel Wireless Wifi Link 5100. I think that my Wireless interface works fine because i can connect with my dlink router and i can launch ping to other sites, for ex.: if i launch ping google.it i receive answer from google, i can use wget in fact i have downloaded kernel linux from kernel.org by wget but i can't connect to internet with firefox. If i use a wired connection I can connect to internet with firefox. This is a strange thing. What can i do? 
Thanks

---

### Post by RedSingularity on 2009-11-08
Did you check your proxy settings in firefox and make sure they are all off?

---

### Post by chuckberry26 on 2009-11-08
Yes, I've selected no proxy in firefox:  when i try to connect with firefox i've launched netstat -ant:
 
proto      recv     send  local address                    foreign adrress       State
tcp           0         1       192.168.1.2:47022           1.0.0.0:80             SYN_SENT
.......
 
it can't  do three-way handshake. I don't have any firewall active

---

### Post by chuckberry26 on 2009-11-08
It's always the same thing, i try to connect to google.it:
 
netstat -ant:
 
tcp       0           1        192.168.1.2         1.0.0.0:80                  SYN_SENT
 
It's foreign address 1.0.0.0 that i don't understand
Any idea?
Thanks

---

### Post by RedSingularity on 2009-11-08
Wait.  You said you can ping with the wireless interface?

---

### Post by chuckberry26 on 2009-11-08
Yes, when my wireless connection was established with router i can ping other sites

---

### Post by chuckberry26 on 2009-11-08
i can use ping and i can use  wget therefore TCP and ICMP work. Where is the problem? I don't have any firewall. Maybe network manager have some bug.
How can i setup a wireless connection manually? Where can i find any tutorials?
Thanks

---

### Post by RedSingularity on 2009-11-08
Have you tried WICD?  Look in synaptic for wicd and try it out.  Though i think it may be a config problem in firefox itself.  I would recommend deleting ALL firefox config files and reinstalling.  Maybe with a newer version of Firefox.

---

### Post by puppywhacker on 2009-11-08
I have seen similar behaviour on a UMTS network, where all traffic was directed to 1.1.1.1 which was one of the transparent proxies of the operator, they use it to save bandwidth. I guess they set up the DNS to return that ip-address for some sites, since it isn't truely transparent and it looks like a dirty hack to me.

---

### Post by chuckberry26 on 2009-11-09
Solved!!! I have set DNS address in the network manager to 208.67.222.222. It is an opendns. It's strange, because with wired connection i can use my provider's DNS.
Thanks at all for help

---

