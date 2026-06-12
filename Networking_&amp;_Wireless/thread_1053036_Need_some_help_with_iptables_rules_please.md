---
title: "Need some help with iptables rules please"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by lotharz0r on 2009-01-28
Hi.
Its been 4 years since I've touched iptables, so sadly I have forgotten way to much to be able to fix this :( 
Hope someone can help me out

I've got a linux server on a school with 2 nics.
One NIC is for teachers, and one for students.

ETH0 = teachers
ETH1 = students

ETH0 is connected to the adsl modem, so no internet traffic is blocked

So all students gets Ethernet, WLAN and internet through ETH1 on this server.
What I need is to have everything except port 80 and 443 blocked on ETH1.
The students are only allowed to use those two ports.
Another problem is that soon they will have their exams.
Then I need to block all internet traffic to everything but two internet IPs, because they take their exams online.
How can I do this?

I tried making something myself, but I ended up either no ports blocked or ebverything blocked :(

ETH1 has the IP 192.168.0.254
ETH0 has 10.0.2.2

All help is greatly appretiated

---

### Post by jimv on 2009-02-04
If you've got a gui installed, using a program like Firestarter makes iptables rules a snap.

---

### Post by lotharz0r on 2009-02-10
Ok, thanks.
There is a GUI installed, I'll try that.

---

### Post by fruit003 on 2009-12-23
I have a Virtual Dedicated Server with 6 IP Addresses. 1 for the server and 5 for other websites.
I want to block the access to port 9999(control panel) and 22(SSH) for all IP Addresses except 1.
They are internal IP Addresses not external.
 
So w1.x1.y1.z1:9999 is accessible but
w2.x2.y2.z2:9999
w3.x3.y3.z3:9999
w4.x4.y4.z4:9999
w5.x5.y5.z5:9999
w6.x6.y6.z6:9999
do not work. Please help
 
I plan to use ipTables to do so since I am using it currently to block ports 993 and 995
 
Also, I plan to add more IP Addresses later to the same server.
SO I would prefer a rule which would allow access to w1.x1.y1.z1:9999
instead of writing 5 rules to deny access to other IP Addresses, so that I dont have write new rules when I add another IP Address.
 
Although this is just preference. Any rule works fine for the time being.
========
[gmc envoy wheel bearing](http://www.carpartswarehouse.com/gmc-envoy-wheel-bearing.html)
[importing car to canada](http://www.vehicleexporting.com/)

---

