---
title: "missing 3GP codec: RMAS"
date: 2009-07-21
forum: Multimedia Software
---

### Post by PCZahra on 2009-07-21
Totem can play the video, but it complains that it can't find the audio codec. It provides a hex code for the codec name, that translates to "rmas". I think this is realaudio, but installing realplayer didn't fix the problem. These videos are recorded on my phone.

---

### Post by andrew.46 on 2009-07-22
Hi PCZahra,

> **PCZahra said:**
> Totem can play the video, but it complains that it can't find the audio codec. It provides a hex code for the codec name, that translates to "rmas". I think this is realaudio, but installing realplayer didn't fix the problem. These videos are recorded on my phone.

I am a little obtuse I am afraid and cannot transpose the hex backwards, can you give the actual hex code? The audio codec in 3gp files would most usually be amr.

Andrew

---

### Post by PCZahra on 2009-07-26
the hex code is 0x726D6173

---

### Post by andrew.46 on 2009-07-26
Hi PCZahra,

> **PCZahra said:**
> the hex code is 0x726D6173

Then I believe your problem sound is amr. The easiest way to play this is with the MPlayer from Medibuntu which under Jaunty Jackalope has been compiled against the amr libraries.

Details for using the Medibuntu libraries:

Medibuntu - Community Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

All the best,

Andrew

---

### Post by yochaigal on 2009-08-25
[http://ajopaul.com/2009/07/15/enable-sound-for-3gp-videos-in-ubuntu-using-mplayer/](http://ajopaul.com/2009/07/15/enable-sound-for-3gp-videos-in-ubuntu-using-mplayer/)
hope it helps.

---

### Post by yochaigal on 2009-08-25
After doing the above, I also had to install the amrwb package, then it worked.

---

### Post by PCZahra on 2009-09-10
Worked, thanks!

---

