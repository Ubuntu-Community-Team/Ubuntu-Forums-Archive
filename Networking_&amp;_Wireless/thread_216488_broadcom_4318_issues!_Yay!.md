---
title: "broadcom 4318 issues! Yay!"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by whitty on 2006-07-15
So the other day it slipped my mind to run fsck instead of just wiping my linux partition when it had an error, and i decided to rebound with a ubuntu install just to try it out. So far i like it, and haven't had any problems unresolvable with a little googling. Unfortunately, one kind of cropped up on me behind my back. When i first installed ubuntu on my gateway mx7525 notebook (well, if you can call something this enormous a notebook) my integrated BCM94318 wireless card was recognized right away and came right up. I was super pleased. After a restart however, it wouldnt come back up right away, and I had to go into the networking config gui in system->administration and view preferences and fiddle without actually changing anything, then it would come up. A few more reboots of the same process, and finally this morning nothing, it wont connect whatsoever. On boot, the status monitor applet that came in gnome said status:disconnected, and iwconfig said, among other things, "Access Point: Invalid". After a bunch of fiddling and trying to do other things, and messing with ndiswrapper and such, it now says the status is idle and iwconfig says "Access Point: Not associated", however i can still not get it to connect, scan, recognize any access points, anything that makes a wireless card useful. If possible, i'd like to get rid of ndiswrapper and use just the default drivers, but i'd kind of like to get the card working, and nothing else i've seen has helped. Unfortunately, i don't even know what to copy here to help anyone help me, so please ask me for the output of any commands you need!

Thanks a lot, Alex

---

### Post by MarkSheely on 2006-07-15
Hi Alex,

This thread has alot of information for BCM4318 users:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

You may have to "undo" some of the the changes you have made before this method will work. 

Good luck (and don't give up),
Mark

---

### Post by whitty on 2006-07-15
I'd actually seen that thread among others and followed it to no avail. Shortly after i posted this thread, I loaded windows to get some work done since i decided to just wait for a response. When I read yours, I decided that i'd load ubuntu and try the thread again before I told you it did nothing, and lo and behold, wireless comes right up, no problems, not even that annoying-but-workable off-at-boot issue. Needless to say i'm quite pleased. Thanks a lot for the quick reply though, and moreover thanks for being so nice about it! I half expected to be told to "look it up, it's been covered 398492138 times!", as I would have in so many other forums.

The only thing i can think of that would have anything to do with the new behavior is having an eth0 ethernet link already present and operational on boot, but i'm not sure why that'd matter. I'm rebooting right now without it to see if it still works.

Thanks a lot!

EDIT: Looks like it works just fine now! Whatever, i'll take it!

---

### Post by MarkSheely on 2006-07-16
That's awesome!  There sure are alot of us BCM4318 users who owe Compwiz18 a huge debt of gratitude. 

Happy Ubuntu-ing,
Mark

---

