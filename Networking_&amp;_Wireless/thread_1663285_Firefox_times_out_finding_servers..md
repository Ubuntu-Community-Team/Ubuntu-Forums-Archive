---
title: "Firefox times out finding servers."
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by jock mackay on 2011-01-09
As a novice at this, I initiated a thread "Firefox stops working" around a week ago in the general forum.

The solving of the problem came to an end when It seemed that I had a general problem with plug ins. With all plug ins disabled, Firefox works as you would expect it to, but If I enable Java, or the Flash plug in Firefox stops connecting to any servers. 

This is the link to the previous post
[http://ubuntuforums.org/showthread.php?t=1659859](http://ubuntuforums.org/showthread.php?t=1659859)

Short of reinstalling Firefox, can anyone come up with an answer.

Jock

---

### Post by PatchesTheCaveman on 2011-01-09
Try disabling IPv6.  There are instructions here:
[http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6](http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6)

That page also has suggestions on other things you can try to fix this issue.

---

### Post by jock mackay on 2011-01-10
> **PatchesTheCaveman said:**
> Try disabling IPv6.  There are instructions here:
[http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6](http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6)

That page also has suggestions on other things you can try to fix this issue.
Thanks for your response. I had already disabled IPv6, but checked to be sure.
I also disabled Prefetch.
However when I enabled Shockwave in order to look at a video clip on the BBC site, the problems started up right away..... inabilityto reach any site.

Prior to making these changes Firefox had been behaving as I would expect it to. My other computers, Win XP, and mac OSX10.4 are also behaving normally.

---

### Post by jock mackay on 2011-01-10
> **jock mackay said:**
> Thanks for your response. I had already disabled IPv6, but checked to be sure.
I also disabled Prefetch.
However when I enabled Shockwave in order to look at a video clip on the BBC site, the problems started up right away..... inabilityto reach any site.

Prior to making these changes Firefox had been behaving as I would expect it to. My other computers, Win XP, and mac OSX10.4 are also behaving normally.
Out of sheer frustration I installed Chromium browser on the computer,and fired it up. The first thing I did was to watch a video clip on the BBC site. It stopped playing half way through, and I could not subsequently access any site, ie same as Firefox.
So I have a problem in that plug-ins/addons seem to cause browsers to stoip commecting to servers.
Ouch!

---

### Post by PatchesTheCaveman on 2011-01-10
Have you tried downloading a large file yet?  If not, give it a shot.  Try to find a file larger than 50MB.  The Internet Archive has a large collection of videos that can legally be downloaded for free, if your unsure of where to find a downloadable file that large:  [http://www.archive.org/details/movies](http://www.archive.org/details/movies)

Videos and Java applets tend to be large files.  We need to see if it's just breaking on large files and you've only noticed it on plugins because that's the only time you download sufficiently large files, or if it is in fact something about the plugins that is doing it.

Also, are you using 32 or 64-bit Ubuntu?

---

### Post by jock mackay on 2011-01-11
> **PatchesTheCaveman said:**
> Have you tried downloading a large file yet?  If not, give it a shot.  Try to find a file larger than 50MB.  The Internet Archive has a large collection of videos that can legally be downloaded for free, if your unsure of where to find a downloadable file that large:  [http://www.archive.org/details/movies](http://www.archive.org/details/movies)

Videos and Java applets tend to be large files.  We need to see if it's just breaking on large files and you've only noticed it on plugins because that's the only time you download sufficiently large files, or if it is in fact something about the plugins that is doing it.

Also, are you using 32 or 64-bit Ubuntu?
Thanks for responding.
I used that  site and downloaded 64Mb which was then played successfully using Movieplayer. While it was playing I surfed with Firefox using multiple tabs and did it successfully.
When the film ended I continued to surf successfully, BUT then I clicked on a video clip on a news page with Shockwave enabled, and within a minute or so the browsing ground to a halt..... unable to access sites. This is exactly what has been happening without fail.
32 or 64 bit...good question. I did not instal ubuntu 10.04 myself, so don't know for sure. Using Dell Inspiron netbook 1018, with Intel Atom processor. Used cat /proc/cpuinfo and got cflush size 64, cache alignment 64, address size:32 bits physical, 48 bits virtual (frankly, all Greek to me.)

---

### Post by PatchesTheCaveman on 2011-01-11
Go to Applications > Accessories > Terminal, type the following in the black box that appears, and press Enter:
```
uname -m
```

If it says *i686*, you're running 32-bit.  If it says *amd64* or *x86_64*, you're running 64-bit.

---

### Post by jock mackay on 2011-01-11
> **PatchesTheCaveman said:**
> Go to Applications > Accessories > Terminal, type the following in the black box that appears, and press Enter:
```
uname -m
```

If it says *i686*, you're running 32-bit.  If it says *amd64* or *x86_64*, you're running 64-bit.
i686 is the answer.

---

### Post by jock mackay on 2011-01-11
> **PatchesTheCaveman said:**
> Go to Applications > Accessories > Terminal, type the following in the black box that appears, and press Enter:
```
uname -m
```If it says *i686*, you're running 32-bit.  If it says *amd64* or *x86_64*, you're running 64-bit.
i686 is the answer.

---

### Post by jock mackay on 2011-01-11
> **PatchesTheCaveman said:**
> Go to Applications > Accessories > Terminal, type the following in the black box that appears, and press Enter:
```
uname -m
```

If it says *i686*, you're running 32-bit.  If it says *amd64* or *x86_64*, you're running 64-bit.
i686 is the answer.

---

### Post by PatchesTheCaveman on 2011-01-11
Okay, so now we need to see what's happening to your network connection when the plugins kill it.  Run these commands on a terminal when it's working:
```
ifconfig -a
route ip
dig google.com
ping google.com
ping 8.8.8.8
```
For the last two commands, you will need to wait about 30 seconds and then press CTRL+C to stop them.

Then, run a page with a plugin till it kills your Internet, and run the above commands again.  Now, copy and paste the before and after to a reply to this thread.  Hopefully that will indicate what's going wrong.

---

### Post by jock mackay on 2011-01-12
> **PatchesTheCaveman said:**
> Okay, so now we need to see what's happening to your network connection when the plugins kill it.  Run these commands on a terminal when it's working:
```
ifconfig -a
route ip
dig google.com
ping google.com
ping 8.8.8.8
```
For the last two commands, you will need to wait about 30 seconds and then press CTRL+C to stop them.

Then, run a page with a plugin till it kills your Internet, and run the above commands again.  Now, copy and paste the before and after to a reply to this thread.  Hopefully that will indicate what's going wrong.
First readout follows - Firefox working well, all plugins disabled.

Version:1.0 StartHTML:0000000167 EndHTML:0000012294 StartFragment:0000000454 EndFragment:0000012278    	 	 	 	p { margin-bottom: 0.21cm; }  eleanor@eleanor-laptop:~$ ifconfig -a  
 eth0      Link encap:Ethernet  HWaddr 5c:26:0a:0d:1c:07   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:26 Base address:0x4000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:fe:22:18   
           inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::72f1:a1ff:fefe:2218/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:2291 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:2544 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:1472192 (1.4 MB)  TX bytes:440253 (440.2 KB)  
           Interrupt:17 Memory:f80c0000-f80c0100  
 

 eleanor@eleanor-laptop:~$ route ip  
 Usage: route [-nNvee] [-FC] [<AF>]           List kernel routing tables  
        route [-v] [-FC] {add|del|flush} ...  Modify routing table for AF.  
 

        route {-h|--help} [<AF>]              Detailed usage syntax for specified AF.  
        route {-V|--version}                  Display version/author and exit.  
 

         -v, --verbose            be verbose  
         -n, --numeric            don't resolve names  
         -e, --extend             display other/more information  
         -F, --fib                display Forwarding Information Base (default)  
         -C, --cache              display routing cache instead of FIB  
 

   <AF>=Use '-A <af>' or '--<af>'; default: inet  
   List of possible address families (which support routing):  
     inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25)  
     netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP)  
     x25 (CCITT X.25)  
 eleanor@eleanor-laptop:~$ dig google.com  
 

 ; <<>> DiG 9.7.0-P1 <<>> google.com  
 ;; global options: +cmd  
 ;; Got answer:  
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18451  
 ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 4, ADDITIONAL: 4  
 

 ;; QUESTION SECTION:  
 ;google.com.			IN	A  
 

 ;; ANSWER SECTION:  
 google.com.		162	IN	A	173.194.37.104  
 

 ;; AUTHORITY SECTION:  
 google.com.		182447	IN	NS	ns3.google.com. 
 google.com.		182447	IN	NS	ns4.google.com. 
 google.com.		182447	IN	NS	ns1.google.com. 
 google.com.		182447	IN	NS	ns2.google.com. 
 

 ;; ADDITIONAL SECTION:  
 ns3.google.com.		336683	IN	A	216.239.36.10 
 ns1.google.com.		134044	IN	A	216.239.32.10 
 ns4.google.com.		344551	IN	A	216.239.38.10 
 ns2.google.com.		344551	IN	A	216.239.34.10 
 

 ;; Query time: 58 msec  
 ;; SERVER: 192.168.1.254#53(192.168.1.254)  
 ;; WHEN: Wed Jan 12 13:08:50 2011  
 ;; MSG SIZE  rcvd: 180  
 

 eleanor@eleanor-laptop:~$ ping google.com  
 PING google.com (173.194.37.104) 56(84) bytes of data.  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=1 ttl=52 time=48.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=2 ttl=52 time=44.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=3 ttl=52 time=44.1 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=4 ttl=52 time=49.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=5 ttl=52 time=44.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=6 ttl=52 time=50.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=7 ttl=52 time=44.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=8 ttl=52 time=44.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=9 ttl=52 time=44.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=10 ttl=52 time=44.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=11 ttl=52 time=44.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=12 ttl=52 time=44.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=13 ttl=52 time=47.2 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=14 ttl=52 time=46.1 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=15 ttl=52 time=49.1 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=16 ttl=52 time=45.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=17 ttl=52 time=48.2 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=18 ttl=52 time=43.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=19 ttl=52 time=44.1 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=20 ttl=52 time=44.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=21 ttl=52 time=43.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=22 ttl=52 time=855 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=23 ttl=52 time=44.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=24 ttl=52 time=44.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=25 ttl=52 time=44.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=26 ttl=52 time=44.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=27 ttl=52 time=44.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=28 ttl=52 time=44.4 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=29 ttl=52 time=44.5 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=30 ttl=52 time=44.2 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=31 ttl=52 time=48.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=32 ttl=52 time=43.5 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=33 ttl=52 time=49.2 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=34 ttl=52 time=43.4 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=35 ttl=52 time=43.9 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=36 ttl=52 time=44.3 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=37 ttl=52 time=55.0 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=38 ttl=52 time=43.6 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=39 ttl=52 time=43.8 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=40 ttl=52 time=46.7 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=41 ttl=52 time=44.5 ms  
 64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_seq=42 ttl=52 time=47.9 ms  
 ^C  
 --- google.com ping statistics ---  
 42 packets transmitted, 42 received, 0% packet loss, time 41056ms  
 rtt min/avg/max/mdev = 43.452/64.920/855.777/123.534 ms  
 eleanor@eleanor-laptop:~$ 



Second read out, Internet killed, all plugins enabled.


Version:1.0 StartHTML:0000000167 EndHTML:0000008249 StartFragment:0000000454 EndFragment:0000008233    	 	 	 	p { margin-bottom: 0.21cm; }  eleanor@eleanor-laptop:~$ ifconfig -a  
 eth0      Link encap:Ethernet  HWaddr 5c:26:0a:0d:1c:07   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:26 Base address:0x4000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:fe:22:18   
           inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::72f1:a1ff:fefe:2218/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:5150 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:5288 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:4287683 (4.2 MB)  TX bytes:802709 (802.7 KB)  
           Interrupt:17 Memory:f80c0000-f80c0100  
 

 eleanor@eleanor-laptop:~$ route ip  
 Usage: route [-nNvee] [-FC] [<AF>]           List kernel routing tables  
        route [-v] [-FC] {add|del|flush} ...  Modify routing table for AF.  
 

        route {-h|--help} [<AF>]              Detailed usage syntax for specified AF.  
        route {-V|--version}                  Display version/author and exit.  
 

         -v, --verbose            be verbose  
         -n, --numeric            don't resolve names  
         -e, --extend             display other/more information  
         -F, --fib                display Forwarding Information Base (default)  
         -C, --cache              display routing cache instead of FIB  
 

   <AF>=Use '-A <af>' or '--<af>'; default: inet  
   List of possible address families (which support routing):  
     inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25)  
     netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP)  
     x25 (CCITT X.25)  
 eleanor@eleanor-laptop:~$ dig google.com  
 

 ; <<>> DiG 9.7.0-P1 <<>> google.com  
 ;; global options: +cmd  
 ;; connection timed out; no servers could be reached  
 eleanor@eleanor-laptop:~$ ping google.com  
 ping: unknown host google.com  
 eleanor@eleanor-laptop:~$ ping 8.8.8.8  
 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.  
 64 bytes from 8.8.8.8: icmp_seq=1 ttl=50 time=52.3 ms  
 64 bytes from 8.8.8.8: icmp_seq=2 ttl=50 time=51.8 ms  
 64 bytes from 8.8.8.8: icmp_seq=3 ttl=50 time=51.5 ms  
 64 bytes from 8.8.8.8: icmp_seq=4 ttl=50 time=51.6 ms  
 64 bytes from 8.8.8.8: icmp_seq=5 ttl=50 time=52.0 ms  
 64 bytes from 8.8.8.8: icmp_seq=6 ttl=50 time=50.1 ms  
 64 bytes from 8.8.8.8: icmp_seq=7 ttl=50 time=50.6 ms  
 64 bytes from 8.8.8.8: icmp_seq=8 ttl=50 time=54.4 ms  
 64 bytes from 8.8.8.8: icmp_seq=9 ttl=50 time=50.9 ms  
 64 bytes from 8.8.8.8: icmp_seq=10 ttl=50 time=52.3 ms  
 64 bytes from 8.8.8.8: icmp_seq=11 ttl=50 time=51.8 ms  
 64 bytes from 8.8.8.8: icmp_seq=12 ttl=50 time=55.5 ms  
 64 bytes from 8.8.8.8: icmp_seq=13 ttl=50 time=51.1 ms  
 64 bytes from 8.8.8.8: icmp_seq=14 ttl=50 time=51.2 ms  
 64 bytes from 8.8.8.8: icmp_seq=15 ttl=50 time=50.5 ms  
 64 bytes from 8.8.8.8: icmp_seq=16 ttl=50 time=50.9 ms  
 64 bytes from 8.8.8.8: icmp_seq=17 ttl=50 time=50.9 ms  
 64 bytes from 8.8.8.8: icmp_seq=18 ttl=50 time=50.7 ms  
 64 bytes from 8.8.8.8: icmp_seq=19 ttl=50 time=50.8 ms  
 64 bytes from 8.8.8.8: icmp_seq=20 ttl=50 time=53.3 ms  
 64 bytes from 8.8.8.8: icmp_seq=21 ttl=50 time=56.0 ms  
 64 bytes from 8.8.8.8: icmp_seq=22 ttl=50 time=54.1 ms  
 64 bytes from 8.8.8.8: icmp_seq=23 ttl=50 time=53.2 ms  
 64 bytes from 8.8.8.8: icmp_seq=24 ttl=50 time=54.3 ms  
 64 bytes from 8.8.8.8: icmp_seq=25 ttl=50 time=51.1 ms  
 64 bytes from 8.8.8.8: icmp_seq=26 ttl=50 time=51.7 ms  
 64 bytes from 8.8.8.8: icmp_seq=27 ttl=50 time=51.2 ms  
 64 bytes from 8.8.8.8: icmp_seq=28 ttl=50 time=58.9 ms  
 64 bytes from 8.8.8.8: icmp_seq=29 ttl=50 time=50.3 ms  
 64 bytes from 8.8.8.8: icmp_seq=30 ttl=50 time=51.7 ms  
 64 bytes from 8.8.8.8: icmp_seq=31 ttl=50 time=50.8 ms  
 ^C  
 --- 8.8.8.8 ping statistics ---  
 32 packets transmitted, 31 received, 3% packet loss, time 31045ms  
 rtt min/avg/max/mdev = 50.174/52.232/58.956/1.939 ms  
 eleanor@eleanor-laptop:~$ 



