---
title: "Fusion remote registering double button presses"
date: 2009-11-11
forum: Mythbuntu
---

### Post by pjhsv on 2009-11-11
G'day

I was running 8.04 without a problem until I installed 9.10 on my laptop and wanted to use it as a second front end.  This meant I needed to upgrade to 0.22 on the main backend/frontend, so figured i'd just upgrade to 9.10 on those too.  8.04 -> 8.10 -> 9.04 -> 9.10 upgrades all seemed to go alright, but I have a couple of outstanding issues.  Main one is that whenever I press a button on the remote, no matter how briefly, the mythtv screen behaves as though i've pressed it twice.  I've run irw at the same time, and even when irw only registers one button press, mythtv still moves down two spots in the menu etc (this is for every button that I can test with, not just up/down/left/right buttons).  My other issue is that mplayer wont play most of my divx files.  The codecs are there, and if I run mplayer from terminal, it loads them up perfectly.  
tail -f /var/log/syslog whilst selecting a video to play (using vnc, not a remote), gives the following syslog output

Nov 11 21:32:27 copernicus lircd-0.8.6[9167]: accepted new client on /var/run/lirc/lircd
Nov 11 21:32:27 copernicus lircd-0.8.6[9167]: removed client

which further confuses me! :)

Of far less importance, is it normal to need to manually rescan the "Watch Videos" section (M, Scan For Changes), when adding new media?  0.21 used to do it automatically when entering Watch Videos.


Any ideas would be awesomely appreciated!!!

ps:  Yes, I know I should have just backed up my media and installed fresh, but I didn't have spare space at the time (HTPC is using one HDD for system + media).  If that's what I end up having to do though..well..so be it :)

Cheers!

---

