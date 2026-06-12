---
title: "Fiber Optic Sound to Receiver - Not Working"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Banshii on 2009-05-02
I keep seeing multiple threads all over the internet about this for Ubuntu, but never any replies. It makes me wonder if this is even an option. Some help with this would be oh so much appreciated.

I have a Fiber Optic port on my mother board which is hooked up to a receiver that works on another Linux partition straight "out of the box". However, I installed Ubuntu 9.04 and it does not work at all through the fiber optic cable. All though it does work through my headphones.

I've been searching through options and can't find any that would enable this. I've tried all available selections in "Sound Preferences" as well.

Is there something I need to download or type in Terminal to get this to work? I'm completely out of ideas now, and can't find a solution through searching these forums or google.

Thanks,
Tim

---

### Post by jrice219 on 2009-05-02
Have you seen any option in ALSA or Volume Control for "Enable SPDIF?"

---

### Post by rggavubt on 2009-05-03
I'm having the same problem.  I have two Home Theater PCs(HTPCs) dual booted with XP and 9.04 and neither have SPDIF sound.  I have also searched the forums and don't see any solutions.  I think this is a serious problem for Ubuntu.  My SPDIF connections are from motherboards equipped with SPDIF outputs.  One connection uses a fiber TOS cable and the other uses a coax cable.  Has anyone got SPDIF sound to work on Ubuntu?:confused:

---

### Post by Banshii on 2009-05-03
No I don't see that option in Volume Control. I have everything enabled and turned up.
Still no sound.

---

### Post by Banshii on 2009-05-03
Hmm, well I got it working now. I'm not sure how. All I did was unplug the fiber optic cable, then plugged it back in. It didn't work right after that until I turned my receiver up very high and I noticed a little fuzzy sound. Then I clicked on the mute button in Volume Control and noticed the fuzzy noise stopped. Then I went into Sound Preferences and tried the Test button once more, Lo & Behold I very loud and long beeping sound.
Finally works, not sure why, but w/e.
Thanks for the help though.

---

### Post by pauna on 2009-05-03
> **Banshii said:**
> I keep seeing multiple threads all over the internet about this for Ubuntu, but never any replies. It makes me wonder if this is even an option. Some help with this would be oh so much appreciated.


Check your /etc/asound.conf (assuming you're using Alsa). My home theater PC, which has a via82xx sound module in the motherboard connecting to external 5.1 receiver via S/PDIF, uses the following:

```

pcm.via82xx {
       type hw
       card 0
   }
   
   ctl.via82xx {
       type hw
       card 0
   }
   
   pcm.!default {
       type plug
       slave.pcm "via82xx"
       #slave.pcm "spdif"
       #slave.rate 48000
   }
}
```

My HTPC box is currently running Hardy Heron based Mythbuntu, but it works.

---

### Post by rggavubt on 2009-10-19
I just installed 9.10 Beta and I now have sound.  I just kept clicking the different options for sound and one finally worked.:popcorn:

---

