---
title: "got codecs and plugins still no dvd playback"
date: 2009-08-03
forum: Mythbuntu
---

### Post by derrickadean on 2009-08-03
i have recently installed mythbuntu on an old p3 with 256mb ram
it works great except for dvd playback doesnt work on xine or the internal player i know i have all the right plugins and codecs and when i try to eject the disk i get an error message thats says failed to eject given device is not a volume drive cds will play fine

---

### Post by SiHa on 2009-08-04
Can you play DVD's outside of Myth?

---

### Post by klc5555 on 2009-08-04
> **derrickadean said:**
> i have recently installed mythbuntu on an old p3 with 256mb ram
it works great except for dvd playback doesnt work on xine or the internal player i know i have all the right plugins and codecs and when i try to eject the disk i get an error message thats says failed to eject given device is not a volume drive cds will play fine

Ubuntu head-scratchingly went to all scsi drive names with ver. 8.04, which makes your dvd drive something along the lines of "/dev/sr0" This would be fine, except the default Mythtv install still tends to list the drive as "/dev/dvd" As does the default install of just about all player software included with Ubuntu. So Ubuntu frequently can't find the referenced device when the software calls for "/dev/dvd".

See if any of these devices (or Mythtv frontend) can access the drive as /dev/sr0  (Or some /dev/srX number if you have more than one removable drive). If yes, then make the appropriate change in the various player configuration files.

---

### Post by KillerKiwi on 2009-08-04
Every single time I have this issue its been because the drive hasn't had its region set

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

```

sudo apt-get install regionset
sudo regionset

```

Make sure you select the correct region code
[http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries](http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries)

---

### Post by derrickadean on 2009-08-05
thank you guys i went to video settings and set the dvd devise dev/sr0/ and it worked perfect

---

