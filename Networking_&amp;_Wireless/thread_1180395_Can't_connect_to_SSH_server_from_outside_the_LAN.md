---
title: "Can't connect to SSH server from outside the LAN"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by sean_whx on 2009-06-06
Hey All,

I am wondering if anyone could help me with the following issue. I googled it left and right but could resolve it. 

I have two computers running Ubuntu 9.04, using static IP, connected via a switch. They can SSH to each other perfectly. And I can ping any websites from these two PCs. But I cannot connect to either of these two PCs from outside the LAN, and cannot even ping them from outside.

It seems that any PCs outside the LAN cannot find these two computers, but these two PCs do have connection to the outside world. How can I solve this problem? 

Another problem is that I cannot visit any website through Firefox. The network is disconnected according to the icon on the upper left side of the desktop, although I have no problem in using ping. This is really weird to me. Could this be the problem of network setting? An example of the setting is:
IP: 10.10.4.122
NetMask: 255.255.255.0
Gateway:10.10.4.1
1st DNS: 150.108.2.11

I remember if I use network manager to set up the network, I could visit websites through Firefox. But I can't use ssh. If I set up the network through command line, I can use ssh but can't visit any website. ......so frustrated. 

Any help is highly appreciated!

---

### Post by sean_whx on 2009-06-06
I just noticed that 10.10.4.122 is a private reserved IP address. I guess I can't use 
$ssh username@10.10.4.122 to connect to it.

How can I connect to it then? ........

---

### Post by jmbertolotti on 2009-06-06
Where is the AP? Do you have a router betweeen the switch and the "outside world"? If you do, try to setup a sshd @ your ap an then you are on you private network. Give more details about your network architecture and maybe i can give you a hand :p

---

### Post by sean_whx on 2009-06-06
Hi jmbertolotti,
 
Thank you for your post.
 
Let me simplify the architecture. Forget about the switch thing. I am not worried about the LAN now. Say I have a computer with the following configuration 
IP: 10.10.4.122 (mostly likely a LAN address. This ip is assigned to me)
Netmask: 255.255.255.0
Gateway: 10.10.4.1
DNS: 150.108.4.11
 
I can ping yahoo.com
$ping yahoo.com
> 
PING www-real.wa1.b.yahoo.com (69.147.76.15) 56(84) bytes of data.
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=1 ttl=53 time=26.2 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=2 ttl=53 time=26.6 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=3 ttl=53 time=26.9 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=4 ttl=53 time=22.5 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=5 ttl=53 time=24.1 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=6 ttl=53 time=23.3 ms
64 bytes from f1.[www.vip.re1.yahoo.com]("http://www.vip.re1.yahoo.com") (69.147.76.15): icmp_seq=7 ttl=53 time=23.9 ms
 
--- www-real.wa1.b.yahoo.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6007ms
rtt min/avg/max/mdev = 22.577/24.848/26.956/1.606 ms
I can also ssh to a server at 150.108.68.199 perfectly. 
But how can I connect to this computer from WAN? I think I need somehow get an external IP. 10.10.4.125 is a reserved private address. I don't think it works over WAN. 
 
I don't know much about networking. Is the gateway 10.10.4.1 the router I am using? I guess something needs to be done with the router. 
 
Lastly, I have to ask u a silly question. what is AP? I am using wired connection here.
 
many thanks! 
 
 
> **jmbertolotti said:**
> Where is the AP? Do you have a router betweeen the switch and the "outside world"? If you do, try to setup a sshd @ your ap an then you are on you private network. Give more details about your network architecture and maybe i can give you a hand :p

---

### Post by uberlube on 2009-06-06
You should set up DynamicDNS and use that to connect from outside your network.

---

### Post by taladan on 2009-06-06
Something that you /have/ to do to get from the outside to the inside is port forwarding.

If you want to be able to access your machines via SSH from the outside world, you need to forward the port(s) from the modem to the router and then from the router to the individual computers.  SSH (normally) operates on port 22.  If you want to open up both machines to the outside world, then you need to set a different port at the modem & the router for one of the computers.  Say port 2222 at the modem to the router.  Then from 2222 from the router to port 22 on the alternate computer.  

This will allow you to shell in via your _external_ address.  

If you have a dynamic IP address, then set up a hostname for yourself at one of the free sites like dyndns.org - you'll also want to enable the keepalive on your modem to dyndns with your username/password if the modem supports it.  If it doesn't, then you'll likely want to look at ddclient for one of your machines - it simply goes out and sends a 'I'm still here and this is my address' signal to dyndns to keep you up to date.

Make sure that you disable root login for your sshd on both machines - don't want to leave that security issue lying about.  

- Note - all of this is simply if you want to be able to access your machine from any other machine anywhere in the world.  If you have something like a laptop that you're wanting to carry around with you to connect from, and won't ever be using someone else's machine(s) or a machine from work, then you can do this all more securely by setting up something like Hamachi (google for Hamachi, it's made by the folks who do logmein) which sets up a personal VPN for your machines only - punches all the right holes and sees all the right ip addresses all the time.

Hope this helps,

Tal

*ETA:* If you're going to do the multiple machines forwarded to the outside world, you'll have to ssh to 2222 to get to the 'other' machine.  While this is self-explanatory to me, it may not be so to some readers.

---

### Post by sean_whx on 2009-06-07
Thanks Tal.
 
That sound complicated, but I will give it a try.  Thanks again. 
 
> **taladan said:**
> Something that you /have/ to do to get from the outside to the inside is port forwarding.
 
If you want to be able to access your machines via SSH from the outside world, you need to forward the port(s) from the modem to the router and then from the router to the individual computers. SSH (normally) operates on port 22. If you want to open up both machines to the outside world, then you need to set a different port at the modem & the router for one of the computers. Say port 2222 at the modem to the router. Then from 2222 from the router to port 22 on the alternate computer. 
 
This will allow you to shell in via your _external_ address. 
 
If you have a dynamic IP address, then set up a hostname for yourself at one of the free sites like dyndns.org - you'll also want to enable the keepalive on your modem to dyndns with your username/password if the modem supports it. If it doesn't, then you'll likely want to look at ddclient for one of your machines - it simply goes out and sends a 'I'm still here and this is my address' signal to dyndns to keep you up to date.
 
Make sure that you disable root login for your sshd on both machines - don't want to leave that security issue lying about. 
 
- Note - all of this is simply if you want to be able to access your machine from any other machine anywhere in the world. If you have something like a laptop that you're wanting to carry around with you to connect from, and won't ever be using someone else's machine(s) or a machine from work, then you can do this all more securely by setting up something like Hamachi (google for Hamachi, it's made by the folks who do logmein) which sets up a personal VPN for your machines only - punches all the right holes and sees all the right ip addresses all the time.
 
Hope this helps,
 
Tal
 
*ETA:* If you're going to do the multiple machines forwarded to the outside world, you'll have to ssh to 2222 to get to the 'other' machine. While this is self-explanatory to me, it may not be so to some readers.

---

### Post by fokmar on 2009-07-03
Can you create a connection when you use a webbased ssh client ? (you can find one at [http://webssh.strangled.net]("http://webssh.strangled.net/") )

---

