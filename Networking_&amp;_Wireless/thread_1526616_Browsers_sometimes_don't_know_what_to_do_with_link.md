---
title: "Browsers sometimes don't know what to do with links"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by rtruswell on 2010-07-08
Hi,

I posted on here yesterday with some networking troubles, I got some good advice, and I thought everything was solved, but it turns out I was wrong. I'm hoping you can help me out once again...

The basic problem is that some websites load normally, and some load very slowly or more typically not at all, regardless of which browser I use (Firefox, Opera, Chromium, even w3m). Following the advice of two very helpful posters here, I disabled IPv6 and also made a couple of changes in Firefox. They helped a little but the browsers still regularly just sit idling and not actually making any progress.

I'm fairly sure it's a software problem, because I have no problem with web browsing from Windows XP on the same machine. I'm also fairly sure it's specific to browsing the web, because no other network activity causes much problem (I work over SSH with no problem, I can ping any site with any packet size, etc.). Email occasionally seems to stop working but much less frequently than web browsing.

Here's one puzzling detail: quite often, browsers do nothing if I just click on a link on a page, but if I manually enter the link into the address bar and hit enter, the page loads fine. So if I left-click on a link, nothing happens, but if I right-click, select "Copy link location", paste the URL into the address bar, and hit enter, the page loads fine. Once again, this works more or less equally well regardless of the browser I use.

I'm totally at a loss here. I've seen the advice on IPv6 (which I've followed) and on MTU (which I don't think is the issue because ping -s 32 produces very similar results to ping -s 1600), and I don't know where else to look. Any suggestions would be very gratefully received.

For what it's worth, here is the output of ifconfig. Let me know if any other info would be useful.

Thanks again,
Rob

eth0      Link encap:Ethernet  HWaddr 00:a0:d1:30:96:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11144 (11.1 KB)  TX bytes:11144 (11.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:f5:e4:4e:02  
          inet addr:192.168.2.14  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20300840 (20.3 MB)  TX bytes:2705269 (2.7 MB)

---

