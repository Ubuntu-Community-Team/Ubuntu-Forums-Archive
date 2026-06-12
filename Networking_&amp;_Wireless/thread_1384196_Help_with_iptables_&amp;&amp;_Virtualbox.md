---
title: "Help with iptables &amp;&amp; Virtualbox"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by kukat on 2010-01-18
Hello! 
A "iptables master" here? ;)

I am practicing my English. I'm from Valencian Country. 

My problem is this: 

I have an internal network with Virtualbox:
I have a karmic koala "text-only" Server:
eth0 --> 192.168.1.38 (connect with Internet and the REAL host)
eth1 --> 192.168.103.1 --> internal network

and two hots: one with Karmic Koala (with X and Gnome) 
eth2 --> with DHCP fixed-address (192.168.103.4)

and other with Windows 7. 
with DHCP fixed-address(192.168.103.5)

I configured the "interfaces" and "resolv.conf" file,SSH, DHCP and DNS with a good result. 

My problem is with the "iptables" script (at /etc/init.d/) with "DROP" by default. I'm confused...I read a lot of manuals, tutorials...And I don't complet the work!! not works....
Can you help me?? 

The ".sh" script is at the attachments...

I don't do any "ping".....and I probed everything....I'm becoming crazy!

---

