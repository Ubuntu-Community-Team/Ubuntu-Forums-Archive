---
title: "Can Maverick release with this bug?"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2010-10-04
Here it is:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

Duplicates and related bugs:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/643118](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/643118)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649534](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649534)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/646076)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/645377](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/645377)

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/646474](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/646474)

Then read Sebastien Bacher's most recent comments!

More, more, more!

It appears that the devs aren't sure what's up :confused:

First impressions do count and I'm stumped :(

Where do we go from here?

I'm NOT the turd in the punch bowl, I'm the guy that's trying to keep the turd out of the punch bowl :)

---

### Post by ranch hand on 2010-10-04
Sure it is good to go.  Bug "only" effects 6 people.  Not much hardware involved.

Every thing is good, every thing is fine.

Seriously I have to say that 10.10 works great on my hardware.  Compared to 10.04.  If we can release a LTS that excludes whole class' of hardware then there is no problem releasing 10.10.

---

### Post by Speed_arg on 2010-10-04
> **ranch hand said:**
> Sure it is good to go.  Bug "only" effects 6 people.  Not much hardware involved.

Every thing is good, every thing is fine.

Seriously I have to say that 10.10 works great on my hardware.  Compared to 10.04.  If we can release a LTS that excludes whole class' of hardware then there is no problem releasing 10.10.
There are quite a lot of bugs. In my netbook I can't even install. Also, after suspending network stops working. It should be released the 29 a more polished product, and not the usually buggy ubuntu as always. The only polished product you can see are LTS and after .2

IMO Ubuntu should release distros every 1 year and not 6 months.

---

### Post by ronacc on 2010-10-04
they probably figure that there can't be all that many crt's left.

---

### Post by ktp on 2010-10-04
> **ranch hand said:**
> Sure it is good to go.  Bug "only" effects 6 people.  Not much hardware involved.

Every thing is good, every thing is fine.

Seriously I have to say that 10.10 works great on my hardware.  Compared to 10.04.  If we can release a LTS that excludes whole class' of hardware then there is no problem releasing 10.10.

I have seen them release with lot worst bugs then this.  So ya I kind of agree with you.

---

### Post by cariboo on 2010-10-04
Weren't these same Intel chipsets problematic in Karmic and Lucid too?

---

### Post by 23meg on 2010-10-05
Since it's getting Martin Pitt love, I wouldn't be worried ;)

(Edit: [Fixed already]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807/comments/34"), by preventing g-s-d from changing XRandr settings. Please test again with the new version, making sure the use_xorg_monitor_settings gconf key is present and set to true.)

---

### Post by tormod on 2010-10-05
> **mgunes said:**
> Since it's getting Martin Pitt love, I wouldn't be worried ;)
Cheers for that :)

This bug was fixed in the package gnome-settings-daemon - 2.32.0-0ubuntu2

---

### Post by xebian on 2010-10-05
> **Speed_arg said:**
> ...

IMO Ubuntu should release distros every 1 year and not 6 months.

OR more correctly, you must upgrade only every year!!!

Releasing every six months is Ubuntu's prerogative.  Your prerogative is whether you will take it or not, and take it now or later or never.  Plain and simple.

---

### Post by kansasnoob on 2010-10-05
> **mgunes said:**
> Since it's getting Martin Pitt love, I wouldn't be worried ;)

(Edit: [Fixed already]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807/comments/34"), by preventing g-s-d from changing XRandr settings. Please test again with the new version, making sure the use_xorg_monitor_settings gconf key is present and set to true.)

I noticed that first thing this morning.

I was admittedly worried as I saw that effect many different hardware setups.

---

### Post by 23meg on 2010-10-05
> **kansasnoob said:**
> I noticed that first thing this morning.

I was admittedly worried as I saw that effect many different hardware setups.

Did it affect any of yours? If so, please test again with the new version.

---

### Post by kansasnoob on 2010-10-05
> **mgunes said:**
> Did it affect any of yours? If so, please test again with the new version.

Yes, I had just been commenting at the bug that Martin Pitt now released a fix for, but I filed a separate bug so Tormod Volden could check some info:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/654660](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/654660)

I hadn't been able to get X with a Live CD since about the 16th of September, and I'd finally just yesterday morning figured out a workaround for the Live CD:

> I was finally able to get the Maverick RC Live CD to boot by pressing F6, then ESC, then typing "text" (w/o the quotes), and then typing:

gconftool-2 --type bool -s "/apps/gnome_settings_daemon/xrandr/turn_on_external_monitors_at_startup" false

Then just typing "startx" (again w/o the quotes) I got a desktop with the expected modes

I don't know why accessing a TTY in other manners wouldn't work, but simply adding "text" to the boot parameters and editing gconf did it. Probably something about when the TTY was accessed :confused:

I'm always learning something new, like simply adding "text" results in a non-graphical boot on the Live CD.

I'll try the Live CD tomorrow when gnome-settings-daemon - 2.32.0-0ubuntu2 should be included. I always check the manifest first for goodies I'm waiting on.

---

### Post by sdowney717 on 2010-10-05
FIXED for me it is fixed. 
It boots up and refresh is 85
Wow, that is nice to see.

---

### Post by Speed_arg on 2010-10-05
> **xebian said:**
> OR more correctly, you must upgrade only every year!!!

Releasing every six months is Ubuntu's prerogative.  Your prerogative is whether you will take it or not, and take it now or later or never.  Plain and simple.

Its not about the upgrading thing, but about how polished releases are. Maybe 9 months, say you add just more 3 months to the current schedule just for fixing the bugs.

---

### Post by kansasnoob on 2010-10-06
Yippeee, I tested the 10-6 daily and it works :guitar:

---

### Post by cariboo on 2010-10-06
> **Speed_arg said:**
> Its not about the upgrading thing, but about how polished releases are. Maybe 9 months, say you add just more 3 months to the current schedule just for fixing the bugs.

If you want polished, stick with the LTS releases.

---

### Post by kansasnoob on 2010-10-06
Thanks to whoever added the "solved" tag :)

I completely forgot.

---

