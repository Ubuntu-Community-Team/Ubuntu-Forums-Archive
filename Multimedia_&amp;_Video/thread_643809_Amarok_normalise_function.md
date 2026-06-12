---
title: "Amarok normalise function?"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by daverave999 on 2007-12-18
In quite a few places now I've seen mention that Amarok can normalise music level 'on-the-fly', either through a script or through a setting that is already present. Despite extensive searching, I seem unable to find how to do this!

Could anyone suggest how I might go about it please?
TIA

---

### Post by Whiffle on 2007-12-18
Tools > Script Manager > General >  amarok_replaygain

---

### Post by daverave999 on 2007-12-18
Perfect! Thanks very much!

For those who read this looking for the same info, to store tags with the normalising info after installing the script:

1. Click configure in the same place that you run the script and look at the dependencies. Install those you don't have through Synaptic. I could only find mp3gain and vorbisgain though I'm not really bothered about other formats at the moment. These are what store the info.

2. Right-click anything in your Amarok playlist, and choose 'Apply replaygain tags>To entire collection using album tags'. This will take a long time.

If you don't do this, replaygain will compare the levels with other tracks in the playlist as I understand it.

Thanks again Whiffle!

Hope this helps others.

---

