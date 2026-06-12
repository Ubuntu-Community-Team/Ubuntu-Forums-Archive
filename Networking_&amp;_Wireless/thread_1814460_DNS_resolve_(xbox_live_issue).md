---
title: "DNS resolve (xbox live issue)"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by jmg158 on 2011-07-29
Hi all,

I know there have been posts about this in the past, but I haven't  generally been able to get anything working, so I figured I'd detail my  process and hopefully the whole story will be there to help someone else  as well (such as the other gentleman posting about bridging). 

So my set up is pretty typical. I've got a wireless router and a  wireless card in my desktop. (wlan0). I'm running a crossover cable  (eth0) from my desktop to my xbox and trying to configure it properly to  play xbox live. I haven't had any real luck with firestarter so unless  anyone knows how to work it well I was planning on using iptables. 

router address --> 192.168.1.1

Here have been my actions in the command prompt.
> 
root@john-RC684AA-ABA-SR2002X-NA640:~# ifconfig eth0 up
root@john-RC684AA-ABA-SR2002X-NA640:~# ifconfig eth0 192.168.1.2
root@john-RC684AA-ABA-SR2002X-NA640:~# cat /proc/sys/net/ipv4/ip_forward
1
root@john-RC684AA-ABA-SR2002X-NA640:~# iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.1.0/24 -j MASQUERADE
I have configured my xbox network settings such that ...
IP address => 192.168.1.3
subnet mask => 255.255.255.0
gateway=> 192.168.1.2

These seem to be the correct setting because on the test the xbox  connects to the network, however, it does not connect to the internet.  The reason it gives for this is because it cannot resolve the DNS.  Clearly I don't know an extensive amount regarding networking, and I  don't really know what this error expresses. 

Can someone please point me in the right direction?

---

