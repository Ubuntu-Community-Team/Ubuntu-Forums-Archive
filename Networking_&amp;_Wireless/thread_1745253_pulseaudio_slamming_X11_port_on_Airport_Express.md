---
title: "pulseaudio slamming X11 port on Airport Express"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by yzwkzfn on 2011-04-30
I upgraded to 10.10 overnight.  To day I launched a VPN client and noticed that the traffic bars were unusually frantic.  I then looked at netstat and I see:

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 x-laptop.loc:57063 Base-Station-0508f:5000 ESTABLISHED
tcp        0      0 x-laptop.loc:57062 Base-Station-0508f:5000 ESTABLISHED
tcp        0      0 x-laptop.loc:52989 yx-in-f102.1e100.ne:www TIME_WAIT  
tcp   964544   2896 x-laptop.loc:44782 Base-Station-0508f3:x11 ESTABLISHED

Looking for what process has port 44782 with lsof:

pulseaudi 29509     ramerk   46u     IPv4      54808      0t0        TCP x-laptop.local:44782->Base-Station-0508f3.local:x11 (ESTABLISHED)

Sound recognizes the airport as a sound device, but it is not enabled
nor is there any application creating sound.  

I just disabled AirTunes on the device and network drops to nil.

This doesn't seem right that i/o should be so 'chatty' for nothing happening

---

