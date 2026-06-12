---
title: "Cannot set up Dynamic DNS"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by sumanatphp@gmail.com on 2011-02-19
Hi Folks,

I was trying to make my Desktop accessible from  anywhere with DynDns. I have AT&T 2wire router 2701-hg b router.  which doesnot have dyndns settings. So installed ddclient. its running  fine.. 

suman@suman-ThinkCentre-A50:/etc/ssh$ sudo /etc/init.d/ddclient status
Status of Dynamic DNS service update utility: ddclient is running.


i did tracepath 

suman@suman-ThinkCentre-A50:/etc/ssh$ tracepath sumanalapati.dyndns-home.com
 1:  suman-ThinkCentre-A50                                 0.190ms pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply


i did nslookup

suman@suman-ThinkCentre-A50:/etc/ssh$ nslookup sumanalapati.dyndns-home.com
Server:        192.168.1.254
Address:    192.168.1.254#53

Non-authoritative answer:
Name:    sumanalapati.dyndns-home.com
Address: 99.61.38.143


I dont know what will solve my problem. Can anyone help me out please.

---

