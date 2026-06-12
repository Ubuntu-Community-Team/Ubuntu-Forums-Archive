---
title: "Setup static IP in Ubuntu 12.04"
date: 2012-05-27
forum: Networking &amp; Wireless
---

### Post by the gene on 2012-05-27
Hi there... well, I am not a complete beginner as far as this subject is concerned, but this time I am stumped...  

I want to set up a static IP for my server ... I have a Billion 400g Router , and the server connected via eth0.
This is the output from "ifconfig" :


root@torserver:/home/thegene# ifconfig
eth0      Link encap:Ethernet  HWaddr 5c:d9:98:be:6b:8b
          inet addr:10.0.0.103  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5ed9:98ff:febe:6b8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21552144 (21.5 MB)  TX bytes:2163682 (2.1 MB)
          Interrupt:5 Base address:0x2c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:252275 (252.2 KB)  TX bytes:252275 (252.2 KB)

What is flabbergasting me atm is the 10.0.0.103 address...   everything works fine but from outside the router e.g. www how do I access the server? If I use the 10.0.0.103 address as a static IP, I still cannot access from outside, only via LAN pc's.    Is this a router hassle or what do I do ? PLEASE can someone assist me?

---

### Post by irv on 2012-05-27
Have you setup your router's port range routing. I have a linksys here is a snap shot of my setting.
[ATTACH]218799[/ATTACH]

---

### Post by the gene on 2012-05-27
Again I say, everything is working 100% except for not being able to access the address 10.0.0.103 from the internet.... all the forwarding etc. is done and set up, all my other pc's have been using this for a long time, its the pits this i do not understand the address should be in a form of 192.168.186.240 etc? thats my hassle...

---

### Post by irv on 2012-05-27
> **the gene said:**
> Again I say, everything is working 100% except for not being able to access the address 10.0.0.103 from the internet.... all the forwarding etc. is done and set up, all my other pc's have been using this for a long time, its the pits this i do not understand the address should be in a form of 192.168.186.240 etc? thats my hassle...

Did you assign the 10.0.0.103 to your computer?
[ATTACH]218801[/ATTACH]
If not why don't you assign the one you want.
My router is 192.168.1.1 so my server is 192.168.1.105. and I can see it from a web browser by just typing in the ip address.

---

### Post by the gene on 2012-05-29
okay m8, so far so good... problem was in the settings on the router, with(out) help from the techies at the support center i finally managed to blunder thru the manual well enough to get the virual host settings and stuff set.

Thanks for trying to help, you did point me in the right direction, cos the routerwasnt forwarding the external ip to the internal one, the mapping wasnt there....


Now I can at least talk to the server, but am still having problems in that when I connect via "example.com/wp-admin"

it tells me "the requested resource (wp-admin) is not available. Apache Tomcat/6.0.35"

sigh... anyone maybe tell me where to start lookin please?

---

### Post by irv on 2012-05-29
> **the gene said:**
> okay m8, so far so good... problem was in the settings on the router, with(out) help from the techies at the support center i finally managed to blunder thru the manual well enough to get the virual host settings and stuff set.

Thanks for trying to help, you did point me in the right direction, cos the routerwasnt forwarding the external ip to the internal one, the mapping wasnt there....


Now I can at least talk to the server, but am still having problems in that when I connect via "example.com/wp-admin"

it tells me "the requested resource (wp-admin) is not available. Apache Tomcat/6.0.35"

sigh... anyone maybe tell me where to start lookin please?

It's been awhile, but as I remember I believe there was a setting in the apache config file somewhere, where I set an ip address.

---

### Post by spynappels on 2012-05-29
Are you running a WordPress site?

what happens if you just go to the root page? example.com/index.htm

It looks to me like the server is accessible, but the content delivery is messed up. If it is WordPress, it could be a permissions issue.

---

### Post by the gene on 2012-05-29
yes m8, running wordpress, I am gonna try a fresh install and see maybe there is a hassle i just dunno any other that can cause it although I also cant access /phpmyadmin like that so it doesnt seem to just be wordpress, seems to me its a permissions or summat setting, thats wrong, i just have no idea where to do what haha sorry we cant all be fundi's hey???

I can get in on prt : 10000 for webmin, full access no problem, so if that helps at all, then it MUSt be permissions  or something that has to be set somewhere?

---

### Post by spynappels on 2012-05-29
Yep, then it definitely sounds like a permissions issue to me. You could try setting permissions on the directories where WP is installed so the www-data user can access them, making sure this is done recursively.

Other than that, I'm not sure as I've never used WP.

Have fun!

---

### Post by the gene on 2012-05-30
righto... some positive feedback, as in :

1. it WAS a router issue, NAT was acting up, got it solved with help from Billion Head Office.
2. WWW-data permissions wer not set either, haha fool me...
3. WP was stuffed up install, deleted all and re-installed, now just 1 problem, doesnt display correctly but that I will get sorted, at least the access from www has been sorted and is now working ok.


Thanks very much everyone for your input, this is what makes aforum a great Forum... kudo's to UBUNTU Forum's memebers...

Oh and server running on dhcp, NOT static, 100%.

---

### Post by irv on 2012-05-30
The gene why don't you mark this one solved? Glad to see all is working.

---

### Post by spynappels on 2012-05-31
> **the gene said:**
> Oh and server running on dhcp, NOT static, 100%.

You might consider running the server either on a static local IP or at the very least with a reserved DHCP address, so the DHCP server will always give it the same IP, makes everything much easier ;-)

Glad you got it sorted anyway.

---

