---
title: "connecting 3g modem disconnects home lan???"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by aircftech on 2010-04-03
Hello all,
 
    running Ubuntu 9.10 x64bit fresh install and updated.
 
 When I connect with my 3g um150 modem it disconnects my home network?? I cannot get them to run both at the same time and of cousre the next thing would be to share the internet connection.
 
Thanks for any help.

---

### Post by 2hot6ft2 on 2010-04-03
> **aircftech said:**
> Hello all,
 
    running Ubuntu 9.10 x64bit fresh install and updated.
 
 When I connect with my 3g um150 modem it disconnects my home network?? I cannot get them to run both at the same time and of cousre the next thing would be to share the internet connection.
 
Thanks for any help.
Network manager will only handle 1 connection at a time. Same with WICD.:-( Unless it's for Internet Connection Sharing that is.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by aircftech on 2010-04-03
really!! :( what if you have 2 nic's? do they plan on fixing this?

---

### Post by 2hot6ft2 on 2010-04-03
> **aircftech said:**
> really!! :( what if you have 2 nic's? do they plan on fixing this?
To configure two nics. you would have to do it in the interfaces file and stop or remove the network manager. Yes , they are planning on making it work with more than one connection and WICD was supposed to do it in version 1.6 but now it looks like maybe in version 2.0. I don't know when NM will have that ability.

There was one post that said it worked in the server version but that was the only time I've heard of it working with 2. I was trying to do it in this thread.
[Ubuntu 2 Ubuntu via Ethernet while still using WiFi?]("http://ubuntuforums.org/showthread.php?t=1391343")
With no luck.

You can bond the 2 adapters but that really doesn't help, unless they are both connected to the same connection. To increase bandwidth.

---

### Post by alexfish on 2010-04-04
Hi

there is a thread here, may be worth reading through

[http://ubuntuforums.org/showthread.php?t=1384085&highlight=Brady](http://ubuntuforums.org/showthread.php?t=1384085&highlight=Brady)

regards

alexfish

---

### Post by aircftech on 2010-04-09
Ok so I got both interfaces working nic and 3g modem and it will work but I have to manually change the ip address for the nic to 192.168.0.?? Why does Ubuntu not pull the same address as the other computer on the network it always pulls a 10.42.43.?? or something?

Oh one quick question how do I set firestarter to startup on boot? maybe that would do it?

---

### Post by alexfish on 2010-04-10
Hi

are you referring to the address for the 3g connection 

for firestart this may help

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

regards

alexfish

---

### Post by aircftech on 2010-04-10
Thanks for the tip I will try that fix for the network manager in your link but it doesnt seem to startup on boot (firestart that is).
 
I was talking about the lan (home network router) getting the wrong address. The 3g pulls its address from verizon.
 
I am talking about my nic card eth0 it never pulls a 192 address even know the other pc and nas box have it.

---

### Post by alexfish on 2010-04-11
hi

are you using NM for both connections, 

you are saying ubuntu is pulling something like 10.42.43.?? or something?

so we need to find out where the address is coming from if you are using NM the details can be found by checking the connection information in NM , the 3G routes  are different to nic

for the 3g connection there will an

IP address

Broadcast addresss

Default route

Primary address  {same as NS1 } Named server 1

Secondary address { same as NS2 } Named server 2


note the IP address and the Broadcast address may vary, but the Default  route should stay static, also the NS1 and NS2 can also vary

or find out from the log file , messages

other info can be found in the resolv.conf , this will show the address returned by NM

also check the route - n command for both interfaces



regards

alexfish

---

### Post by aircftech on 2010-04-11
Thanks again for your help.

It pulling the address from my router. Maybe I need to disable that so firestarter can had dhcp. 

It is all working but no sharing it will only use one connection at a time or default im guessing. when hit connect eth0 (my lan home network) I can see the other pc's just no internet and when I hit my 3g verizon connection I can go online. Just cant get the shareing to work.

Nevermind got it working followed this post if anyone else is having trouble fiil in the dns info.

[http://ubuntuforums.org/showthread.php?t=1384085&highlight=Brady](http://ubuntuforums.org/showthread.php?t=1384085&highlight=Brady)

Thanks Alexfish also for the time.

---

