---
title: "Reduce latency for games"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by automaton26 on 2009-06-21
I imagine that default networking is configured to maximize throughput, rather than minimize latency. But for online gaming, I would rather improve ping times at the expense of download speeds. Does anyone have any simple suggestions for doing this, without rebuilding the kernel ?

I've seen suggestions like "add the following to /etc/sysctl.conf" :

> 
# improve broadband latency
net.ipv4.tcp_low_latency=1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_rfc1337 = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1


But can anyone suggest whether any/all of those are likely to help, or make things worse ?

[actually, it would be great to have an option in "System Settings" to optimize the networking for ***Downloading*** or ***Gaming*** - because Windoze doesn't have that either...]

---

### Post by Laryllan on 2009-06-21
Does it work? Do you have less latency in games?

---

### Post by automaton26 on 2009-06-21
It's difficult to tell without trying each one at a time...that's why I'd be interested in a more educated opinion than mine :)

---

### Post by zika on 2009-06-21
> **automaton26 said:**
> It's difficult to tell without trying each one at a time...that's why I'd be interested in a more educated opinion than mine :)I've tried it now just from the curiosity and it works. I will attempt to measure it today but it is certainly visible improvement. Thank You (even though I do not use any games ... :) )
[COLOR=Blue]**update:**[/COLOR]No measurable gain ... :( I just started to write a post when I saw the post below that is very well written so I will just say, read below ... :)

---

### Post by Brandon Williams on 2009-06-21
Changing TCP options will not lead to any improvement in network latency, so if you're looking for improvements in ping (i.e. ICMP echo) times or UDP latency, then none of these settings will make a difference. A latency-dependent game _should_ be using UDP, since it's probably already too late by the time the system figures out that it needs to retransmit a lost packet. This is the same reason why VOIP uses UDP and also why the settings you indicate would not have an impact on VOIP latency.

In addition, I don't think that any of the settings you list will give you any improvement in TCP latency that would be noticeable while gaming, provided that you don't also have a large-throughput connection going in the background. The only thing that I can think of to do in TCP to improve latency would be to set the TCP_NODELAY socket option, but that must be done by the application and can't be done system wide. This is all based on my knowledge of the internal workings of the linux TCP engine and not based on application specific experimentation/experience, though, since I'm not an online gamer. If you try out these options and they appear to improve your latency, then there's no reason not to stick with them.

As for the settings themselves, the only ones that look to be any different from the Linux defaults are: net.ipv4.tcp_low_latency, net.ipv4.tcp_timestamps, net.ipv4.tcp_rfc1337, and net.ipv4.route.flush. 

TCP timestamps are primarily useful for high-bandwidth connections, as their use helps with loss detection and determining latency values. Turning it off would not improve latency, and your system will tend to perform better in all cases if you have more accurate RTT calculations. I would not turn it off.

tcp_low_latency is documented to "prefer low-latency over high-throughput", but there is only one place where it is actually looked at. In that one place, it will only have an impact if you are running a high-throughput app but still want low-latency. I don't think you'll see much impact while playing a game if that's all you're doing, but you would see throughput degradation when all you're doing is pushing bits.

RFC 1337 doesn't have anything to do with latency, and would not have any impact on it. It enables features that allow better handling of the arrival of duplicate packets.

And finally, net.ipv4.route.flush is a control knob, not a setting. Setting it to 1 causes the route cache to be flushed now (forgetting previously stored RTT and MTU data), but will not have any impact going forward, other than the fact that new connections may be less efficient (including displaying longer initial packet latency) until the route cache has been repopulated.

---

### Post by automaton26 on 2009-06-22
OK, that all sounds reasonable, so I won't change those settings. And I appreciate the detailed explanation.

So I guess that my only remaining excuse for losing online is advancing old age!

Thanks a lot.

---

### Post by zika on 2009-06-22
> **automaton26 said:**
> OK, that all sounds reasonable, so I won't change those settings. And I appreciate the detailed explanation.
So I guess that my only remaining excuse for losing online is advancing old age!
Thanks a lot.LOL!:lol:

---

