---
title: "Seeing double screens on recorded playback"
date: 2010-02-09
forum: Mythbuntu
---

### Post by usererror on 2010-02-09
I just started recording media again from my tuners after getting a new video card for my backend.  My backend is also my front end.

All video is working great, with a bit of tearing during avi playbacks, but thats not a big deal.

When I play back recorded TV I get two screens in one.  I see the recorded show twice, once on top half of the screen, and again on the bottom half of the screen.

If I play the stream from mythweb, its completely normal.  I am using the restricted drivers for my nvidia card. ATI Technologies Inc RV710 [Radeon HD 4350]

---

### Post by nickrout on 2010-02-09
> **usererror said:**
> I just started recording media again from my tuners after getting a new video card for my backend.  My backend is also my front end.

All video is working great, with a bit of tearing during avi playbacks, but thats not a big deal.

When I play back recorded TV I get two screens in one.  I see the recorded show twice, once on top half of the screen, and again on the bottom half of the screen.

If I play the stream from mythweb, its completely normal.  I am using the restricted drivers for my nvidia card. ATI Technologies Inc RV710 [Radeon HD 4350]

Ummm thats not an nvidia card...

Its ATI.

---

### Post by matt06 on 2010-02-09
Take a look at your playback profiles and/or de-interlacing options.

---

### Post by usererror on 2010-02-09
> **nickrout said:**
> Ummm thats not an nvidia card...

Its ATI.

A valid point, my bad.  My Desktop has an NVidia card which I would put in the Mythbox but the ATI card has HDMI out so that is why the ATI is in the mythbox.

How do I check the playback profiles/de-interlacing options?  I've never looked at that before.  I streamed a recorded show to my desktop and it of course played back fine.

Thanks in advance.

---

### Post by matt06 on 2010-02-09
On my 9.10 system the Playback Profiles are in Utilities/Setup, Setup, TV Settings, Playback, Playback Profiles (3/9), Current Video Playback Profile.  The deinterlace settings are on the 2nd page under Edit for each decoder/renderer entry.

I am not familiar with which profiles are appropriate for ATI cards so I can't help you there.  Don't be afraid to try different ones, but be sure to note which profile you are using now and any settings you change in case you want to go back to your current config.  You can also check the frontend log at /var/log/mythtv/mythfrontend.log for any errors when playback starts.

---

### Post by nickrout on 2010-02-09
ATi is generally a bad choice, but check out your deinterlacers as suggested elsewhere in the thread.

---

### Post by usererror on 2010-02-09
I will check them out.  It must be something with this particular ATI card.  I have an older ATI card with S-VIDEO out in my other frontend only machine and recorded TV plays back just fine.  I am planning on rebuilding this backend/frontend with a newer processor in the future, perhaps I should also look for a nvidia based card with HDMI on slickdeals in the future.  I will post back my findings tomorrow evening. 

Thank you.

---

### Post by nickrout on 2010-02-09
> **usererror said:**
> I will check them out.  It must be something with this particular ATI card.  I have an older ATI card with S-VIDEO out in my other frontend only machine and recorded TV plays back just fine.  I am planning on rebuilding this backend/frontend with a newer processor in the future, perhaps I should also look for a nvidia based card with HDMI on slickdeals in the future.  I will post back my findings tomorrow evening. 

Thank you.

I have seen a very recent post somewhere else about this double screen thing. In fact I thought your post was a duplicate when I first saw it. I am sure the solution was to do with interlacing settings, but I just cannot find the other thread to find the exact solution.

---

### Post by Neon Dusk on 2010-02-10
> **nickrout said:**
> I have seen a very recent post somewhere else about this double screen thing. In fact I thought your post was a duplicate when I first saw it. I am sure the solution was to do with interlacing settings, but I just cannot find the other thread to find the exact solution.

Is this it? - [http://www.gossamer-threads.com/lists/mythtv/users/421688](http://www.gossamer-threads.com/lists/mythtv/users/421688)

---

### Post by usererror on 2010-02-11
Fixed!  on the 3/9 page it was set to CPU+ I changed it to Standard and that fixed it.  It plays normally.  Thanks!

Now where the heck did the "mark solved" feature go??

---

### Post by usererror on 2010-03-20
Just had to do this again.  Rebuild my mythtv to  9.10 fresh install with newer hardware for CPU & MB.  Changed this again to fixed the double playaback.

---

