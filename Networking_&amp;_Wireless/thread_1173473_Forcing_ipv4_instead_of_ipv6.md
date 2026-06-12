---
title: "Forcing ipv4 instead of ipv6"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by Glaciusor on 2009-05-29
I got a USB wireless network card (Gigafast) and it works in Ubuntu 9.04, so I got one for my stepdad to go with a computer I grabbed from near-recycling that I put 9.04 on, however I forgot to make sure that it was the same exact one as mine and it turns out it is a little bit older and it won't connect. I posted here before about it and I was directed to do a few debugging things, but then my thread was lost. I researched some of the messages of interest that I got and found that it is often an issue where it is trying to use ipv6 but not degrading to ipv4. My network cannot use ipv6 and apparently it isn't auto-degrading to ipv4 so when my machine tries to connect it fails after a few minutes of trying.
 
As a last resort I was going to attempt disabling ipv6 and forcing ipv4, however I cannot find how to do that online for this version of Ubuntu (9.04 desktop). The instructions I did find are for either other flavors of Linux or for older versions that require me to edit files that are no longer where they used to be located. 
 
Thanks for the help ^_^.

---

### Post by munky99999 on 2009-05-29
ipv6 isnt necessary in practical matters and simply slows your routing down anyway.

[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

Should work well enough.

---

### Post by Glaciusor on 2009-05-29
Well, I guess that isn't the issue. The ipv6 module wasn't even loaded, but neither is ipv4... I know it's not a hardware issue because it worked fine on Windows. I don't know what to do next. I'm about ready to just find another wireless device that is *exactly* like the one I have that works. Thanks for the info anyway ^_^.

---

### Post by superprash2003 on 2009-05-30
you dont need to force ipv4 if your network doesnt support ipv6.. post otuput of ifconfig from the terminal.. your pc probably isnt receiving an ip

---

### Post by Glaciusor on 2009-05-31
Yeah, it definitely isn't. I've been through all that before. I am not sure why it isn't getting an IP address though. It sees the network, but I just can't get it to connect.

---

