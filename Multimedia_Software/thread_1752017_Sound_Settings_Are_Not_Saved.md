---
title: "Sound Settings Are Not Saved"
date: 2011-05-07
forum: Multimedia Software
---

### Post by Bill333 on 2011-05-07
I am running a dedicated audio PC (Ubuntu 10.04 on Intel Atom 525) with a Juli@ sound card.  I had everything set up and working great up until I accidentally pulled the sound card out of its slot while the computer was running.  After that, the computer no longer recognized the Juli@ card.  

I managed to fix the basic problem by following the Comprehensive Sound Problem Solution Guide- deleting and reinstalling ALSA is what did the trick.  The only problem remaining is that the computer no longer remembers the output settings in the Sound Preferences dialog.  The setting stays for as long as the computer is on, but as soon as I turn it off and reboot it, the sound output setting reverts back to the internal audio.

I tried 'sudo alsactl store 1', but this does not work.

Does anyone know how to fix this?

---

### Post by Bill333 on 2011-05-10
Bump.  Does anyone have any idea what to do about this?

Thanks.

---

### Post by lidex on 2011-05-10
Try removing your pulse configuration files, set levels as needed, then run that command again. You sure that card is position 1?
```

rm -r ~/.pulse ~/.pulse-cookie 

```

---

