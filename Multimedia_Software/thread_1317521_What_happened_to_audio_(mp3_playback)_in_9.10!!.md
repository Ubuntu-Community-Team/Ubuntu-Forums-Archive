---
title: "What happened to audio (mp3 playback) in 9.10?!?!?"
date: 2009-11-06
forum: Multimedia Software
---

### Post by pointym5 on 2009-11-06
On two separate machines (an HP dv7 laptop and an Asus eee 1009HA netbook), mp3 playback since the 9.10 upgrade suffers from horrible noise bursts, generally at the beginning of tracks. I notice this on both machines and it sounds similar on each.  I've heard similar problems when playing tracks with Audacious2 and with mpg123 from the command line; the noise sounds exactly the same.

I suppose it could be a driver issue with "snd_hda_intel".

---

### Post by HappyFeet on 2009-11-06
> **pointym5 said:**
> 
I suppose it could be a driver issue with "snd_hda_intel".

Yeah, intel sound chips are notoriously bad.

---

### Post by pointym5 on 2009-11-06
> **HappyFeet said:**
> Yeah, intel sound chips are notoriously bad.

Maybe, but they didn't do this in 9.04.  The bad behavior (and it's not at all subtle) is new with 9.10.

This isn't a hardware issue; it's not like a little noise. The anomalies are bursts of complete grunge. This is clearly a software regression.

---

### Post by setiamon on 2009-11-06
My x-fi soundcard worked great in jaunty,no pops or clicks after instaling the drivers.

In karmic my X-fi "works out of the box" if by work that audio is buried in distortions,echo's,static.


I have searched and read everything and asked in the channel but nothing...

I wouldn't have upgraded to karmic if i thought it would be this messed up with my audio.

---

### Post by pointym5 on 2009-11-06
I need to try my external USB sound thingy for a while.

---

### Post by wojox on 2009-11-06
I thought it was related to pulseaudio. The first time I played a movie it sounded like my sub-woofer was full of firecrackers.

I went to System > Preferences > Sound > Hardware > Profile and changed it around till I found something I liked.

---

### Post by pointym5 on 2009-11-06
> **wojox said:**
> I thought it was related to pulseaudio. The first time I played a movie it sounded like my sub-woofer was full of firecrackers.

I went to System > Preferences > Sound > Hardware > Profile and changed it around till I found something I liked.

and that thing that you liked was ... ?

Honestly, I don't think this is a "preferences" issue. The behavior is random - different playbacks of the same track don't always have the same growly startup noise.

---

### Post by tgalati4 on 2009-11-06
Perhaps add yourself to the pulse-rt group.  This gives pulseaudio higher priority during playback.

sudo adduser pointym5 pulse-rt
groups

---

### Post by ad_267 on 2009-11-06
I'm pretty sure you're talking about this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461062](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461062)

I had the same problem, there's a fix given on that page. The problem is also described here: [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

---

### Post by setiamon on 2009-11-07
so far none of the fix's have fixed it.

I experience staticy distortions at best(In flash) and competly garbled sound from everything else like playing a mp3,switching profile does not fix this.Removing pulse audio does not fix this. commenting out the last line of alsa-base.conf doesn't fix this.


Nothing so far has fixed this issue and i have notice a few others have it.anyone able to help me?


X-fi Xtreme music chipset 20k1

---

### Post by pointym5 on 2009-11-07
> **ad_267 said:**
> I'm pretty sure you're talking about this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461062](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/461062)

I had the same problem, there's a fix given on that page. The problem is also described here: [http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

No, that is definitely, absolutely not the problem; not even close.

What's being put out from the sound hardware is digital noise, in bursts, generally at the start of playback (but not only at the start; it's random). When the driver isn't producing noise, the sound is OK.

---

### Post by pointym5 on 2009-11-07
> **tgalati4 said:**
> Perhaps add yourself to the pulse-rt group.  This gives pulseaudio higher priority during playback.

sudo adduser pointym5 pulse-rt
groups

No, thanks for the suggestion but that's not at all what's wrong here. This is a driver problem.

---

### Post by setiamon on 2009-11-07
I agree pointm5 it is something wrong that they should prioritize this.

---

### Post by liquider on 2009-11-24
[_This post_]("http://ubuntuforums.org/showthread.php?t=1332182#7") fixed the aforementioned noise in my audacious2.
If it also fixes all the random freezes and hangs is yet to be determined. :)

EDIT: After following the advice in [_that post_]("http://ubuntuforums.org/showthread.php?t=1332182#7"), I now renamed the file back to default, restarted audacious2 (in order to disable the plugin in preferences) and guess what, it still works flawlessly (with all plugins enabled)! Can someone say odd? I'm satisfied, though. :)

---

