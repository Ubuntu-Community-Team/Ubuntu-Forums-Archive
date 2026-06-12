---
title: "Wired weird network problem - please stop me killing myself!"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by xirb on 2010-01-03
Dear folks
I'm quite new to Ubuntu. Have been quite happy using it the few times I have had a chance to far, but now Ubuntu makes me wanna kill myself because I cannot access the internet (and I'm a internet addicted). Could you PLEASE try and help me, so I can avoid that outcome? :)
 
No matter what I have tried I suddenly cannot access the (damned) internet. This is the full info:
 
- The PC is a Atom based noname touch screen PC, which came with Ubuntu 9.04 and I upgraded to v. 9.10.
 
- The internet was accessable using both 9.04 and 9.10 until now (first time I try in 2010). I might have had to reboot at some point before when it did not connect at once, but now I have rebooted 50 times and done all kind of weird moves without any luck.
 
- I'm using a wired/cabled connection by the way. What is weird is that I cannot think of anything that I have changed that could course this. (I did try to change the screen reslution and I did eat crisps for breakfast, both f which I suspect should not affect the internet connection). 
 
- The (cabled) internet connection was connected using a switch until today. When I booted the system no connection is found at all! To make sure that they other PC on the switch was not doing some black hat voodoo crap (it's a Win Vista machine) to my switch, I disconnected this setup and put the cable into the Ubuntu machine directly - not using the switch, that is. Also I have tried using the cable which normally goes into my NAS instead - just to make sure that it was not the cable itself and that it was not bacause the router did not send *all* it's love to my NAS and ignoring everything else (I'm not very familiar with networking as you might have guessed by now). 
 
- WHEN using the direct cable connection (without the switch) **[COLOR=blue]I get a "[COLOR=black]Auto[/COLOR] [COLOR=black]eth0[/COLOR]"-connection in the top bar. It even pretends to be connected, but NO it's really not![/COLOR]** That is apparently just to mess with me, because I feel no real connection: Netiher Firefox nor Pidgin can connect to anything (the keep saying "Loading..." og "Connecting")!
When looking at Network Connections it even says [COLOR=red]NEVER[/COLOR] in the "Last [COLOR=black]used[/COLOR]" coloumn next to Auto [COLOR=#ee6600]eth0[/COLOR], to make sure I get it..:
 
[IMG]http://www.myupload.dk/showfile/r397430cbfc2.jpg[/IMG]
 
 
With this setup I tried the ifconfig request which was kind enough to give me this info:
[IMG]http://www.myupload.dk/showfile/r397426ca27d.jpg[/IMG]
 
- I have even tried to change the settings for the Auto [COLOR=#ee6600]eth0[/COLOR] to make it a static thingy instead of the auto/DCHP thingy it ought to be now. I did not have info to fill into all the fields though, e.g. DNS, so that did of course not working netiher.
 
- What is ALSO weird (so much that it almost belongs in a episode of X-Files or Twilight Zone) is that I can't even access my router administration from the Ubuntu machine after it lost the connection - when trying 192.18.1.1 it just get the same "Loading..." as on all other external pages.. (The first time the password dialog showed, but I suspect this was something from the cache since I cannot make it appear again and cannot get any further).
 
 
[COLOR=#00bfbf](Also I at some point when using the switch earlier I did get another look in the ifconfig, but I guess that's not important compared to the above where the PC at least think that it might have a connection:[/COLOR]
[COLOR=#00bfbf][IMG]http://www.myupload.dk/showfile/r397412c88e5.jpg[/IMG][/COLOR]
[COLOR=#00bfbf]....) [/COLOR]
 
Having tried everything I can think of and can't even find any clues on what to try og the GoogleNet I now feel like killing myself. Or switch back to Windows permanently. Whicever is less painfull. Could you PLEASE help me avoid that? 
**Thank you very much for your time and help!**

---

### Post by Iowan on 2010-01-03
Your first screen shots suggest that the machine got IP address 192.168.1.103. The last shot shows no address. > When looking at Network Connections it even says NEVER in the "Last used" coloumn next to Auto eth0, to make sure I get it..: My Karmic machine  also shows "never" in the "Last used" column (I happen to be using it now). It also seems slow to load pages. I may try the tricks [here]("http://ubuntuforums.org/showthread.php?t=1156441") to see if it speeds up.

Post results of **route -n** and contents of */etc/resolv.conf*. I kinda doubt they are the problem - missing gateway or DNS servers usually generate different errors.

---

### Post by xirb on 2010-01-03
> **Iowan said:**
> Your first screen shots suggest that the machine got IP address 192.168.1.103. The last shot shows no address.
I will entirely forget about using the switch for now since that doesn't even get my an IP. But till can't connect using the "direct line" even though it looks as if I have an IP from the screenshot.
 
> **Iowan said:**
> 
My Karmic machine also shows "never" in the "Last used" column (I happen to be using it now). It also seems slow to load pages. I may try the tricks [here]("http://ubuntuforums.org/showthread.php?t=1156441") to see if it speeds up.
Thanks! I have just commented out the line and deleted the reference from that file and rebooted. Still no luck though!
You wrote "slow" and "speeds up" - my problem is not that it is slow - apparantly I have no connection as all - nothing at all ever appears!
 
> **Iowan said:**
> Post results of **route -n** and contents of */etc/resolv.conf*. I kinda doubt they are the problem - missing gateway or DNS servers usually generate different errors.
 
I have attached a picture of the route -n result:
[IMG]http://www.myupload.dk/showfile/r3976078b752.jpg[/IMG]
 
resolv.conf contains:
domain opasia.dk
search opasia.dk 
nameserver 193.162.153.164
nameserver 194.239.134.83
 
 
Thank you very much for helping - **hope you have more input for me so I can get it to work! :-)**

---

### Post by Iowan on 2010-01-03
My **route -n** is (almost) identical, my */etc/resolv.conf* is (of course) much different. I might wonder about the domain, but I'm not sure what it should be...

I presume you can *ping* the router (192.168.1.1).

---

### Post by CharlesA on 2010-01-03
My route -n looks the same minus the APIPA IP (169.254.x.x):
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.240 U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```

Are you able to ping the router?

I tried pinging the nameserver but only got a response from 194.239.134.83.

---

### Post by xirb on 2010-01-03
Hi guys
Thanks for noticing my question / caring!
 
Yes, when pinging 192.168.1.1 I get lines in the terminal ending with "ms", e.g. "0,705 ms", so I believe that I can reach/ping the router. (Apart from when trying to go through the switch where the lines just says "Network is unreachable".)
 
Any suggestions on what might be wrong/what I can do?
Thanks!

---

### Post by SecretCode on 2010-01-03
If you can ping your router, it seems to me like there's nothing wrong in your ubuntu setup. How is your router connected to the world - ADSL?

I would try, in no particular order:
- are there any other computers in the house/building using the same router?
- rebooting the router (and trying to get into its admin console again)
- checking if the line shows synchronisation
- checking if your internet account is paid up for January :)

---

### Post by Iowan on 2010-01-03
The switch *should* be transparent. I'm not sure what's going on there - the Windows box still works through the switch - as before?
On the other front, have you tried to ping internet by address?
 (Try 74.125.95.106)

---

### Post by CharlesA on 2010-01-04
> **Iowan said:**
> The switch *should* be transparent. I'm not sure what's going on there - the Windows box still works through the switch - as before?
On the other front, have you tried to ping internet by address?
 (Try 74.125.95.106)

Indeed. Also might want to try booting off a LiveCD and seeing if you can get online.

It should be working, but I'm not sure why it's not.

---

### Post by xirb on 2010-01-04
How is your router connected to the world - ADSL?
- Yes, the router connects to ADSL.
 
Are there any other computers in the house/building using the same router?
- Yes, a laptop on Wifi and Windows Vista PC on cable. have even tried to use the same cable and the Win-PC connects after only a short "thinking break"..
 
Rebooting the router (and trying to get into its admin console again)
- Did try to take the power from the router and the ADSL "modem" and rebooting the Ubuntu-PC - but no luck, can still not access internet nor router-admin-page.
 
Checking if the line shows synchronisation
- I don't know what that is/how to do it. :-s
 
Checking if your internet account is paid up for January :smile: 
- Haha, YES it IS paid for January. :P
 
The switch *should* be transparent. I'm not sure what's going on there - the Windows box still works through the switch - as before?
- Yes, the Win-PC connects using the switch without problem. But if I could at least get the Ubuntu-machine to connect at all, I don't mind too much loosing the switch.. 
 
Also might want to try booting off a LiveCD and seeing if you can get online.
- The touch screen PC don't even have a CD-drive.. But I guess I could try to make some USB-magic happen, even though I'm not familiar with that (and it only has 1 USB-port, so I cannot connect mouse at the same time :))
 
**Any other advise is (also) very welcome - thank you guys!**

---

### Post by SecretCode on 2010-01-04
OK, we can rule out the ADSL and the router if other machines connect OK.

Not sure if you tried pinging an external internet host - try
```
ping 209.85.229.104
ping 72.163.4.161
```

If those don't work, go to a working PC (Windows is fine) and run
```
ping www.google.com
ping www.cisco.com
```
and see if it reports the same addresses I used above. If they're different (and they respond to pings on Windows) try pinging those addresses from Ubuntu.

Next, try typing _nslookup_ - you'll get a sub-prompt '>' - and the following commands at the sub-prompt:
```
server
www.cisco.com
exit
```
Post all the output here.

---

### Post by xirb on 2010-01-04
Thanks for the input - I will try that as soon as possible when I get away from job. Thanks!

---

### Post by xirb on 2010-01-04
I am able to ping the outside IP's - VERY strange indeed!
 
- Unlike "the highjacker" :-) I don't ever see my homepage or anything..
 
Results:
```
omaihuo@aomaihuo-desktop:~$ ping 209.85.229.104
PING 209.85.229.104 (209.85.229.104) 56(84) bytes of data.
64 bytes from 209.85.229.104: icmp_seq=2 ttl=58 time=65.0 ms
64 bytes from 209.85.229.104: icmp_seq=3 ttl=58 time=61.8 ms
64 bytes from 209.85.229.104: icmp_seq=8 ttl=58 time=61.9 ms
64 bytes from 209.85.229.104: icmp_seq=9 ttl=58 time=64.9 ms
64 bytes from 209.85.229.104: icmp_seq=11 ttl=58 time=62.3 ms
aomaihuo@aomaihuo-desktop:~$ ping 72.163.4.161
PING 72.163.4.161 (72.163.4.161) 56(84) bytes of data.
64 bytes from 72.163.4.161: icmp_seq=1 ttl=117 time=159 ms
64 bytes from 72.163.4.161: icmp_seq=4 ttl=117 time=159 ms
64 bytes from 72.163.4.161: icmp_seq=6 ttl=117 time=159 ms
64 bytes from 72.163.4.161: icmp_seq=8 ttl=117 time=159 ms
64 bytes from 72.163.4.161: icmp_seq=10 ttl=117 time=158 ms
64 bytes from 72.163.4.161: icmp_seq=12 ttl=117 time=158 ms
64 bytes from 72.163.4.161: icmp_seq=13 ttl=117 time=159 ms
aomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.cisco.com]("http://www.cisco.com/")
Server:  193.162.153.164
Address: 193.162.153.164#53
Non-authoritative answer:
[www.cisco.com]("http://www.cisco.com/") canonical name = [www.cisco.com.akadns.net]("http://www.cisco.com.akadns.net/").
[www.cisco.com.akadns.net]("http://www.cisco.com.akadns.net/") canonical name = geoprod.cisco.com.akadns.net.
geoprod.cisco.com.akadns.net canonical name = origin-www.cisco.com.
Name: origin-www.cisco.com
Address: 72.163.4.161
> exit
 

```

---

### Post by SecretCode on 2010-01-04
{xirb,Neytiri} Can you 
```
ping www.cisco.com
ping www.google.com
```

In Firefox, can you visit [http://72.163.4.161/](http://72.163.4.161/) (replacing 72.163.4.161 with whatever IP address responded to the ping for [www.cisco.com](www.cisco.com), if it's different?

Your DNS nameservers are working fine, but I think maybe firefox is not keeping up with them.

---

### Post by ugm6hr on 2010-01-04
I have moved Neytiri's posts to a separate thread, since it can get confusing when actively helping 2 different people:
[http://ubuntuforums.org/showthread.php?t=1372477](http://ubuntuforums.org/showthread.php?t=1372477)

---

### Post by xirb on 2010-01-04
Now it gets even more weird - what worked just before does not work now:
 
```
aomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> ^Caomaihuo@aomaihuo-desktop:~$ 
aomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> ^Caomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.google.dk]("http://www.google.dk/")
;; connection timed out; no servers could be reached
> [www.cnn.com]("http://www.cnn.com/")
Server: 194.239.134.83
Address: 194.239.134.83#53
Non-authoritative answer:
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.224.25
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.224.26
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.226.25
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.226.26
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.255.18
Name: [www.cnn.com]("http://www.cnn.com/")
Address: 157.166.255.19
 
aomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> exit
aomaihuo@aomaihuo-desktop:~$ ping 157.166.255.19
PING 157.166.255.19 (157.166.255.19) 56(84) bytes of data.
 
--- 157.166.255.19 ping statistics ---
30 packets transmitted, 0 received, 100% packet loss, time 29005ms

```
 
I can't believe it!? Any ideas?

---

### Post by Iowan on 2010-01-04
Whilst you've got the ping-er going - see if you can reach your router/gateway. Also, check some of the other "vitals": **route -n**, **ifconfig -a**, and */etc/resolv.conf*... just to see if something has changed.

---

### Post by adam814 on 2010-01-04
Hmm...I've never seen a plain ADSL modem assign a machine an address in the 192.168.0.0/16 network block.  Those I've seen assign a routable (non-private) IP to the next device, be it a router or computer.  Is there a built-in router in the ADSL modem?

Also if you can ping external IPs you at least have some of the elements of a connection.  If ICMP packets can get through, but DNS times out and web-browsing (even by address instead of hostname) won't work and using Windows you can do it all it sounds to me like you're firewalled in Ubuntu.

Can you post the output from this?
```
sudo iptables -L
```

---

### Post by xirb on 2010-01-05
The connection seems to be unstable or something - sometimes nslookups works, sometime it don't:
 
```
aomaihuo@aomaihuo-desktop:~$ nslookup
> server
Default server: 193.162.153.164
Address: 193.162.153.164#53
Default server: 194.239.134.83
Address: 194.239.134.83#53
> [www.cisco.com]("http://www.cisco.com/")                
;; connection timed out; no servers could be reached
> [www.google.com]("http://www.google.com/")
Server:  194.239.134.83
Address: 194.239.134.83#53
Non-authoritative answer:
[www.google.com]("http://www.google.com/") canonical name = [www.l.google.com]("http://www.l.google.com/").
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 74.125.79.104
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 74.125.79.99
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 74.125.79.147
> [www.yahoo.com]("http://www.yahoo.com/")
Server:  193.162.153.164
Address: 193.162.153.164#53
Non-authoritative answer:
[www.yahoo.com]("http://www.yahoo.com/") canonical name = [www.wa1.b.yahoo.com]("http://www.wa1.b.yahoo.com/").
[www.wa1.b.yahoo.com]("http://www.wa1.b.yahoo.com/") canonical name = www-real.wa1.b.yahoo.com.
Name: www-real.wa1.b.yahoo.com
Address: 87.248.113.14
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> [www.bbc.com]("http://www.bbc.com/")
Server:  194.239.134.83
Address: 194.239.134.83#53
Non-authoritative answer:
[www.bbc.com]("http://www.bbc.com/") canonical name = [www.bbc.net.uk]("http://www.bbc.net.uk/").
Name: [www.bbc.net.uk]("http://www.bbc.net.uk/")
Address: 212.58.253.68
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> [www.cisco.com]("http://www.cisco.com/")
;; connection timed out; no servers could be reached
> [www.bing.com]("http://www.bing.com/")
Server:  193.162.153.164
Address: 193.162.153.164#53
Non-authoritative answer:
[www.bing.com]("http://www.bing.com/") canonical name = search.ms.com.edgesuite.net.
search.ms.com.edgesuite.net canonical name = a134.g.akamai.net.
Name: a134.g.akamai.net
Address: 195.215.37.64
Name: a134.g.akamai.net
Address: 195.215.37.14
> [www.ask.com]("http://www.ask.com/")
;; connection timed out; no servers could be reached
> [www.about.com]("http://www.about.com/")
;; connection timed out; no servers could be reached
> [www.google.com]("http://www.google.com/")
Server:  194.239.134.83
Address: 194.239.134.83#53
Non-authoritative answer:
[www.google.com]("http://www.google.com/") canonical name = [www.l.google.com]("http://www.l.google.com/").
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.147
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.99
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.105
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.104
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.103
Name: [www.l.google.com]("http://www.l.google.com/")
Address: 66.102.13.106
> [www.ask.com]("http://www.ask.com/")
;; connection timed out; no servers could be reached
> [www.whitehouse.gov]("http://www.whitehouse.gov/")
Server:  194.239.134.83
Address: 194.239.134.83#53
Non-authoritative answer:
[www.whitehouse.gov]("http://www.whitehouse.gov/") canonical name = [www.whitehouse.gov.edgekey.net]("http://www.whitehouse.gov.edgekey.net/").
[www.whitehouse.gov.edgekey.net]("http://www.whitehouse.gov.edgekey.net/") canonical name = e2561.g.akamaiedge.net.
Name: e2561.g.akamaiedge.net
Address: 95.100.10.135
> [www.apple.com]("http://www.apple.com/")
;; connection timed out; no servers could be reached
> exit
aomaihuo@aomaihuo-desktop:~$ ping 95.100.10.135
PING 95.100.10.135 (95.100.10.135) 56(84) bytes of data.
64 bytes from 95.100.10.135: icmp_seq=2 ttl=62 time=39.9 ms
64 bytes from 95.100.10.135: icmp_seq=3 ttl=62 time=39.9 ms
64 bytes from 95.100.10.135: icmp_seq=4 ttl=62 time=39.9 ms
64 bytes from 95.100.10.135: icmp_seq=7 ttl=62 time=40.1 ms
64 bytes from 95.100.10.135: icmp_seq=8 ttl=62 time=39.9 ms
64 bytes from 95.100.10.135: icmp_seq=9 ttl=62 time=40.1 ms
64 bytes from 95.100.10.135: icmp_seq=10 ttl=62 time=40.4 ms
64 bytes from 95.100.10.135: icmp_seq=11 ttl=62 time=39.9 ms
^C
--- 95.100.10.135 ping statistics ---
11 packets transmitted, 8 received, 27% packet loss, time 10022ms
rtt min/avg/max/mdev = 39.924/40.073/40.440/0.214 ms
aomaihuo@aomaihuo-desktop:~$ ping 66.102.13.147
PING 66.102.13.147 (66.102.13.147) 56(84) bytes of data.
64 bytes from 66.102.13.147: icmp_seq=3 ttl=58 time=64.9 ms
64 bytes from 66.102.13.147: icmp_seq=4 ttl=58 time=65.3 ms
64 bytes from 66.102.13.147: icmp_seq=10 ttl=58 time=65.3 ms
64 bytes from 66.102.13.147: icmp_seq=11 ttl=58 time=65.4 ms
64 bytes from 66.102.13.147: icmp_seq=14 ttl=58 time=65.4 ms
64 bytes from 66.102.13.147: icmp_seq=16 ttl=58 time=65.2 ms
^C
--- 66.102.13.147 ping statistics ---
16 packets transmitted, 6 received, 62% packet loss, time 15037ms
rtt min/avg/max/mdev = 64.917/65.300/65.434/0.374 ms
 
 
aomaihuo@aomaihuo-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.06 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.754 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.679 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.734 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.739 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.739 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.776 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.739 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=0.737 ms
^C
--- 192.168.1.1 ping statistics ---
15 packets transmitted, 9 received, 40% packet loss, time 14007ms
rtt min/avg/max/mdev = 0.679/0.773/1.064/0.108 ms
aomaihuo@aomaihuo-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
 
aomaihuo@aomaihuo-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:c5:ae:b6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fec5:aeb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24431 (24.4 KB)  TX bytes:47558 (47.5 KB)
          Interrupt:27 Base address:0xc000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:258 (258.0 B)  TX bytes:258 (258.0 B)
 

```
 
This is the other info:
>  
resolv.conf:
# Generated by NetworkManager
domain opasia.dk
search opasia.dk
nameserver 193.162.153.164
nameserver 194.239.134.83
 
 
aomaihuo@aomaihuo-desktop:~$ sudo iptables -L
[sudo] password for aomaihuo: 
Chain INPUT (policy ACCEPT)
target prot opt source destination 
Chain FORWARD (policy ACCEPT)
target prot opt source destination 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination 


---

### Post by SecretCode on 2010-01-05
You're getting two nameservers, and both of them sometimes return responses, but I wonder if they are both reliable
```
nameserver 193.162.153.164
nameserver 194.239.134.83
```


On a working windows machine, type 
```
ipconfig /all
```- to see if windows is using the same nameservers.


Also, try this at an Ubuntu command line
```
wget http://www.ubuntu.com
```
If this works, then the problem is specific to Firefox.

---

### Post by adam814 on 2010-01-05
> aomaihuo@aomaihuo-desktop:~$ sudo iptables -L
[sudo] password for aomaihuo: 
Chain INPUT (policy ACCEPT)
target prot opt source destination 
Chain FORWARD (policy ACCEPT)
target prot opt source destination 
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
Well, that rules out firewall problems.  There are no DROP/REJECT lines in your iptables rules, so it can't be the problem.

I'm guessing it's the DNS servers you're using.  NetworkManager should have a properties tab for the connection that will let you specify static DNS (I use wicd myself and it has one).  You could set it to 8.8.4.4 to see if Google Public DNS is more reliable for you.

---

### Post by Victor_Os on 2010-01-05
There are instructions for changing the DNS to google public DNS on Ubuntu - [http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html) .

From the pings I see a lot of dropped packets, even to 192.168.1.1

> --- 192.168.1.1 ping statistics ---
15 packets transmitted, 9 received, 40% packet loss, time 14007ms
rtt min/avg/max/mdev = 0.679/0.773/1.064/0.108 ms

Could this be a hardware problem ?  

It would be great if you could try a live CD/USB and see if the problem persists. There is a utility to create a bootable USB with Ubuntu in the System->Administration->USB creator (or a similar name). You will need an empty USB drive and the Ubuntu 9.10 .iso image. There is some more info at [http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator) .

Good luck!

---

### Post by xirb on 2010-01-10
I really find this to be the most strange issue I ever have had with any computer!
Because of the many packet losses I tried another network cable. With this the internet works on my Ubuntu-PC - I can connect to any website! :P

What is really weird is that the old cable STILL works flawlessly on the Windows-PC. When pinging from there I get 0% packet loss. Somehow it must have transformed itself into a Windows-only cable!?! :confused:
Also the Ubuntu-machine does not want to connect when using the switch EVEN when it is the only thing connected (of course the cable from the router to the switch is plugged in as well), even though the above Windows-only-cable is not being used..
So I fear that there are still some weird stuff going on on the Ubuntu-machine that will cause me trouble later when it needs to be moved to other locations.. ](*,) 

Thanks for all your help guys - and please feel free to comment if you might have any inout what is really going on and if it can be helped...!

---

### Post by SecretCode on 2010-01-10
> **xirb said:**
> What is really weird is that the old cable STILL works flawlessly on the Windows-PC. When pinging from there I get 0% packet loss. Somehow it must have transformed itself into a Windows-only cable!?! :confused:

I'm sure Microsoft would love to sell a whole bunch of these cables. :wink:

The cable probably does have something up with it, but the windows drivers and/or card settings do more link-level error-correction. The linux drivers could probably be configured to do the same, but I don't know if it's worth putting much effort into (considering whether the driver developers are themselves going to put much effort into it).

The matter of not connecting using the switch is a worry, as you say. Perhaps it's something to do with 10/100/1000 speed autosensing. ... Do you want to put more effort into resolving **this**?

---

