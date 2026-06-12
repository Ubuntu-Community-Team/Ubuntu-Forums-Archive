---
title: "Sound Driver Registry Problem with Wine 9.34"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by evanmanny on 2007-05-28
I'm using wine 9.34 and trying to get Rosetta stone to work. When I run the program there is no sound and I get the error "err:wave:DSDB_MapBuffer Please run winecfg, open 'Audio' page and set 'Hardware Acceleration' to Emulation'".  When I open winecfg and go to the audio tab I get this message that says "There is no audio driver currently specified in the registry. A recommended driver has been selected for you. You can use this driver or select another driver if available. You must click Apply for the selection to take effect." Clicking ok brings up the audio page where OSS Driver is selected and NAS Driver, JACK Driver, EsounD Driver, and ALSA Driver are the other choices. Hardware Acceleration is set to Full. Now I've tried selecting all of the different drivers and changing the acceleration to emulation like the original error suggested. If I close winecfg after changing the settings and then open it again everything is the way it should be after changing it. If I run Rosetta though I get the original message and then winecfg gives me the same message and goess back to OSS.

I'm really lost on this. I'm thinking that it might have something to do with an entry in wine's registry. Maybe wine running Rosetta somehow results in the deletion of a key that holds information on audio drivers? I've done a lot of searching around on the internet and haven't found any cases of the wine message chronically coming up. Any help would be greatly appreciated.

---