Thanks again for spending time on this.
Jock

---

### Post by PatchesTheCaveman on 2011-01-12
Your plugins are killing DNS somehow.  That's incredibly strange.

One more before and after copy/paste round, this time running:
```
cat /etc/resolv.conf
```

Once you've got that copied, I have a couple commands I want you to run to try and fix it:
```
sudo bash -c "echo nameserver 192.168.1.254 > /etc/resolv.conf
```

Give it a try again.  If it still doesn't work, one more thing:
```
sudo bash -c "echo nameserver 8.8.8.8 > /etc/resolv.conf
sudo bash -c "echo nameserver 8.8.4.4 >> /etc/resolv.conf
```

Give it a shot one more time.  Let me know how it goes.

NOTE:  That last solution will configure your computer to use free DNS servers provided by Google.  All domain names resolved by your system until you reboot will be sent to Google.  If you have a problem with this, you may use another DNS provider such as OpenDNS.  For more information about this service, including their privacy policy, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by jock mackay on 2011-01-12
> **PatchesTheCaveman said:**
> Your plugins are killing DNS somehow.  That's incredibly strange.

One more before and after copy/paste round, this time running:
```
cat /etc/resolv.conf
```

Once you've got that copied, I have a couple commands I want you to run to try and fix it:
```
sudo bash -c "echo nameserver 192.168.1.254 > /etc/resolv.conf
```

