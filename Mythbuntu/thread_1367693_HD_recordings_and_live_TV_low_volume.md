---
title: "HD recordings and live TV low volume"
date: 2009-12-29
forum: Mythbuntu
---

### Post by Areceth on 2009-12-29
All the recordings (and live tv) from my HDHomerun have really low volume. Is there a way to raise the volume on these recordings? I have already ensured that all the settings in alsamixer are at 100%. The volume on the analog channels is just fine.

---

### Post by azmyth on 2009-12-29
I believe the volume is low from the signal. I'm getting my HD OTA and I was constantly fussing with the volume and at times I'd go to one area of myth and get blasted. I ended up doing the volume leveling trick with ladspa. Not perfect but I haven't fooled around with the leveling settings.

[http://www.knoppmythwiki.org/index.php?page=VolumeLeveling](http://www.knoppmythwiki.org/index.php?page=VolumeLeveling)

You can't run mythmusic through it or the music will sound really bad.

---

### Post by the_pod on 2009-12-30
I made a tweak yesterday to my system that I found somewhere in these boards and it worked out for me.  The problem was that my HD channels were substantially lower in volume than my other channels (all are digital).

In  Setup > General, I changed it from Dolby 5.1 to Stereo leaving everything else the same and saw an improved volume level on all the HD programming on my system. 

My setup is digital coax directly to myth, output to receiver.

This may or may not help you but it certainly improved my day yesterday after 4 months of low volume and wife fussing.

---

### Post by Areceth on 2009-12-30
> **the_pod said:**
> I made a tweak yesterday to my system that I found somewhere in these boards and it worked out for me.  The problem was that my HD channels were substantially lower in volume than my other channels (all are digital).

In  Setup > General, I changed it from Dolby 5.1 to Stereo leaving everything else the same and saw an improved volume level on all the HD programming on my system. 

My setup is digital coax directly to myth, output to receiver.

This may or may not help you but it certainly improved my day yesterday after 4 months of low volume and wife fussing.


It was already set to stereo. I did switch to 5.1 just for fun and the volume got a lot lower. 

I remember a post somewhere about using ac3filter to accomplish this, if anyone knows a good post or howto, otherwise I will try the ladspa trick.

---

