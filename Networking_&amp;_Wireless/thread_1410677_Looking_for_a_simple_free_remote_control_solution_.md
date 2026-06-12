---
title: "Looking for a simple free remote control solution that works on Windows AND Linux."
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by 13thSlayer on 2010-02-19
And maybe macs, but that's not so important. I mean something like Teamviewer so i can click-click and be there in no time, without knowing my IP (it's dynamic so that's a toughy, when i was using VNC i had to write a crontab script that uploaded my IP to a place i could always access every hour). Looked trough tons of apps, Googled for hours, found nothing... *sigh*

---

### Post by pirateghost on 2010-02-19
> **13thSlayer said:**
> And maybe macs, but that's not so important. I mean something like Teamviewer so i can click-click and be there in no time, without knowing my IP (it's dynamic so that's a toughy, when i was using VNC i had to write a crontab script that uploaded my IP to a place i could always access every hour). Looked trough tons of apps, Googled for hours, found nothing... *sigh*
why not just utilize a service like [DynDNS.com]("https://www.dyndns.com")

then you can continue to use VNC

---

### Post by 13thSlayer on 2010-02-19
> **pirateghost said:**
> why not just utilize a service like [DynDNS.com]("https://www.dyndns.com")

then you can continue to use VNC
...Woah. Never thought of that, thanks for a suggestion.

---

### Post by LepeKaname on 2010-02-19
I use no-ip.com which also have a script that you can install:

"aptitude install noip2"

---

### Post by efflandt on 2010-02-20
I have been using no-ip.com for many years (on a Celeron 300 box), so I can ssh home.  Even got several subdomain names to learn/play around with name based virtual web hosting (they also have a wildcard in their DNS so you can name your own sub.subdomains to point to your dynamic IP).  For example if you have myname.no-ip.com, then anything.myname.no-ip.com would also point to it.

But instead of having their client tickle their server periodically to grab my public IP, I run a Perl LWP script as a daemon that monitors the PPPoE IP on my modem/router every 5 minutes, and just notifies no-ip.com if it has changed.

Another option for remote access is logmein.com.  They have a 32-bit deb version.  I tried using it with nswrapper in 64-bit, which allowed Firefox to recognize it as a plugin, and it came up with the menus, but no desktop (maybe needs 32-bit java?).  It worked to connect 32-bit Ubuntu 9.10 to WinXP.

---

