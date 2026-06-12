---
title: "Firefox freezes system on certain websites."
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by 2WhEElTeRRoRisT on 2007-07-30
I am having some issues viewing certain sites with Firefox. To view some myspace profiles slows my computer to almost a stand still. When I bring up yahoo.com after checking my email it freezes entirely. The mouse will move but nothing else will respond. I can't even get it to force quit. I checked my plugins and it says i have the newest java plugins, so I don't think that should be an issue. I really don't know what to check on here though, I am still really new to Linux. If there is any more information you need just let me know how to get it and I will post it. I have been pretty excited to use Linux, but if I can't view web pages then I can't keep it. Help save me from going back to windows.

---

### Post by fifthecho on 2007-07-30
(1) Start the application "gnome-system-monitor"
(2) Select the CPU Tab
(3) Single-click the "% CPU" Column header to sort processes by CPU usage.
(4) Navigate to a site in question in Firefox.
(5) Switch to the Gnome System Monitor to see what process is eating all your CPU cycles.


My guess would be that given your citations of MySpace and Yahoo that the Flash Player or Java plugins are merely taking a bit of time to initialize.
This is normal and should realistically only occur once per browsing session.
If the System Monitor shows "java" eating all of your CPU, then you know it is Java.
If the System Monitor shows "firefox-bin" eating all of your CPU, the culprit is probably Flash.

What are your system specifications? Perhaps adding a bit of system RAM or the like could reduce the noticed effects when these plugins are loaded into your browser.

---

### Post by 2WhEElTeRRoRisT on 2007-07-30
Well when I get to yahoo's page nothing works anymore. I have the little system monitor working all the time in the bar and it stops showing any updates. I can't even tab over to another program. With myspace I can at least still control things, it doesn't completely freeze. So I will have to test it with that page. I will have to post up tomorrow how that works out.

As for resources, my computer has AMD XP 3200+, 2 Gigs RAM, 50 Gigs HD space for Linux so I can't imagine that is too slow to run those pages.

Thank you for the reply by the way, I was starting to think that nobody read these things.

---

### Post by 2WhEElTeRRoRisT on 2007-07-30
I decided I couldn't wait.

The only things that were showing to be using any resources were the system monitor and Firefox. If i played the movie on the myspace page it would jump up to about 50%, but for the most part was no higher than 12% with everything paused.  It would sometimes show on the resources as being 100%, but the only two programs showing to be using anything were those two and they did not add up to 100.

It did constantly switch between sleeping and running, is that normal? I am unfamiliar with that.

In the middle of replying to this I did get an update for the Flash player, but it didn't seem to make much difference for me. I haven't tried the yahoo page again because the only thing I can do from there is restart manually.

I will test it after leaving this post.

---

### Post by 2WhEElTeRRoRisT on 2007-07-30
Sorry to keep doing these posts like this, but I went to yahoo and it actually didn't crash this time. That was the first time that has happened. The only thing that I have noticed is that if I point at some of the expanding tabs the cpu jumps to 100% until it is open and goes back down. Just like last time I couldn't find what program was causing it to reach 100%. I also read through the list of processes and there was no java one at all. Should there be one in the list if I am viewing these pages?

---

### Post by sdowney717 on 2007-07-30
try using seamonkey
some sites crash firefox and worked for me with seamonkey
[http://ubuntuforums.org/showthread.php?t=508021](http://ubuntuforums.org/showthread.php?t=508021)

---

