---
title: "Can anyone help, atleast for this one ? huh"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by baskar007 on 2009-09-16
I am newbie for linux. i have a dual  boot sys (win XP and ubunt 9.04 juanty)
I already posted 2 threads about networking issue but there is no valid response 
threads located at:
[http://ubuntuforums.org/showthread.php?t=1263509](http://ubuntuforums.org/showthread.php?t=1263509)
[http://ubuntuforums.org/showthread.php?t=1260094](http://ubuntuforums.org/showthread.php?t=1260094)

could any one give respponse for this one?????????

"Google sites are not open in ubuntu?"
If this problem causes by IPv6  then how to disable ipv6?
I had tried many way to disaple ipv6 but no effect.!

> baskar@baskar-desktop:~$ ip a | grep inet6
    inet6 ::1/128 scope host 
baskar@baskar-desktop:~$ 


---

### Post by gordintoronto on 2009-09-16
I don't understand what you are asking, so I can't help you.

Generally, you will get better/faster responses if your message subject attracts people who might know the answer, such as "Firefox can't access Google site."

Then describe your environment, the program, the exact error message.

---

### Post by mtb-cliff on 2009-09-16
From your second post, there is a response that may lead to the solution - you need to find out which daemon you uninstalled.

Is the problem wired and wireless or just wireless? 

Try booting from a live-CD and seeing if you have the same issues. 

If wireless issue only, then the Realtek drivers are sometimes problematic. You may have to end up using the ndis wrapper with a Windows XP driver if it is the driver that is at issue. My personal experience with the Realtek driver is that I had to go to the [http://linuxwireless.org/](http://linuxwireless.org/) and install the latest wireless drivers.

I have had no problems with any of the wired drivers.

---

### Post by baskar007 on 2009-09-16
> **gordintoronto said:**
> I don't understand what you are asking, so I can't help you.

Generally, you will get better/faster responses if your message subject attracts people who might know the answer, such as "Firefox can't access Google site."

Then describe your environment, the program, the exact error message.
OK,

My problem is:
I cant access google sites (google.com,blogger,etc..) 
if i type [www.google.com](www.google.com) in address bar it'll take very long time (5min) after displays cannot find the server. 
i had tried opera,mozilla,Epiphany

i have wireless broadband connection. 
same connection with windows xp have no problem.

---

### Post by baskar007 on 2009-09-16
> **mtb-cliff said:**
> From your second post, there is a response that may lead to the solution - you need to find out which daemon you uninstalled.

Is the problem wired and wireless or just wireless? 

Try booting from a live-CD and seeing if you have the same issues. 

If wireless issue only, then the Realtek drivers are sometimes problematic. You may have to end up using the ndis wrapper with a Windows XP driver if it is the driver that is at issue. My personal experience with the Realtek driver is that I had to go to the [http://linuxwireless.org/](http://linuxwireless.org/) and install the latest wireless drivers.

I have had no problems with any of the wired drivers.

i reinstalled ubuntu after that issue.still have a same problem

---

### Post by ahood on 2009-09-16
> **baskar007 said:**
> OK,

My problem is:
I cant access google sites (google.com,blogger,etc..) 
if i type [www.google.com](www.google.com) in address bar it'll take very long time (5min) after displays cannot find the server. 
i had tried opera,mozilla,Epiphany

i have wireless broadband connection. 
same connection with windows xp have no problem.

A. Is only Google inaccessible or other all websites?

B. Have you tried 802.11b/g WiFi (common wireless) connection?

---

### Post by Maheriano on 2009-09-16
The reason nobody is helping you is because your thread topic titles suck. I'm seriously getting tired of these threads that you have to click on to figure out what the issue is.

---

### Post by baskar007 on 2009-09-16
> **ahood said:**
> A. Is only Google inaccessible or other all websites?

B. Have you tried 802.11b/g WiFi (common wireless) connection?

yes only google sites are inaccessible, Other sites are extremly faster than XP !

I have tried with 802.11b/g same issue present

---

### Post by baskar007 on 2009-09-16
> **Maheriano said:**
> The reason nobody is helping you is because your thread topic titles suck. I'm seriously getting tired of these threads that you have to click on to figure out what the issue is.

hoo which title's are sucks this thread or older?

---

### Post by wojox on 2009-09-16
Open a terminal and paste this in and tell me what happens.

```
w3m -v http://www.google.com
```

---

### Post by badger_fruit on 2009-09-16
> **baskar007 said:**
> OK,

My problem is:
I cant access google sites (google.com,blogger,etc..) 
if i type [www.google.com]("http://www.google.com") in address bar it'll take very long time (5min) after displays cannot find the server. 
i had tried opera,mozilla,Epiphany

i have wireless broadband connection. 
same connection with windows xp have no problem.

"Wireless broadband" - no such thing, you have _broadband_ which connects to a (Cable or ADSL) modem which may be part of a router or stand-alone.  if stand-alone, you have a WIRELESS ACCESS POINT ("WAP") connected to it.  THAT is what you are connecting to, not the internet directly.

Ok, if it works from XP and not from Ubuntu then it's not your ISP blocking them.
If you can access most sites in Ubunutu then it's unlikely to be the drivers, I'd expect either all or none to work.
You can't access abc.com from ANY browser under Ubunut so eliminates plugins such as adblockers or the like which are specific to the browser.

The only other possible cause could be the router or WAP.

If your PC is set to get a DHCP address in Windows but Static on ubuntu, there may be a rule on the router's access restrictions to only allow access (or deny access) to certain sites from certain IP addresses.

Check the configuration of the router for any such blocks - perhaps it could be the network configuration of the PC, Windows may use 4.2.2.1 as the DNS server, your Ubunutu might use the ISP's DNS server, which could be out of date and need to be refreshed by them (unlikey though as it works under XP but something worth considering).

I would check the router configuration for any DENY rules set up on it.
Good luck.

---

### Post by baskar007 on 2009-09-16
> **wojox said:**
> Open a terminal and paste this in and tell me what happens.

```
w3m -v http://www.google.com
```

The terminal displays this only:

 **[www.google.co.in](www.google.co.in) contacted. Waiting for reply...**


for more than 3 min:(

---

### Post by baskar007 on 2009-09-16
> **badger_fruit said:**
> "Wireless broadband" - no such thing, you have _broadband_ which connects to a (Cable or ADSL) modem which may be part of a router or stand-alone.  if stand-alone, you have a WIRELESS ACCESS POINT ("WAP") connected to it.  THAT is what you are connecting to, not the internet directly.

Ok, if it works from XP and not from Ubuntu then it's not your ISP blocking them.
If you can access most sites in Ubunutu then it's unlikely to be the drivers, I'd expect either all or none to work.
You can't access abc.com from ANY browser under Ubunut so eliminates plugins such as adblockers or the like which are specific to the browser.

The only other possible cause could be the router or WAP.

If your PC is set to get a DHCP address in Windows but Static on ubuntu, there may be a rule on the router's access restrictions to only allow access (or deny access) to certain sites from certain IP addresses.

Check the configuration of the router for any such blocks - perhaps it could be the network configuration of the PC, Windows may use 4.2.2.1 as the DNS server, your Ubunutu might use the ISP's DNS server, which could be out of date and need to be refreshed by them (unlikey though as it works under XP but something worth considering).

I would check the router configuration for any DENY rules set up on it.
Good luck.

Thank you.
I use 3G wireless connection, My isp say me its a mobile brodband thats why i am said 'i have mobile brodband connection.

and i'll tried to set a DNS server by editing resolv.conf file, But it will automatically changes after reconnecting   .....?

---

### Post by wojox on 2009-09-16
Are you running MoBlock or Dansguardian or any kind of blocking software?

---

### Post by baskar007 on 2009-09-16
> **wojox said:**
> Are you running MoBlock or Dansguardian or any kind of blocking software?

No   

i have Routed Internet Connection..

---

### Post by ubongo2008 on 2009-09-16
i guess you allready tried something like this?
```
    gateway="192.168.0.1"
    ip_subnet="192.168.0.04/24"
    dns_server="192.168.0.1"
    search_domain="192.168.0.1"
    interface="eth0"

    ifconfig $interface down
    ifconfig $interface $ip_subnet
    route add default gw $gateway
   
    echo "search            $search_domain"     >   /etc/resolv.conf
    echo "nameserver    $dns_server"           >> /etc/resolv.conf
    ifconfig $interface up

```


maybe you should change 

> 
gateway="192.168.0.1"
    ip_subnet="192.168.0.04/24"
    dns_server="192.168.0.1"
    search_domain="192.168.0.1"
    interface="eth0"

those values to fit your system

use ```
ifconfig -a 
```
to view your interfaces and how they are set up

---

### Post by badger_fruit on 2009-09-16
> **baskar007 said:**
> Thank you.
I use 3G wireless connection, My isp say me its a mobile brodband thats why i am said 'i have mobile brodband connection

Ah yes, I'm sorry - it's because I'm old I forgot about such technology!!

So your network card (dongle or whatever) uses 3G to connect to your ISP ... right, again, sorry for the "no such thing comment", I presumed the configuration was laptop -> Local WAP --> Internet.

I wouldn't worry too much about manually changing your DNS servers in /etc/resolve.conf - like you said, it'll wipe them anyway with the new DHCP config (although if you look around these forums, there are ways to keep them, I just can't remember right now!).

It is indeed a very strange issue, a lot of the possible causes are eliminated by the simple fact that they don't present themselves under a different OS.  I don't see how a driver can stop you from visiting CERTAIN websites though.  I can't see the technology of the website causing a problem either, I mean Google uses Ajax but other then that, not a lot more.

I'm all out of ideas for now, good luck in finding a solution, I'll be watching this thread with interest!!

---

### Post by baskar007 on 2009-09-17
> **ubongo2008 said:**
> i guess you allready tried something like this?
```
    gateway="192.168.0.1"
    ip_subnet="192.168.0.04/24"
    dns_server="192.168.0.1"
    search_domain="192.168.0.1"
    interface="eth0"

    ifconfig $interface down
    ifconfig $interface $ip_subnet
    route add default gw $gateway
   
    echo "search            $search_domain"     >   /etc/resolv.conf
    echo "nameserver    $dns_server"           >> /etc/resolv.conf
    ifconfig $interface up

```


maybe you should change 



those values to fit your system

use ```
ifconfig -a 
```
to view your interfaces and how they are set up


ifconfig -a     retuns:
eth0      Link encap:Ethernet  HWaddr 00:b0:4a:04:2b:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:25 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

[B]ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.254.107.232  P-t-P:192.168.52.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:495 errors:1 dropped:0 overruns:0 frame:0
          TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:390219 (390.2 KB)  TX bytes:80188 (80.1 KB)[/B]

---

### Post by baskar007 on 2009-09-17
> **badger_fruit said:**
> Ah yes, I'm sorry - it's because I'm old I forgot about such technology!!

So your network card (dongle or whatever) uses 3G to connect to your ISP ... right, again, sorry for the "no such thing comment", I presumed the configuration was laptop -> Local WAP --> Internet.

I wouldn't worry too much about manually changing your DNS servers in /etc/resolve.conf - like you said, it'll wipe them anyway with the new DHCP config (although if you look around these forums, there are ways to keep them, I just can't remember right now!).

It is indeed a very strange issue, a lot of the possible causes are eliminated by the simple fact that they don't present themselves under a different OS.  I don't see how a driver can stop you from visiting CERTAIN websites though.  I can't see the technology of the website causing a problem either, I mean Google uses Ajax but other then that, not a lot more.

I'm all out of ideas for now, good luck in finding a solution, I'll be watching this thread with interest!!

thankyou !:)

---

### Post by Udayakiran on 2009-09-17
Hi, have you tried changing the dns to something the ISP gave you? If you are using bsnl, try the ones that apply to their landline connection. Or try one of the free dns.

---

### Post by baskar007 on 2009-09-17
the problem has been solved by Bypass routs,tHank you guys who all helped me. once again thanks to all.

[http://softwareroxer.blogspot.com/2009/09/cannot-access-google-sites-from.html](http://softwareroxer.blogspot.com/2009/09/cannot-access-google-sites-from.html)

---

