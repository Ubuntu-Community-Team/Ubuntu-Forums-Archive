---
title: "IRC lose network disconnect"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by atomicben on 2009-09-12
This is the goofiest problem EVER.

Anytime I try to connect to IRC my network connection gets dropped.

Details:
Ubuntu: Jaunty; Gnome
I'm connected (wired) to my router.  Everything is really stable - I've never had a problem like this.

As I said, anytime I try to connect to IRC my network connection gets dropped - I get a pop up like you would get if you turned off/rebooted your router.

I downloaded XCHAT and tried to connect to EFnet, it came up fine, I logged in, the MOTD shows up and instantly my network connection goes down.  My network icon starts spinning and after 30 seconds or so it re-connects to the network, but I'm disconnected from IRC, I try again - I get MOTD, I get disconnected.  

So ok, I'm thinkiong XCHAT had a problem so I start my XP Virtual Machine (Sun xVM), install mIRC, the exact same thing happens.  I connect, I get MOTD, BAM - network goes down.  

Now I'm really confused so I try a web based IRC client called mibbit.  [www.mibbit.com]("http://www.mibbit.com")
and the exact thing happens again.  

THis is messed up.  I saw a similar old post with no solution [http://ubuntuforums.org/showthread.php?t=576680](http://ubuntuforums.org/showthread.php?t=576680)

Does anyone have some ideas?

Thanks.

Ben

---

### Post by grotesk on 2009-09-13
Are you using a Linksys router? I remember having a somewhat similar problem some years ago and remember looking it up and coming across a bug in Linksys code:

[http://seclists.org/bugtraq/2006/Mar/0087.html](http://seclists.org/bugtraq/2006/Mar/0087.html)

Your issue seems to closely mirror this behavior as most IRC servers send an XDCC PING just after connect time.

As a troubleshooting measure, consider taking your router out of the equation altogether and plugging your Ubuntu box directly into your cable/DSL/whatever-your-telco-gives-you modem and see if the problem persists. If it doesn't, it's likely an issue with your router that a firmware upgrade might solve. If the problem stays it might be your Linux box after all, but I'd say the smart money's on the router.

---

### Post by atomicben on 2009-09-13
Thanks, I think you've pointed me in the right direction.  When I connected this time, I kept and eye on my DLINK router.  The router went dead for a few seconds.  I haven't tried connecting direct to my cable modem yet, but I'll bet that clears it up.

Thanks again.

---

### Post by grotesk on 2009-09-13
I suspect that a firmware upgrade may be helpful. D-Link may have this as a known issue.

---

### Post by zinouch on 2009-09-13
maybe you can find a upgrade for your firmware

---

### Post by atomicben on 2009-11-06
Thanks to all that replied.  It turned out to be my router.  It was a DLink DI 524.  Updating the firmware didn't work.  If I connected directly to my cable modem it was fine.  I bought myself a nice new Cisco/Linksys and it's been perfect ever since.
 
Thanks again.  Sorry so long to get back to you.

---

