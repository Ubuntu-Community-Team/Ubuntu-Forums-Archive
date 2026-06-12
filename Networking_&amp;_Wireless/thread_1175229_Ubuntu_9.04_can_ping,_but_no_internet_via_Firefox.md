---
title: "Ubuntu 9.04: can ping, but no internet via Firefox"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by blondeMatrix on 2009-05-31
Hi All,

I have just updated (fresh install) to Ubuntu 9.04 on my dual boot Compaq Evo W4000.  With all previous installations of Ubuntu, internet access has never been an issue.  I simply ensured my US Robotics ADSL Ethernet router (wired connection) was switched on during install, and following installation opened up Firefox and was in action.  Not this time though!

I can ping...

chris@fairfax:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (66.249.89.104) 56(84) bytes of data.
64 bytes from jp-in-f104.google.com (66.249.89.104): icmp_seq=1 ttl=242 time=209 ms
64 bytes from jp-in-f104.google.com (66.249.89.104): icmp_seq=2 ttl=242 time=209 ms
64 bytes from jp-in-f104.google.com (66.249.89.104): icmp_seq=3 ttl=242 time=207 ms
^C64 bytes from jp-in-f104.google.com (66.249.89.104): icmp_seq=4 ttl=242 time=211 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 207.919/209.545/211.156/1.222 ms


But when I start Firefox, and browse to Google, Firefox reports it is "waiting for www.google.com", and just keeps on waiting - forever.  Here is the output of "ifconfig"...

