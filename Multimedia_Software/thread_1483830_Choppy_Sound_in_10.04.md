---
title: "Choppy Sound in 10.04"
date: 2010-05-15
forum: Multimedia Software
---

### Post by Marsonis on 2010-05-15
I'm having choppy sound in 10.04.  I didn't have it in 9.10 and I don't know enough about how it works to try to fix it.  

Here are some things I have noticed, however.  

1. The choppy sound is present in a 64bit and 32bit install.  At first I thought it may just be a 64bit issue so I reinstalled to 32bit and it is still present.

2. It does not seem to matter what media type I am playing.  I notice it most with videos from Youtube and music from Pandora.

3. It seems to occur more often at intense moments of music.  I'm not really sure how to describe it, but it is typically the climax of a song where it is a little louder and more intense.

Any help would be greatly appreciated.

Thanks.

---

### Post by Vladimir Hidalgo on 2010-05-17
I'm experiencing this too.

If I recall correctly, this started since an upgrade of OpenAL or something in the like.

Default Lucid + lastest ALSA did not gave me troubles until the before mentioned upgrade.

I can describe this as if the sound buffer got full or something, then everything stucks (like video playback)

In VLC selecting ALSA/PulseAudio/OSS make no difference.

I wonder if your sound chipset is Intel® High Definition Audio too.

---

### Post by Marsonis on 2010-05-17
Yep.

My audio device is: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by lidex on 2010-05-17
Try this fix:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

---

### Post by held7over on 2010-05-18
Ubuntu 10.04  (But I have had this problem I think since 9.04)

Does this sound like your fix would work for me?  Every so often, whether it is system notifications, or Skype, or music, or video, about half second to a second of sound is simply gone from the stream. What I mean is, there is no pause in the sound track, it is just as though the missing sound was clipped out of the sound track by some editor and the two raw ends merged together to make a continuous track of sound. When watching a movie, this results in parts of the sentences that are being spoken, simply not being in the sound track or you might hear half a word if you are lucky....and sometimes the video itself suddenly speeds up to resync itself with the auto track making the characters suddenly shift into overdrive and then put on the breaks again! Ha. 

Is this anywhere near related to what you are talking about here?

---

### Post by Mattatk on 2010-05-27
I fixed the sound problem by using synaptic to uninstall pulseaudio.
(This may be a little dicey, as it also uninstalls ubuntu-desktop)
I then reinstalled pulseaudio and ubuntu-desktop.

In retrospect, I am not sure why this worked. I haven't tried video yet.

I'm running 10.04 on my Inspiron 6000. 10.04 is a bit sluggish in some respects (like loading the lock screen log in dialogue). I'm thinking that my old laptop may not be getting a lot of hardware support love these days.

---

