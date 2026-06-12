---
title: "sysctl.conf settings for best Internet connection speeds"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by dkolars on 2011-02-28
Attempting to get "up to speed" with my Comcast cable connection... Ubuntu 9.10, Dell Vostro 400 desktop, Firefox 3.6.13...  Comcast says I should have 12 Mbps connection... if I get 1.0 Mbps, I'm doing good... they just tested everything, and said everything is fine on their end...

So, started digging on the web and thru the forums, and found this:

[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)

But, like ALL too many things, it's dated... it's from 2008...  I've set my settings to what is there, and disabled ipv6 in Firefox.  Hey, now, I'm sometimes up to 1.4 Mbps!!

Also found this, but no date...

[http://www.santa-li.com/linuxonbb.html](http://www.santa-li.com/linuxonbb.html)

I go to my girlfriends house, and her AT&T DSL is 4.5 Mbps or better!!!  She's running XP Pro.

Reading the forums, I see that folks have said there is a network connection problem with 9.10... and then I see that others are saying the same thing about 10.04 and 10.10!!  I have 10.10 on my laptop, and am dealing with it not seeing wireless when I leave my house... but that is another issue...

I'd love to get some connection speed from my system!!

Running some tests ([http://bandwidth.com/tools/speedTest/](http://bandwidth.com/tools/speedTest/)) gives me weird results:  Download 2.64 Mbps, Upload 4.12 Mbps.  NOT what it should be.

Dunno exactly what info is needed... Speedguide.net gives me results below, but I've tried changing numbers (says my RWIN is low) and nothing changes:

**TCP options string** = **020405b40402080adf1dca100000000001030306**
                     					                                           **MTU** = **1500**
[COLOR=#228b22]MTU is fully optimized for broadband.[/COLOR]
                     					                                           **MSS** = **1460**
Maximum useful data in each packet = 1448, which is less than MSS because of Timestamps, or other TCP/IP options used.
                     					                                           **Default TCP Receive Window (RWIN)** = **5888** 
					    RWIN Scaling (RFC1323) = 6 bits                          (scale factor: 2^6=64)												
                        Unscaled TCP Receive Window = 92 
						
[SIZE=1][COLOR=#ff0000]Under many Linux distributions, the Analyzer only shows the Current TCP Window.[/COLOR][/SIZE]
RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.
For optimum performance, consider changing RWIN to a multiple of MSS.
Other RWIN values that might work well with your current MTU/MSS: [COLOR=#228b22]
64240  (up to 2 Mbit lines, depending on latency. MSS * 44) 
128480 (1-5 Mbit lines, depending on latency. MSS * 44 * 2) 
256960 (2-14 Mbit lines, depending on latency. MSS * 44 * 2^2) 
513920 (8-30 Mbit lines, depending on latency. MSS * 44 * 2^3) 
1027840 (25-60 Mbit lines depending on latency. MSS * 44 * 2^4) [/COLOR]
					                        					                                           [**bandwidth**** * delay product**]("http://www.speedguide.net/faq_in_q.php?category=89&qid=185") (Note this is not a [speed test]("http://www.speedguide.net/speedtest/")):

 Your TCP Window limits you to: 236 kbps (29 KBytes/s) @ 200ms
 Your TCP Window limits you to: 94 kbps (12 KBytes/s) @ 500ms
Consider increasing your RWIN value to optimize TCP/IP for broadband.
                     					                                           **MTU Discovery (RFC1191) = ON**
                     					                                           **Time to live left** = **57 hops**
[COLOR=#22b200]TTL value is ok.[/COLOR]
                     					                                           **Timestamps (RFC1323) = ON**
*Note: Timestamps add 12 bytes to the TCP header of each packet, reducing the space available for useful data.*                      					                                           **Selective Acknowledgements (RFC2018) = ON**
                     					                                           **[IP type of service field (RFC1349)]("http://www.speedguide.net/tcpoptimizer.php#advanced_qos")** = **00000000 (0)**
                                        				   				   [CENTER] 		   [CENTER]  [IMG]http://www.speedguide.net/ads_php/adlog.php?bannerid=171&clientid=107&zoneid=15&source=&block=0&capping=0&cb=164a85495f8058034af80663977cb5b6[/IMG]
[/CENTER]
  [/CENTER]
  Thanks for any advice!!

---

### Post by dkolars on 2011-03-01
Well, some improvement... found this:

[http://ubuntuforums.org/archive/index.php/t-872346.html](http://ubuntuforums.org/archive/index.php/t-872346.html)

Using what I could understand from this, I am now d/l'ing at 2.3 Mbps according to [http://www.testmy.net](http://www.testmy.net)

Looking at the link from the forums, I have no idea where some of his numbers are coming from, i.e., the 187000...  

Here's the values I'm using:
net.core.rmem_default = 65536
net.core.rmem_max = 513920
net.core.wmem_default = 65536
net.core.wmem_max = 513920
net.ipv4.tcp_wmem = 4096 264000 524288
net.ipv4.tcp_rmem = 4096 264000 524288
net.ipv4.tcp_mem = 4096 65536 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1

So, for now this will have to do...  I gots other things to do besides tweak my system -- why is this such a problem with Ubuntu?

---

