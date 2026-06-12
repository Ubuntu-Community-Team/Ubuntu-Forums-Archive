---
title: "Strange internet problem. PLEASE HELP!"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Cgrace on 2008-12-19
Hey guys. I'm pretty new to Ubuntu and everything. But I've been having a great experience with it for the past two months. I just got back home though, and reconnected to an my Verizon FIOS modem. Now all of a sudden, my synaptic and update manager can't update themselves normally. And in addition, I only have access to very limited websites. For instance, I can only read email and google stuff, I can't actually access any google links...
It will just say: "Address Not Found."

I really need help, and tried looking through previous posts on this forum. I fiddled with the repositories to get the best working one which seems to help with updating synaptic...etc, however it doesn't even effect the fact that I can't access the majority of the internet. What should I post up here to get help?
I read about fiddling with the DNS server settings, but I don't know what that means.

I know my Internet is working too because I can still get on networks for video games and stuff (MAME kaillera for ex.)

I'd really appreciate anyone's help. Thanks so much in advanced.

---

### Post by Cgrace on 2008-12-19
Does anyone know why I would be able to search through google, but not access any of its links? What would be letting me partially use my internet?

---

### Post by Cgrace on 2008-12-19
I just found some old post talking about MTU and fiddling with that in terminal. I tried that, and that didn't work either. Any other suggestions?

---

### Post by Yardarm on 2008-12-19
my first thought would be a DNS problem, it translates names like ubuntufourms.org into IP addresses.  If it has some names cached, you would still be able to see those sites, but not new ones.  When you enter:

```
dig ubuntuforums.org
```

in the terminal, what does it spit out?

---

### Post by Cgrace on 2008-12-19
I also get this message when trying to reload synaptic.

