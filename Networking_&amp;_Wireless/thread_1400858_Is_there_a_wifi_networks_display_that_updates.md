---
title: "Is there a wifi networks display that updates?"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by bit mad on 2010-02-07
I would like to be able to drive around looking for free open wifi hotspots (my passenger of course, not me!) The current NetworkManager applet doesn't refresh, so you end up with a huge ever-growing list that never clears, and no idea what's actually currently in range at the moment. 

This applies to the netbook version of 10.04 and also Linux Mint (7). At the moment I'm favouring Linux Mint because it shows an icon if it's a secured non-open network and Ubuntu doesn't* (quite apart from the frustrations of having all the windows always maximised with no easy way to drag and drop copy a file! - and the shut down menu doesn't always work either. -and what's the point in a Big Friendly Icons system for netbooks when there are still so many tiny icons to try to hit with the mousepad?) *

But anyway, can I install some sort of "wardrive"-ish applet that would replace the usual method, showing a frequently updated list of current connection possibilities? 

Thanks :)

---

### Post by bit mad on 2010-02-11
Apparently wifi-radar might do the job
[http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html](http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html)
[http://www.linux.com/archive/feed/55647](http://www.linux.com/archive/feed/55647)

Thanks to  [http://forums.linuxmint.com/viewtopic.php?f=53&t=41492#p238407](http://forums.linuxmint.com/viewtopic.php?f=53&t=41492#p238407)
:)

---

### Post by bit mad on 2010-02-12
well it kinda works, but still fills up with wifi that I've left behind streets away, doesn't seem to clear, can't be filtered to show only free/open networks or display in any other order than the default, and hangs after a while. Not quite what I wanted, but it'll do for now.
[]("http://www.linux.com/archive/feed/55647")

---

### Post by bingobingo on 2010-02-13
Picky, Picky, wifi-radar works just fine. It shows all live nets in your area, just delete all the other connection that read 'null', no signal strength, or with no 'blue' in it.

---

### Post by bit mad on 2010-02-14
Picky? Maybe - but IMHO being picky is a what drives human progress :)
If we have needs and wishes and work towards them, or find ways to inspire others to work towards solutions, it is to the benefit of all.

I'm new to wireless networking and laptops, but I assumed there would be an easy way to see what networks were within range on which channels, a list that would would dynamically change if you move about (without clogging up with details no longer relevant), and allow you to easily pick one and try to connect.

Instead, I find the whole thing lacking and confusing. We get a list of networks that clogs up, no clues whether two strong networks are on the same channel, possibly conflicting with each other, and I've had a load of frustration as I try to make sense of network names that hang about from one PC session to the next despite the lappy being booted up in a new location, with no way to clear the details, lists of networks that won't refresh, connections that fail to connect (or even appear at all despite them being there in Windows or another distro) with a message about another network miles away disconnecting when I'm trying a different one... there's just no good dialog about what's going on or why. Up comes some 'key ring' stuff which makes no sense to me whatsoever so I just hope for the best... when it works it's great but, wow, it's like pulling teeth sometimes!

Wifi-radar doesn't work from the menu. It didn't work from the command line either, until I "sudo chown"ed a .config file! Now I find it's easier to call it from a script, and it even annoys me that the finished script has to sit there uselessly on the screen because if you close it then it closes the app that it has launched too! This is all madness to a refugee from Windows, LOL

Surely wifi shouldn't be this annoying?! I had to jump through hoops to get it running at all, and now it's far from optimal in use, too. Perhaps it's just me, though?! It's puzzling  that something as crucially useful like this can be in such a state on an otherwise impressive OS.

---

### Post by bit mad on 2010-02-14
Looks like swscanner might be more my cup of tea :)
[http://www.swscanner.org/en/node/230](http://www.swscanner.org/en/node/230)

---

### Post by sparvik on 2010-02-14
not much help but try a LTS release of ubuntu. Less frustration I think.

---

### Post by niffcreature on 2010-02-14
i think that the speed at which available wireless networks is updated is a function of the hardware.

---

### Post by bingobingo on 2010-02-15
No you are right that there is something wrong with wifi-radar in 9.10, I already posted to ask others about this, and no response, I do not even know if it is working for anyone or no one. I do remember some cool wifi apps on [www.revision3.com/tekzilla](www.revision3.com/tekzilla), but I would have to search their archives.

---

### Post by bit mad on 2010-02-18
Thanks

I've solved my 'problem' from the other direction, as such - I've tried all the easy places to park in my local town in the evening and I've gotten to know where there are free hotspots - the hard way by trial and error :p

---

