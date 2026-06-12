---
title: "loopmounted 12.04 iso on hdd no wireless icon"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by utnubuuser on 2012-03-01
Hoping someone can point me in the right direction...

I've got the 12.04Beta iso loopmounted from my hdd, and it boots ok, but there's no network icon available for selecting wireless network.

I've also booted 11.10 this way, and with 11.10 I  get the network icon, though all the managed networks are greyed-out, and there seems to be no way to enter the network key (wpa2 wpa2-personal).

Any suggestion where to start searching?  Might my permissions be askew because of the way I've got the ISOs booting from within my /boot folder? The instructions I've followed for booting the iso from the hdd is to create a folder, /iso, within the /boot folder, add a casper-rw file and the appropriate entry in my 40_custom file.
To do that however, I have to work with gksu-nautilus in order to move the iso from my /Downloads folder to the /boot/iso folder...   might that be messing with the permissions of the liveCD iso? (They, /boot and /iso,  are owned by root)
I've booted other ISOs this way, and don't recall any such problems - ie:10.04,

---

