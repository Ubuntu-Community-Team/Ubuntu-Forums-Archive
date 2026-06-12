---
title: "Can someone help me understand this proposed fix?"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by cknight on 2009-06-21
I've been having bizarre network problems.  Some sites ([www.rv.net/forum](www.rv.net/forum)) load incredibly slowly in any browser and I have specific troubles with Firefox and google (spefically google mail and google maps).  Reading up on [this site]("http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/"), it looks like my problem might be related to TCP window-scaling.

I think  I understand the general principles here, but my networking knowledge is on rather shaky ground.  One suggested fix is to do the following:
```
sudo nano /etc/sysctl.conf

...add the following two lines 
net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

...then restart sysctl with
sysctl -p

```

This has made some improvements (especially with [www.rv.net/forum](www.rv.net/forum)), but before I mess around further, I'd like to understand more about what the above does.  

If I understand correctly, the above changes window-scaling from 6x to 2x?  Does this mean that by implementing the above I'm degrading potential performance for all websites to increase chances that a few will work?  E.g. what side effects/disadvantages does the above do?

And would changing that last column value to 64K be the equivalent of:
```
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

Ta

---

### Post by jhannah on 2009-06-21
For what it's worth, the site seems to load extremely slow for me as well. I expect it is something on their side and ultimately out of control. TCP window scaling issues would likely be more a prolific issue.

Nevertheless, the site you are reading is suggesting you modify the TCP tuning options using sysctl. The two configurations being modified here are related to the TCP autotuning options for sending and recieving packets. The first value of each is the minimum amount of memory the kernel should allocate for every TCP packet, regardless of the other criteria is uses to decide the size of this buffer. The second is the default size to use. The third is the maximum size that can be allocated for any TCP packet. Keep in mind, these are per-connection values for the buffer sizes.

There are a number of other TCP-related sysctl options that can be modified to suit your needs. There are a few others listed on [http://wwwx.cs.unc.edu/~sparkst/howto/network_tuning.php]("http://wwwx.cs.unc.edu/%7Esparkst/howto/network_tuning.php") with a decent summary. You can always google around to find out exactly what you are going to be changing.

Lastly, echoing 0 to /proc/sys/net/ipv4/tcp_window_scaling disables TCP window scaling all together in the kernel. That is almost certianly not what you want to do and, provided your maximum values for tcp_rmem and tcp_wmem are over 65k, it will be ignored.

All in all, I think the issue you are seeing is simply with the site being unreliable which is something you would need to contact the administrators of the page about to get resolution.

Anyway, I hope that helps explain what those changes would do.

---

### Post by cknight on 2009-06-21
Jon, thanks for your well thought out reply which does help me understand the issues.  I probably should have included that this proposed fix I'm researching came out of [this post]("http://ubuntuforums.org/showthread.php?p=7495395").  This post proved that this issue was a Linux only issue.  E.g. same site accessed by the same hardware via Mac or Windows worked fine.  Which is what intrigued me and thought it might be relevant to my firefox issue.

Implementing the proposed fix above fixed the [www.rv.net](www.rv.net) site (not that I use this site), and I think improved (but ultimatlely did not fix) my firefox/google problems. 

However, disabling tcp_window_scaling altogether seems to have finally found the fix to my google/firefox issue.  So far so good.  I've been looking for this for ages.  

Since you seem hesitant about applying this, I'd be interested in what compromises I'm making by disabling tcp_window_scaling but gaining access to vital sites in Firefox (note: this affects Opera to, but to a lesser extent)

---

### Post by Brandon Williams on 2009-06-21
For tcp window scaling, the window in question is the advertised receive window. If you disable window scaling, then the maximum advertised receive window will be 64K, which means that no more than 64K bytes will ever be transmitted in 1 round-trip-time (RTT). If the RTT for a connection is 100 miliseconds (10 round-trips per seconds), then a 64k receive window will limit you to 640KBps (5Mbps) download rates. If the RTT is 50 msec, then the maximum throughput will be 1280KBps (10Mbps).

Based on these numbers, the 64KB limit would be OK for most home broadband users iff their average RTT were around 50 msec. But a lot of sites will have longer RTTs than that, and would load slower as a result of the limited window size. Window-scaling allows you to increase your potential throughput by allowing more unacknowledged bytes to be outstanding, and therefore increase the bytes you can transmit in one RTT.

The maximum rmem and wmem per socket have a similar impact. The maximum rmem setting limits the maximum size of the advertized receive window, and the maximum wmem setting limits the maximum size of the send window, the smaller of which will limit maximum throughput in cases where the window-scale setting is not the limiting factor.

All of that having been said, what were the tcp_rmem and tcp_wmem settings on your machine before you changed them? The default settings on Ubuntu since at least Hardy (4194304) recognize the need for large maximum settings in order to allow broadband-speed throughput. The settings you propose would significantly lower the defaults, especially if you were to also disable window scaling. I don't see any reason to believe that this would improve the performance of these sites.

---

### Post by HavocXphere on 2009-06-21
Interesting thread.:KS

This is at the TCP/IP level & system wide, so I doubt that the browser has anything to do with it.

@OP:
On [http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/) there is a comment which suggests that you can change it on a per site basis:> 
 With kernel 2.6.17.13 or higher, you can also do:

THEIR_IP=1.2.3.4
MY_GATEWAY=5.6.7.8

ip route add $THEIR_IP/32 via $MY_GATEWAY window 65535

which only limits window scaling for that destination without interfering with your other connections.



---

### Post by dmizer on 2009-06-21
Well, first of all the howto you're referencing is about 3 years old, so the information provided will be dubious at best. I think we can safely say that this is not your problem.

Your problem is more likely related to IPv6 hardware routing problems. If you're using Jaunty, this is a bit complex because IPv6 is now a part of the kernel. You'll have to add the ipv6.blacklist=yes option to the kernel parameters.

For more information and to confirm that this is indeed your problem, you should look at this bug: [https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218](https://bugs.launchpad.net/ubuntu/jaunty/+source/glibc/+bug/313218)

---

### Post by cknight on 2009-06-22
Thanks everyone for your help.  Its such a great community here.

> Based on these numbers, the 64KB limit would be OK for most home broadband users
Brandon, thanks for this as it really cleared up the potential impact.  I've got about a 3Mbps connection, so it looks like it won't be often that I would need a greater
than 64Kb window at the moment, but I'm still loathe to limit my connection if I don't have to.

> I don't see any reason to believe that this would improve the performance of these sites.
And yet it does :)

> so I doubt that the browser has anything to do with it
I think your right, in that the underlying problem here is at the TCP/IP level, however, different browsers are definetly handling it differently (not so much for the 
[www.rv.net](www.rv.net) site, but for goole maps/mail)

Thanks for your tip on changing settings at an IP level.  This does sound a better solution as I am wary of limiting/disabling window scaling now that I know more about what 
it does.

> Well, first of all the howto you're referencing is about 3 years old, so the information provided will be dubious at best. I think we can safely say that this is not 
your problem.

While it might not be the problem (though using tcpdump shows the same characteristics), the fix described does work for me.  I'll try reenabling the window-scaling
tonight and work with the disabling of IPv6 via the kernel.  Out of curiosity, if you leave the Jaunty kernel as is (e.g. IPv6 enabled) and disable IPv6 in Firefox via about:config, does this
have any effect, do the two have to be aligned (e.g. both enabled or disabled), or does the firefox setting have no effect with the Jaunty kernel?

---

### Post by Brandon Williams on 2009-06-22
You can quickly figure out whether this is likely to be an IPv6 issue with the following tcpdump command lines: 'sudo tcpdump -i any port 53 | grep AAAA' and 'sudo tcpdump -i any ip6'. The first will show you whether your system is making any IPv6 DNS lookup requests (the most commonly reported problem) and the seconds will show you whether your system is attempting to establish any connections over IPv6. If neither of these command lines shows you any packet captures while surfing to slow sites, then IPv6 is most likely not your problem. If you see output from the first command (the one that looks for AAAA records), then disabling IPv6 DNS in Firefox will most likely improve your web surfing.

The article that you linked to indicates that the problem is not Linux, but rather some specific hardware on the internet that has bad support for tcp window-scaling. The most common case that people saw in the past was their internet gateway devices having trouble with window scale factors greater than 2, and the fix was to configure Linux so that it would not use such a window scale. It certainly _could_ be the case that some such hardware still exists on the net, and that your path to the web sites in question just happens to be hitting these devices. If you're seeing an improvement with those sites, then the changes you indicate for tcp_wmem and tcp_rmem are probably the right way to go for you.

I recommend against disabling tcp_window_scaling altogether, though, since the indication was that a window scale of 2 is OK. If your configuration allows the receive window to get as big as 174760, then you can even sustain full 3Mbps throughput with an RTT of 400 msec, while a 64K window needs an RTT of 166 msec or less.

---

### Post by cknight on 2009-06-22
> **Brandon Williams said:**
> You can quickly figure out whether this is likely to be an IPv6 issue with the following tcpdump command lines: 'sudo tcpdump -i any port 53 | grep AAAA' and 'sudo tcpdump -i any ip6'. 
Thanks for these Brandon.  After putting my system back to default Jaunty settings with regards to window-scaling and packet receive size and rebooted, I tried the above.  Neither produced any output which didn't suprise me greatly as I've tried disabling IPV6 in Firefox in the past which didn't produce any noticable difference.

> I recommend against disabling tcp_window_scaling altogether, though, since the indication was that a window scale of 2 is OK.
Unfortunately, while the window scale of 2 worked for the rv.net site (which I don't use) it didn't resolve my issues with google mail/maps (which i do use).  Only disabling window scaling alltogether has made a difference (e.g. fixed it completely).

What still baffles me is whose hardware is at fault here.  My router? My isp's router?  Some random 3rd party inbetween?  E.g. would getting a new router for my home potentially resolve this issue?

---

### Post by Brandon Williams on 2009-06-22
If it's only for some sites, it's unlikely (though not impossible) that replacing your home hardware would resolve the issue. What type of internet gateway/router do you have at home? Someone else might have the same hardware and would be able to tell you whether or not it's reasonable to assume that your hardware is causing trouble.

---

