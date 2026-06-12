---
title: "Belkin Wireless G PCI Adapter"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by em3raldxiii on 2009-11-09
First of all, please let me appologize if there has been an identical thread for this issue, but suffice to say that it had me stumped for several days.  I decided to post this thread as soon as I had the problem solved - I would be happy to remove or merge this thread with an appropriate one, but for now I wanted to help my fellow Ubuntu users immediately and with as little pain as possible.

**Outline of the Problem**
Freshly installed Ubuntu 9.10 Karmic Koala on an oldish computer (think Athlon XP processor, and an AGP video card to get the idea of it's approximate age).  Upon installation, the wireless NIC did not show up.  At all.  If I did *lspci *in the command prompt, I was given a generic Atheros network adapter (Ethernet Controller: Atheros Communications Inc. Device ff1a (rev 01); since the fix (see below), it now shows up as *Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)*.

There were no wireless devices showing up in *System > Administration > Network Tools*.  I was beginning to despair, but fear not!  The solution was ridiculously simple.

[B]Quick Specs on my system.
[/B]Clean install of 9.10, fully updated as of Nov 8, 2009.
No changes to anything, aside from a few failed MadWIFI makes (apparently the stable versions are not compatible with our kernel).
Network Card:***  Belkin Wireless G***

[LIST]
[*]  On the card itself is this:  **F5D7000v8**
[/LIST]

[LIST]
[*]  Also on the card is this:  ver **8000tt**
[/LIST]

[LIST]
[*]  Further digging got me this chipset:  **AR5007G**  (note this is not 'EG' ... I dont know what the difference is)
[/LIST]
Note:  Apparently the different versions (such as v7 and lower, or ver 7000 and lower) use a different chipset than the Atheros one, and so problems with those cards may not be helped by this.

I have enabled all of the various multiverse and universe repositories, although I don't think that matters at this point.  I haven't installed anything else, except *build-essential* which was needed for the 'make' commands I was trying on a bunch of failed attempts to fix my wireless problem.

**Final Solution**
Apparently, this card is supported by the Ath5k driver.  Now from what I have read, this may not be the highest performance driver - apparently the ath9k is supposed to be better some how ... faster, supporting more features, etc.  But you know what?  At this point, I am not worried about that.  I just want the darned thing to work, know what I am saying?  So for some crazy reason, the Ath5k driver is blacklisted in the official Ubuntu 9.10 install.  I have no idea why ... there is probably a reason.  So the solution is simply to remove the blacklisting.

Here is how to do this:


[LIST=1]
[*]Open your favorite terminal application: * Applications > Accessories > Terminal*.
[*]Edit your */etc/modprobe.d/blacklist-ath_pci.conf* file:
```
gksu gedit */etc/modprobe.d/blacklist-ath_pci.conf*
```
[*]Comment out the line that says 'blacklist ath5k'by putting a # sign in front[B]:
[/B]```
#blacklist ath5k
```
[*]Bookmark this page, then Reboot your computer (Note that if you were a more advanced Ubuntu user than me, you would just do a modprobe somethingorother code in here and I think you can skip the reboot, but I am just a regular joe who doesn't know such things).
[/LIST]
Now, apparently you might have to also comment out the same line in your */etc/modprobe.d/madwifi.conf *file, but I don't even have that file, so I cannot verify this.  You may want to check by using* gksu gedit /etc/modprobe.d/madwifi.conf ... *if you get a blank page, then just close it without saving (it means you don't actually have that file so it shouldn't be an issue).

Okay ... that's it folks.  I know I sorta beat the thing to death here by being so verbose, but I wanted to make sure that even completely new users to Ubuntu would be able to follow this.  Please don't be afraid to ask questions - even things you think might be silly.  And also, if you have something to suggest or add, please try to keep it as novice-friendly as possible.  I absolutely hate finding "help" pages that are too technical to get through.  Ubuntu is supposed to be Linux for Human Beings here, which includes novices ;)

---

### Post by BugBear on 2009-11-22
Thanks for making the effort to post your solution.  It had me hopeful as I am using a Belkin G Plus card that worked fine out of the box with Ubuntu 8.04 but is nowhere to be found in the system after installing Ubuntu 9.10.
Unfortunately your fix didn't sort out my problem - the card is still not recognised.  Some additional detail:
Model no: F5D7001 ver. 2001df
Serial no (?) : 2006280FD59
There is also a Broadcom chip on the card with the markings:
BCM4318EKFBG
HD0615  P20
778981  B5

I'd greatly appreciate any other suggestions on how to get this card to work again...
Peter

---

### Post by em3raldxiii on 2009-11-23
It does sound like a similar issue but it also looks like your card has a Broadcom chipset.  I am on my phone right now so I can't really be of much help atm.  

On a more frustrating note, after moving that computer to its permanent home, the wireless no longer showed up.  And entering modprobe ath5k seemed to load the modules only once.  When I tried to add it to the modules file, it would load the modules but I was never able to see the WiFi networks again.   I eventually gave up (4 hrs later), and I went and bought a D-Link wireless G pci card.  I used the list of known working out-of-the-box hardware (which i'll link later).  I popped it in, booted, and everything was good.  It has a different atheros chipset.

---

