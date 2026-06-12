---
title: "eth0 unstable - not to say funky !"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by cerien on 2011-05-13
Hello all
 
This is my first use of Ubuntu, but I have previous decent experience on Centos & Mandriva.
 
I've just installed Natty 11.04 on a box that was running a mandriva 2010 - and the network is acting quite strange.
 
When I define a static IP for eth0 through the gui, along with route & dns, it sort of works: ssh is fine, vnc too. However, I have an asterisk running on the box, and it is wild: some packets get lost in the box.
 
An ngrep shows the packets reaching the interface, but they dont show in asterisk !!! I've done a ufw disable, iptables is empty (why cant I service iptable restart btw ?). ip route list show decent routes (eth0 default);
 
When I switch to DHCP, it is better, but unstable... If i plug a wifi usb stick, it seems to be better... 
 
Is there some known issues that could explain this behaviour ? The nic is a: Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller 
 
Any help will be much appreciated.... and will probably make keep ubuntu on my machine !
 
J.

---

### Post by noah++ on 2011-05-13
You are running Asterisk, as in the PBX application? How are you discerning that the data that's entering your interface is not reaching Asterisk (as opposed to, say, Asterisk ignoring or rejecting it)?

If the packets are really getting dropped or rejected after *ngrep* sees them, it seems unlikely to be a problem with your NIC.

---

### Post by cerien on 2011-05-16
Hi, 

thanks for the reply ! Yes, it is asterisk as the pbx open source software.

The ngrep shows me that the packets reach the interface. 

Asterisk logs dont show the packets... Hence, they get lost somewhere in between... 

Firewall is disabled (iptables empty and ufw disabled - the server is on lan not exposed to internet)

J.

---

### Post by cerien on 2011-05-19
Hi

I think i eventually found the issue (unfortunately i switched to fedora and got the same issue).

the modem-router I am using to connect to the net is a packaged box that also does dns. It appears that it does not support IPV6 correctly, and cause some requests to fail... replacing the default dns by any other public (like google) fixed the issue...

hope this helps someone later !

J.

---

### Post by Youfan on 2011-05-29
I get the same problem here. I use Windows XP and Lucid Lynx on my PC,  and everything's fine. On my notebook I use Windows 7 and Natty Narwhal,  but I get a little problem with the Natty. The network connection  (eth0) is very unstable. When I switch to Windows 7 on the same  notebook, it works fine. Both of my PC and my notebook use the same  network. So, I think it must be the config. I've deleted and removed the  old connection on the Natty and made a new one, but it's still unstable. I've  changed the IP Address config manually, but it didn't work.

So I guess I'll change the DNS now. I hope it'll work. Thanks.

---

### Post by Youfan on 2011-05-29
It works flawlessly... Neat. I use Google Public DNS. Thanks dude.  :popcorn:

---

