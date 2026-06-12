---
title: "Problem w/Nforce4 mobo audio"
date: 2008-11-04
forum: Multimedia Software
---

### Post by 2WhEElTeRRoRisT on 2008-11-04
I have been looking all over trying to find a solution to this problem and I can not seem to find one. I recently switched one computer from windows to Ubuntu. The audio was working fine with Windows. I thought it might have been because I simply swapped hard drives over and I thought it might just not be properly recognizing. So I started a new drive on that computer to see if that was the problem. Same problem on both the original and the new Ubuntu drives. It seems to recognize the hardware because it shows up in the settings list. I play the test audio and it acts like it is playing, but I do not hear anything. I tested the cable with my iPod and it works just fine. I even tried every audio jack just to see if I was being stupid and putting it in the wrong one. I switched computers because ati sucks with linux. the video quality from the nvidia is so much better. I really don't want to have to switch it back, but I won't have a choice if I can't get this sound working. So if there is anything that you think I can try I would be glad to hear it. Also, if there is any more information that would be helpful just say so. Thank you.

---

### Post by m_l17 on 2008-11-05
Try adjusting the levels with:

```
$ alsamixer
```

Raise all the levels and if you get sound, just lower them one by one until you don't get any. That way you will know which one affects your sound and safely lower the that you will not use. But leave the master at 100 for the test. 

I had the same problem after a fresh install. On my Nforce4 mobo the level I needed to adjust is labeled "side". I adjust that to 100 and sound started working.

Whatever you set the levels to will be set as default. The only one you will be able to adjust after using alsamixer, will be master.

---

### Post by bscbrit on 2008-11-05
Try System->Preferences->Sound

For Sound Playback (3 separate places) try using a different sound sub-system and then press the Test button.  You might find one of the NVidia ones works better than the one you currently have selected.

---

### Post by 2WhEElTeRRoRisT on 2008-11-05
I went into alsamixer to try the side option that worked for you. Mine does not even show a side. I did turn everything up, but nothing worked. I have also tried what bscbrit suggested of trying. It just seems so weird to me that I don't get any sort of error message. Everything seems to work, I just don't get any sound. I just upgraded to 8.10 and I use both Gnome and KDE if that helps any. I didn't have any sound with 8.04 either. This is just so frustrating because I can't even say that I am getting such and such error message, what does that mean. It does almost seem like something is muted. Is there another sound mixer that might be in use besides the alsa?

---

### Post by bscbrit on 2008-11-05
> **2WhEElTeRRoRisT said:**
> Is there another sound mixer that might be in use besides the alsa?

Yes - read my post immediately before this your last one.

---

