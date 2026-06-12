---
title: "Sound is muted after reboot"
date: 2009-09-29
forum: Mythbuntu
---

### Post by slamhound on 2009-09-29
I'm guessing there's some simple solution to this, but I can't figure it out.  I'm setting up a new 9.10 system and am almost there with it.  But one weird problem cropped up after making a few changes.  Every time I reboot the computer, the sound is muted.  I have to go to "mixer" and then unmute and raise the volume for "front".  

I think the first time it was muted actually occurred during DVD playback through myth, but since then, it just occurs on reboot.  Once I change the settings in mixer, everything works until I reboot.

Any advice?

---

### Post by klc5555 on 2009-09-29
You may have done a logout from X and done a "save settings" while the mixer was muted. So it comes up that way on X startup. Try logging out with a "save settings" with the mixer unmuted.

---

### Post by slamhound on 2009-09-29
Okay, I tried that, but still no sound after reboot.  Any other suggestions for things to try?

---

### Post by faical117 on 2009-10-16
try this:
unmute the sound
and  #sudo alsactl store

---

### Post by faical117 on 2009-10-16
sudo alsa force-reload

sudo alsactl store 0

---

### Post by igoddard on 2009-10-16
Delete /var/lib/alsa/asound.state, set the controls in the mixer (you might find the actual problem is in the front channel) and then, as root, run alsactl store.

---

### Post by slamhound on 2009-10-16
Thanks.  Just changing volume and running "sudo alsactl store" worked for me.

---

