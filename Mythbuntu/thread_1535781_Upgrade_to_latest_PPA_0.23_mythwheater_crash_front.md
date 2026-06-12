---
title: "Upgrade to latest PPA 0.23: mythwheater crash frontend"
date: 2010-07-21
forum: Mythbuntu
---

### Post by dibuntux on 2010-07-21
As I state in the title, mythwheater, that was working couple of weeks ago, now crash the frontend as soon as selected.

Any idea? TIA

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by dibuntux on 2010-07-27
From mythweb, if I select mythweather i get:

Error

Could not find '/usr/share/mythtv/mythweather/scripts/us_nws/animaps.pl'.
This most likely means that MythWeather is not installed on this host.

So, I tried re-installing the mythweather plugin - but i get the same error.

Any ideas? TIA

---

### Post by uncle hammy on 2010-07-27
I had the same issue.  It appears a bunch of the satellite screens have been removed, and if you have them listed as a source it causes the crash.  

Try going through your screen settings and doing a change location for your static and animated maps.  Be forewarned, if you're in the USA, what's available now is sad...nothing but environment Canada maps.

---

### Post by dibuntux on 2010-07-29
Thank you for your suggestion, I'm in Rome, Italy.

I used to have Animated map, current conditions and 3 days forecast. 
Now only 3 days forecast can find a location... 

So it is a jump backward for mythweather... sad

Hope it helps other puzzling with it.

---

### Post by lerrup on 2010-10-14
> **dibuntux said:**
> Thank you for your suggestion, I'm in Rome, Italy.

I used to have Animated map, current conditions and 3 days forecast. 
Now only 3 days forecast can find a location... 

So it is a jump backward for mythweather... sad

Hope it helps other puzzling with it.

Well it's just helped me!

thanks.

Anyone know how to add new sources?

---

### Post by bcg30506 on 2010-10-14
I too ran into this issue after upgrading to 0.23.1 and removing then re-adding all my screens fixed it.  They changed sources from weather channel to wunderground.

---