chris@fairfax:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:a5:fa:6b:df  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fefa:6bdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7242 (7.2 KB)  TX bytes:11233 (11.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr be:3b:01:70:7b:3a  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


The problem is not with my router (nor my ISP), as I am using it to post this thread (from within Windows of course).

Your help would be greatly appreciated.  If it proves too difficult to resolve, I guess I will simply have to install an earlier version of Ubuntu.

Best regards,

Chris.

---

### Post by Mazin on 2009-05-31
Can other programs access the Internet?  Like Synaptic, links, pidgin, etc.?

Do you have any proxy settings in your Firefox preferences OR your System preferences?

Those are just the diagnostics I could come up with atm.

---

### Post by blondeMatrix on 2009-05-31
Hi,

Thanks for your reply.

I attempted to add 3rd Party repositories to Synaptic, but it stuck on downloading file 1 of 17.  So I guess this means Synaptic cannot connect to the network.  Strangely, the news for Pidgin is better - it does connect, and I can message buddies.

Regarding proxy settings, I haven't touched these, so they are still set to their default: Firefox set to use "system proxy settings", and system network proxy set at "direct connection to internet".

Puzzling.

---

### Post by blondeMatrix on 2009-06-01
Hi, just a brief note to say I'm still grappling with this one...

---

### Post by ptsubin on 2009-06-01
Are you connected to Auto-Ethernet? Then using the network applet in system tray, select edit connections. There edit the current connection and if you are using DHCP, in IPv4 settings, select DHCP addresses only and manually set your gateway as you see in windows. This may work, as it worked for me.

---

### Post by blondeMatrix on 2009-06-01
I tried both "DHCP - Addresses Only" and "Manual", to no avail.  Why would I be able to ping [www.google.com](www.google.com) but not browse there via Firefox?  Is the problem with Firefox or the network connection?

Frustrating.

---

### Post by superprash2003 on 2009-06-01
post output of sudo iptables -L . in firefox are you able to open [http://209.85.171.100](http://209.85.171.100)

---

### Post by blondeMatrix on 2009-06-03
> **superprash2003 said:**
> post output of sudo iptables -L . in firefox are you able to open [http://209.85.171.100](http://209.85.171.100)

Hi, thank you for your reply.  As requested...

chris@fairfax:~$ sudo iptables -L
[sudo] password for chris: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Also, no, Firefox hangs in "waiting" mode for that IP address too.

Regards,

Chris.

---

### Post by jonobr on 2009-06-03
it seems odd that your resolving the google address but not showing the page.
Im wondering if this is not just stored in your router or access point.

I would recommended pinging another address you have not used yet which responds.

eg 
ping pingplotter.com
PING pingplotter.com (216.92.151.75) 56(84) bytes of data.
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=1 ttl=47 time=106 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=2 ttl=47 time=107 ms


If that works and you still cant get the page to load, 
try using a text based browser like w3m,
that should be on your system,
you should see the attached from w3m google.com


If you dont see that, then I would think its related to firewall as superprash indicates.
If you see whats in the graphic, then maybe try a different browser?
eg seamonkey or epiphany ?

---

### Post by blondeMatrix on 2009-06-03
> **jonobr said:**
> it seems odd that your resolving the google address but not showing the page.
Im wondering if this is not just stored in your router or access point.

I would recommended pinging another address you have not used yet which responds.

eg 
ping pingplotter.com
PING pingplotter.com (216.92.151.75) 56(84) bytes of data.
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=1 ttl=47 time=106 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=2 ttl=47 time=107 ms


If that works and you still cant get the page to load, 
try using a text based browser like w3m,
that should be on your system,
you should see the attached from w3m google.com


If you dont see that, then I would think its related to firewall as superprash indicates.
If you see whats in the graphic, then maybe try a different browser?
eg seamonkey or epiphany ?

Hi, thanks for your help.  I pinged pingplotter.com...

chris@fairfax:~$ ping pingplotter.com
PING pingplotter.com (216.92.151.75) 56(84) bytes of data.
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=1 ttl=53 time=283 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=2 ttl=53 time=286 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=3 ttl=53 time=285 ms
64 bytes from pingplotter.com (216.92.151.75): icmp_seq=4 ttl=53 time=285 ms
^C
--- pingplotter.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 283.145/285.332/286.805/1.349 ms


I then had a crack at browsing via w3m...

chris@fairfax:~$ w3m [http://www.google.com](http://www.google.com)
[www.google.com](www.google.com) contacted. Waiting for reply...
w3m: Can't load [http://www.google.com](http://www.google.com).

It too hangs in "waiting" mode, until I Ctrl-C.  Interestingly, I get the same response when attempting even to browse my US Robotics ADSL router...

chris@fairfax:~$ w3m [http://192.168.1.1](http://192.168.1.1)
192.168.1.1 contacted. Waiting for reply...
w3m: Can't load [http://192.168.1.1](http://192.168.1.1).

So, I think we've established the following...

  1) The problem is not with Firefox, as w3m encounters the same problem.
  2) The problem is not with the router.  I'm using the very same router from the same PC via the same ethernet card to compile this message (within Windows).  Also, the router worked fine with Ubuntu 6.10 last week, and the router hasn't been altered since then.

I had a look for the Ubuntu OS firewall, but couldn't find it listed on any of the Gnome menus.  At least I think we are making progress in identifying the cause of this problem.

Regards,

Chris.

---

### Post by blondeMatrix on 2009-06-04
Hi, just a brief note to say I'm still grappling with this one...

---

### Post by markvdm on 2009-06-04
I'm having the same issue. I thought it was related to ICS on my Windows Mobile, but I too can ping any site and get a reply, but pages just say waiting when trying to load. There are certain pages I can see.

---

### Post by jonobr on 2009-06-04
> So, I think we've established the following...

1) The problem is not with Firefox, as w3m encounters the same problem.
2) The problem is not with the router. I'm using the very same router from the same PC via the same ethernet card to compile this message (within Windows). Also, the router worked fine with Ubuntu 6.10 last week, and the router hasn't been altered since then.

I had a look for the Ubuntu OS firewall, but couldn't find it listed on any of the Gnome menus. At least I think we are making progress in identifying the cause of this problem.

I think your correct with all of this above.

Could you try 

```
sudo tcpdump -vvv port 80
```
and see if that gives any indication of where your packets are going and what they are doing?

I will say , this is a noodle scratcher.....

---

### Post by blondeMatrix on 2009-06-04
> **jonobr said:**
> Could you try 

```
sudo tcpdump -vvv port 80
```
and see if that gives any indication of where your packets are going and what they are doing?

Hi, as requested...

```

chris@fairfax:~$ sudo tcpdump -vvv port 80
[sudo] password for chris: 
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

Which didn't seem to tell me much, so I ran it again while I attempted to browse [www.google.com](www.google.com) via Firefox...

```

chris@fairfax:~$ sudo tcpdump -vvv port 80
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
09:56:28.495409 IP (tos 0x0, ttl 64, id 38344, offset 0, flags [DF], proto TCP (6), length 60) fairfax.local.60025 > jujube.canonical.com.www: S, cksum 0xb42e (correct), 3231178804:3231178804(0) win 5840 <mss 1460,sackOK,timestamp 4294931964 0,nop,wscale 5>
09:56:28.562809 IP (tos 0x0, ttl 61, id 3749, offset 0, flags [none], proto TCP (6), length 60) jujube.canonical.com.www > fairfax.local.60025: S, cksum 0x1138 (correct), 691204276:691204276(0) ack 3231178805 win 65535 <mss 1460,nop,wscale 0,nop,nop,timestamp 3711644 4294931964>
09:56:28.562888 IP (tos 0x0, ttl 64, id 38345, offset 0, flags [DF], proto TCP (6), length 52) fairfax.local.60025 > jujube.canonical.com.www: ., cksum 0x3c34 (correct), 1:1(0) ack 1 win 183 <nop,nop,timestamp 4294931981 3711644>
09:56:28.563058 IP (tos 0x0, ttl 64, id 38346, offset 0, flags [DF], proto TCP (6), length 443) fairfax.local.60025 > jujube.canonical.com.www: P 1:392(391) ack 1 win 183 <nop,nop,timestamp 4294931981 3711644>
09:56:28.734352 IP (tos 0x0, ttl 61, id 5872, offset 0, flags [none], proto TCP (6), length 52) jujube.canonical.com.www > fairfax.local.60025: ., cksum 0x3b63 (correct), 1:1(0) ack 392 win 65535 <nop,nop,timestamp 3711645 4294931981>
09:56:32.376494 IP (tos 0x0, ttl 64, id 38347, offset 0, flags [DF], proto TCP (6), length 52) fairfax.local.60025 > jujube.canonical.com.www: F, cksum 0x36f1 (correct), 392:392(0) ack 1 win 183 <nop,nop,timestamp 4294932935 3711645>
09:56:32.441249 IP (tos 0x0, ttl 61, id 51017, offset 0, flags [none], proto TCP (6), length 52) jujube.canonical.com.www > fairfax.local.60025: ., cksum 0x353d (correct), 613:613(0) ack 393 win 65535 <nop,nop,timestamp 3711652 4294932935>
09:56:33.383907 IP (tos 0x0, ttl 64, id 45638, offset 0, flags [DF], proto TCP (6), length 60) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: S, cksum 0xb6f5 (correct), 3301296260:3301296260(0) win 5840 <mss 1460,sackOK,timestamp 4294933186 0,nop,wscale 5>
09:56:33.582161 IP (tos 0x0, ttl 52, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40673: S, cksum 0x06d7 (correct), 3895956156:3895956156(0) ack 3301296261 win 5840 <mss 1460>
09:56:33.582237 IP (tos 0x0, ttl 64, id 45639, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0x1e94 (correct), 1:1(0) ack 1 win 5840
09:56:33.582670 IP (tos 0x0, ttl 64, id 45640, offset 0, flags [DF], proto TCP (6), length 483) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: P 1:444(443) ack 1 win 5840
09:56:33.810011 IP (tos 0x0, ttl 52, id 49803, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40673: ., cksum 0x1a89 (correct), 1:1(0) ack 444 win 6432
09:56:33.810987 IP (tos 0x0, ttl 52, id 49804, offset 0, flags [DF], proto TCP (6), length 699) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40673: P 1:660(659) ack 444 win 6432
09:56:33.811026 IP (tos 0x0, ttl 64, id 45641, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0x1758 (correct), 444:444(0) ack 660 win 6590
09:56:33.886768 IP (tos 0x0, ttl 64, id 19868, offset 0, flags [DF], proto TCP (6), length 60) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: S, cksum 0x479d (correct), 3309778652:3309778652(0) win 5840 <mss 1460,sackOK,timestamp 4294933312 0,nop,wscale 5>
09:56:34.083165 IP (tos 0x0, ttl 52, id 0, offset 0, flags [DF], proto TCP (6), length 44) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40674: S, cksum 0x999a (correct), 2551767357:2551767357(0) ack 3309778653 win 5840 <mss 1460>
09:56:34.083236 IP (tos 0x0, ttl 64, id 19869, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0xb157 (correct), 1:1(0) ack 1 win 5840
09:56:34.083355 IP (tos 0x0, ttl 64, id 19870, offset 0, flags [DF], proto TCP (6), length 449) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: P 1:410(409) ack 1 win 5840
09:56:34.307152 IP (tos 0x0, ttl 52, id 3541, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40674: ., cksum 0xad6e (correct), 1:1(0) ack 410 win 6432
09:56:34.311242 IP (tos 0x0, ttl 52, id 3542, offset 0, flags [DF], proto TCP (6), length 741) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40674: P 1:702(701) ack 410 win 6432
09:56:34.311283 IP (tos 0x0, ttl 64, id 19871, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0xa86f (correct), 410:410(0) ack 702 win 7010
09:56:34.403740 IP (tos 0x0, ttl 64, id 15746, offset 0, flags [DF], proto TCP (6), length 60) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: S, cksum 0x5ab2 (correct), 3318957635:3318957635(0) win 5840 <mss 1460,sackOK,timestamp 4294933441 0,nop,wscale 5>
09:56:34.471164 IP (tos 0x0, ttl 61, id 35474, offset 0, flags [none], proto TCP (6), length 60) nol-vip02.cwwtf.bbc.co.uk.www > fairfax.local.54757: S, cksum 0x4e2a (correct), 4281931109:4281931109(0) ack 3318957636 win 65535 <mss 1460,nop,wscale 0,nop,nop,timestamp 12456176 4294933441>
09:56:34.471245 IP (tos 0x0, ttl 64, id 15747, offset 0, flags [DF], proto TCP (6), length 52) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: ., cksum 0x7926 (correct), 1:1(0) ack 1 win 183 <nop,nop,timestamp 4294933458 12456176>
09:56:34.471387 IP (tos 0x0, ttl 64, id 15748, offset 0, flags [DF], proto TCP (6), length 485) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: P 1:434(433) ack 1 win 183 <nop,nop,timestamp 4294933458 12456176>
09:56:34.735925 IP (tos 0x0, ttl 64, id 15749, offset 0, flags [DF], proto TCP (6), length 485) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: P 1:434(433) ack 1 win 183 <nop,nop,timestamp 4294933525 12456176>
09:56:35.271933 IP (tos 0x0, ttl 64, id 15750, offset 0, flags [DF], proto TCP (6), length 485) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: P 1:434(433) ack 1 win 183 <nop,nop,timestamp 4294933659 12456176>
09:56:36.343921 IP (tos 0x0, ttl 64, id 15751, offset 0, flags [DF], proto TCP (6), length 485) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: P 1:434(433) ack 1 win 183 <nop,nop,timestamp 4294933927 12456176>
09:56:38.487923 IP (tos 0x0, ttl 64, id 15752, offset 0, flags [DF], proto TCP (6), length 485) fairfax.local.54757 > nol-vip02.cwwtf.bbc.co.uk.www: P 1:434(433) ack 1 win 183 <nop,nop,timestamp 4294934463 12456176>
09:56:38.576978 IP (tos 0x0, ttl 61, id 20843, offset 0, flags [none], proto TCP (6), length 52) nol-vip02.cwwtf.bbc.co.uk.www > fairfax.local.54757: ., cksum 0x5d7f (correct), 5817:5817(0) ack 434 win 65535 <nop,nop,timestamp 12456184 4294934463>
09:56:43.591496 IP (tos 0x0, ttl 64, id 27317, offset 0, flags [DF], proto TCP (6), length 60) fairfax.local.52529 > cf-in-f103.google.com.www: S, cksum 0x029f (correct), 3468160527:3468160527(0) win 5840 <mss 1460,sackOK,timestamp 4294935738 0,nop,wscale 5>
09:56:43.820733 IP (tos 0x0, ttl 53, id 14709, offset 0, flags [none], proto TCP (6), length 60) cf-in-f103.google.com.www > fairfax.local.52529: S, cksum 0x3fc5 (correct), 1899418757:1899418757(0) ack 3468160528 win 5672 <mss 1430,sackOK,timestamp 1120353034 4294935738,nop,wscale 6>
09:56:43.820811 IP (tos 0x0, ttl 64, id 27318, offset 0, flags [DF], proto TCP (6), length 52) fairfax.local.52529 > cf-in-f103.google.com.www: ., cksum 0x83a9 (correct), 1:1(0) ack 1 win 183 <nop,nop,timestamp 4294935796 1120353034>
09:56:43.821261 IP (tos 0x0, ttl 64, id 27319, offset 0, flags [DF], proto TCP (6), length 435) fairfax.local.52529 > cf-in-f103.google.com.www: P 1:384(383) ack 1 win 183 <nop,nop,timestamp 4294935796 1120353034>
09:56:44.076739 IP (tos 0x0, ttl 53, id 14710, offset 0, flags [none], proto TCP (6), length 52) cf-in-f103.google.com.www > fairfax.local.52529: ., cksum 0x8177 (correct), 1:1(0) ack 384 win 106 <nop,nop,timestamp 1120353290 4294935796>
09:56:44.510687 IP (tos 0x0, ttl 52, id 3543, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40674: F, cksum 0xaab0 (correct), 702:702(0) ack 410 win 6432
09:56:44.547929 IP (tos 0x0, ttl 64, id 19872, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0xa86e (correct), 410:410(0) ack 703 win 7010
09:56:44.563641 IP (tos 0x0, ttl 52, id 49805, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40673: F, cksum 0x17f5 (correct), 660:660(0) ack 444 win 6432
09:56:44.599911 IP (tos 0x0, ttl 64, id 45642, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: ., cksum 0x1757 (correct), 444:444(0) ack 661 win 6590
09:56:55.752696 IP (tos 0x0, ttl 64, id 19873, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40674 > fxfeeds.acelb.sj.mozilla.com.www: F, cksum 0xa86d (correct), 410:410(0) ack 703 win 7010
09:56:55.752763 IP (tos 0x0, ttl 64, id 45643, offset 0, flags [DF], proto TCP (6), length 40) fairfax.local.40673 > fxfeeds.acelb.sj.mozilla.com.www: F, cksum 0x1756 (correct), 444:444(0) ack 661 win 6590
09:56:55.948196 IP (tos 0x0, ttl 52, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40674: ., cksum 0xaaaf (correct), 703:703(0) ack 411 win 6432
09:56:55.954197 IP (tos 0x0, ttl 52, id 0, offset 0, flags [DF], proto TCP (6), length 40) fxfeeds.acelb.sj.mozilla.com.www > fairfax.local.40673: ., cksum 0x17f4 (correct), 661:661(0) ack 445 win 6432
^C
43 packets captured
43 packets received by filter
0 packets dropped by kernel

```

There's some rather odd looking URLs in there, if that is what they are.  Like "jujube.canonical.com.www" and "fxfeeds.acelb.sj.mozilla.com.www".  But no sign of "www.google.com".

Best regards,

Chris.

---

### Post by blondeMatrix on 2009-06-04
Actually, I just spotted "cf-in-f103.google.com.www" towards the bottom.

Chris.

---

### Post by Claus7 on 2009-06-04
Hello,

i)disable ipv6 from firefox. I had exactly the same problem and I was not able to have internet. So, check this out and see what you get.
ii)if this does not work, then did you have before updating any problem? I did have and I solved it with changing my dns provider. 

May this link will help you about it:
[http://ubuntuforums.org/showthread.php?t=1137127](http://ubuntuforums.org/showthread.php?t=1137127)

Regards!

---

### Post by blondeMatrix on 2009-06-04
> **Claus7 said:**
> Hello,

i)disable ipv6 from firefox. I had exactly the same problem and I was not able to have internet. So, check this out and see what you get.
ii)if this does not work, then did you have before updating any problem? I did have and I solved it with changing my dns provider. 

May this link will help you about it:
[http://ubuntuforums.org/showthread.php?t=1137127](http://ubuntuforums.org/showthread.php?t=1137127)

Regards!

Hi, thanks for your help.  I followed the procedure to disable ipv6, as suggested...

chris@fairfax:~$ uname -r
2.6.29-02062903-generic

chris@fairfax:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:a5:fa:6b:df  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6499 (6.4 KB)  TX bytes:10947 (10.9 KB)

Which it seems to have done but, unfortunately, it hasn't solved my problem - Firefox and w3m still hang in "waiting" mode.

Perhaps I'll have a crack later at manually setting an alternative DNS provider.

Chris.

---

### Post by Claus7 on 2009-06-05
Hello,

you do not have to have a crack (about the dns provider that is). From the link I gave you, there is another link that points exactly to the place where you can change your dns provider, to an open one, without needing to have a crack. Check it out because it is easy and it really "transformed" my connection in every ubuntu distro.

If this does not work, at least it is very easy to convert back your original options.

I'm telling you all these because I was also able to ping, yet not been able to open web pages.

Regards!

---

### Post by jonobr on 2009-06-05
Hey,

Thanks for the traces, I should have mentioned that you need to open firefox to see the traffic.... Sorry :-(

WHat that trace does is it shows the packets leaving and returning using port 80, which is the default port for web pages etc

What the trace does show as Claus 7 points out is traffic is being issued and received from Google and its not be interpreted or sent by the browser.
I recommend following Claus 7 recommendations and elimnating that as a possibility

---

### Post by UBSec on 2009-06-05
Hi,

Do you use any proxy ? To check it :

echo $http_proxy 

> If yes you should put the right settings in firefox and for the command line

from the command line enter:

export http_proxy="http://my_proxy_address:my_proxy_port" 

from firefox : can you check please the settings and tell us what do you get ?

edit/preferences/advanced/network/settings 

> If you dont have a proxy choose no proxy 

> Can u try also
  wget ubuntu.com (u may get the same results as w3m , but let's try, it does not cost anything)

> Next show the ouput of your routing table 
   netstat -rn 

> To be sure about the routes taken by your paquets try
   ping -R ubuntu.com

> Also check your resolver (if you can ping a site with its name, it may work properly, but let's just perform some checks to be sure )
   nslookup ubuntu.com

UBSec

---

### Post by blondeMatrix on 2009-06-05
Hi **Claus7** and **jonobr**.  As suggested, I updated my DNS...
```

	//Changed DNS from...
	chris@fairfax:~$ cat /etc/resolv.conf
	# Generated by NetworkManager
	nameserver 192.168.1.1

	//To...
	chris@fairfax:~$ cat /etc/resolv.conf
	# Generated by NetworkManager
	nameserver 208.67.222.222
	nameserver 208.67.220.220

```
But it hasn't fixed the problem, sorry to say.


Hi **UBSec**, I've performed each of your requests (as indented, with comments)...
```

Do you use any proxy ? To check it :

echo $http_proxy

	chris@fairfax:~$ echo $http_proxy

	chris@fairfax:~$ 
	//I guess this means no

> If yes you should put the right settings in firefox and for the command line

from the command line enter:

export http_proxy="http://my_proxy_address:my_proxy_port"

from firefox : can you check please the settings and tell us what do you get ?

edit/preferences/advanced/network/settings

> If you dont have a proxy choose no proxy

	***Done**

> Can u try also
wget ubuntu.com (u may get the same results as w3m , but let's try, it does not cost anything)

	chris@fairfax:~$ wget ubuntu.com
	--2009-06-06 13:39:59--  [http://ubuntu.com/](http://ubuntu.com/)
	Resolving ubuntu.com... 91.189.94.156
	Connecting to ubuntu.com|91.189.94.156|:80... connected.
	HTTP request sent, awaiting response... ^C
	//No response, so Ctrl-C

> Next show the ouput of your routing table
netstat -rn

	chris@fairfax:~$ netstat -rn
	Kernel IP routing table
	Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
	192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
	169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
	0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

> To be sure about the routes taken by your paquets try
ping -R ubuntu.com

	chris@fairfax:~$ ping -R ubuntu.com
	PING ubuntu.com (91.189.94.156) 56(124) bytes of data.
	^C
	--- ubuntu.com ping statistics ---
	10 packets transmitted, 0 received, 100% packet loss, time 8999ms

	//But can ping Google...
	chris@fairfax:~$ ping [www.google.com](www.google.com)
	PING google.navigation.opendns.com (208.67.219.230) 56(84) bytes of data.
	64 bytes from google.navigation.opendns.com (208.67.219.230): icmp_seq=1 ttl=50 time=206 ms
	64 bytes from google.navigation.opendns.com (208.67.219.230): icmp_seq=2 ttl=50 time=205 ms
	64 bytes from google.navigation.opendns.com (208.67.219.230): icmp_seq=3 ttl=50 time=204 ms
	^C
	--- google.navigation.opendns.com ping statistics ---
	4 packets transmitted, 3 received, 25% packet loss, time 3003ms
	rtt min/avg/max/mdev = 204.302/205.350/206.594/1.080 ms

> Also check your resolver (if you can ping a site with its name, it may work properly, but let's just perform some checks to be sure )
nslookup ubuntu.com

	chris@fairfax:~$ nslookup ubuntu.com
	Server:		208.67.222.222
	Address:	208.67.222.222#53

	Non-authoritative answer:
	Name:	ubuntu.com
	Address: 91.189.94.156

UBSec

```
I hope this gives you some clues.  I appreciate your help.

Regards,

Chris.

---

### Post by Claus7 on 2009-06-06
Hello,

so it seems that it is not a proxy problem either. There is a long time since I configured my network. Do you think that it might be the problem the inet addr: 192.168.1.3 instead of being 192.168.1.2?
edit:Looking more I do not think that this is a problem either.

I compared this with my configuration and I see this difference. 

edit:after you changed the dns settings did you try to restart your network?

edit: Do you mind using some other browser just to see what will happen?

Regards!

---

### Post by blondeMatrix on 2009-06-08
Hi, yes, after I altered the DNS I did restart my network.  Also, it is the same for all browsers I've tried.

Chris.

---

### Post by UBSec on 2009-06-08
Hi,

We've a strange problem here. Let's try other stuffs please .


> can u use the option -R with ping. It records the routes that your packets take.

ping -R [www.google.com]("http://www.google.com")


> sorry , but can you try again tcpdump plus the option -n (do not resolve the IP) and try to browse via firefox

tcpdump -vvv -n 

> Is 192.168.1.1 your gateway ? Is it a router, modem or another host ? Does it have a firewall ? 

ping 192.168.1.1


Your ip address is 192.168.0.3, isnt it ? Have u sat it statically or u got it from a DHCP ? 

can you post your /etc/network/interfaces ? 

> can u show all your iptables tables ? nat , mangle, filter ?

  iptables -L -t nat 
  iptables -L -t filter
  iptables -L -t mangle

Then try to flush iptables with :

 iptables -F 
  
then try to connect the net 

> another solution is to use a 9.04 (desktop) livecd to check if u will have the same trouble .

UBSec

---

### Post by 8yun on 2009-07-02
Hello Guys,

any news of this problem. I have the actually the same problem. Is it because the network card driver doggy? My laptop is ThinkPad T60.

1. I even could not open my router's administrative webpage via firefox or w3m. 

2. Ping to any website is ok.

3. Wireshark capture a lot of packet retransmission messages and bad checksum. Please see attachment:
[IMG]http://ipvpiq.blu.livefilestore.com/y1pvZ4lPSMb2OvNeOYrPaVJ5Lp1sFWKkZRs679X9s7xNmFWRKaOUhrMDMngz_9T4iENHp9fbSOdrbiUAoNsHbu0KPO6ZqnRy6oh/ubuntu904.png[/IMG]
My laptop ip: 192.168.30.3
Router ip: 192.168.30.1

4 network card information:
roger@roger-laptop:~$ sudo ethtool eth0
[sudo] password for roger: 
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

Thanks.

---

### Post by blondeMatrix on 2009-07-04
Hi UBSec (and others),

I have done as you requested (indented)...
```
Hi,

We've a strange problem here. Let's try other stuffs please .


> can u use the option -R with ping. It records the routes that your packets take.

ping -R www.google.com

	chris@fairfax:~$ ping -R www.google.com
	PING www.l.google.com (74.125.19.104) 56(124) bytes of data.
	64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=1 ttl=53 time=258 ms
	64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=2 ttl=53 time=249 ms
	64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=3 ttl=53 time=228 ms
	64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=4 ttl=53 time=235 ms
	^C
	--- www.l.google.com ping statistics ---
	4 packets transmitted, 4 received, 0% packet loss, time 3003ms
	rtt min/avg/max/mdev = 228.968/243.275/258.282/11.480 ms


> sorry , but can you try again tcpdump plus the option -n (do not resolve the IP) and try to browse via firefox

	chris@fairfax:~$ sudo tcpdump -vvv -n
	tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
	15:41:25.367794 IP (tos 0x0, ttl 64, id 41017, offset 0, flags [DF], proto TCP (6), length 60) 192.168.1.3.35946 > 74.125.19.147.80: S, cksum 0x5391 (correct), 1583683967:1583683967(0) win 5840 <mss 1460,sackOK,timestamp 47430 0,nop,wscale 5>
	15:41:25.564505 IP (tos 0x0, ttl 53, id 606, offset 0, flags [none], proto TCP (6), length 60) 74.125.19.147.80 > 192.168.1.3.35946: S, cksum 0x3e13 (correct), 2484944556:2484944556(0) ack 1583683968 win 5672 <mss 1430,sackOK,timestamp 3649989081 47430,nop,wscale 6>
	15:41:25.564565 IP (tos 0x0, ttl 64, id 41018, offset 0, flags [DF], proto TCP (6), length 52) 192.168.1.3.35946 > 74.125.19.147.80: ., cksum 0x8200 (correct), 1:1(0) ack 1 win 183 <nop,nop,timestamp 47479 3649989081>
	15:41:25.565047 IP (tos 0x0, ttl 64, id 41019, offset 0, flags [DF], proto TCP (6), length 435) 192.168.1.3.35946 > 74.125.19.147.80: P 1:384(383) ack 1 win 183 <nop,nop,timestamp 47480 3649989081>
	15:41:25.788989 IP (tos 0x0, ttl 53, id 607, offset 0, flags [none], proto TCP (6), length 52) 74.125.19.147.80 > 192.168.1.3.35946: ., cksum 0x7fef (correct), 1:1(0) ack 384 win 106 <nop,nop,timestamp 3649989303 47480>
	15:42:20.935958 IP (tos 0x0, ttl 64, id 41020, offset 0, flags [DF], proto TCP (6), length 52) 192.168.1.3.35946 > 74.125.19.147.80: F, cksum 0x498f (correct), 384:384(0) ack 1 win 183 <nop,nop,timestamp 61322 3649989303>
	15:42:21.928890 IP (tos 0x0, ttl 64, id 41021, offset 0, flags [DF], proto TCP (6), length 52) 192.168.1.3.35946 > 74.125.19.147.80: F, cksum 0x4896 (correct), 384:384(0) ack 1 win 183 <nop,nop,timestamp 61571 3649989303>
	15:42:22.125724 IP (tos 0x0, ttl 53, id 618, offset 0, flags [none], proto TCP (6), length 40) 74.125.19.147.80 > 192.168.1.3.35946: R, cksum 0x30a0 (correct), 2484944557:2484944557(0) win 0
	15:42:25.932893 arp who-has 192.168.1.1 tell 192.168.1.3
	15:42:25.933616 arp reply 192.168.1.1 is-at 00:c0:49:c0:d0:12
	^C
	10 packets captured
	10 packets received by filter
	0 packets dropped by kernel

> Is 192.168.1.1 your gateway ? Is it a router, modem or another host ? Does it have a firewall ?

ping 192.168.1.1

	//It is a US Robotics ADSL Ethernet/USB Router
	//It has a firewall, but no changes have been made to it since running Ubuntu 6.10, and
	//I can access the internet when I boot into Windows.
	chris@fairfax:~$ ping 192.168.1.1
	PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
	64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=2.96 ms
	64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=1.50 ms
	64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=1.74 ms
	64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=1.55 ms
	^C
	--- 192.168.1.1 ping statistics ---
	4 packets transmitted, 4 received, 0% packet loss, time 3004ms
	rtt min/avg/max/mdev = 1.503/1.938/2.960/0.597 ms

Your ip address is 192.168.0.3, isnt it ? Have u sat it statically or u got it from a DHCP ?

	//eth0 is set to Automatic (DHCP)

can you post your /etc/network/interfaces ?

	auto lo
	iface lo inet loopback

> can u show all your iptables tables ? nat , mangle, filter ?

iptables -L -t nat

	chris@fairfax:~$ sudo iptables -L -t nat
	Chain PREROUTING (policy ACCEPT)
	target     prot opt source               destination         

	Chain POSTROUTING (policy ACCEPT)
	target     prot opt source               destination         

	Chain OUTPUT (policy ACCEPT)
	target     prot opt source               destination      

iptables -L -t filter

	chris@fairfax:~$ sudo iptables -L -t filter
	Chain INPUT (policy ACCEPT)
	target     prot opt source               destination         

	Chain FORWARD (policy ACCEPT)
	target     prot opt source               destination         

	Chain OUTPUT (policy ACCEPT)
	target     prot opt source               destination    

iptables -L -t mangle

	chris@fairfax:~$ sudo iptables -L -t mangle
	Chain PREROUTING (policy ACCEPT)
	target     prot opt source               destination         

	Chain INPUT (policy ACCEPT)
	target     prot opt source               destination         

	Chain FORWARD (policy ACCEPT)
	target     prot opt source               destination         

	Chain OUTPUT (policy ACCEPT)
	target     prot opt source               destination         

	Chain POSTROUTING (policy ACCEPT)
	target     prot opt source               destination       

Then try to flush iptables with :

iptables -F

then try to connect the net

	//Done, but Firefox still stuck in "Waiting" mode

> another solution is to use a 9.04 (desktop) livecd to check if u will have the same trouble .

UBSec
```

---

### Post by blondeMatrix on 2009-07-04
> **8yun said:**
> Hello Guys,

any news of this problem. I have the actually the same problem. Is it because the network card driver doggy? My laptop is ThinkPad T60.

1. I even could not open my router's administrative webpage via firefox or w3m. 

2. Ping to any website is ok.

I too wonder whether the Ubuntu 9 driver for my network card is dodgy.  As all worked fine on Ubuntu 6.

Likewise, I can't even "open my router's administrative webpage via firefox".

Chris.

---

### Post by Jarkycat on 2009-07-05
Hello,

This sounds like the exact issue (ping and resolve with no problems, but fail to receive anything else) I had with my ethernet connection, though not sure if this solution is network chipset specific.  It was a SIS190 ethernet device that had a problem with the default MTU in ubuntu.

Let's try temporarily changing your MTU and see if it works.


At the termimal, type in:
**sudo ifconfig eth0 mtu 1492**

then give Firefox a try again.



Also, it would also be helpful to know the exact chipset of your ethernet device... unless its missed it somehow in this thread.

At the terminal,type in:
**lspci | grep Ethernet**

and post the contents for us.

---

### Post by blondeMatrix on 2009-07-09
> **Jarkycat said:**
> Hello,

This sounds like the exact issue (ping and resolve with no problems, but fail to receive anything else) I had with my ethernet connection, though not sure if this solution is network chipset specific.  It was a SIS190 ethernet device that had a problem with the default MTU in ubuntu.

Let's try temporarily changing your MTU and see if it works.


At the termimal, type in:
**sudo ifconfig eth0 mtu 1492**

then give Firefox a try again.

No, this didn't work either sorry

> 
Also, it would also be helpful to know the exact chipset of your ethernet device... unless its missed it somehow in this thread.

At the terminal,type in:
**lspci | grep Ethernet**

and post the contents for us.

chris@fairfax:~$ lspci | grep Ethernet
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

I hope this helps.  Thank you for your help.

Chris.

---

### Post by Brandon Williams on 2009-07-09
I've heard that some network hardware doesn't handle TCP window scaling very well for window scale values greater than 2. Try turning off window scaling.

```
sudo sysctl -w net.ipv4.tcp_window_scaling=0
```

I doubt this will be it because it just doesn't look like that kind of problem, but it's worth a try.

The things that's really strange here is that the server is acknowledging that it received the request, but it never actually sends a response, which means that it isn't a routing problem. This is illustrated by the sequence number in the server's FIN. The only explanation that I can think of for the server receiving the request but never sending a response is that the responding server is in fact a proxy of some sort. And yet, you say that you aren't using a proxy.

---

### Post by ismoke101 on 2009-07-16
hi i also have the same problem, the network icon is not even functioning as it use to be, when i entered a webpage and close ny router, network icon really still looks connected. frustrated with this one grrrrrr

---

### Post by ismoke101 on 2009-07-20
is it a dns problem or about the ipvs thing,...

---

### Post by blondeMatrix on 2009-07-24
Despite me not being the only one to encounter this problem, finding a solution seems to have drawn a blank.  Never mind.  Thank you everyone for your help.

I've reverted back to Windows (on the exact same hardware), but will perhaps give the next release of Ubuntu a whirl - before giving up on Ubuntu completely.

Regards,

Chris.

---

### Post by thai cat on 2009-07-26
I have the same problem, but it seems there are no answers for it. Any distro with 9.04: Mint, Ubuntu and EEEbuntu on two different computers, I cannot view certain websites such as Yahoo.com for example and MSN on Pidgin won't connect. No problems with Windows 7 (why is Windows so easy?). Nor any problems with 8.04. For example Mint 6, no probs, but Mint7, forget it. I am on a NTT fiber optic PPoE connection in Japan. Also ubuntu 9.04 has a hard time with this connection. I often have to delete the connection and create a new one for it to reconnect. Frustrating. On a regular ADSL line at work I have no problems connecting to anything. For two months I have tried to solve this, but can't seem to find an answer. These "little problems" are what drives people away from Linux and back to Windows. Or at least back to 8.04 :confused:

---

### Post by ismoke101 on 2009-07-26
i found a thread saying something about ipv6 and dhcp. i think its not on the actual kernel of linux but i think it is outside linux, (correct me if im wrong :D) im not using my ubuntu for almost a 3 weeks and it sucks using windows, i miss my ubuntu :-#

---

### Post by spear1bearer on 2009-09-19
I used to have exactly the same problem as blondeMatrix: all the symptoms were the same, even the pidgin behavior was the same. Then I found a solution here: 

[http://www.snailbook.com/faq/mtu-mismatch.auto.html](http://www.snailbook.com/faq/mtu-mismatch.auto.html)

This is pretty much what Jarkycat suggested, but he didn't explain his choice of 1492. So, perhaps, MTU=1492 is not a correct value for you. To see what MTU you are using on linux, look through the output of ifconfig.
For me, switching from mtu=576 to mtu=1500 did the trick:

```
sudo ifconfig eth0 mtu 1500

```(where eth0 is the name of your network card)

The most important thing is to match the MTU sizes on your network cards, routers etc.
You can test the "bottleneck" MTU on the path from your computer to Goggle by pinging with this command:

```
ping www.google.com -c 4 -M do -s 1472

```The last number, plus 28, is the size of the packets being sent out. So, -s 1472 corresponds to a 1500-byte packet. Set it to a large value and work your way down until you stop getting error messages saying ```
Frag needed and DF set
``` Then add 28 and assign that value as your network card's MTU.

---

### Post by upekshapriya on 2009-09-23
I had exactly the same problem in Xubuntu 9.04 and discovered what was causing it when I upgraded to 9.10 alpha (in the hope of solving the problem) by using "update-manager -d" - [http://www.ubuntu.com/testing/karmic/alpha2#Upgrading%20from%20Ubuntu%209.04](http://www.ubuntu.com/testing/karmic/alpha2#Upgrading%20from%20Ubuntu%209.04). 

In 9.10 there is no usplash screen to hide the startup messages and I saw a firewall called firehol was being run. I worked out how to stop it running ('firehol stop' I think it was) and hey presto I could now surf with Firefox.

I could find no documentation on the Ubuntu documentation pages [https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=firehol&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=firehol&sa=Search) mentioning that it is run by default, which was strange. 

(I didn't find the firehol instructions easy to understand and ended up uninstalling it as I don't really need a firewall - being behind NAT.)

---

### Post by bogo-mips on 2009-12-20
For what its worth - I had the same issue a while ago via a pppoe connection.

In the end, setting the mtu on _ppp0_ to 576 (not on eth0. it is still sitting on the 1500 default), fixed it for me. (figures in the 1400 had not improvement)

Hope this can help someone later.
[FONT=Courier New]
ifconfig ppp0 mtu 576[/FONT]

---

### Post by ivboy on 2010-01-22
Hi
I have the opposite problem of this ... interface is geting ip address from the dhcp. The local ping from the terminal is ok ... i can ping and the ping has reply ... but if i ping [www.google.com](www.google.com) im getting no reply. But if i try to open google.com with firefox the page
opens ...  does anyone knows any solution for this ?

---

### Post by ivboy on 2010-01-23
Tnx again

So i found the solution and i would like to share with all off you ...
The problem was with the NOD32 SS firewal, in the machine that was running the VMware ... when i disabled it, i was getting the reply in shell that i needed. it was a little bit strange but that's it ... :)

Tnx again for the post ...

---

### Post by asearle on 2010-01-24
Hi everyone,

I find that I have a very similar problem with Ubuntu 9.10 ...

- I can ping addresses (any address) no problem
- I can google things in Firefox (using the little entry area top right) and results are returned immediately

... but ...

- When I try to navigate with Firefox the results never arrive (either when I click on a link displayed after googling) or when I enter the URL directly.
- When I try to run a software upgrade or install some packages are retrieved but most fail.

I tried adjusting my MTU (to 1492, the recommended level) and I tried switching off IPv6 (both in Firefox and in Networking) but this didn't change anything.

Arrgghh ... this problem is driving me crazy.

Any thoughts?

Hopeful regards,
Alan

---

### Post by asearle on 2010-01-24
Some more information ...

In order to diagnose this weird problem (i.e. pinging OK but no network in order areas, e.g. Firefox) I have been trawling through my old live CDs and find the following ...

Kubuntu 9.04 ... pings OK but no Konquerer Connection
Xubuntu 8.10 ... pings OK but no Firefox Connection (here IPv6 is not available anyway)
Knoppix 4.0 ... Full connection (e.g. under Konquerer)

This is all with the same laptop: An HP NC6400.

Any thoughts on this one?  Why is Ubuntu but not Knoppix showing the problem?

If anyone has any ideas for further diagnostics then I am happy to try anything.

Regards and many thanks,
Alan Searle

---

### Post by asearle on 2010-01-24
There seem to be lots of great suggestions in this thread and I have been trying as many as I can ...

- I have set the MTU to various levels (currently 576)
- I have matched the MTU on my router with my network settings in Ubuntu (576)

... but I am still getting this strange 'connected but not connected' situation.

Someone mentioned that it might be a firewall issue and so I wanted to ask if my fresh installatin of Ubuntu 9.10 automatically has a firewall activated?  If so then where can I best adjust this (or switch it off).  And is this advisable?

Many thanks,
Alan

---

### Post by asearle on 2010-01-24
I got my problem fixed with the following command ...

sudo ifconfig eth0 mtu 1492

... however it needs to be re-entered every time I reboot.

Am looking for a permanent solution at the moment.

Regards,
Alan

---

