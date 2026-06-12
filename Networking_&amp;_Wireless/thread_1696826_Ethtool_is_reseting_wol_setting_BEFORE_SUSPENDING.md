---
title: "Ethtool is reseting wol setting BEFORE SUSPENDING"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by Ansemx324 on 2011-02-27
Hey everyone,

So I have tried looking on the web for a solution to this, but I can't find anything. I have only found 2 posts with the same problem and both went unanswered.

So I want to set my ubuntu machine to WOL with both Magic Packet and Unicast (the g and u functions in ethtool wol)

wol supported: pumbg (thus g and u are both supported)

I use "sudo ethtool -s eth0 wol ug"       and check to see if it changed, and it does

sudo ethtool eth0
"wol: ug"

After I suspend though, only magic packet will wake it up! I go back in and check with "sudo ethtool eth0" and low and behold, it is back to only being "wol g", which is the default.

For some reason it must bump back to default before going into suspend. NOTE, this is with suspend, not even a reboot or a shutdown! Even suspend will reset it to default. I have worked on adding a script to /etc/init.d, adding lines to /etc/rc.local, and adding lines to /etc/networking/interfaces, all with no change.

Any idea what is going on and why it is resetting wol back to default?? I know I should be happy at LEAST it does magic packet, but I want to know why it wont change.

Thanks everyone!

Thomas

---

### Post by Ansemx324 on 2011-03-20
Bump. Any ideas?

Ive really looked around at over 50-100 articles, but they are all either off-topic or outdated.

PS: Also, my eth0 is managed by network manager and doesnt show up in /etc/network/interfaces, so adding any lines in this file wont really help since eth0 isnt in this file anyway.

---

### Post by User-0209 on 2011-07-22
There is a script in /usr/lib/pm-utils/power.d named disable_wol. In the "enable" branch it explicitly sets wol to g. If you change this to ug you'll probably have it sticky.

However, I still have problems waking the computer with a normal ping.

---

### Post by putrid on 2012-06-02
> **User-0209 said:**
> There is a script in /usr/lib/pm-utils/power.d named disable_wol. In the "enable" branch it explicitly sets wol to g. If you change this to ug you'll probably have it sticky.

However, I still have problems waking the computer with a normal ping.

Sorry for bringing up this old thread. But wanted to thank User-0209. And to let others with the same issue to know that this worked for me (using suspend).

btw. for waking the computer with a normal ping, follow [this guide]("http://johnlewis.ie/wake-on-lan-over-wireless/")

---

