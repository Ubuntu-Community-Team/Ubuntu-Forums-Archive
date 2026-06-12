---
title: "Using apple's remote app to control Ubuntu box?"
date: 2011-07-30
forum: Multimedia Software
---

### Post by eyekode on 2011-07-30
First some background: I currently have iTunes running on a Vista box attached to my TV. I have an Ubuntu box running 11.04 and shairport which serves as remote speakers for the iTunes server.

This works fairly well as I can control it with my iPhone, or iPad etc. Very slick interface and my wife loves it :).

But I would prefer to not use iTunes to as the server. I would like to let that Vista box sleep most of the day.

Doing a little bit of reading it sounds like I should be able to use mt-daapd as a replacement for iTunes. So I installed firefly and gave it a shot.

I can get it streaming music fine. But I cannot Apple's "Remote" app to add the new library. When I did some poking I read that I should make a file that ends in ".remote" and put my device name + the pairing passcode from my iPhone in this file.

When I enter the "Add Library" mode on my iPhone it should broadcast an mDNS event. And in fact it looks like it does because: avahi-browse -r -k _touch-remote._tcp
Can see my iPhone.

But when I do a tail -f on the mt-daapd logfile I never see a connection come up. I have tried debug level 8 in the messaging. Still nothing.

In my search for a fix I noticed mt-daapd is no longer being developed but there is forked-daapd. This is actually where I found the instructions for pairing via Remote.

Should I bail on mt-daapd? Will there someday be Ubuntu support for forked-daapd?

Thanks!
Salem

---

### Post by eyekode on 2011-07-30
I could not find a package for forked-daapd so I followed this thread:

[http://ubuntuforums.org/showthread.php?t=1746302](http://ubuntuforums.org/showthread.php?t=1746302)

It worked like a charm. I hope Ubuntu makes the switch to forked-daapd!
Salem

---

