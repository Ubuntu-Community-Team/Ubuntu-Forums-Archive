---
title: "I keep having to recreate my wifeless profile"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by rathodr on 2013-06-20
Since I've had my laptop, my wireless has been working without issue. Recently, I made two changes: a D-Link Wireless Router and I switched from DSL to cable. Also, I opted for 15mbs download speed where I had only 3mbps before.

It seems my problem started around the same time: every once in a while (and I can't see understand what scenario causes this), when I turn my laptop on from standby or a cold boot, I can't use the wireless. I ceck ifconfig and I get an IP (usually the same as before). I get the other network parameters too, but I can't ping the router. I think the message is there is not route to host?

I then delete the wireless profile and reboot. Sometimes this works, and other times, it doesn't. Sometimes, I have to let time pass before it lets  me use the wireless again. Other devices in the house seem to work without issue (tablet, phones, tv, etc.).

I am not sure the information to attach to begin the diagnosis process. Any thoughts?

In advance, thank you for taking time to respond to this issue.

---

### Post by newbie-user on 2013-06-21
Still chuckling about the title of your post. Have you set up a static ip on your laptop? Perhaps you have set up a DHCP range that is too small to accommodate all your devices? Is your router a/b/g/n and your laptop wireless only a/b/g? Maybe you have another DHCP server running on the network.

---

### Post by rathodr on 2013-06-30
Somedays, I wish it were wifeless :)

Anyway, I have a DLink N300/N350 ? My laptop was connected to it for a while when I had DSL. and then I decided to get cable for the ISP and then things seem to behave differently. I did notice two things: when I hav my laptop in a particular part of the family room, I will not get internet access (even though I seem to have an IP). I believe this may be due to antenna orientation. I have a small background in antenna theory - even though they make these wireles devices *omni-directional*, I think that's a misnomer. The second is that I have a similar result when I bring the laptop out of Suspend mode.

In both cases, it seems I have the same IP as before (which is ok), but it doesn't want to connect me to anything (no ping results).

I am now able to Disable Wireless (by clicking the "Enable Wireless" option from the networking systray icon) and then re-enable it. I usually need to give it a few seconds to make the connection and it goes back to normal.

I suspect there may permission issues on my laptop?

---

### Post by rathodr on 2013-08-15
Bump.

Any ideas why I keep having to disable wireless and then re-enable it when I restart my laptop? Thanks in advance for your help :)

---

### Post by 1clue on 2013-08-15
I had the wifeless profile active for way too long, glad to have gotten rid of it.

Is the N300 the only DHCP server on the network?  If you don't know, then are there ANY other DHCP servers on the network?  Including smart phones with wireless hotspot.

What happens if you plug your laptop in with an ethernet cable?  If you get a connection that way after you're already broken, then that should eliminate DHCP as the problem.

When you get the problem, give us the output of:

**ifconfig**

and

**netstat -rn**

---

