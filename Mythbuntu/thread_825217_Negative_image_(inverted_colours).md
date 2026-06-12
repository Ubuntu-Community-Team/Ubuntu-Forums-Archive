---
title: "Negative image (inverted colours)"
date: 2008-06-10
forum: Mythbuntu
---

### Post by nelsonmuntz on 2008-06-10
Having just gotten over a double image issue by updating my deinterlacer settings (thanks again laga), I've now immediately hit two new issues:

1. The LiveTV image is displaying with colours inverted. On first powering on the machine this evening and starting LiveTV, the colours appeared to be normal, but all subsequent attempts to start LiveTV (including after powering the machine off and on), have returned it to showing negative images again. I've tried various deinterlacer options, including my original one (which incidentally no longer exhibits the double image issue!) but to no avail. Note that I don't have the 'invert' filter set within my playback settings. I tried adding this just for kicks, but it made no difference!

2. Frontend now crashes without a word when exiting LiveTV. The last line in the mythfrontend.log file reads:

    2008-06-11 00:29:36.771 TV: Changing from WatchingLiveTV to None

There is also nothing untoward appearing in the mythbackend.log file.

I've failed to unearth anything on these two issues here in the forum or using Google. If anybody has suggestions, I'd be most appreciative.

Thanks,
nelsonmuntz

---

### Post by JugeHuge on 2008-06-11
Hello..

1, You mean that people looks like smurfs??
here is solution for that: [https://help.ubuntu.com/community/MythTV/FAQs]("https://help.ubuntu.com/community/MythTV/FAQs")

```
 Question: After my Hardy (Mythtv .21) upgrade I have blue skin people with the MythTV internal player, using ATI video card using the free drivers. What happened?!

Answer: It seems Mythtv .21 can set the Hue to "0". You can set it back (to approx 50%) and your color should come back. To do that:

   1.      Open MythTV and select Live TV.
   2.      Press M to bring up the menus
   3.      Arrow down to Adjust Picture then hit right arrow, then arrow down to Hue.
   4.      Press the right arrow to bring up the slider.
   5.      Press the right arrow until it's at approximately 50%, or whatever looks best for your setup.

If you press M inside LiveTV and get nothing, (no slider, and it just goes back to Live TV) check to make sure you have the OSD theme installed and selected correctly under the menu in Utilities/Setup > Setup > TV Settings > Playback OSD. 
```

2. i have same problem and haven't found solution on that..

---

### Post by nelsonmuntz on 2008-06-15
Thanks JugeHuge, that sorted the first problem nicely! I'm still struggling with the second one, among others, but will let you know if I solve it.

Cheers,
nelsonmuntz

---

