---
title: "Kaffeine 1.0-pre2 deinterlacing dvb"
date: 2009-11-02
forum: Multimedia Software
---

### Post by r-mo on 2009-11-02
Just upgraded to karmic and it comes with the pre-release kde4 version of kaffeine :( Is there any way of getting it to deinterlace the video from my dvb card?  It used to be that you could just press 'i' to turn it on or off in the good old days.  The only thing you seem to be able to configure now is keyboard shortcuts and interlacing isn't in there :(

On a side note is it a design philosophy of kde4 to remove features from its apps or is it just that they need to mature a bit more?

---

### Post by realzippy on 2009-11-03
This I would like to know also.
I want my old kaffeine back in Karmic!!  ;)
Tried to compile 0.8.8 but no way,the KDE3.5 libs are missing.
Found no solution to get them run in Karmic,any help please?!
Kaffeine 1.0-pre2 uses the tvtime deinterlacer,0.8.x used Xine (afaik).edit:
also tvtime,but where to configurate?.

Not amusing is the incredible amount of time what it takes now for channel
hopping,even on the same transponder.
Channel switching takes nearly 3 seconds.. can anyone confirm?

---

### Post by realzippy on 2009-11-03
Found a ppa to downgrade to good old kaffeine that works;completely remove Kaffeine 1.0-pre2 before.

wget [https://launchpad.net/~pkern/+archive/ppa/+files/kaffeine_0.8.7-1ubuntu6~ppa0_i386.deb](https://launchpad.net/~pkern/+archive/ppa/+files/kaffeine_0.8.7-1ubuntu6~ppa0_i386.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_i386.deb

64bit:
wget [https://launchpad.net/~pkern/+archive/ppa/+files/kaffeine_0.8.7-1ubuntu6~ppa0_amd64.deb](https://launchpad.net/~pkern/+archive/ppa/+files/kaffeine_0.8.7-1ubuntu6~ppa0_amd64.deb)
sudo dpkg -i kaffeine_0.8.7-1ubuntu6~ppa0_amd64.deb


edit : impressed of old kaffeine speed compared to the new one...do not understand why they changed a well running application
to a beta (alpha) version of a program what just seems to have the name in common?No need for kde 4 in gnome ;-)

---

### Post by mtron on 2009-11-09
well, the change is needed because kaffeine up till version 0.8.8 uses qt3. So the port to qt4 is on the way. This will bring us much more possibilities - once phonon is really done.

---

### Post by sparky64 on 2009-12-28
Quick thanks.
I really hope they sort out the "new kaffeine it's like something that belongs on windows at the moment.

Oh and don't forget to lock the version.
I had to do this twice as i had a load of updates (new install).

---

