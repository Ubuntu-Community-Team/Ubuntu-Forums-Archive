---
title: "HVR-950Q  xc5000 n0_poweroff=1   help?"
date: 2010-11-24
forum: Multimedia Software
---

### Post by chee on 2010-11-24
I am running 10.10 on an Inspiron 6400.   Everything works great except my HVR-950Q.   I have it working with Me-TV (digital) and it works with tvtime but stutters constantly.  It also stutters with DTV HD but I thought that was due to my old laptop not keeping up.

So I read somewhere that this USB card has issues with powering,  and the fix was to add "options xc5000 no_poweroff=1 debug=1" to the files /etc/modprobe.d/local.conf and /etc/modprobe.d/xc5000.conf

So I looked for those 2 files but I didn't have them,  so I made them and inserted the lines but I am guessing that that won't have the same effect.

So if anyone has any insight into this fix I would be very interested,  everything I read just states that the people inserted the lines,  nothing about having to create the files, etc.

Thank you.

---

### Post by chee on 2010-11-27
No has heard of this?  Or done this?   Or read about this?

---

### Post by fixitdude on 2012-06-18
If you look back into the fixes there was a issue with the "stuttering" you talked about, and some other stuff at the link below.

You want to go to 12.04 Ubuntu, which is a major hassle but not so bad if you can just install it new and NOT upgrade.

I am still having problems with mythtv scanning the channels, but Kaffeine is working most of the time. There's been a lot of USB unplugging going on around here and I am really tired of it.

The power off stuff is mostly for mythtv and it had some sort of problems with it powering down.

I don't understand why these drivers have to get stuck, you would think these guys understand how to write code that doesn't get stuck by now.

[http://www.kernellabs.com/blog/?p=1388](http://www.kernellabs.com/blog/?p=1388)

Oh, and if you found this by searching google, you could look at my other posts on the 950Q.

---

### Post by jmore9 on 2012-06-18
I use a pinnacle 800i and hvr 1600 under 12.04 and both work the they should.  Only problem is me-tv is broken in 12.04 it worked in 11.10 and 11.04 but after clean install of 12.04 found it was broken.

Now kaffeine works outstanding , it would not scan at all in 11.10 or 11.04.  Go figure.

---

