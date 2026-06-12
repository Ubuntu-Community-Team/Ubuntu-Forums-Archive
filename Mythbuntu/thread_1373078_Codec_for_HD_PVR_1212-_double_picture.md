---
title: "Codec for HD PVR 1212- double picture"
date: 2010-01-05
forum: Mythbuntu
---

### Post by jshaw16 on 2010-01-05
I have install and have gotten the Hauppauge 1212 to work on Mythbuntu after some effort. Unfortunately, the View TV comes up with 2 identical pictures when connected to the cable source. I have tried to correct this by adjusting the TV setup, but have not been able to get a high quality picture with just one picture on the screen. Has anyone had this problem and found the appropriate settings? My trial and efforts have not produced good results. Any help would be appreciated.

---

### Post by the_pod on 2010-01-05
Above and below each other?  If so, you most likely need to turn off the deinterlacer.  It's stashed somewhere in playback in a sub-menu under the profiles that are applicable to different resolutions.

Hope that helps.

---

### Post by jeffas on 2010-02-07
I had exactly that (two copies of the picture, one above the other). I don't think this is anything to do with codecs or what receiver you're using (I was getting this on playback of recordings as well).
I fixed it by setting primary deinterlacer to either 'Linear blend" or "One field" in each profile, as described here: [http://www.mythtv.org/wiki/Deinterlacing](http://www.mythtv.org/wiki/Deinterlacing). That page also gives alternative approaches.
Thanks the_pod for correctly identifying this as an interlacing problem!

---

