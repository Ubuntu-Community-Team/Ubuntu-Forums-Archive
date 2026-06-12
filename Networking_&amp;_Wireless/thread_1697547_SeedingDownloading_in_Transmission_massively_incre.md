---
title: "Seeding/Downloading in Transmission massively increases ping"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by AdmiralNotorious on 2011-03-01
hello

i know this may not be the best place to sport a bittorent question like this one, but you guys seem the most helpful group i've encountered in a long time

whenever i'm seeding even a single torrent, (or DOWNLOADING for that matter) my entire network is slowed down massively. I looked into it, and it can increase my ping (in some cases) well over 10 fold (based on measurements taken from pingtest.net)

it seems to me that i never used to have this problem, and i would love to know if any of you have any wisdom to share on the issue.

note- my problem is concerning ping, NOT bandwidth

---

### Post by mimor on 2011-03-01
You can limit the bandwidth used by transmisson or set up a QOS on your router.
You might also want to avoid placing a hub between your router and the transmission machine. :)

---

### Post by mikewhatever on 2011-03-01
You need to look into your client config settings:

- max global/per torrent connections
- max up/down limits
- max up slots per torrent

Sometimes, one or several of those are way too high for the line or router/modem capabilities.

---

### Post by AdmiralNotorious on 2011-03-01
i dont think the problem is as simple as you are making out to be. if i am seeding a **single** torrent, the effect is massive on my ping, but is not magnified with the addition of other torrents either downloading or seeding.but if i pause all torrents then everything is perfectly fine again, night and day

something is amiss, i know it, for i never used to have to deal with this crap

---

### Post by marvselby on 2011-03-02
You're absolutely right.  There is something amiss.  I spent the better part of today tracking down a problem that has driven me to the edge of the abyss of insanity.  I just recently tried Transmission and I found I was having trouble loading pages - r-e-a-l  s-l-o-w.  Doing a ping to the router(s) was fine but when I pinged something like 8.8.8.8 my ping times were in like seconds.  What I noticed (and maybe you didn't) was that there were lost packets - anywhere from 20-50%.  After a careful step-by-step analysis I found that whenever Transmission was running on any of my machines, the problem was evident on all of the machines.  I even connected one machine directly to my modem with the same result.

Okay, I'm not savvy enough on TCP/IP to say for certain, but I have the distinct "hunch" the problem is with packet collisions and I have to surmise the problem is caused by Transmission.  I haven't had time yet to look at the bug reports.

The thing that fixed my problem was going back to using Vuze.  I've never had a problem with it.

---

### Post by AdmiralNotorious on 2011-03-03
thank u for taking me seriously, but unfortunately our problems are not the same. i tested for packet losses and there was between a 0 and 3% loss, no where near enough to show for an increase in ping from 90 to 1500 with seeding a few torrents. i swear it is driving me up the wall, because there doesn't seem to be a good reason for it, as the effect occurs in all 4 bittorent clients i use and on all my machines, with, as you said with your problem, effect on the entire network.

could the problem be with my modem? i have broadband, but we just switched to digital cable and they gave us a new one. could it be that it isn't properly handling the requests for torrent data or something to that effect?

---

### Post by marvselby on 2011-03-03
I have broadband too and replaced my modem about 6 months ago because the old one died, but I'm pretty sure the modem is not the cause.  Connected directly to the modem there was no problem until I started Transmission.  I also have the problem in more than one distro - Lucid and Maverick - so I'd have to assume the problem is not distro-specific.

From reading one other post, the conventional wisdom seems to be to throttle the upload speed in Transmission.  I tried that (set it to 20 kilobits/s) with no luck.  That does seem to make some sense because a runaway upload could affect overall performance.  You might want to try [http://www.speedtest.net/]("http://www.speedtest.net/") to see what your modem/connection is capable of.  Right now my connection is running at 7.28 megabits/sec download and .48 megabits/sec upload but that changes everytime I run the test (only natural due to variances in net traffic).  You might try running the test with and without Transmission running.  That might give you a clearer idea of what is happening.  I know with Vuze running and seeding, my upload speed drops by a little under half.

You might also pay attention to the upload speed indicated by Transmission.  I'll almost bet it's exceeding your upload potential.

I just went back and reset the upload speed in Transmission to 10 KBS and it seems to be behaving itself now.  Ping times are just about right and I am able to load pages in my browser without having time to go get a cup of coffee.  I also ran the speed test while Transmission is running and my upload speed dropped by the expected amount.  Could we have a cure here?

---

### Post by veni4 on 2011-03-06
For this problem, you contact the Internet service provider,
After that check your ping test, through this site [http://www.whoisxy.com/ping.aspx](http://www.whoisxy.com/ping.aspx)
It has the best information of IP address, IP address to domain, domain name to IP,domain name, hosting, and ping test to know the particular connection is online or not!!!!!

---

