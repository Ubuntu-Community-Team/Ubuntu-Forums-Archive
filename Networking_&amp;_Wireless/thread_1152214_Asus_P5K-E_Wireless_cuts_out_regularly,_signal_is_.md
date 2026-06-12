---
title: "Asus P5K-E Wireless cuts out regularly, signal is bad..?"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by noblerabbit on 2009-05-07
So I have the Asus P5K-E mobo, with the integrated wifi. In Vista my signal was about 50%, and I never had any problems.

Now, in Jaunty, it still worked out of the box, but something is very wrong. The signal is at 13% and constantly cuts off. Sometimes it reconnects, sometimes it asks me for the WPA key (even though sometimes it doesnt need it...?).

Loading webpages are a nightmare, its so slow. Sometimes it feels like dialup (we have a 20Mb connection).

The weird thing is, as long as im connected (though barely, at 13%) i can run download managers and get great speeds from rapidshare (normally 1-1.3MB/s).

So clearly somethign is wrong with the driver here, it does funny things, can't decide to be slow or fast, favours some activities over others...

I have tried to run the windows driver (both x64 and 32bit) in ndiswrapper but to no avail, it doesnt work at all.

I know there is some kind of bug fix being worked out for the rtl8187 (i think this is what i have but im not sure). So is there anyone out there with the same mobo as me who can get their wireless to work??

Help is much appreciated!! I am still new to linux, having only used it regularly for a month or so..

So thank you in advance for any help you can provide!

---

### Post by noblerabbit on 2009-05-10
the signal seems to be the same on all the networks i pick up. 13% approximately. in windows my own network was at 50 and some of the other ones nearby at 80. i dont get why the signal is so low in ubuntu..?

---

### Post by noblerabbit on 2009-05-11
nothing?

---

### Post by noblerabbit on 2009-05-11
i should add an update now, the connection has been pretty stable the past 2 days, not really dropping off anymore (*touches wood*), but the signal is still really low.

what is most irritating is the web pages loading. it takes anywhere between 1-10 mins to load an average web page. once again, this is the slow part. given that the connection doesnt drop i can get good download speeds and such... so i dont understand what the problem is.

thing is, browsing is what i need to do most, and at this point its getting to be a little ridiculous. i dont have the option to run a wired connection (router is in other room) and i dont have another wireless adapter. 

i dont think i will buy a new wireless adapter to make ubuntu run so i guess its back to windows, unless some clever programmer figures this one out.

---

### Post by noblerabbit on 2009-05-11
heh well here is another interesting update:

after having a bit of a think about why web pages were so slow to load and why i still could get high speeds once a connection was established (in the case of a big http download) i applied some networking knowledge that came to me (from one of my lectures at uni last year.. what do you know, they do sink in!)

i had a search around to see if anyone using ubuntu had experienced slow DNS resolving. hey presto, theres a huge issue with IPv6 and misconfigured networks.

long story short i changed firefox's about:config to disable IPv6 and browsing is now much faster.


of course, signal is still low, and as a result the connection cuts out. but as long as im connected, internet activity is working as it should.

---

### Post by noblerabbit on 2009-05-12
false alarm, disabling IPv6 did very little.

today browsing is slow as molasses again :(

---

### Post by noblerabbit on 2009-05-14
today i plugged in a belkin usb adapter, which was recongised right away by jaunty.

same problem, connectino at 13-15% dropping off and not being able to connect.

this leads me to conclude that jaunty is not for me as it does not work well with any wireless. i may go back to hardy, but for now im sticking with windows because it works and i need my internet.

---

### Post by superprash2003 on 2009-05-14
[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

---

