---
title: "Awww Snap! sound problems again!"
date: 2010-02-22
forum: Multimedia Software
---

### Post by hakloss on 2010-02-22
So last week, I had crappy sound problems, but I fixed it by just turning down the volume in pulseaudio by a notch. Everything was working fine and dandy....Until Now.

Now I have no sound. I admit, I screwed with ALSA drivers and such that I have no clue about in the process of trying to fix last week's problem. (Is Ubuntu now mocking my lack of experience, I'm getting that feeling)

So once again I went to the sound guide at the top of this forum. I successfully installed a fresh kernel... but no sound. I tried the steps for ALSA driver compilation...BUT NO SOUND. Instead it tells me:

haley@haley-desktop:~$ sudo modprobe snd-
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base line 1: ignoring bad line starting with '"options'
FATAL: Module snd_ not found.

I would adore your help, together we can show Ubuntu who boss!

PS I have a nVvidia AC97 sound card. It has a chipset thingy: intel 8x0 (Sound guide told me to look it up, don't know if its important)

---

### Post by mörgæs on 2010-02-23
If you boot the machine with a 9.04 live CD (without changing the present installation), does the sound work better?

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by Enigmapond on 2010-02-23
I had the same issues. Thought I worked them out and SNAP it was bad again in a few days. The answer to the above question will probably be yes as it did for me...so much so that I trashed everything Karmic and went back to Jaunty and have since not had ONE issue and I'm back to a stable distro...that will most likely be what you'll have to do.

I went WEEKS trying to hack pulseaudio to work well....save yourself this headache...just re-install Jaunty.

Good Luck..,,

PS I pray they will get this sound issue fixed for Lynx.....

---

### Post by drauchomyn on 2010-02-24
I just figured out the solution to my audio woes.  I'm also running AC97 with intel 8x0.

I've been banging my head against the wall for over week trying to fix the damn thing and going through every sound troubleshooting guide, but I finally found the solution  : )

When you type sudo modprobe snd-, hit tab twice instead of hitting enter. As long as you can find snd-intel8x0 in there, you're good to go. 

If everything is okay with modprobe, then follow the solution posted here:

[http://ubuntuforums.org/showthread.php?t=1383493](http://ubuntuforums.org/showthread.php?t=1383493)

Good luck.

---