> W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/Release.gpg](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/Release.gpg)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/main/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/Release.gpg](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/Release.gpg)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/Release.gpg](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/Release.gpg)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Failed to fetch [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'mirror.cc.columbia.edu'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any guesses, suggestions?

---

### Post by Cgrace on 2008-12-19
Greatly appreciate the reply Yardarm.
Here's what it spits back:

> ; <<>> DiG 9.5.0-P2 <<>> ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41087
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 3, ADDITIONAL: 3
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;ubuntuforums.org.        IN    A

;; AUTHORITY SECTION:
ubuntuforums.org.    42026    IN    NS    ns3.canonical.com.
ubuntuforums.org.    42026    IN    NS    ns1.canonical.com.
ubuntuforums.org.    42026    IN    NS    ns2.canonical.com.

;; ADDITIONAL SECTION:
ns3.canonical.com.    144661    IN    A    209.6.3.210
ns1.canonical.com.    144661    IN    A    91.189.94.173
ns2.canonical.com.    144661    IN    A    91.189.94.219

;; Query time: 36 msec
;; SERVER: 129.22.4.3#53(129.22.4.3)
;; WHEN: Fri Dec 19 18:49:02 2008
;; MSG SIZE  rcvd: 149

---

### Post by albinootje on 2008-12-19
> **Cgrace said:**
> 
Here's what it spits back:

Looks good.

And this ?
```

$ host mirror.cc.columbia.edu

```
This is what i get here :
mirror.cc.columbia.edu is an alias for stewie.atg.columbia.edu.
stewie.atg.columbia.edu has address 128.59.59.71
stewie.atg.columbia.edu mail is handled by 100 stewie.atg.columbia.edu.

And what about asking a friend over with a laptop to check whether the same problem appears ? With the idea to find out whether your Ubuntu has a problem and/or your modem, and/or your ISP.

---

### Post by Cgrace on 2008-12-19
Thanks for the reply, albinootje. I get the same response with "host mirror.cc.columbia.edu"

I just had a friend over actually, and I had him hook himself up to the same modem, and his internet was fine. However, he uses vista. I find it hard to believe I have corrupted anything in Ubuntu, seeing as I've only had it for a short time and haven't downloaded anything harmful.

---

### Post by Yardarm on 2008-12-19
There is no answer section there, so that's your problem.  Are you set to a static IP or are you obtaining your IP automatically?  If you get it automatically, it should give you a DNS server automatically as well.  

I'm not familiar with the Verizon modem.  Is that a wireless card connecting to the Verizon cell phone network?  Is it managed by NetworkManager (the network icon in the upper right hand corner of the screen by the clock)?

---

### Post by Cgrace on 2008-12-19
I'm pretty sure I'm having my IP obtained automatically, because I haven't done anything on my own to make it static. 

You are correct, it's managed by NetworkManager. I'm pretty sure Verizon should just be an ordinary internet provider. I have my ethernet cable hooked up to a NetGear Dual Speed Hub DS104 if that helps at all.

---

### Post by Yardarm on 2008-12-19
Gotcha, so it's just a wired ethernet connection.  If you click on the NetworkManager icon, "Auto eth0" should be selected, is that correct?

Also, what are the contents of /etc/resolv.conf? You can enter "less /etc/resolv.conf" in the terminal to see.

---

### Post by Cgrace on 2008-12-19
Right, "Auto eth0" is selected as well as my wireless. But I'm almost certain when wired, the eth0 connection over-rides the wireless.

Anyway. Here's the results from "less /etc/resolv.conf"
> # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 129.22.4.3
nameserver 129.22.104.56
nameserver 192.168.1.1
search cwru.edu home

---

### Post by Yardarm on 2008-12-19
That is odd.  Everything on your laptop looks fine.  You should be able to use both your wired and wireless connections at the same time.  I think that was supposed to be one of the big features of NetworkManager 0.7.  A few more things to try:

1. If you're going through a router, unplug the power, and either plug it back in or connect directly to your ISP connection.

2.  Turn off your wireless card using:
```
sudo ifdown wlan0
```
Just to make sure it isn't a conflict there.  You can bring it back up with:
```
sudo ifup wlan0
``` or rebooting.  You can cycle the DHCP IP address on your ethernet card the same way
```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by Cgrace on 2008-12-19
Hm. I just tried those things too, but it didn't help. Any other suggestions?

---

### Post by jonobr on 2008-12-20
Stupid question, is it only when you click a link returned by google ,as you emntioned that.

If you go to it directly is it any different?
Do you go to the url route to see if that's any different,

ie  if you go to [www.website.com/place/here(using](www.website.com/place/here(using) website.com as an example)


have you tried just the [www.website.com](www.website.com)

if that doesn't work, could you do an nslookup on the website that doesn't work.

in your terminal window enter

nslookup website.com (using website.com as an example)

it will give you back the ip , if it doesnt ....very odd

if it does, could you go to the ip address it returns

i.e. website.com = 192.168.1.99

in your browser enter 192.168.1.99, does the same happen?

If that doesnt work, in the terminal window type w3m website.com

what happens ? (hit q to exit w3m)

When you do w3m 192.168.1.99 what happens again, hit q to quit.

also posting the results of ifconfig will be useful

---

### Post by Cgrace on 2008-12-20
Thanks for the reply jonobr.
Okay, so instead of website.com I'm using 'www.winehq.org'
That being said, "nslookup winehq.org" spits back:
> ;; Got recursion not available from 129.22.4.3, trying next server
;; Got recursion not available from 129.22.104.56, trying next server
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    winehq.org
Address: 209.46.25.134

"w3m winehq.org" spits back:
> w3m: Can't load winehq.org.

"w3m 192.168.1.99" spits back:
> w3m: Can't load 192.168.1.99.

And since you asked for it, ifconfig spits back:
> eth0      Link encap:Ethernet  HWaddr 00:1d:72:62:6f:e8 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:176 (176.0 B)  TX bytes:176 (176.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:92:3c:cd 
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe92:3ccd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3567 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2677175 (2.6 MB)  TX bytes:716953 (716.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-92-3C-CD-63-63-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Really appreciate the help. I'm very confused.

---

### Post by Cgrace on 2008-12-20
I just wired my laptop back in through ethernet, so here's the updated ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:1d:72:62:6f:e8 
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe62:6fe8/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5372 (5.3 KB)  TX bytes:15335 (15.3 KB)

          Interrupt:17

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:176 (176.0 B)  TX bytes:176 (176.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:92:3c:cd 
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe92:3ccd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2812140 (2.8 MB)  TX bytes:769728 (769.7 KB)


wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-92-3C-CD-63-63-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Rakdoll on 2008-12-20
Hi,
I’m totally new to Ubuntu, and already run into my first problem. I’m not posting here because I’m lazy and want others to do the work. The reason is I just don’t have a glue what’s going wrong here. Hope I can learn from you guys who know better. I will also do my best to figure this out, and hopefully help Cgrace out with the problem.

I have been reading thru this thread with great interest, since I’m sharing exactly the same problem, only a few differences. I noticed that I can connect to any google hosted website, like google, google maps and google docs. I can also search for websites, but can’t connect to them.

To connect to internet I’m using a HTC Touch Pro windows mobile phone, which shares the internet connection, provided by my finnish service provider saunalahti. That connection is direct to the internet with no proxy and using server assigned ip address. 

My PC is hooked to my phone thru USB cable and Ubuntu automatically sets up the connection to Wired network (Hight Tech Computer Generic RNDIS): Auto eth1. 

My wifi interface has no trouble connecting to my home or any other access point. Also the HTC phone connection shared thru USB cable works like a charm in Windows Vista, as Cgrace pointed out.

Here is all the requested information, just to compare with ones posted before. (I know it's a little lengthy. If it bothers you, im willing to delete my post :()Anyway, thanks for any possible help. I'll do my best to figure this out also.

dig ubuntuforums.org
> ; <<>> DiG 9.5.0-P2 <<>> ubuntuforums.org
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 58245
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 3

;; QUESTION SECTION:
;ubuntuforums.org.		IN	A

;; ANSWER SECTION:
ubuntuforums.org.	40	IN	A	91.189.94.12

;; AUTHORITY SECTION:
ubuntuforums.org.	13226	IN	NS	ns1.canonical.com.
ubuntuforums.org.	13226	IN	NS	ns3.canonical.com.
ubuntuforums.org.	13226	IN	NS	ns2.canonical.com.

;; ADDITIONAL SECTION:
ns3.canonical.com.	13840	IN	A	209.6.3.210
ns1.canonical.com.	13840	IN	A	91.189.94.173
ns2.canonical.com.	13839	IN	A	91.189.94.219

;; Query time: 72 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sat Dec 20 22:24:26 2008
;; MSG SIZE  rcvd: 165

less /etc/resolv.conf/
> # Generated by NetworkManager
nameserver 192.168.0.1

nslookup for a site not working:
> nslookup [www.xda-developers.com](www.xda-developers.com)
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	[www.xda-developers.com](www.xda-developers.com)
Address: 82.94.251.230

with firefox trying to reach the address i get:
> Connection Interrupted
The connection to the server was reset while the page was loading.
The network link was interrupted while negotiating a connection. Please try again.

the same message pops up when trying to connect to 82.94.251.230 with firefox.

when connecting xda-developers.com or 82.94.251.230 with w3m:
> Opening socket
Viewing <> No line

 ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:14:0b:3f:ae:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2002:554d:d0d1:a:8200:60ff:fe0f:e800/64 Scope:Global
          inet6 addr: fec0::a:8200:60ff:fe0f:e800/64 Scope:Site
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1478  Metric:1
          RX packets:224 errors:177 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51555 (51.5 KB)  TX bytes:53518 (53.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2928 (2.9 KB)  TX bytes:2928 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:e0:45:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-E0-45-39-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by albinootje on 2008-12-20
> **Cgrace said:**
> 
That being said, "nslookup winehq.org" spits back:
```

;; Got recursion not available from 129.22.4.3, trying next server
;; Got recursion not available from 129.22.104.56, trying next server
Server: 192.168.1.1
Address: 192.168.1.1#53

Non-authoritative answer:
Name: winehq.org
Address: 209.46.25.134 

```


Seems like two of your nameservers are failing in your setup, but 192.168.1.1 works for you.
What happens if you manually put 192.168.1.1 as only (or first) nameserver in /etc/resolv.conf ?
And then try something in Firefox or w3m right away.
It's possible that Network-manager will try to overwrite /etc/resolv.conf soonish.

---

### Post by Cgrace on 2008-12-20
Thanks albinootje! Changing all ip's to 192.169.1.1 worked! However, like you said it's definately only temporary. On a reboot, or even just the act of wiring in (through ethernet), it resets the /etc/resolv.conf to the original settings that doesn't work. Where am I getting those two non-working ip's from? Is the 192.169.1.1 from my wireless? Then why doesn't the wired one work?

Even still, I'm very grateful you've let me get access to the internet, even if its temporary! Thank you so much.

---

### Post by albinootje on 2008-12-20
> **Cgrace said:**
> Thanks albinootje! Changing all ip's to 192.169.1.1 worked! However, like you said it's definately only temporary. On a reboot, or even just the act of wiring in (through ethernet), it resets the /etc/resolv.conf to the original settings that doesn't work. Where am I getting those two non-working ip's from? Is the 192.169.1.1 from my wireless? Then why doesn't the wired one work?

Even still, I'm very grateful you've let me get access to the internet, even if its temporary! Thank you so much.

Cool! :)

You must be getting the other DNS-servers from your DSL-router which hands out the ip-addresses (If I remember your setup correctly).
Since you seem to be taking your laptop to other places, I think it makes sense to create some profile in Network Manager (Can network-manager do that ?) and save the 192.168.1.1 (not 192.169.1.1) there as DNS-server.

---

### Post by Cgrace on 2008-12-20
Okay that makes sense. The network manager thing recognizes the wifi profile already, so I don't think there's anything I can do with that to make it get rid of the unecessary DNS-servers.

I'm trying to install Wicd to see if it manages my available internets easier. I'll let you know how that turns out. If you have any other ideas, I'd love to hear them.

---

### Post by Cgrace on 2008-12-21
Sweet. Wicd is much easier to manage compared to the default ubuntu network manager. It seems like it saves the newly updated IPs as well. Thanks for the help guys.

---

