---
title: "Very very very odd computer problems caused by network"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by nbv4 on 2009-08-19
Every few days, my computer will crash. It doesn't so much "crash" as it just gets really really wierd. Heres how it starts: Out of the blue, firefox will just lock up. I'll load up a page, then two seconds later try to load another page, and it will just sit there. No warning. All widgets are unclickable, but I can still maximize and minimize and move the window around. If I click on the "X" to close the window, it gives me the "firefox is not responding" dialog box. I click close, and then the window goes away with no fuss. If I try to relaunch firefox, i get a window that says firefox is already running. Trying to run any browser results in similar outcomes.

After it does this, my computer seems to be in "network BBAADDD" mode. Anything that uses my network connection will either crash or become unresponsive. Irssi will show a lag that increases and increases. If I load up system monitor and try to bring up the "Resources" tab, it will crash, I assume because it tries to draw a graph with my network useage.

It seems to only do this if bittorrent is open. Or sometimes it'll do this when I'm watching a Hulu video (but not usually). I can download 500+ MB files through the web OR through bittorrent with no crashing. But if I leave my bittorrent window open, it'll eventually cause my computer to go in "network zombie mode".

Also the wierdest thing BY FAR is what happens after I do a restart. It will shut down loke normal with the splash screen and all, but then it ALWAYS go to a black screen with a blinking underscore cursor at the top left and just hangs there. I've had it sit there for 3 hours. The only way for it to restart is to manually push the reset button on my case. Then the really weird part: when it does come back, my wireless will sometimes be working, and sometimes it wil just say "no network". If I click on the little icon with red-x, it acts as if I have no wireless card installed at all. I then have to do another restart of my system. This time is almost always restarts normally without requiring my to manually press the reset switch. After I put in my username and password, theres a 50/50 chance that wire is there. If it isn't, I do the whole thing over again. Sometimes I have to reset my computer 3 or 4 times before wireless is there.

Here is a screenshot I made last time my computer was in it's crash state:

[[IMG]http://img191.imageshack.us/img191/333/screenshotagd.th.png[/IMG]](http://img191.imageshack.us/i/screenshotagd.png/)

note the CPU useage hich is very low, while the load average (the red graph at the top) is climbing. At the time of the crash, load average was below 1. About 3 minutes later it was around 7. CPU time less than 5% the whole time.

Any ideas as to whats going on here?

Ubuntu 9.04 64-bit
Netgear WG311 wireless card using nsidwrapper
GIGABYTE GA-MA770-UD3 AM2+/AM2 AMD 770 ATX AMD Motherboard

---

### Post by dmizer on 2009-08-20
I suspect that Firefox is not completely closing.

Change the sort order of top by hitting <shift>+f and select "%MEM" by hitting the letter n

Or, just try running:
```
sudo killall firefox
```

---

### Post by nbv4 on 2009-08-20
> **dmizer said:**
> I suspect that Firefox is not completely closing.

Change the sort order of top by hitting <shift>+f and select "%MEM" by hitting the letter n

Or, just try running:
```
sudo killall firefox
```

Did you read my whole post? The problem is definitely not firefox. My whole system goes haywire. Any application that uses the internet is effected. Opera, Chrome, irssi, qbittorrent, etc.

---

### Post by dmizer on 2009-08-20
Yes, I read your entire post.

I still think your problem is Firefox related, especially since you get the message that Firefox is still running when you try to restart it.

Surely, it can't hurt anything to try my suggestions?

---

### Post by nbv4 on 2009-08-20
I'm 99% sure it's not firefox. There was a time when I thought it was firefox, so I installed Opera, but I still had this problem. Instead of giving me the error that Opera is already running, It just wouldn't load. I think some internal part of the network layer of my system is crashing, which is causing anything that uses the internet to crash as well.

---

