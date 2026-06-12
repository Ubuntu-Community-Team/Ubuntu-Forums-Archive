---
title: "Strange connection issue with server"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by Tiersin on 2009-08-19
Alright, I have an issue thats been stumping me. I have a home server running Ubuntu 9.04. Today I was cleaning my room and had shut it off for a while. When I wen to turn it on, I get local connectivity only. I can access the server from other computers on the network, and I can also access it from the internet, but I cant connect to the internet from the server. I can remotely ssh into it, but I cannot get to the outside world from within the server. This is really confusing to me. Any help would be appreciated. 

Here is my ifconfig results as well as my /etc/networking/interfaces file.  I have my system set for static ip. 

ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:08:54:53:9f:ea  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe53:9fea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360570 (360.5 KB)  TX bytes:2257427 (2.2 MB)
          Interrupt:16 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:725739 (725.7 KB)  TX bytes:725739 (725.7 KB)

/etc/network/interfaces

auto lo
iface lo inet loopback

#primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.1.255
	gateway 192.168.1.1

---

### Post by prshah on 2009-08-19
> **Tiersin said:**
> but I cannot get to the outside world from within the server. 

I think you may have a DNS problem.

Can you check/post the contents of your /etc/resolv.conf file?

Can you ping [www.google.com?](www.google.com?)

66.102.9.103 ?

192.168.1.1 ?

---

### Post by Tiersin on 2009-08-19
I think you are probably right. My resolve.conf file is empty, just a comment #created by Network Manager. I cant ping google.com but it will ping ip addresses. So that begs the question, what goes in resolv.conf?

---

### Post by superprash2003 on 2009-08-24
nameserver 208.67.222.222

---

### Post by Tiersin on 2009-08-24
Thank you. I added open DNS's other name servers as well. I appreciate the help.

---

### Post by prshah on 2009-08-24
> **Tiersin said:**
> I added open DNS's other name servers as 

How did you add the name servers? If you directly edited the resolv.conf file, then it will be regenerated blank the next time you reboot or restart network. 

To prevent this, ie, to make DNS settings "stick" see [Re: My DNS servers are cleared from my network settings / resolv.conf on restart?]("http://ubuntuforums.org/showpost.php?p=6942058&postcount=3")

---