Give it a try again.  If it still doesn't work, one more thing:
```
sudo bash -c "echo nameserver 8.8.8.8 > /etc/resolv.conf
sudo bash -c "echo nameserver 8.8.4.4 >> /etc/resolv.conf
```

Give it a shot one more time.  Let me know how it goes.

NOTE:  That last solution will configure your computer to use free DNS servers provided by Google.  All domain names resolved by your system until you reboot will be sent to Google.  If you have a problem with this, you may use another DNS provider such as OpenDNS.  For more information about this service, including their privacy policy, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)
Here is the result of the test you asked me to do, before and after.

Version:1.0 StartHTML:0000000167 EndHTML:0000002189 StartFragment:0000000454 EndFragment:0000002173    	 	 	 	p { margin-bottom: 0.21cm; }  Internet working, all plugins disabled.
 

 

 eleanor@eleanor-laptop:~$ cat /etc/resolv.conf  
 # Generated by NetworkManager  
 domain home  
 search home  
 nameserver 192.168.1.254  
 eleanor@eleanor-laptop:~$ cat /etc/resolv.conf
 

 

 Internet killed..plugins enabled
 

 eleanor@eleanor-laptop:~$ cat /etc/resolv.conf  
 # Generated by NetworkManager  
 domain home  
 search home  
 nameserver 192.168.1.254  
 eleanor@eleanor-laptop:~$  
 

 

 Weird thing..............while I was typing this, the Internet sprang into life ie, the clip that stalled started up. It didn't last more than 30 seconds, when it died again.
 

 I have not taken the further actions until I hear from you.
 

 Jock

---

### Post by Timpotten on 2011-01-12
I have the same problem with a32-bit. It slowed down and then  stopped completely before Christmas. A 'clean load' of 10.10 from DVD did not cure it. Then it started working again for no known reason, by offering a massive update. 

It has worked until after loading Opera browser. IPv6 is disabled, ping on "system>administration>>network tools" now times out on both name google.com  and address 74.125.230.81

---

### Post by PatchesTheCaveman on 2011-01-12
jock mckay:  Skip the second set of commands.  That won't help.  Run plugins to kill your Internet again and try the last set of commands and see if that revives it.

Timpotten:  Are you experiencing the same behavior as jock mckay in that your Internet works until you use a plugin such as Flash or Java?  In that case, follow the steps I provided in post #11 to provide your network status before and after so I can see what might be going on.  If you have a different problem, please follow the instructions in the stick on the top of the forum and provide it in a new thread.

---

### Post by jock mackay on 2011-01-13
> **PatchesTheCaveman said:**
> jock mckay:  Skip the second set of commands.  That won't help.  Run plugins to kill your Internet again and try the last set of commands and see if that revives it.

Timpotten:  Are you experiencing the same behavior as jock mckay in that your Internet works until you use a plugin such as Flash or Java?  In that case, follow the steps I provided in post #11 to provide your network status before and after so I can see what might be going on.  If you have a different problem, please follow the instructions in the stick on the top of the forum and provide it in a new thread.
OK, so I cut and pasted your instructions. The response was " bash : etc/resolv.conf : Permission denied".

---

### Post by Timpotten on 2011-01-13
I have Ubuntu 10.10 running on  my desktop and Mac OS X 10.4.110 laptop. Both machines are connected to the router in wired mode. 

I could access internet from both machines without any issues until just before Christmas 2010 when  Firefox slowed down and stopped as above, with the network icon indicating a good connection (the Mac connected by the same cord worked correctly). 

After much surfing, I decided to do a 'clean load' of 10.10 from DVD. Amazingly that did not cure the problem – neither Firefox browser nor Thunderbird mail would connect.  I abandoned the machine over the holiday, then it started working again for no known reason, by offering a massive update. 

It has continued to work until after loading Opera browser. IPv6 is disabled, ping on "system>administration>>network tools" now times out on both name google.com and address 74.125.230.81

I have also disabled all the Firefox extensions and plug-ins, restarted the computer without success.

This morning I tried update manager to see if that could communicate. It failed to lock "The package indexes are currently changed by apt-get". 

