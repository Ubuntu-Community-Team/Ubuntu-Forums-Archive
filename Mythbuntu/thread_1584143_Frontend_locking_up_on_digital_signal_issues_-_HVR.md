---
title: "Frontend locking up on digital signal issues - HVR-1600"
date: 2010-09-28
forum: Mythbuntu
---

### Post by Calmor on 2010-09-28
Hello all,

I've just recently gotten a good workout for my newest Mythbuntu setup.  I'm running 10.04 x64 with an NVidia card and HVR-1600 hooked up to an OTA antenna.  

I do pretty well with a signal for the most part.  I'm on the first floor of a four-floor apartment building which I cannot put an antenna on top of.  Thus, I have an indoor antenna as high as I can have it, facing the direction of the signal (I've tried several positions, actually, in all sorts of "facing" the source)

Anyway, most of the time the picture is amazing, and with the NVidia card, I can watch HDTV with low CPU effort.

Sometimes, as a large vehicle drives by for example, I get some signal loss.  Blocks, some audio distortion, etc.  Usually the system handles it just fine, but sometimes the frontend just freezes hard until I kill it (ssh into the box and killall mythfrontend.real).  I'm convinced that it would run for days if I didn't have anyone ride past.

Is there any way to make the system more tolerant of these breaks in signal?

Thank you!

---

### Post by Quadari on 2010-09-28
So while this might not address your question directly, I have heard, but cannot confirm myself, that the HVR-1600 can be known to have signal issues, and that using an inline amp can help.

Something like [this Motorola one]("http://www.amazon.com/Motorola-Booster-484095-001-00-Bi-Directional-Amplifier/dp/B000066E6Y/ref=sr_1_fkmr0_1?ie=UTF8&qid=1285716620&sr=8-1-fkmr0") might help?

Or I'm sure you could get something similar at your local Radio Shack/Electronics Shop.

So maybe one of those would fix the signal problem, and then you wouldn't have to deal with the freezes?  Just a thought.

As for why the freezes occur, I'm not sure I can be of too much help on that one.

---

### Post by tmcgary on 2010-09-28
Quadari is right in that an inline amp is helpful for signal loss between your antenna/cable jack at the wall and your video capture card (ie hvr-1600). Specifically with that card it is useful when receiving clearQAM signals from a cable company-fed wall jack. From the wiki's and forums I've read the HVR-1600 is supposed to receive OTA ATSC signals quite well. 

However, in this particular instance it sounds like the signal loss is between the transmission towers putting out ATSC signals and your antenna. This could possibly be rectified with an active amplifying antenna, I believe, but I am not optimistic. I don't think an inline amp would work. If someone has actual experience in fixing this or more technical explanation please chime in, I'd love to know for my own knowledge:)!!

As far as the freeze, I dont know whats going on specifically, but I had the same issue until I fixed my clearQAM problem with an inline amp.

EDIT: If you wanted to try and see, get the renta-shack-- er, radio shack active inline amp-if it doesn't work return it in 30 days for a full refund :-D

---

### Post by Calmor on 2010-09-29
Quadari and tmcgary - thanks for your suggestions.  I forgot to mention that I do have an inline amp that came with the antenna hooked up.  I don't think the problem is a signal level getting to the PC - in fact the HVR-1600 actually suffers from less blockiness and signal loss than the pipe going straight to the TV's internal tuner.  I was quite happy with its performance in reception.

I think my problem is that when the large vehicles roll by, I'm getting some signal blockage or reflection to the antenna causing some glitches in the data.  In any event, I'd hope that the frontend could handle these momentary lapses in video information, especially since the backend seems to be able to handle it fine. 

Thanks again for your suggestions!

---

### Post by GaryP2 on 2010-09-29
You might want to look at tweaking some of the VDPAU profile settings to see you can improve the situation. Try using the VDPAU "slim" or "normal" profile. Post #8 from kokkonenfi on this thread has some custom filter settings that I'm anxious to try to see if I can improve video quality when I get QAM errors. Something like this may potentially help eliminate the lockups you're seeing as well.
 
[http://ubuntuforums.org/showthread.php?t=1583016](http://ubuntuforums.org/showthread.php?t=1583016)

---

### Post by Calmor on 2010-09-30
Will give that a try, including trying to get the latest NVidia drivers.  I think I'm running an old, old version (180.x or whatever the first VDPAU driver was), as the new ones were for some reason not available when I installed.

I never put 2 and 2 together to figure it was a potential video driver issue.

---

### Post by Calmor on 2010-10-03
Just an update, I was originally running the 195 driver.  I tried getting the latest via the PPA but the 260 driver had a lot of artifacts on blacks and tweaked all of the themes terribly.  I saw that seemed to be a fairly widespread problem, so I went back to the 195 driver until that gets worked out.  I'm going to try a few VDPAU settings as well to see if anything helps.

I've also added a reset script to my remote so that if it does lock, a two-button sequence will reset it.

Thanks for the help!

---

### Post by LowSky on 2010-10-04
Calmor are you sure you were using the 260 driver?

After you install 260 you need to run the command nvidia-xconfig to generate a new xorg file and then reboot? If you don't Ubuntu doesn't use it and switches back to the Noveau driver. Its a weird little bug.

---

