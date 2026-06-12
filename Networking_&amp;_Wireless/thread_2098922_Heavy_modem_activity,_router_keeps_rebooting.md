---
title: "Heavy modem activity, router keeps rebooting"
date: 2012-12-28
forum: Networking &amp; Wireless
---

### Post by rectec794613 on 2012-12-28
Hello community. I hope this is a good place to ask about this. Lately I've been running a Tor relay from my Raspberry Pi. I've noticed that after it's been running for a while (around 48 hours) the router that it's connected to suddenly reboots itself. But this is not the main problem right now.

A few hours ago, I completely shut down the relay and unplugged the Pi. But my cable modem has been showing a heavy amount of activity, and my router has been rebooting itself rather frequently. My connection speed also dips at times, usually right before the router reboots.

I've re-plugged the modem and the router several times, and I've let them sit unplugged for about 15 minutes, but there's still a lot of network activity. Normally, my router's lights would blink to show activity from their respective connection (wired or wireless), but I only see the modem's lights blinking. It's very odd.

I have Wireshark up and running but I have no idea what to look for. I'd very much appreciate some assistance. This has been bugging me so much the past few hours. Thanks.

---

### Post by chadk5utc on 2012-12-28
What type router do you have? does it have syslog server setting? I monitor and log all connections my router handles in my server logs.How many computer/server if any on your network? you may be able to login to your router and watch the security log to see where the traffic is coming from and going to if your router has such??

---

### Post by rectec794613 on 2012-12-28
> **chadk5utc said:**
> What type router do you have? does it have syslog server setting? I monitor and log all connections my router handles in my server logs.How many computer/server if any on your network? you may be able to login to your router and watch the security log to see where the traffic is coming from and going to if your router has such??

I have a Netgear WNR2000v3. I'm running DD-WRT on it. I can't seem to get any logs to show. I've had logs enabled for almost a year now, on medium level, and I've never been able to see any output. Right now I have 1 phone and 1 desktop connected. The router seems to have gained some stability the past 20 minutes.

---

### Post by chadk5utc on 2012-12-28
DD-wrt is great I would try to get the logs working(restore from a backup if possible) for sure they are very helpful also do you have any firewall rules on this? Im not sure what kind of interface DD has but the routers I have are all linux based with individual firewalls and routing all of which are logged to my server for central logging and simplicity. Im not sure if you can install software into ddwrt but if so you may try ntop or iftop you may check their forums for more info on troubleshooting that OS. but logging is a must. disconnect it from the net and trouble shoot it local only and see if there is any thing running that shouldnt be? its basically stripped Linux so most commands should work. Having said all that the easiest way to ensure the router is reset/reconfigure it then lock it up tight as you can. I get times where China constantly beats on my router I can see it in the logs.

---

