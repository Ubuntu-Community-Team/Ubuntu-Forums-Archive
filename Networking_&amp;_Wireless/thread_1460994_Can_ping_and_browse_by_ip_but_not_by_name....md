---
title: "Can ping and browse by ip but not by name..."
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by vfds34 on 2010-04-23
Okay,

recently I got new wireless card, att usb Quicksilver(based/produce by Option?), for att.  Regular gnome network manager freezes the computer when I am plugging it it therefore I installed the one from wicd.net.

Also, I am using HSOConnect (to connect by to G3 network), and sometimes I connect to regular wireless g connection through router.


Under both cases I can ping the website by IP and can access the website by ip (ex. google) but can not ping or browse by name.

As a side note... I can use and access Skype fine under g3 network and normal wireless.

I tried browsing and finding other solutions in past few days but ended up breaking everything and reinstalling to get back to the point I am at now.

I am working on the road, so not being to broswse is rather crippling to me.... also I can access internet normally only from home from different computer now.


Thanks!

---

### Post by pricetech on 2010-04-23
Short answer; DNS problem.  You probably aren't getting DNS addresses via DHCP for whatever reason.  You'll need to manually set DNS.

208.67.222.222 and 208.67.220.220 are Open DNS servers.  Try that and see if it helps.

---

### Post by Iowan on 2010-04-23
You can see what your machine is currently trying to use for DNS by looking at */etc/resolv.conf*. 8.8.8.8 and 8.8.4.4 are Google's DNS server addresses.

---

### Post by wojox on 2010-04-23
Try disabling IPv6 [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

---

### Post by vfds34 on 2010-04-23
> **pricetech said:**
> Short answer; DNS problem.  You probably aren't getting DNS addresses via DHCP for whatever reason.  You'll need to manually set DNS.

208.67.222.222 and 208.67.220.220 are Open DNS servers.  Try that and see if it helps.

this is from resolv.conf


nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1



it does not help.

---

### Post by vfds34 on 2010-04-23
> **wojox said:**
> Try disabling IPv6 [http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)


did not help either


......
Just short a recap, ping(in terminal) works if you ping IP not name(if by name it gives you "unkown host" msg), Skype works i figure it uses ips for whatever it does... browsing in firefox/opera does not work "Server not found" but I can get to pages if typing in IP of the page. IP for the google.com gives me the website,.. but "google.com" (typed in into address bar) gives me "Server not found"

---

### Post by Iowan on 2010-04-23
[Here]("http://ubuntuforums.org/showthread.php?t=971064") is a thread I bookmarked some time ago. It probably doesn't apply, but can't hurt to check.

---

### Post by vfds34 on 2010-04-23
Still found no solution... another hint might be that switching back to gnome network manager makes it work normally through wireless... except I cannot use 3G card(for whatever reason it freezes the computer, someone mentioned that it is some bug in gnome network manager)...


something happens that upon instalation of wicd that causes ping by ip work but not by name, both in termnial and browsers.

---

### Post by alexfish on 2010-04-23
hi
depending on the option device you are using and the ISP , there can be problems 

HSO connections may require updates in the firmware  , this affects both windows and linux , RE Kernel

it is recommended that any drivers etc  are done through the correct channels. in short for linux look up this site

 [http://www.pharscape.org/](http://www.pharscape.org/)

they also have a forum. you will probably find this site is one of the most knowledgeable and helpful sites I have seen

regards

alexfish

---

### Post by vfds34 on 2010-04-24
> **alexfish said:**
> hi
depending on the option device you are using and the ISP , there can be problems 

HSO connections may require updates in the firmware  , this affects both windows and linux , RE Kernel

it is recommended that any drivers etc  are done through the correct channels. in short for linux look up this site

 [http://www.pharscape.org/](http://www.pharscape.org/)

they also have a forum. you will probably find this site is one of the most knowledgeable and helpful sites I have seen

regards

alexfish


Thanks alexfish, I went through all of the instructions on the pharscape.org, that is how I solved most of the problems with the device. Thanks to that site I can connect now and at least use Skype. I do not understand, the device seems to be working for other people, I guess, normally. 

I tryied removing the gnomenetworking, wicd, and what have you and installing them from scratch in various ways and it did not help either. Probably I am missing something small....

Other thing, I tried registering on pharscape to ask questions but registration are not open.


As someone said above, it is probably do to some DNS problem or other setting in the Ubuntu I just cannot seem to figureout what it might be. I know that the device is okay, because it works in windows just fine. Tried following troubleshooting guide too... . Anyways, if I will not figure it out with in next couple days I will be forced to swich back to windows at least for next couple weeks. I will still try wiping all and reinstalling Ubuntu and see if that will help... if anything, it will give me excuse to update my backups.

---

### Post by alexfish on 2010-04-24
Hi
 

 I know a range of icon as sold by orange (also using hso connect )does have a problem similar to yours and have installed resolvconf { from the repo's } although this will want to remove wvdial or gnomeppp , but has cured the problem  
 

 before attempting this can you provide some info , can you post the results of the below
 

 make the connection using your default settings , IE set the Ipv4 settings to Automatic (ppp)
 

 then have a look to see if any address are in the etc/resolv.conf (as returned by the network manager)and also the etc/ppp/resolv.conf  
 

 also have a look in the log file messages to see if what is been returned there
 

 I would expect to see something like the below
 

 local  IP address 10.158.254.63 
 remote IP address 10.64.64.64 
 local  IP address 10.158.136.207 
 primary   DNS address 149.254.201.126 
 secondary DNS address 149.254.192.126
 

 also from the terminal  
 

 Code
 

 ifconfig

  	 	 	 	 	 	  hopefully this may shed some light on the problem
 

 regards
 

 alexfish

---

### Post by ipyrro on 2010-11-28
Hello,

Can anyone explain me why I also can not ping with name, but can with IP-address. 


xxxxx@yyyy:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.30.1
xxxxx@yyyy:~$ ping 192.168.30.244
PING 192.168.30.244 (192.168.30.244) 56(84) bytes of data.
64 bytes from 192.168.30.244: icmp_seq=1 ttl=64 time=13.3 ms
64 bytes from 192.168.30.244: icmp_seq=2 ttl=64 time=5.14 ms
64 bytes from 192.168.30.244: icmp_seq=3 ttl=64 time=5.34 ms
64 bytes from 192.168.30.244: icmp_seq=4 ttl=64 time=4.92 ms
^C
--- 192.168.30.244 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 4.926/7.181/13.317/3.546 ms
xxxxx@yyyy:~$ nslookup 192.168.30.244
Server:		192.168.30.1
Address:	192.168.30.1#53

244.30.168.192.in-addr.arpa	name = site.name.local.

xxxxxx@yyyy:~$ ping site.name.local
ping: unknown host site.name.local

I do have my own nameserver for my own intranet addresses. This works OK with windows machines but not with Ubuntu Linux machines. What might be the problem?

---

