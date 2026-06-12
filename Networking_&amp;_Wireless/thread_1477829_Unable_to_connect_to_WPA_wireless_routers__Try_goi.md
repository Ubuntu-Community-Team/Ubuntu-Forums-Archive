---
title: "Unable to connect to WPA wireless routers?  Try going into suspend mode!"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by DodgeV83 on 2010-05-09
Backstory:

On my 32bit Lucid installation, this would only work after running the following commands in a terminal:

sudo rmmod wl
*wait a few seconds*
sudo modprobe wl

Once I run those commands, it usually connects on the next try.  If it doesn't, I run them again and it works.

Now I just installed Lucid 64bit, and the trick no longer worked!  I found myself stuck for hours trying to get wireless to connect.  WEP connected just fine, "no security" wireless was fine, but when the router was in WPA ONLY, WPA2 ONLY or a mixed WPA mode, I was never able to connect...

This got me thinking about the circumstances which led to my first getting wireless to work on my 32bit Lucid install...it was right after going into suspend mode!

Solution:

Sure enough, on my 64bit install I went into suspend mode, came out, and immediately connected via wireless on WPA2!  I tested this a few times, and if it did not connect, doing the

sudo rmmod wl
*wait a few seconds*
sudo modprobe wl

trick worked.  Let me know if this works out for you!

---

