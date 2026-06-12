---
title: "Mythtv: Internal color problems (tv/videos blue hue)"
date: 2008-04-27
forum: Mythbuntu
---

### Post by rob3435 on 2008-04-27
Sorry for the noise: with fixes17145 the internal picture control Hue is auto set to 0, change to 50 and all colors return..

--original problem
I was running 8.04 and everything was fine, just updated to the 0.21.0+fixes17145 in the weekly repo this afternoon.  Now all the tv/videos have a very dark blue hue. (amd64, lulius/mythbuntu themes)  Is anyone else seeing this?

Using tv-out on an ati 9600, oss radeon driver. Looking thru mythtv's svn found this commit, that affects the hue, supposedly a fix for real problem..

[http://svn.mythtv.org/trac/changeset/16896/branches/release-0-21-fixes](http://svn.mythtv.org/trac/changeset/16896/branches/release-0-21-fixes) 

Regards,
Robert Nelson

---

### Post by JugeHuge on 2008-06-11
Hello..

here is one solution for blue hue problem:[https://help.ubuntu.com/community/MythTV/FAQs]("https://help.ubuntu.com/community/MythTV/FAQs")

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

---

### Post by rts on 2008-06-29
> **JugeHuge said:**
> 
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

I press M inside LiveTV and get many options, but none say "Adjust Picture", nor can I find any sort of colour adjustment options anywhere.

So how do I get the hue back?

---

### Post by the_pod on 2009-07-12
Same issue here with an ATI chipset. It's been annoying me for a week (but my capture card is being replaced) so figured it was a hardware problem. Messing with a DVD playback and had the blue people as well.  

Colors are fine with the standard Ubuntu driver but with the ATI proprietary it's like watching the oompa loompas.  Really want the ATI to work since it provides 1080 and the standard driver only runs at 720.

It's late now but I'll test this scheme tomorrow.  I'm glad there's something that may work.

---

### Post by the_pod on 2009-07-13
Worked like a champ. Thanks.

---

