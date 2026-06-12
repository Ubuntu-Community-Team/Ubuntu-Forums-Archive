---
title: "Q:  Audicity &amp; Multiple Tracks"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Woody_in_MN on 2007-11-06
What hardware (sound card) do I need to be able to create multiple tracks (stereo, and over dubbing) with Audicity?

I currently have a AMD 32 bit box, running Xubuntu 7.10, and am using the motherboard sound ports.  I can record the first track using a mic.  (Very faint - I know, I know, I need a pre-amp) - anyway I can record the first track, but when I select "add track" - I get a pop up error when I try to record the secopnd track.  This happens even when I specify the 1st track is "left", and the 2nd track as "right".  I also tried to input the 2nd track using the " line in" port - but it still errors out.

I think I am hitting a hardware limitation (the sound card) - but its possible I don't have something configured proerly.

Can someone that knows something about these things help me?

Tanks,

 - W

---

### Post by dabl on 2007-11-06
We'll need to know about your onboard sound system.  It certainly will support stereo recording and playback (2 tracks) -- beyond that it depends on what is.  And your microphone is mono, (1 track), so that's all you'll get from it, regardless of the chip.

```
lspci
``` should show the sound chip.  There's also a package in the repos named "hwinfo" that you can install and then run to see more about your hardware:

```
sudo apt-get install hwinfo
```


and then at the command prompt ```
hwinfo
```

:)

---

### Post by Woody_in_MN on 2007-11-06
dabl,

Thanks.  I am not at my home system right now.  When I get home tonight, I will do those commands and post what I get.

Thanks,

 - W

---

### Post by Woody_in_MN on 2007-11-06
:)

It most have been a software setting (preferences?)  I was able to overdub w/ both Audacity, and Arbour.  I also tried Jokosher, but that was kind of buggy for me.  I could not get to record at all.

 - W

---

