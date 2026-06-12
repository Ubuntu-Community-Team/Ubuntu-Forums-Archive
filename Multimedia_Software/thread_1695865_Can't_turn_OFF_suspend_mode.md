---
title: "Can't turn OFF suspend mode"
date: 2011-02-26
forum: Multimedia Software
---

### Post by lotusinbloom on 2011-02-26
Disclaimer:  I have very little linux desktop experience...I've only used command line stuff for work in my previous life.  I am joyfully coming off of a long addiction to MS but am having a bit of a hard time adjusting.

ISSUE:
I can't seem to figure out how to turn off suspend mode. I have turned every setting I could find in the power management to "do nothing" and I have turned off all of my power mgmt options in the system bios.  A "friend" suggested I remove HAL...which caused me to lose my secondary internal HD and all of my usb devices...and the issue persisted.  Every 20 minutes of no action the screen blanks and my monitor goes into standby mode which is making watching movies in bed a less than relaxing experience.  

Some background that may or may not be useful:  I installed kubunutu 10.04 (2.6.32-28-generic) from cd on a fresh HD.  Initially I had issues with the wireless network and alsa/pulse sound.  I worked through those through much trial and error but the suspend issue persists.  I've uninstalled and re-installed lots of packages I probably shouldn't have been messing with and would really like to avoid a reinstall as this seems to be the final fix I need to get things running the way I want them.  

Any advice is greatly appreciated!

---

### Post by inobe on 2011-02-26
your doing good, the more you play around, you become familiar with your system, keep it up.

i will try to help make it easier, and explain why some things act as if they are broken, fortunately kde is a very big powerful desktop environment, unfortunately it lacks it's weight on a 700mb kubuntu cd, it lacks many packages because it's on a cd and it doesn't have enough space, so we have to build onto it.

there are a few things you can do to expand the system.

first in package kit, search for **screensavers**

install those, now select a screen saver in system settings> display and monitor.

now go to power management and give it a try.

edit: the screensavers you want would be kscreensavers, you can get the extras too.

---

### Post by lotusinbloom on 2011-02-26
I'm not sure how or why...but this seems to have worked!!

Thank you very much!

---

### Post by inobe on 2011-02-27
> **lotusinbloom said:**
> I'm not sure how or why...but this seems to have worked!!

Thank you very much!

in some linux distributions like opensuse, it's a huge 4.7gig dvd iso, you may still find something missing!

nah, joking around :lol:

some things you should know, pulseAaudio isn't really needed, kde doesn't need it, it does a finer job on a gnome/ ubuntu desk, kde has kmix, kde is very well capable of handling your sound devices, for whatever reason' pulse was incorporated, i don't know why, i haven't the foggiest idea.

wireless gets better with every version of kde, currently i am on kde 4.6 with kubuntu 10.10, the changes are big and a great distance from where you are now, 4.4 ?

basically stating, you should prepare to make the jump to 11.04, or at least to 10.10, much has changed, over 30,000 bug fixes, i am certain many of the problems you've experienced were those of bugs!

when i stated that you are doing good, so as long kde is on a cd, you will always need to build, keep playing around with your system to prepare yourself for the latest and greatest, a lessor chance that you won't muck up the next installation ;)

if you need things like wallpapers, search in packagekit, get the missing extras, the stuff that can't fit on the cd, but can fit on a hard drive.

currently my system is configured very well, it's solid as a rock, very stable, yet i am getting ready to wipe the drive next month and begin again with 11.04, and desperately awaiting the next version of kde.

currently i have this box setup as a media server, watch stuff on my tv via network configuration, and i use it as my main box, so i'm on the box wile my family watches media from it on the other side of house, they don't need to load movies in some dvd/ bluray box, the systems performance is unaffected, 4gigs ram, 2tb hard drive space, i'm just showing off now, ignore this paragraph, it's late, i'm bored, nothing happening :P

---

### Post by lotusinbloom on 2011-02-28
ooohhh...media server huh...that sounds like fun.  In fact I think you've just given me my next project.  I guess now its time to figure out file sharing and such...or maybe I should just stay where I am until I can get to 11.04/4.6? Ah decisions decisions...stay tuned for some more threads of desperation from me...you've been quite helpful thus far.

---

