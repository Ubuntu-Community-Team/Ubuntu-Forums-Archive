---
title: "Odd WICD issues"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by darkenedday on 2008-12-10
I recently installed wicd to use be able to browse wireless networks in e17, since WICD requires no tray, I am attempting to use the wl driver for my dell xps m1530's wireless card, I believe its a dell 1395 wireless card. . . it worked fine under networkmanager and I had managed to get it to work in WICD by removing my ndiswrapper driver and using the proprietary restricted driver "wl" instead, however I then restarted  my computer later that night and suddenly I could not see any networks... 

I then looked at the restricted driver manager and realized that the wl driver was activated but "not in use" which I found to be odd. . . so I deactivated it and reactivated it and still no networks in WICD. . . 

ifconfig revealed that my wireless had changed to eth1 from wlan0. . . weird. . . 
ifup eth1 or eth-anything returns the error "ignoring unknown device eth(whatever)=eth(whatever)" 
:confused:

help?

maybe a conflict with the OSS driver for the wireless and the restricted? I do remember I had to blacklist one of the drivers before to use my ndiswrapper, I believe it was "wl" but then why would it work at all. . . ? 

if someone could walk me through un-blacklisting either driver and possibly re-blacklisting the OSS one if the latter doesn't fix it altogether, that would at least be a start...

---

### Post by darkenedday on 2008-12-10
bump

---

### Post by moore.bryan on 2008-12-10
> **darkenedday said:**
> ... since WICD requires no tray, I am attempting to use the wl driver for my dell xps m1530's wireless card,...
could you explain what you mean here?

---

### Post by darkenedday on 2008-12-10
> **moore.bryan said:**
> could you explain what you mean here?

e17 has no system tray like gnome's where u'd normally see your network manager applet apear
running with wicd --no-tray

UPDATE: I've managed to figure out to edit my blacklist file, just had to find it, 

and

lshw -c network reveals that the wireless interface is "UNCLAIMED" at start up, it would seem it's not loading ANY drivers for my network card on startup. . .

it's a bcm4312 chipset if that helps

---

### Post by yasha on 2008-12-10
I had the same issue with my 4328 chip. I installed, and I think I followed some old instructions on how to get the wireless working rather than straight off using the restricted STA driver, this changed it to WLAN0 from eth1, then trying to use the STA driver afterwards didn't work at all, as it would install but say not in use.

Disabling the modules didn't work, so I just waxed the whole f'n thing and started over. Now it's working again with the STA driver.

---

### Post by moore.bryan on 2008-12-11
got it... unfortunately, i don't have any insight for you, but if anything comes to mind, i'll let you know.

---

### Post by darkenedday on 2008-12-12
alright, I fixed it, I resinstalled and went back to 8.04, everything seems to work better in 8.04, 8.10 broke almost everything. . . it's even working with my ndiswrapper driver now. . .

---

### Post by moore.bryan on 2008-12-12
that might make everything else make a little sense. i couldn't find anything definitive about *your* wireless card, but it seems as though some percentage of dell lappies have atheros cards. if that actually is the case for you, then the upgrade from hardy to intrepid and subsequent wireless "break" my have been because of the introduction of the new atheros drivers. exactly why that also screwed-up your ndiswrapper stuff is beyond me, though.

---

### Post by darkenedday on 2008-12-12
who knows, computers are logic machines, and at times a bit too logical for us humans IMO. . . sometimes things "just happen"

however, I have the dell 1395 wireless mini-card PCI-e
it's a broadcom 4310 revision 01 chipest though. . . which seem to have problems period, unless you do use ndiswrapper. . .

---

### Post by moore.bryan on 2008-12-12
fair enough... i hope intrepid eventually works for you!

---

### Post by darkenedday on 2008-12-12
judging by past experience with ubuntu, I will most likely have to wait 6 months for the next release, interpid didn't come with much new anyway, so it's ok, I think what really caused my problems was installed kubuntu-desktop, with kde 4.1 thats when the network trouble started (something about knetapplet and my normal network manager applet) and then once I installed 8.10 everything went to hell. . . 

it's ok, worst case scenario I'll switch back to openSUSE which is simple enough for my fiance to use, but I know everything tends to work more smoothly in my experience... it would seem my days of switching distros like socks are over though, untill I can get my fiance's laptop up and running :-)

---

### Post by moore.bryan on 2008-12-14
i actually have found intrepid working infinitely better with my lenovo thinkpad z61e, but once again: with linux it's all about customization. in my point of view, as long as one is using *some* kind of linux that's a good thing.

:-)

be well and best of luck.

---

