---
title: "Slow wireless speed"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by buster2209 on 2010-01-14
I've been using Ubuntu 8.04 for about a year and the wireless has been fine but now it's gone screwy and I can't figure out why.

This has happened on my laptop and wife's who uses Ubuntu Hardy also.

The speed drops to almost 0 mb/s whenever the signal strength is less than 95%.

It isn't the internet connection as vista (I dual boot) works fine below 95% signal strength.

To get the internet speed to be at a level that can load an internet page, I have to within 3 feet of the router!!

Both of the laptops don't use ndiswrapper, the internet connected straight away from a fresh install.

Any ideas?

---

### Post by rumli on 2010-01-15
What kernel version are you using?  You can find out by typing "uname -r".  I had very slow wireless with Linux kernel 2.6.31-17-generic, so I chose an earlier kernel in the GRUB menu upon bootup, and things worked better.

---

### Post by buster2209 on 2010-01-15
[IMG]http://cur.cursors-4u.net/smilies/images1/smi20.gif[/IMG]

After browsing the web, it turns out the card used for wi-fi in my laptop and my wife's is the same, and the linux driver can be iffy.

The 'solution' was to use ndiswrapper.  Needless to say, this killed my wi-fi and now I'm doing a clean install.

I think I've traced the problem to an update both laptops got 2 days ago that required a system restart.  My wife's laptop just got it (again) this morning which I assume is the fix for whatever f-ed everything up.

Sometimes, very rarely, I miss windows, but then I remember the ENDLESS problems keeping me up to an ungodly hour that made me want to strangle Bill Gates!  ;)

---

