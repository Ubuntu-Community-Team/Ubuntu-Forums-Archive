---
title: "How to get Diamond Extreme 7.1 in Natty working"
date: 2011-07-10
forum: Multimedia Software
---

### Post by Shogun15 on 2011-07-10
Dear all,

I am trying to set up the Diamond Extreme 7.1 DDL in Natty. The only thing that works are the analog outputs.

But in order to enjoy movies with DD 5.1 or DTS I need the optical out to function. Another problem is that my old Yamaha receiver doesn't handle DTS directly, so I need either Dolby Digital Live to transform it or ffdshow audio codecs (throughput to spdif only results in noise). And third, I am addicted to DDL to enjoy stereo sources in surround sound. DDL works much better than Dolby  Prologic II.

Any idea how to get this working in Natty? At least I need to get the optical out working (though Dolby Digital Live is also very desirable). I tried to set things in alsa mixer but without results. Coming from the Windows side and being new to Ubuntu I really have a hard time to get things working the way I was used to. Is there at least some similar codec pack like ffdshow that I could use in Ubuntu?

Any help would be very appreciated.

---

### Post by Mark Phelps on 2011-07-11
Notice this uses the CMI8768+ audio chip.  If you Google for Open Sound (should find 4Front Technologies) and go to their site, you will have to hunt around the for info on that chip.

You may then have to replace ALSA with OSS to get the sound working with this chip.

---

