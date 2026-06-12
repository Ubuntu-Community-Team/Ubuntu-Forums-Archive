---
title: "TCP/IP Tweaking Question"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by upchucky on 2009-08-02
The following is the results of my connection settings to the net, I have 2 questions about tweaking my broadband connection settings.

1, how do I increase the TTL (Time to Live) from 53 hops to a higher value? a value around 120 is more common.

2, how do I increase the RWIN (TCP Recieve Window) value from 5888 to a more realistic number of 16616?

I suspect that the above default settings are contributing to my slow connection speed and page timeouts. 



[HTML]TCP/IP Analyzer results

« SpeedGuide.net TCP Analyzer Results » 
Tested on: 08.02.2009 07:37 
IP address: xxx.xxx.xxx.xxx 
Client OS: Linux 
 
TCP options string: 020405b40402080a000541340000000001030307 
MSS: 1460 
MTU: 1500 
TCP Window: 5888 (NOT multiple of MSS)

Under many Linux distributions, the Analyzer only shows the Current TCP Window.
RWIN seems to be set to a very small number. If you're on a broadband connection, consider using a larger value.
For optimum performance, consider changing RWIN to a multiple of MSS.
Other RWIN values that might work well with your current MTU/MSS:
64240  (up to 2 Mbit lines, depending on latency. MSS * 44)
128480 (1-5 Mbit lines, depending on latency. MSS * 44 * 2)
256960 (2-14 Mbit lines, depending on latency. MSS * 44 * 2^2)
513920 (8-30 Mbit lines, depending on latency. MSS * 44 * 2^3)
1027840 (25-60 Mbit lines depending on latency. MSS * 44 * 2^4) 
 
RWIN Scaling: 7 bits (2^7=128) 
Unscaled RWIN : 46 
Recommended RWINs: 64240, 128480, 256960, 513920, 1027840 
BDP limit (200ms): 236kbps (29KBytes/s)
BDP limit (500ms): 94kbps (12KBytes/s) 
MTU Discovery: ON 
TTL: 53 
Timestamps: ON 
SACKs: ON 
IP ToS: 00000000 (0) 
TTL   : 53 hops
[/HTML]

---

### Post by Brandon Williams on 2009-08-02
First, window-scale and the receive window. As the comment says, you're only seeing the current receive window, which will grow dynamically as the connection receives more data, just as the sender's congestion window will. There is no reason, based on these results, to be concerned about the size of the receive window. It will quite quickly ramp up to a reasonable value based on the connection's throughout.

Second, TTL. What gives you the idea that 120 is more typical? That would be quite unusual, and would not account for slow connections. If 52 hops isn't enough, then your connection won't get through in the first place _and_ you really need to find a different ISP.

If your connection is slow, you'll need to look elsewhere for the solution.

---

### Post by upchucky on 2009-08-03
Thanks Brandon,

I have 2 other machines running windows xp the values of 120 hops and Rwin 16616, came from checking their settings. both those machines load pages faster and timeout on less pages than my 2 ubuntu machines.

the above test of both ubuntu machines indicates that my TCP window is not a multiple of MSS and to improve performance by making it a multiple.

if this is true, then how do i change setting in ubuntu to make it a multiple?

as for my ISP, I have broadband high speed wireless mesh networking and the only other ISP available in this area is Hughes satelite. (been there done that).

as a side note the two windows machines load up google home page instantly, while the two ubuntu machines take about 15 to 20 seconds to load up google.

My down speed tests at about 920kbps
Up speed tests at about 160kbps

I am the last account sharing a node, and i suspect that someone on my node is doing lots of filesharing, music, or movie downloads but the better speed of the windows machines makes me go Hmmmm?

any ideas?

---

### Post by Brandon Williams on 2009-08-03
I didn't intend to indicate that you need to change ISP (though I see how it appears that way). I mostly intended to indicate that it should not be taking you more than 52 hops to get where you're trying to go and that the problem most likely lies elsewhere. That said, I'm not familiar enough with the technology underpinning wireless mesh, so I suppose it's possible that the TTL really is the problem. If you want to check whether or not this is an issue, try using tcptraceroute to google in order to figure out how many hops it really requires to get there. For me, tcptraceroute says that it takes 19 hops to get to [www.google.com](www.google.com). I would be surprised to see it require 2.5 times that many hops, but it could happen.

If it turns out that this really is a problem for you, try increasing the ip_default_ttl value with 'sudo sysctl -w net.ipv4.ip_default_ttl=120'. If that helps, then you can add the setting to /etc/sysctl.conf so that it takes effect on reboot.

As for the receive window, with a default MSS of 1460, you would have to start with quite a large receive window (46720, I think) in order for the initial window to be a multiple of 1460, considering the scaling factor of 6. As I noted previously, given the way that linux manages the advertised receive window, there is no reason to believe that this would improve anything. You're more interested in what the receive window grows to, not what it starts at. Run tcpdump on your machine to figure out whether the window size gets up to a reasonable value fairly quickly. In my experience, the default settings on Linux are adequate for maintaining high throughput on a broadband connection even if the round-trip time is relatively long.

Are you sure that the 15 to 20 seconds for loading google is a throughput problem, and not, for example, a nameserver issue? If you refresh as soon as google is done loading the first time, does it load significantly faster the second time?

Try running 'sudo tcpdump -w tcpdump.out -i any' in another terminal when you first load the page so that you can see what's happening. This will dump the packet headers to a file that can be read with tcpdump -r tcpdump.out, allowing you to more easily look for a variety of issues. For example, you'll be able to see when a nameserver request goes out for [www.google.com](www.google.com) and how long it takes for a response to come back.

---

### Post by upchucky on 2009-08-04
Since my last post, i have discovered that my isp is briefly dropping out, the windows machines seem to not notice it depending on how long it drops for, but the linux machines take a few seconds to reconnect.

My isp is looking into the problem.

Thank you for the tips, in the event they say it is my problem I may need more help.

Thanks again

---

