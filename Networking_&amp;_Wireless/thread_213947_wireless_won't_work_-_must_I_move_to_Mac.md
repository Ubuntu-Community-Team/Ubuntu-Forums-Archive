---
title: "wireless won't work - must I move to Mac?"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2006-07-12
My bcm4306 card worked fine under Breezy using NDIS.  I've tried to use the same commands (subsituting eth1 now for wlan0)
sudo modprobe ndiswrapper //seems to work okay
sudo iwlist eth1 scan // this does not work - does not recognize scan 

but how else am I to get the essid name ?  

It's really frustrating that the Ubuntu team really broke wireless in Dapper and then ignored any user documentation on the changes.  I've spent hours trying to get this to work and I can't afford much more time - maybe it's just time to throw this in the trash and buy a powermac.

---

### Post by Nels on 2006-07-12
In the last week I installed Ubuntu on my PowerBook, dual booting with OSX. I've been very happy to find that everything pretty much worked and was recognized. The one great exception is the wireless. I also have the BCM43xx card. Trying to get this recognized has become a real headache and I can see how it could be a deal breaker for a switcher. I've also spent hours following the various instructions, on various threads, with no luck. I've downloaded (through wired connection) network manager gnome, wpa supplicant, wpa gui, firmware updates, BCM43xx fwcutters,etc. etc.. I've altered files and configs and who knows what, no doubt, leaving  it all a complete unintelligible, irreparable hash I'm afraid. It would seem that something so fundamental as this would have been set up to work more easily. This would have been a good place for a GUI front, if only to put it all in one place. After many frustrating hours with this it is good to boot into OSX where it all works without a hitch and for months at a stretch. But nevertheless I do appreciate the great future of Linux in general and in Ubuntu in particular. It is a surprisingly attractive OS that does give even more room for expression then a mac.

---

