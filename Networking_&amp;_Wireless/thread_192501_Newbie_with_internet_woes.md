---
title: "Newbie with internet woes"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by schaver on 2006-06-08
I just installed Ubuntu today, and it's the first time I've ever ventured away from Windows, so please feel free to assume that I know absolutely nothing about the Terminal, the apps, or the OS in general.  

I installed Ubuntu on an older computer (AMD 2500+ 1gb RAM, 80gb hdd, Nvidia GeForce4 MX, if any of that's relevant) while I was at the office today and it worked great.  Now that I've brought the machine home, though, I find myself only able to access certain web sites.  For example, I can go to Wikipedia, Something Awful, and if I type in search terms in the Google toolbar in Firefox, I receive search results.  However, I cannot get to the Google homepage itself, look at any articles on Wikipedia, or navigate away from the front page of SA.  Because I could do all these things before it leads me to believe that it's not an issue with drivers or the ethernet connection itself, but rather something in Ubuntu itself.

It's a cable internet connection that links into a router.  Other computers coming from the same router can access the internet with no problem.  

Specifically, the error message I receive when a page cannot be accessed is "The connection has timed out."  

Thanks in advance to anyone who knows how to fix this issue!

---

### Post by cgjones on 2006-06-08
Does your home network use DHCP, or static IP addresses?

---

### Post by schaver on 2006-06-08
[QUOTE=cgjones]Does your home network use DHCP, or static IP addresses?[/QUOTE]

DHCP

---

### Post by cgjones on 2006-06-08
I forgot to ask what the work network uses?

---

### Post by schaver on 2006-06-08
[QUOTE=cgjones]I forgot to ask what the work network uses?[/QUOTE]

Work network uses a similar setup; only difference is the router is one big Cisco switch and doesn't have a wireless router in addition to the wired one.

---

### Post by cgjones on 2006-06-08
Go to Accessories >> Terminal, then type in the following command and post the output of it here.
```
sudo arp -a
```
I may be way off track here, but give it a try and we'll see what we can figure out.

---

### Post by fordfan753 on 2006-06-08
Sounds like a DNS problem. Do you know what DNS servers your ISP uses? Make sure they are added to /etc/resolv.conf

---

### Post by schaver on 2006-06-08
Hm, nothing happens.  I have to use a different computer so I can't ctrl+c and shift+ins, so let me just double-check: sudo arp -a.  That's all it is, right?  If not, could the lack of an output be another symptom?

---

### Post by schaver on 2006-06-08
[QUOTE=fordfan753]Sounds like a DNS problem. Do you know what DNS servers your ISP uses? Make sure they are added to /etc/resolv.conf[/QUOTE]


Yeah I do, but I'm not sure how to get into /etc/resolv.conf.  Just typing that command in get me a Permission Denied message and when putting sudo in front of it it says command not found.

---

### Post by cgjones on 2006-06-08
Try going to System >> Administration >> Networking and click on the DNS tab. Do you have a DNS server entry that makes sense? I'm thinking that maybe the DNS entry got set based on the work network, and it's still trying to use the work DNS. I would have thought that if both networks use DHCP, you would have gotten the correct DNS server for your home network.

sudo arp -a returning nothing is most likely part of the problem. I forget what the timeout is on arp entries, but if you had just tried going to a website, there should be an entry in there.

---

### Post by fordfan753 on 2006-06-08
```
sudo gedit /etc/resolv.conf
```

DNS Servers should look like this in the file:
```
nameserver xxx.xxx.xxx.xxx
```

For most ISPs there will be two DNS servers that you need to add.

---

### Post by schaver on 2006-06-08
[QUOTE=fordfan753]```
sudo gedit /etc/resolv.conf
```

DNS Servers should look like this in the file:
```
nameserver xxx.xxx.xxx.xxx
```

For most ISPs there will be two DNS servers that you need to add.[/QUOTE]


Alright, my DNS servers are showing up as:
24.159.193.40 and
68.115.71.53

Both in the network settings and resolv.conf.

Do those sound right?

---

### Post by fordfan753 on 2006-06-08
Are they the DNS servers your ISP tells you to use? They will be different per ISP. If you're sure they're right then it's not a DNS problem.

---

### Post by schaver on 2006-06-08
[QUOTE=fordfan753]Are they the DNS servers your ISP tells you to use? They will be different per ISP. If you're sure they're right then it's not a DNS problem.[/QUOTE]

OK, I'm sure they're correct.  I even called the company to triple-check it.  What next?

---

### Post by schaver on 2006-06-08
Also, I'm now unable to connect to Wikipedia and the other sites I used to be able to.

---

### Post by fordfan753 on 2006-06-08
Hmm....Firefox IPv6 maybe.....

Open Firefox, type "about:config" in the address bar, look for "network.dns.disableIPv6" and toggle it, if it's false set it to true. Restart Firefox, and see if it makes a difference.

---

### Post by schaver on 2006-06-08
[QUOTE=fordfan753]Hmm....Firefox IPv6 maybe.....

Open Firefox, type "about:config" in the address bar, look for "network.dns.disableIPv6" and toggle it, if it's false set it to true. Restart Firefox, and see if it makes a difference.[/QUOTE]

Alright, I set it to true but the problem persists.

---

### Post by fordfan753 on 2006-06-08
You could try setting it up with a static IP address.

I'm late for something, I'll think about it and get back to you.

---

### Post by schaver on 2006-06-08
[QUOTE=schaver]Alright, I set it to true but the problem persists.[/QUOTE]

Also, Gaim and Ekiga don't work either, so it's the whole connection that's having issues.

---

### Post by schaver on 2006-06-09
For anyone still reading this, I've got a slightly better handle on what the problem is.  First off, I can connect to my router and modem perfectly fine.  Other computers on the network can ping the PC fine, and the PC has no trouble pinging other computers or devices on the network.  

The network is set up with DHCP, and setting a static IP address still didn't let the computer see outside the network.  However, I am able to sporadically connect to other websites, including Wikipedia, Google, and Something Awful.  However, these connections only last for a minute (maybe less) before the computer goes back to being unable to reach outside the network.  During the windows of time during which I can access certain sites, Firefox still takes a long time to load the pages.

Everything on the system tells me that it recognizes the Ethernet card and the drivers are up-to-date, so I can say with nearly 100 percent confidence the problem doesn't lie here.

The problem is also not solely with Firefox, as Gaim cannot connect either.  Turning off IPv6 does nothing to stop the problem.  

It seems now that the problem may be the system is taking a ridiculously protracted amount of time to connect with servers, and the time-out messages may just be time-out messages as opposed to a complete inability on the part of the computer to reach outside the network.  Any thoughts?

---

### Post by marcos_cu on 2006-06-09
I am having al,most exactly the same problem with my new dapper install. I can ping the router and other machines on the network but cannot get around this apparent DNS issue. My router is a Safecom...

So I am also in need of help!

---

### Post by uuser on 2006-06-09
I've had exactly the same problem on two installs of Dapper. After the first install I followed these directions:
--------------------------------
[I]1. Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining
network.http.proxy.pipelining
network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set "network.http.pipelining" to "true"

Set "network.http.proxy.pipelining" to "true"

Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once.

3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it recieves.

If you're using a broadband connection you'll load pages 2-3 times faster now, 
[/I]---------------------------------
and that fixed my problem entirely. After the second install, I had the same problem browsing, did the intructions again, and it DIDN'T help. So now I'm in exactly the same position you are. I have DSL, wireless, DHCP, WEP-enabled.

---

### Post by schaver on 2006-06-09
Did all that but still no luck with getting the connection to work.  Also tried doing a fresh install of Ubuntu, also to no avail.  Anyone have any other thoughts?

Edit: It seems like I can always get to the front page of Something Awful, but none of the pictures show up.

---

### Post by Slim Odds on 2006-06-09
[quote=schaver]Anyone have any other thoughts?[/quote] 
Yes, get your basic network functioning (before you worry about web sites, etc).

It **really** helps to see some network information, like output from: 'ifconfig', 'route -n', 'cat /etc/resolv.conf'

Start simple, ping a web site by name, like: ping [www.yahoo.com]("http://www.yahoo.com")

Also, traceroute is really helpful.

---

### Post by schaver on 2006-06-09
[QUOTE=Slim Odds]Yes, get your basic network functioning (before you worry about web sites, etc).

It **really** helps to see some network information, like output from: 'ifconfig', 'route -n', 'cat /etc/resolv.conf'

Start simple, ping a web site by name, like: ping [www.yahoo.com]("http://www.yahoo.com")

Also, traceroute is really helpful.[/QUOTE]

Here's what IF Config is turning out:
```

eth0     Link encap:Ethernet HWaddr 00:0C:76:13:55:C9
           inet addr 192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
           inet 6 addr: fe80: :20c:76ff:fe13:55c9/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packet:427 errors:0 dropped:0 overruns:0 frame:0
           TX packet:452 errors:0 dropped:0 overruns:0 frame:0
           collisions:0 txqueuelen:1000
           RX bytes:245091 (239.3 KiB) TX bytes:46034 (44.9 KiB)
           Interrupt:177 Base address:0xa000

lo         Link encap:Local Loopback
           inet addr:127.0.0.1 Mask:255.0.0.0
           inet addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
           RX packets:13 errors:0 dropped:0 overruns:0 frame:0
           TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:672 (672.0 b) TX bytes:672 (672.0 b)

```

---

### Post by Slim Odds on 2006-06-09
Ok, your IP address looks reasonable.

What about 'route -n'? 

Also try this: 'traceroute www.google.com'

---

### Post by schaver on 2006-06-09
[QUOTE=Slim Odds]Ok, your IP address looks reasonable.

What about 'route -n'? 

Also try this: 'traceroute www.google.com'[/QUOTE]

```

andy@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway       Genmask       Flags  Metric Ref     Use Iface     
192.168.1.0    0.0.0.0        255.255.255   U      0        0        0 eth0 
0.0.0.0        192.168.1.1    0.0.0.0       UG     0        0        0 eth0

```

Traceroute returns a "command not found" error message

---

### Post by Slim Odds on 2006-06-09
[quote=schaver]```

andy@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway       Genmask       Flags  Metric Ref     Use Iface     
192.168.1.0    0.0.0.0        255.255.255   U      0        0        0 eth0 
0.0.0.0        192.168.1.1    0.0.0.0       UG     0        0        0 eth0

``` 
Traceroute returns a "command not found" error message[/quote] 
The route looks fine. You might need to type: /sbin/traceroute

Also, did you try ping?

---

### Post by schaver on 2006-06-09
```

bash: /sbin/traceroute: No such file or directory

```

Hm, won't let me traceroute for some reason.  

THIS is weird. . .
First of all, it doesn't return any packets when I enter 
```
ping http://www.google.com
```
but when I type
```
ping www.google.com
```
It DOES return packets.  However, the message Terminal displays is
```
PING www.l.google.com (64.233.167.99) 56(84) bytes of data
```
First of all, what does that "l" mean?  Second, Firefox still doesn't display google.com.  Third, it DOES display the IP address for Google.  Very strange. . .

EDIT: I formatted and reinstalled Ubuntu, but that didn't do anything.  I also still couldn't use the internet while the boot disc was in, so that's one symptom I'm not experiencing that also seems to be floating around the forums.

---

### Post by Slim Odds on 2006-06-09
[quote=schaver]```

First of all, it doesn't return any packets when I enter 
[code]ping http://www.google.com
``` but when I type
```
ping www.google.com
``` It DOES return packets.  However, the message Terminal displays is
```
PING www.l.google.com (64.233.167.99) 56(84) bytes of data
``` First of all, what does that "l" mean?  Second, Firefox still doesn't display google.com.  Third, it DOES display the IP address for Google.  Very strange. . .
[/quote] 
I'll check where traceroute is when I get home, it also might be in /usr/sbin

ping uses ICMP not HTTP, to you would ping [www.google.com]("http://www.google.com") and not [http://www.google.com]("http://www.google.com")

You must have typed this in manually, because [www.l.google.com]("http://www.l.google.com") is 64.233.187.99 not 64.233.167.99

[www.google.com]("http://www.google.com") is actually an alias for [www.l.google.com]("http://www.l.google.com")

So it looks like your DNS is working. You don't show any other output from ping, are you really getting packets back?

---

### Post by miguelito on 2006-06-09
i'm have the same problem, but in ubuntu 5.10, i don't have problem whit de connection...

---

### Post by fordfan753 on 2006-06-10
Traceroute needs to be installed, which is hard with no internet.

---

### Post by Slim Odds on 2006-06-10
[quote=fordfan753]Traceroute needs to be installed, which is hard with no internet.[/quote] 
I believe that traceroute is installed by default.

---

### Post by di4blit0 on 2006-06-10
I'm having the same problem here with ubuntu, mandriva, suse, but linspire works fine for me :confused:

---

### Post by nrwilk on 2006-06-10
I have this exact same problem as well.  I've had it with two other installs of dapper too.  The last times it seemed to sort-of go away, but this time the problem is persisting.

I cannot access some websites EVER, some I can access occasionally, some work all the time.  The websites that never work include google, wikipedia, and ebay.  The websites that work sometimes seem to be random.  The ones that work all the time are my own site, ubuntuforums.org, and very few others.  Kopete works flawlessly on both AIM and jabber networks.

I'm pretty sure that this is a DNS issue for me because in my /etc/resolv.conf file, one of my DNS entries ALWAYS gets replaced with the IP of my router (192.168.0.1).  Everytime I replace it with the correct DNS IP, it gets replaced again, and even then I cannot get better internet access.

How can I diagnose the problem and how can I mke my /etc/resolv.conf not replace the correct IP with my router IP?

Here's my setup if it helps:
* Onboard nvidia nforce4 ethernet port (eth0).  Not being used.
* Linksys PCI add-on card. (eth1).  I use this one.

If I switch the cable to the onboard port, I can get all websies for about a minute, and then it starts doing the same sporadic thing again.

If I put only correct DNS IPs in /etc/resolve.conf, and then issue a```
sudo dhclient eth1
``` it still doesn't work.

Please help!

Thank you,
nrwilk

---

### Post by fordfan753 on 2006-06-10
If you use a static IP on the host, the router *shouldn't* overwrite the entry in /etc/resolv.conf I'm guessing you're using DHCP. I recommend trying a static.

---

### Post by nrwilk on 2006-06-11
using a static IP works to fix my problem flawlessly.

I thought about trying this before, but I figured that something so simple and obvious would probably not help, hehe.

Thanks so much!

nrwilk

---

### Post by schaver on 2006-06-11
[QUOTE=Slim Odds]I'll check where traceroute is when I get home, it also might be in /usr/sbin

ping uses ICMP not HTTP, to you would ping [www.google.com]("http://www.google.com") and not [http://www.google.com]("http://www.google.com")

You must have typed this in manually, because [www.l.google.com]("http://www.l.google.com") is 64.233.187.99 not 64.233.167.99

[www.google.com]("http://www.google.com") is actually an alias for [www.l.google.com]("http://www.l.google.com")

So it looks like your DNS is working. You don't show any other output from ping, are you really getting packets back?[/QUOTE]


Well, you DID bust me in that I hand typed it, however I double-checked and that's exactly what it's say:
```

PING www.l.google.com (64.233.167.147) 56(84) bytes of data.
64 bytes from 64.233.167.147: icmp_seq=1 ttl=244 time=21.8ms
64 bytes from 64.233.167.147: icmp_seq=2 ttl=244 time=19.3ms
64 bytes from 64.233.167.147: icmp_seq=3 ttl=244 time=22.6ms

```

etc.  Could this be a part of the problem?  Also, I had my friend putz around on the computer and he tried doing a static IP address. . . AND IT WORKED!  Then I think he changed to DHCP again to see if the problem would persist, and it did, so he changed back to the EXACT SAME static IP settings he'd used before, but the problem wouldn't go away.  24 hours later I'm still trying to mess around with different IP addresses and so on to see if I can't get it to work, but to no avail.  The one thing he did that was rather unorthodox was he deleted the default DNS Servers and used 192.168.1.1 as the DNS server.  Perhaps the problem lies here but I'm just not doing it right?

nrwilk said he was getting weird results from his sudo dhclient command, so I thought maybe that was relevant.  Here's what I'm getting:
```

andy@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.  For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0c:76:13:55:c9
Sending on LPF/eth0/00:0c:76:13:55:c9
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.103 -- renewal in 32533 seconds.

```

The only thing that seems fishy to me in that (granted I'm still very new to using the OS) is that the DHCPREQUEST line shows 255.255.255.255, which looks like my subnet mask except with another 255 on the end instead of 0.  Are there any other terminal commands I could run that might make the problem more clear?

---

### Post by fordfan753 on 2006-06-11
[QUOTE=schaver]The one thing he did that was rather unorthodox was he deleted the default DNS Servers and used 192.168.1.1 as the DNS server.  Perhaps the problem lies here but I'm just not doing it right?[/QUOTE]

This is definitely where the problem lies. My router seems to think it's a DNS server, and every time I use DHCP the host is left with the router as it's only DNS server, and can't access the internet. This is very annoying, especially when you get halfway through a net install and find out the net doesn't work!

There are two (possibly more) solutions to this:
1. Use a static ip addressing scheme network wide. You may also disable dhcp on the router since you wont be using it any more
2. Use a static ip on one host, then run a dhcp server on that host, and disable dchp on the router.

Option 1 is just generally good. There is nothing wrong with a static ip addressing scheme, in fact there are many advantages.

Option 2 is good for networks with more than say 3 or 4 computers, when you still want to use dhcp for some unknown reason.

---

### Post by schaver on 2006-06-12
Alright everybody, I'm writing this post from the UBUNTU DESKTOP!!!  I still haven't got the internet to work on the connection at home, but it IS working here at the office.  While I'm here, maybe somebody wants to tell me what to look for that may be different from the home network?  Otherwise I'll look around at the settings here and see if I can't see the change for myself.

Currently, the DNS is set to 10.0.1.1.  The network and the computer are set on DHCP.

---

### Post by Slim Odds on 2006-06-12
[quote=fordfan753]This is definitely where the problem lies. My router seems to think it's a DNS server, and every time I use DHCP the host is left with the router as it's only DNS server, and can't access the internet. This is very annoying, especially when you get halfway through a net install and find out the net doesn't work![/quote] 
I hear lots of people in a panic because their router is being used as a DNS server. This is usually OK, most small NAT/Firewall routers will act as DNS forwarders. Therefore, the address of the router is a valid DNS server.

I have a Netgear WGR614 (a really old one) that works just fine this way.

---

### Post by nrwilk on 2006-08-18
OK, while using a static IP for wired connections at home is great for my desktops, what can I do about this when working on my laptop at other locations?  I cannot assign a static IP to eth1 (my Intel Pro Wireless wifi card), because I'll need to use different IPs depending on what network I'm on.  But, everytime I log on at home I have to re-enter my second DNS entry in order for the internet to fully work.  Should I just write a script that I can run when at home which re-writes /etc/resolv.conf with the correct DNS IPs?  Is there a way to make my DSL modem stop believing that it is a DNS server?

I really hope someone can help resolve this problem for all those of us who have it.

Thanks!

nrwilk


EDIT: I've found a quick and dirty solution in this thread: [http://www.ubuntuforums.org/showthread.php?t=134731](http://www.ubuntuforums.org/showthread.php?t=134731)

I just added the following line to /etc/dhcp3/dhclient.conf
```
prepend domain-name-servers 205.171.2.65, 205.171.3.65;

``` 
of course, the IPs to everyone's DNS servers will be different.  This makes it so that I have four entries in resolv.conf so it looks like this:
```
205.171.2.65
205.171.3.65
192.168.0.1
205.171.3.65
``` 
But, It still works.

Let me know if this is somehow not good. :)

---