Restarting the computer again, Update appeared to be working, but could download nothing ("Downloaded 0B of 31 B)"  neither Firefox or Thunderbird worked.

I found your thread: [http://ubuntuforums.org/showthread.php?t=1663263&highlight=network](http://ubuntuforums.org/showthread.php?t=1663263&highlight=network). In the absence of an internet connection (for apt-get) the solution seems to be to reload the system, and start from scratch (remembering to back-up the hidden files of user(s) to save preferences – although you may perhaps be able to see the old partition if  installed  as an additional os). 

Regret delay in reply, thanks, Tim

---

### Post by jock mackay on 2011-01-13
> **jock mackay said:**
> OK, so I cut and pasted your instructions. The response was " bash : etc/resolv.conf : Permission denied".
I know it might not be scientific, but as the internet only operates, as well as it can, when all plugins are disabled, could it make sense to uninstall  them all now, and reinstall them subsequently as required by individual sites? If any or all of them kill the internet, I am no worse off, and if any one does it, we will know where to look for the trouble.

---

### Post by PatchesTheCaveman on 2011-01-13
> I know it might not be scientific, but as the internet only operates, as well as it can, when all plugins are disabled, could it make sense to uninstall them all now, and reinstall them subsequently as required by individual sites? If any or all of them kill the internet, I am no worse off, and if any one does it, we will know where to look for the trouble.
You can disable and enable plugins at will in Tools > Add-Ons in Firefox.  No need to uninstall them.

That doesn't help you much though, because they'll still kill your Internet when you try to use them!

Run a plugin till it kills your Internet again, then run these commands:
```
sudo bash -c "echo nameserver 8.8.8.8 > /etc/resolv.conf"
sudo bash -c "echo nameserver 8.8.4.4 >> /etc/resolv.conf"
```

I think it failed last time because I accidentally left of the closing quotes.  See if it comes back to life after you run those.

---

### Post by drdos2006 on 2011-01-13
This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by jock mackay on 2011-01-13
> **PatchesTheCaveman said:**
> You can disable and enable plugins at will in Tools > Add-Ons in Firefox.  No need to uninstall them.

That doesn't help you much though, because they'll still kill your Internet when you try to use them!

Run a plugin till it kills your Internet again, then run these commands:
```
sudo bash -c "echo nameserver 8.8.8.8 > /etc/resolv.conf"
sudo bash -c "echo nameserver 8.8.4.4 >> /etc/resolv.conf"
```

I think it failed last time because I accidentally left of the closing quotes.  See if it comes back to life after you run those.
I ran the code, complete with quotes and rebooted. Situation is sompletely unchanged. BBC clip ran for about 20 seconds and then stoppd. Other tabs return 'Connectin timed out.  Server taking too long to respond."

I wish I had a smiley to send.

Jock

---

### Post by PatchesTheCaveman on 2011-01-14
Okay, I'm going to start by explaining the technical details about your particular problem, because it is fairly bizarre, and actually appears to be a potential security vulnerability.  This is not only for your benefit but for other readers who have an inkling of what might be going on.  I apologize if you are knowledgeable about some of the concepts involved and I oversimplify things.

If you don't know what DNS is, it's the Domain Name System, essentially the phone book of the Internet.  It's what links a human-readable name like *ubuntu.com* to the IP address that your ISP uses to actually get the data back and forth from your computer.  Your computer asks a server usually provided by your ISP what IP address to go to for *ubuntu.com*, and it sends it back.

For some reason, when you use a plugin, your computer loses its ability to talk to DNS servers.  However, if it already knows the IP address, it can still talk to servers on the Internet.

We tested this in post #12.  If you noticed, before you ran the plugins, the ping command was able to receive a reply *google.com*, and the *dig* command was able to return a list of IP addresses from your DNS server for it.  But after you ran the plugins, *dig* was unable to contact your DNS server, and *ping* couldn't communicate with *google.com*.  But it was able to communicate with a server on IP address *8.8.8.8* (which is actually a free, public DNS server run by Google).

In that last set of commands, I had you configure your computer to use a different DNS server, and that didn't help.

By the way, the reason I said this looks like a security vulnerability is that, a regular user should not be able to take a Linux computer off the Internet just by running Flash!  That makes it a denial-of-service vulnerability, which have become rather famous recently.  But don't worry, your computer not open for hackers or anything.  If we figure out what's going on, you'll be responsible for an important fix to Ubuntu!

Now, there's one missing piece of the puzzle.  Ping is a rather simple method of communication, it just sends a packet to the server requesting that it send a packet pack to acknowledge it's there and can hear you.  We need to test if what you have actually lost is the ability to maintain a sustained communication to a server, or if this problem is just specific to DNS.

To do that, I need you to run plugins to break your Internet again.  (Incidentally, this should be the second to last time you'll have to this.)  Then, open a terminal and run this command:
```
wget http://209.85.175.105/
```
That will attempt to download the Google homepage via its IP address.  If it succeeds, it will save a file called *index.html* in your current directory with the HTML code of the Google homepage.  If it fails, you will get some sort of error which you should copy and paste into a reply to this thread.

Unfortunately, that doesn't really help us fix it at all, while it does narrow down the problem quite significantly.  Next, I'm going to have you run some software that will monitor your Internet communications at their most basic level in an attempt to pinpoint what exactly is going wrong where.

I'll give it some time though, because I need to get some stuff together so I can properly instruct you on how to do that, and also to give other users some time in the event they have some inkling as to what's going on here.  Not to mention this post is already quite the novel!  ;-)

---

### Post by jock mackay on 2011-01-14
Thanks, Patches.
I will not be able to get at this for about 12 hours, but I will send you the results after I have run this test. I am new to Ubuntu, so this is all fascinating to me.

jock

---

### Post by ripat on 2011-01-14
If I may suggest something, can you open a console and run this command:
```
$ sudo tail -f /var/log/syslog
```You keep that window open and try to replicate the failure using you browser's plugin. You might see something interesting related to dns.

To exit the *tail -f*, just do ctrl-c.

---

### Post by jock mackay on 2011-01-14
OK, Patches, here is the result of the test. I do not see any error code, just the giving up after 20 attempts.
Do you recommend I try ripat's suggestion?

Version:1.0 StartHTML:0000000167 EndHTML:0000006422 StartFragment:0000000454 EndFragment:0000006406    	 	 	 	p { margin-bottom: 0.21cm; }  wget [http://209.85.175.105/](http://209.85.175.105/) 

 

 eleanor@eleanor-laptop:~$ wget [http://209.85.175.105/](http://209.85.175.105/)  
 --2011-01-14 14:44:18--  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:44:40--  (try: 2)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:45:03--  (try: 3)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:45:27--  (try: 4)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:45:52--  (try: 5)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:46:18--  (try: 6)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:46:45--  (try: 7)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:47:13--  (try: 8)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:47:42--  (try: 9)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:48:12--  (try:10)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:48:43--  (try:11)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:49:14--  (try:12)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:49:45--  (try:13)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:50:16--  (try:14)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:50:47--  (try:15)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:51:18--  (try:16)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:51:49--  (try:17)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:52:20--  (try:18)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:52:51--  (try:19)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Retrying.  
 

 --2011-01-14 14:53:22--  (try:20)  [http://209.85.175.105/](http://209.85.175.105/)  
 Connecting to 209.85.175.105:80... failed: Connection timed out.  
 Giving up.  
 

 eleanor@eleanor-laptop:~$ 



Jock

---

### Post by jock mackay on 2011-01-14
Just for information, my son in law, who has been using Linux for a couple of years, helped me to use he Synaptic Manager to install "Flash plug in non free". Then when I only had Shockwave enabled, I was able to watch a complete BBC news video clip , and other sites remained active too. Seemed like good news. When he left I enabled all my plugins, and started to watch a clip, and within a minute the internet was dead.....unable to find server.
Situaation normal.
Jock

---

### Post by jock mackay on 2011-01-14
Just for information, my son in law, who has been using Linux for a couple of years, helped me to use he Synaptic Manager to install "Flash plug in non free". Then when I only had Shockwave enabled, I was able to watch a complete BBC news video clip , and other sites remained active too. Seemed like good news. When he left I enabled all my plugins, and started to watch a clip, and within a minute the internet was dead.....unable to find server.
Situaation normal.
Jock

---

### Post by jock mackay on 2011-01-14
Just for information.
Tonight my son in law who has been using linux for a couple of years helped me to instal Flash plugin non free, and subsequently with only Shockwave enabled in Firefox I was able to view a BBC video clip to the end, quite unusual. When he left I enabled all the plug ins, and played a video clip, but within a minute it stopped, and subsequently "unable to find server" appeared  situation normal.
Jock

---

### Post by jock mackay on 2011-01-14
Just for information.
Tonight my son in law who has been using linux for a couple of years helped me to instal Flash plugin non free, and subsequently with only Shockwave enabled in Firefox I was able to view a BBC video clip to the end, quite unusual. When he left I enabled all the plug ins, and played a video clip, but within a minute it stopped, and subsequently "unable to find server" appeared  situation normal.
Jock

---

### Post by PatchesTheCaveman on 2011-01-14
*Connection timed out.*  That means your computer is losing the ability to make sustained communications.

But since switching plugins seemed to help, we'll work that angle before reverting to drastic mesasures!  Enable all of your plugins, then type the following in Firefox or Chrome's address bar:
```
about:plugins
```
Then, go to File > Save As or press CTRL+S and save the plugins information page to a file, then attach it to a reply to this thread.

---

### Post by ripat on 2011-01-15
> **ripat said:**
> If I may suggest something, can you open a console and run this command:
```
$ sudo tail -f /var/log/syslog
```You keep that window open and try to replicate the failure using you browser's plugin. You might see something interesting related to dns.

To exit the *tail -f*, just do ctrl-c.

First reflex when one have a problem in Linux, look at at the log. Then investigate further. ;)

---

### Post by jock mackay on 2011-01-15
> **PatchesTheCaveman said:**
> *Connection timed out.*  That means your computer is losing the ability to make sustained communications.

But since switching plugins seemed to help, we'll work that angle before reverting to drastic mesasures!  Enable all of your plugins, then type the following in Firefox or Chrome's address bar:
```
about:plugins
```
Then, go to File > Save As or press CTRL+S and save the plugins information page to a file, then attach it to a reply to this thread.
Could not get file to send. Hope this is satisfactory
Jock
Version:1.0 StartHTML:0000000167 EndHTML:0000063223 StartFragment:0000000821 EndFragment:0000063207    	 	 	 	p { margin-bottom: 0.21cm; }h1 { margin-bottom: 0.21cm; }h1.western { font-family: "Times New Roman",serif; }h1.cjk { font-family: "DejaVu Sans"; }h1.ctl { font-family: "DejaVu Sans"; }h2 { margin-bottom: 0.21cm; }h2.cjk { font-family: "DejaVu Sans"; }h2.ctl { font-family: "DejaVu Sans"; }td p { margin-bottom: 0cm; }th p { margin-bottom: 0cm; }a:link {  }  [B]  [SIZE=3]function setDirection() {
    var frame = document.getElementById("directionDetector");
   var direction = frame.contentDocument
                         .defaultView
                         .window
                         .getComputedStyle(frame.contentDocument.getElementById("target"), "")
                         .getPropertyValue("direction");
    document.body.removeChild(frame);
    document.dir = direction;
 }

  function setupDirection() {
    var frame = document.createElement("iframe");
    frame.setAttribute("id", "directionDetector");
   frame.setAttribute("src", "chrome://global/content/directionDetector.html");
    frame.setAttribute("width", "0");
    frame.setAttribute("height", "0");
    frame.setAttribute("style", "visibility: hidden;");
   frame.setAttribute("onload", "setDirection();");
   document.body.appendChild(frame);
  }
  setupDirection();

 /* JavaScript to enumerate and display all installed plug-ins

  * First, refresh plugins in case anything has been changed recently in
   * prefs: (The "false" argument tells refresh not to reload or activate
   * any plug-ins that would be active otherwise.  In contrast, one would
   * use "true" in the case of ASD instead of restarting)
   */
  navigator.plugins.refresh(false);


  var numPlugins = navigator.plugins.length;

  if (numPlugins > 0)
    document.writeln("<h1 id=\"plugs\">" + pluginsbundle.GetStringFromName("installedplugins_label") + "<\/h1>");
  else
    document.writeln("<h1 id=\"noplugs\">" + pluginsbundle.GetStringFromName("nopluginsareinstalled_label") + "<\/h1>");

  document.writeln("<div id=\"findmore\">" + pluginsbundle.GetStringFromName("findmore_label") + " ");
  document.writeln("<a href=\"" + regionbundle.GetStringFromName("more_plugins_url") + "\">" + regionbundle.GetStringFromName("more_plugins_label") + "<\/a>.");
  document.writeln("<\/div>");

 document.writeln("<div id=\"installhelp\">" + pluginsbundle.GetStringFromName("installhelp_label") + " ");
  document.writeln("<a href=\"" + regionbundle.GetStringFromName("plugindoc_url") + "\">" + regionbundle.GetStringFromName("plugindoc_label") + "<\/a>.");
  document.writeln("<\/div><hr>");

 for (var i = 0; i < numPlugins; i++)
  {
    var plugin = navigator.plugins[i];

    if (plugin)
    {
      document.write("<h2 class=\"plugname\">");
     document.write(plugin.name);
      document.writeln("<\/h2>");

      document.writeln("<dl><dd><span class=\"label\">" + pluginsbundle.GetStringFromName("file_label") + "<\/span> ");
      document.write(plugin.filename);
      document.writeln("<\/dd><dd><span class=\"label\">" + pluginsbundle.GetStringFromName("version_label") + "<\/span> ");
      document.write(plugin.version);
      document.writeln("<\/dd><dd>");
      document.write(plugin.description);
      document.writeln("<\/dd><\/dl>");

      document.writeln("<table border=\"1\" class=\"contenttable\">");
      document.writeln("<thead>");
      document.writeln("<tr><th class=\"type\">" + pluginsbundle.GetStringFromName("mimetype_label") + "<\/th>");
      document.writeln("<th class=\"desc\">" + pluginsbundle.GetStringFromName("description_label") + "<\/th>");
      document.writeln("<th class=\"suff\">" + pluginsbundle.GetStringFromName("suffixes_label") + "<\/th>");
      document.writeln("<th class=\"enabled\">" + pluginsbundle.GetStringFromName("enabled_label") + "<\/th><\/tr>");
      document.writeln("<\/thead>");
      document.writeln("<tbody>");

      var numTypes = plugin.length;
      var mimetype;
      var enabled;
      var enabledPlugin;
      for (var j = 0; j < numTypes; j++)
      {
        mimetype = plugin[j];

        if (mimetype)
        {
          enabled = pluginsbundle.GetStringFromName("no_label");
          enabledPlugin = mimetype.enabledPlugin;
          if (enabledPlugin && (enabledPlugin.filename == plugin.filename))
            enabled = pluginsbundle.GetStringFromName("yes_label");

          document.writeln("<tr>");
          document.writeln("<td>" + mimetype.type + "<\/td>");
         document.writeln("<td>" + mimetype.description + "<\/td>");
          document.writeln("<td>" + mimetype.suffixes + "<\/td>");
          document.writeln("<td>" + enabled + "<\/td>");
          document.writeln("<\/tr>");
        }
      }

     document.write("<\/tbody>");
      document.write("<\/table>");
    }
  }Installed plugins[/SIZE][/B]

  	 		[SIZE=3]Find more information about browser plugins at 		[mozilla.org]("https://pfs.mozilla.org/plugins/"). [/SIZE] 		
 	
 	 		[SIZE=3]Help for installing plugins is available from 		[plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). [/SIZE] 		
 	
 	 	**[SIZE=3]Shockwave Flash[/SIZE]**

 	[SIZE=3]File: libflashplayer.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]Shockwave Flash 10.2 d151[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/x-shockwave-flash[/SIZE]
 				 				 					[SIZE=3]Shockwave Flash[/SIZE]
 				 				 					[SIZE=3]swf[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/futuresplash[/SIZE]
 				 				 					[SIZE=3]FutureSplash Player[/SIZE]
 				 				 					[SIZE=3]spl[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]DivX Browser Plug-In[/SIZE]**

 	[SIZE=3]File: gecko-mediaplayer-dvx.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3][Gecko 		Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.9.2

Video Player Plug-in for QuickTime, 		RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]video/divx[/SIZE]
 				 				 					[SIZE=3]DivX Media Format[/SIZE]
 				 				 					[SIZE=3]divx[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/vnd.divx[/SIZE]
 				 				 					[SIZE=3]DivX Media Format[/SIZE]
 				 				 					[SIZE=3]divx[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]QuickTime Plug-in 7.6.4[/SIZE]**

 	[SIZE=3]File: gecko-mediaplayer-qt.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3][Gecko 		Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.9.2

Video Player Plug-in for QuickTime, 		RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]video/quicktime[/SIZE]
 				 				 					[SIZE=3]Quicktime[/SIZE]
 				 				 					[SIZE=3]mov[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-quicktime[/SIZE]
 				 				 					[SIZE=3]Quicktime[/SIZE]
 				 				 					[SIZE=3]mov[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]image/x-quicktime[/SIZE]
 				 				 					[SIZE=3]Quicktime[/SIZE]
 				 				 					[SIZE=3]mov[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/quicktime[/SIZE]
 				 				 					[SIZE=3]Quicktime[/SIZE]
 				 				 					[SIZE=3]mp4[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/quicktime[/SIZE]
 				 				 					[SIZE=3]Quicktime - Session Description Protocol[/SIZE]
 				 				 					[SIZE=3]sdp[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-quicktimeplayer[/SIZE]
 				 				 					[SIZE=3]Quicktime[/SIZE]
 				 				 					[SIZE=3]mov[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]RealPlayer 9[/SIZE]**

 	[SIZE=3]File: gecko-mediaplayer-rm.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3][Gecko 		Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.9.2

Video Player Plug-in for QuickTime, 		RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]audio/x-pn-realaudio[/SIZE]
 				 				 					[SIZE=3]RealAudio[/SIZE]
 				 				 					[SIZE=3]ram,rm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/vnd.rn-realmedia[/SIZE]
 				 				 					[SIZE=3]RealMedia[/SIZE]
 				 				 					[SIZE=3]rm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/vnd.rn-realaudio[/SIZE]
 				 				 					[SIZE=3]RealAudio[/SIZE]
 				 				 					[SIZE=3]ra,ram[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/vnd.rn-realvideo[/SIZE]
 				 				 					[SIZE=3]RealVideo[/SIZE]
 				 				 					[SIZE=3]rv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-realaudio[/SIZE]
 				 				 					[SIZE=3]RealAudio[/SIZE]
 				 				 					[SIZE=3]ra[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-pn-realaudio-plugin[/SIZE]
 				 				 					[SIZE=3]RealAudio[/SIZE]
 				 				 					[SIZE=3]rpm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/smil[/SIZE]
 				 				 					[SIZE=3]SMIL[/SIZE]
 				 				 					[SIZE=3]smil[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]Windows Media Player Plug-in[/SIZE]**

 	[SIZE=3]File: gecko-mediaplayer-wmp.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3][Gecko 		Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.9.2

Video Player Plug-in for QuickTime, 		RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/asx[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-asf-plugin[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-msvideo[/SIZE]
 				 				 					[SIZE=3]AVI[/SIZE]
 				 				 					[SIZE=3]avi,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/msvideo[/SIZE]
 				 				 					[SIZE=3]AVI[/SIZE]
 				 				 					[SIZE=3]avi,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-mplayer2[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ms-wmv[/SIZE]
 				 				 					[SIZE=3]Microsoft WMV video[/SIZE]
 				 				 					[SIZE=3]wmv,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-asf[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]asf,asx,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-asx[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]asx,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wm[/SIZE]
 				 				 					[SIZE=3]Media Files[/SIZE]
 				 				 					[SIZE=3]wm,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wmv[/SIZE]
 				 				 					[SIZE=3]Microsoft WMV video[/SIZE]
 				 				 					[SIZE=3]wmv,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ms-wmv[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wmv,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wmp[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wmp,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ms-wmp[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wmp,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wvx[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wvx,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ms-wax[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wax,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ms-wma[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]wma,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-drm-v2[/SIZE]
 				 				 					[SIZE=3]Windows Media[/SIZE]
 				 				 					[SIZE=3]asx,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/wav[/SIZE]
 				 				 					[SIZE=3]Microsoft wave file[/SIZE]
 				 				 					[SIZE=3]wav,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-wav[/SIZE]
 				 				 					[SIZE=3]Microsoft wave file[/SIZE]
 				 				 					[SIZE=3]wav,*[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]mplayerplug-in is now 	gecko-mediaplayer 0.9.9.2[/SIZE]**

 	[SIZE=3]File: gecko-mediaplayer.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3][Gecko 		Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 0.9.9.2

Video Player Plug-in for QuickTime, 		RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]audio/x-mpegurl[/SIZE]
 				 				 					[SIZE=3]MPEG Playlist[/SIZE]
 				 				 					[SIZE=3]m3u[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG[/SIZE]
 				 				 					[SIZE=3]mpg,mpeg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG[/SIZE]
 				 				 					[SIZE=3]mpg,mpeg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG[/SIZE]
 				 				 					[SIZE=3]mpg,mpeg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-mpeg2[/SIZE]
 				 				 					[SIZE=3]MPEG2[/SIZE]
 				 				 					[SIZE=3]mpv2,mp2ve[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG[/SIZE]
 				 				 					[SIZE=3]mpg,mpeg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG[/SIZE]
 				 				 					[SIZE=3]mpg,mpeg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mpeg2[/SIZE]
 				 				 					[SIZE=3]MPEG audio[/SIZE]
 				 				 					[SIZE=3]mp2[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mpeg2[/SIZE]
 				 				 					[SIZE=3]MPEG audio[/SIZE]
 				 				 					[SIZE=3]mp2[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mp4[/SIZE]
 				 				 					[SIZE=3]MPEG 4 audio[/SIZE]
 				 				 					[SIZE=3]mp4[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mp4[/SIZE]
 				 				 					[SIZE=3]MPEG 4 audio[/SIZE]
 				 				 					[SIZE=3]mp4[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/mp4[/SIZE]
 				 				 					[SIZE=3]MPEG 4 Video[/SIZE]
 				 				 					[SIZE=3]mp4[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-m4v[/SIZE]
 				 				 					[SIZE=3]MPEG 4 Video[/SIZE]
 				 				 					[SIZE=3]m4v[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/3gpp[/SIZE]
 				 				 					[SIZE=3]MPEG 4 Video[/SIZE]
 				 				 					[SIZE=3]mp4,3gp[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mpeg3[/SIZE]
 				 				 					[SIZE=3]MPEG audio[/SIZE]
 				 				 					[SIZE=3]mp3[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mpeg3[/SIZE]
 				 				 					[SIZE=3]MPEG audio[/SIZE]
 				 				 					[SIZE=3]mp3[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mpegurl[/SIZE]
 				 				 					[SIZE=3]MPEG url[/SIZE]
 				 				 					[SIZE=3]m3u[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mp3[/SIZE]
 				 				 					[SIZE=3]MPEG audio[/SIZE]
 				 				 					[SIZE=3]mp3[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Media[/SIZE]
 				 				 					[SIZE=3]ogg,oga,ogm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Media[/SIZE]
 				 				 					[SIZE=3]ogg,oga,ogm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Audio[/SIZE]
 				 				 					[SIZE=3]ogg,oga[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Audio[/SIZE]
 				 				 					[SIZE=3]ogg,oga[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Video[/SIZE]
 				 				 					[SIZE=3]ogg,ogm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Vorbis Video[/SIZE]
 				 				 					[SIZE=3]ogg,ogm[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-vlc-plugin[/SIZE]
 				 				 					[SIZE=3]VLC plug-in[/SIZE]
 				 				 					[SIZE=3]vlc[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-google-vlc-plugin[/SIZE]
 				 				 					[SIZE=3]Google VLC plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/flac[/SIZE]
 				 				 					[SIZE=3]FLAC Audio[/SIZE]
 				 				 					[SIZE=3]flac[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-flac[/SIZE]
 				 				 					[SIZE=3]FLAC Audio[/SIZE]
 				 				 					[SIZE=3]flac[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/fli[/SIZE]
 				 				 					[SIZE=3]FLI animation[/SIZE]
 				 				 					[SIZE=3]fli,flc[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-fli[/SIZE]
 				 				 					[SIZE=3]FLI animation[/SIZE]
 				 				 					[SIZE=3]fli,flc[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-flv[/SIZE]
 				 				 					[SIZE=3]Flash Video[/SIZE]
 				 				 					[SIZE=3]flv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/flv[/SIZE]
 				 				 					[SIZE=3]Flash Video[/SIZE]
 				 				 					[SIZE=3]flv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/vnd.vivo[/SIZE]
 				 				 					[SIZE=3]VivoActive[/SIZE]
 				 				 					[SIZE=3]viv,vivo[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-matroska[/SIZE]
 				 				 					[SIZE=3]Matroska Audio[/SIZE]
 				 				 					[SIZE=3]mka[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-matroska[/SIZE]
 				 				 					[SIZE=3]Matroska Video[/SIZE]
 				 				 					[SIZE=3]mkv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-nsv-vp3-mp3[/SIZE]
 				 				 					[SIZE=3]Nullsoft Streaming Video[/SIZE]
 				 				 					[SIZE=3]nsv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-mod[/SIZE]
 				 				 					[SIZE=3]Soundtracker[/SIZE]
 				 				 					[SIZE=3]mod[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-aiff[/SIZE]
 				 				 					[SIZE=3]AIFF Audio[/SIZE]
 				 				 					[SIZE=3]aif[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/basic[/SIZE]
 				 				 					[SIZE=3]Basic Audio File[/SIZE]
 				 				 					[SIZE=3]au,snd[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-basic[/SIZE]
 				 				 					[SIZE=3]Basic Audio File[/SIZE]
 				 				 					[SIZE=3]au,snd[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/midi[/SIZE]
 				 				 					[SIZE=3]MIDI Audio[/SIZE]
 				 				 					[SIZE=3]mid,midi,kar[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-scpls[/SIZE]
 				 				 					[SIZE=3]Shoutcast Playlist[/SIZE]
 				 				 					[SIZE=3]pls[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-mng[/SIZE]
 				 				 					[SIZE=3]Multiple-Image Network Graphics[/SIZE]
 				 				 					[SIZE=3]mng[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]VLC Multimedia Plugin (compatible 	Totem 2.30.2)[/SIZE]**

 	[SIZE=3]File: libtotem-cone-plugin.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]The [Totem]("http://www.gnome.org/projects/totem/") 		2.30.2 plugin handles video and audio streams.[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/x-vlc-plugin[/SIZE]
 				 				 					[SIZE=3]VLC Multimedia Plugin[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/vlc[/SIZE]
 				 				 					[SIZE=3]VLC Multimedia Plugin[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-google-vlc-plugin[/SIZE]
 				 				 					[SIZE=3]VLC Multimedia Plugin[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg multimedia file[/SIZE]
 				 				 					[SIZE=3]ogg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg multimedia file[/SIZE]
 				 				 					[SIZE=3]ogg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Audio[/SIZE]
 				 				 					[SIZE=3]oga[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Audio[/SIZE]
 				 				 					[SIZE=3]ogg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Video[/SIZE]
 				 				 					[SIZE=3]ogv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ogg[/SIZE]
 				 				 					[SIZE=3]Ogg Video[/SIZE]
 				 				 					[SIZE=3]ogg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/annodex[/SIZE]
 				 				 					[SIZE=3]Annodex exchange format[/SIZE]
 				 				 					[SIZE=3]anx[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/annodex[/SIZE]
 				 				 					[SIZE=3]Annodex Audio[/SIZE]
 				 				 					[SIZE=3]axa[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/annodex[/SIZE]
 				 				 					[SIZE=3]Annodex Video[/SIZE]
 				 				 					[SIZE=3]axv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/mpeg[/SIZE]
 				 				 					[SIZE=3]MPEG video[/SIZE]
 				 				 					[SIZE=3]mpg, mpeg, mpe[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/wav[/SIZE]
 				 				 					[SIZE=3]WAV audio[/SIZE]
 				 				 					[SIZE=3]wav[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-wav[/SIZE]
 				 				 					[SIZE=3]WAV audio[/SIZE]
 				 				 					[SIZE=3]wav[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/mpeg[/SIZE]
 				 				 					[SIZE=3]MP3 audio[/SIZE]
 				 				 					[SIZE=3]mp3[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-nsv-vp3-mp3[/SIZE]
 				 				 					[SIZE=3]NullSoft video[/SIZE]
 				 				 					[SIZE=3]nsv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/flv[/SIZE]
 				 				 					[SIZE=3]Flash video[/SIZE]
 				 				 					[SIZE=3]flv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-totem-plugin[/SIZE]
 				 				 					[SIZE=3]Totem Multimedia plugin[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]Windows Media Player Plug-in 10 	(compatible; Totem)[/SIZE]**

 	[SIZE=3]File: libtotem-gmp-plugin.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]The [Totem]("http://www.gnome.org/projects/totem/") 		2.30.2 plugin handles video and audio streams.[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/x-mplayer2[/SIZE]
 				 				 					[SIZE=3]AVI video[/SIZE]
 				 				 					[SIZE=3]avi, wma, wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-asf-plugin[/SIZE]
 				 				 					[SIZE=3]ASF video[/SIZE]
 				 				 					[SIZE=3]asf, wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-msvideo[/SIZE]
 				 				 					[SIZE=3]AVI video[/SIZE]
 				 				 					[SIZE=3]asf, wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-asf[/SIZE]
 				 				 					[SIZE=3]ASF video[/SIZE]
 				 				 					[SIZE=3]asf[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wmv[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-wmv[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wvx[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wm[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-ms-wmp[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmv[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ms-wms[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wms[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-ms-wmp[/SIZE]
 				 				 					[SIZE=3]Windows Media video[/SIZE]
 				 				 					[SIZE=3]wmp[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/asx[/SIZE]
 				 				 					[SIZE=3]Microsoft ASX playlist[/SIZE]
 				 				 					[SIZE=3]asx[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]audio/x-ms-wma[/SIZE]
 				 				 					[SIZE=3]Windows Media audio[/SIZE]
 				 				 					[SIZE=3]wma[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]DivX® Web Player[/SIZE]**

 	[SIZE=3]File: libtotem-mully-plugin.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]DivX Web Player version 1.4.0.233[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]video/divx[/SIZE]
 				 				 					[SIZE=3]AVI video[/SIZE]
 				 				 					[SIZE=3]divx[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]QuickTime Plug-in 7.6.6[/SIZE]**

 	[SIZE=3]File: libtotem-narrowspace-plugin.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]The [Totem]("http://www.gnome.org/projects/totem/") 		2.30.2 plugin handles video and audio streams.[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]video/quicktime[/SIZE]
 				 				 					[SIZE=3]QuickTime video[/SIZE]
 				 				 					[SIZE=3]mov[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/mp4[/SIZE]
 				 				 					[SIZE=3]MPEG-4 video[/SIZE]
 				 				 					[SIZE=3]mp4[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]image/x-macpaint[/SIZE]
 				 				 					[SIZE=3]MacPaint Bitmap image[/SIZE]
 				 				 					[SIZE=3]pntg[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]image/x-quicktime[/SIZE]
 				 				 					[SIZE=3]Macintosh Quickdraw/PICT drawing[/SIZE]
 				 				 					[SIZE=3]pict, pict1, pict2[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]video/x-m4v[/SIZE]
 				 				 					[SIZE=3]MPEG-4 video[/SIZE]
 				 				 					[SIZE=3]m4v[/SIZE]
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]iTunes Application Detector[/SIZE]**

 	[SIZE=3]File: librhythmbox-itms-detection-plugin.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]This plug-in detects the presence of iTunes when 		opening iTunes Store URLs in a web page with Firefox.[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/itunes-plugin[/SIZE]
 				 				 					
					
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 		 	 	**[SIZE=3]Java(TM) Plug-in 1.6.0_23[/SIZE]**

 	[SIZE=3]File: libnpjp2.so[/SIZE] 		[SIZE=3]Version: [/SIZE] 		 		[SIZE=3]The next generation [Java]("http://java.sun.com/") 		plug-in for Mozilla browsers.[/SIZE] 	 		 		 		 		 		 			 				 					[SIZE=3]MIME Type[/SIZE]
 				 				 					[SIZE=3]Description[/SIZE]
 				 				 					[SIZE=3]Suffixes[/SIZE]
 				 				 					[SIZE=3]Enabled[/SIZE]
 				 			 		 		 			 				 					[SIZE=3]application/x-java-vm[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in Applet[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.1.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.1.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.1.3[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.2.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.2.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.3[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.3.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.4[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.4.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.4.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.5[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;version=1.6[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-applet;jpi-version=1.6.0_23[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in JavaBeans[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.1.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.1.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.1.3[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.2.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.2.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.3[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.3.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.4[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.4.1[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.4.2[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.5[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;version=1.6[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]
 				 			 			 				 					[SIZE=3]application/x-java-bean;jpi-version=1.6.0_23[/SIZE]
 				 				 					[SIZE=3]Java&#8482; Plug-in[/SIZE]
 				 				 					
					
 				 				 					[SIZE=3]Yes[/SIZE]

---

### Post by ripat on 2011-01-15
As I said above, the beauty of linux is that when an error occurs, it is always logged in some way. Check syslog. What you can (should) also do is to launch firefox from a console:
```
$ firefox
```

And see if it trows any errors in the console while using FF.

Only once you know what type of error occurred, you can investigate further. That way of doing can significantly reduce the Needle in the Hay process.

---

### Post by jock mackay on 2011-01-15
> **ripat said:**
> As I said above, the beauty of linux is that when an error occurs, it is always logged in some way. Check syslog. What you can (should) also do is to launch firefox from a console:
```
$ firefox
```

And see if it trows any errors in the console while using FF.

Only once you know what type of error occurred, you can investigate further. That way of doing can significantly reduce the Needle in the Hay process.
Ripat, thank you for taking an interest. I did open firefox from the console and used it until it killed the internet. No report appeared.
However I did run the command in your post number 32, and the console output is shown below.

Version:1.0 StartHTML:0000000167 EndHTML:0000004374 StartFragment:0000000454 EndFragment:0000004358    	 	 	 	p { margin-bottom: 0.21cm; }  eleanor@eleanor-laptop:~$ sudo tail -f /var/log/syslog  
 [sudo] password for eleanor:  
 Jan 15 15:08:54 eleanor-laptop kernel: [   36.025095] wlan0: no IPv6 routers present  
 Jan 15 15:08:56 eleanor-laptop kernel: [   37.089466] HW_VAR_CHECK_BSSID, set to 0  
 Jan 15 15:08:57 eleanor-laptop kernel: [   38.611275] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE  
 Jan 15 15:08:57 eleanor-laptop kernel: [   38.611334] ===========rtl8192ce_UpdateHalRAMask: Rate_index:0, ff005:80  
 Jan 15 15:08:57 eleanor-laptop kernel: [   38.611355] HW_VAR_CHECK_BSSID, set to 1  
 Jan 15 15:09:36 eleanor-laptop kernel: [   77.090326] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData  
 Jan 15 15:09:36 eleanor-laptop kernel: [   77.090438] HW_VAR_CHECK_BSSID, set to 0  
 Jan 15 15:09:37 eleanor-laptop kernel: [   78.610349] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE  
 Jan 15 15:09:37 eleanor-laptop kernel: [   78.610413] ===========rtl8192ce_UpdateHalRAMask: Rate_index:0, ff005:80  
 Jan 15 15:09:37 eleanor-laptop kernel: [   78.610439] HW_VAR_CHECK_BSSID, set to 1  
 Jan 15 15:09:49 eleanor-laptop AptDaemon: INFO: Initializing daemon  
 Jan 15 15:10:36 eleanor-laptop kernel: [  137.094706] HW_VAR_CHECK_BSSID, set to 0  
 Jan 15 15:10:37 eleanor-laptop kernel: [  138.615386] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE  
 Jan 15 15:10:37 eleanor-laptop kernel: [  138.615450] ===========rtl8192ce_UpdateHalRAMask: Rate_index:0, ff005:80  
 Jan 15 15:10:37 eleanor-laptop kernel: [  138.615475] HW_VAR_CHECK_BSSID, set to 1  
 Jan 15 15:11:07 eleanor-laptop kernel: [  168.754834] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData  
 Jan 15 15:11:56 eleanor-laptop kernel: [  217.089422] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData  
 Jan 15 15:11:56 eleanor-laptop kernel: [  217.089613] HW_VAR_CHECK_BSSID, set to 0  
 Jan 15 15:11:57 eleanor-laptop kernel: [  218.610359] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE  
 Jan 15 15:11:57 eleanor-laptop kernel: [  218.610429] ===========rtl8192ce_UpdateHalRAMask: Rate_index:0, ff005:80  
 Jan 15 15:11:57 eleanor-laptop kernel: [  218.610461] HW_VAR_CHECK_BSSID, set to 1  
 Jan 15 15:13:18 eleanor-laptop kernel: [  299.963103] ========>too long to sleep:39, fffffff6, 9c4  
 Jan 15 15:13:36 eleanor-laptop kernel: [  317.095408] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData  
 Jan 15 15:13:36 eleanor-laptop kernel: [  317.095602] HW_VAR_CHECK_BSSID, set to 0  
 Jan 15 15:13:37 eleanor-laptop kernel: [  318.614357] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE  
 Jan 15 15:13:37 eleanor-laptop kernel: [  318.614421] ===========rtl8192ce_UpdateHalRAMask: Rate_index:0, ff005:80  
 Jan 15 15:13:37 eleanor-laptop kernel: [  318.614444] HW_VAR_CHECK_BSSID, set to 1  
 ^C  
 eleanor@eleanor-laptop:~$ 



The crash occurered at 15.15.11.07  I only hope this helps.

---

