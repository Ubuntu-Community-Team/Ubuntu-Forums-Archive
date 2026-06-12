---
title: "2, probably related, sound video issues."
date: 2009-03-02
forum: Multimedia Software
---

### Post by d4ng3r on 2009-03-02
Alright, so I had Ubuntu installed on my computer for a while, and then the harddrive died, so I had to reinstall everything.
Since then I have not been able to:
1-play mp3's, MIDI's or anything of the sound sort with VLC, Amaorok, Rythmbox, anything...In fact this last time I tried to open a MIDI, totem opened and my whole computer froze up, and I don't think that is supposed to happen.
2 - Play DVD's, not even with VLC


I'm pretty sure I installed all the codecs correctly, although last time I did it with some program, Activix, or something of the sort?  And this time I just did it through the Syn Manager after adding the restricted repositories.  I really have no idea where to start troubleshooting this one, any advice?

---

### Post by renebs on 2009-03-02
here is a/the start: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449),

---

### Post by miegiel on 2009-03-02
Some stuff to try if you have no sound :

```
lspci
```
Verify that your soundcard is in the list, if it's not either your PC didn't see it during boot or ubuntu has no drivers installed for it.

If it's a card try sticking it in a different slot on your motherboard and verify if there is a linux driver for your card. [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/) is a good place to start i assume :)

If your card is listed by lspci, than go to "System > Preferences > Volume control" to see if your sound might be muted. Under "Edit > Preferences" you can select channels that are hidden by default.

---

### Post by d4ng3r on 2009-03-02
I get sounds from youtube or whatever, I just cant play music/video files correctly

---

### Post by miegiel on 2009-03-02
Have you added the medibuntu repository and added the codecs you meed to play the files?

If not see : [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You might also want to check "System > Preferences > Sound" Do you get a sound if you click on the "test" buttons? If you don't try changing the device till you get the test sound and then try your apps again.

I assume "lspci" showed your sound card(s) since you get sound on youtube. Was the [_Comprehensive Sound Problem Solutions Guide_]("http://ubuntuforums.org/showthread.php?t=205449") helpful?

---

### Post by d4ng3r on 2009-03-03
huh that fixed it, I just needed to go to sound and switch "music and movies" from autodetect to ALSA

---

### Post by miegiel on 2009-03-03
gratz\\:D/

---

