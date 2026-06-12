---
title: "HVR2255 fails with mythbuntu 16.04 version 0.28"
date: 2016-09-22
forum: Mythbuntu
---

### Post by singogli on 2016-09-22
After a fresh install of mythbuntu 16.04 with version 0.28-55-g2faf5fe Hauppauge HVR2255 capture card does not work.  Backend log shows "Opening DVB frontend device failed .#012#011#011#011eno:No such file or directory (2)" errors. Also "Problem with capture cards. card x failed init" errors. Correct firmware is installed.  Syslog shows firmware loading correctly and both DVB adapters registering with no errors. I can schedule recordings with HDHomerun device and play them so everything else is working .  Deleting all capture cards and reinstalling there is no change to the HVR2255 status.  HVR2255 was working with previous 14.04 install with modified kernel so hardware is O.K. uname -a shows 4.4.0-38-generic which is supposed to have support for this card.  Frontend system status shows "Tuner x has an error" for all four HVR2255 tuner devices. Does anyone have the HVR2255 working with the 16.04 mythbuntu release?  Any problems getting it to work?  Is there anywhere else to look for why cards failed init?

---

### Post by Salvador_Cabaruvia on 2016-10-30
I having the same issue with one HVR-2255, but my older cards, hvr-1600 and 1800 appear to work. Running tests now such as livetv. Note: the mythbuntu1604.1.iso when I first installed appeared to having all my hvr cards working but did a software update and now HVR-2255 stopped working.  I will tomorrow reload mythbuntu 1604.1.iso and see if it works without the updates. Post results to let you know.

---

### Post by Salvador_Cabaruvia on 2016-10-31
I have reinstall mythbuntu1604.1.iso that downloaded from Ubuntu site. I did complete install where formats /dev/sda1 and does full install. I choose the option to down updates and followed the defaults. You have to download hvr-2255 firmware, linuxtv wiki has directions. Once this is done my hvr-2255 is working. Of course you have to configure mythtv but once done, I checked livetv and I can switch between all four tuners. Right now I am checking out if I can record four shows at once. Hope that helps. I won't be doing any updates until see that other people have it working with updates.

---

