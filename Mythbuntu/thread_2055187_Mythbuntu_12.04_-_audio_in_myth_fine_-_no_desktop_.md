---
title: "Mythbuntu 12.04 - audio in myth fine - no desktop audio"
date: 2012-09-08
forum: Mythbuntu
---

### Post by DeweyOxberger on 2012-09-08
I'm posting this for my future self (to help me remember what to do).  Maybe it will help someone else:

Installed Mythbuntu 12.04 on a system with NVidia GT240 or there abouts.

Myth now has a cool audio setup that worked slick but it talks straight to the alsa device you select. I forgot to set a system default device.  Tried to play a movie in the browser.  Ack! Kids cheezed.  No audio.  Panic time.  How does alsa work again?

```
aplay -L
``` Shows all the possible devices.

I know I had picked one that worked in myth.  Popped in and saw it was something about CARD=NVIDIA_1, DEV=1.

The aplay -L list had this entry:

```
hdmi:CARD=NVidia_1,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output

```

That must be it.  So did:

```
speaker-test -c 2 -D hdmi:CARD=NVidia_1,DEV=1
```

Since my Samsung TV is 2 channel audio (YMMV) and got the nice audio test noise.  It worked.  So:

```
cd /etc
sudo nano asound.conf
```

Then made typed this:

```
pcm.!default {
type plug
slave.pcm "hdmi:CARD=NVidia_1,DEV=1"
}
```

Saved the file.  I can't figure out how to restart the sound subsystem.  Seems to not matter.  Cool.

Did a speaker test with the default device:

```
speaker-test -c 2
```

It worked.

Desktop audio restored.  Party on.

Future Dewey, dang your brain is turning to mush.  Hopefully this will help you.

Present Dewey

---

### Post by Kantalias on 2012-09-09
This process has typically worked for me as well but I had to deal with a new hitch when I upgraded to 12.04.  There is a great generalized guide linked here: [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240).  Not that what you've shared is wrong or lacking, just that (as the guide reveals) there are a variety of potential pitfalls with audio configuration and other folks may have different problems.

---

### Post by DeweyOxberger on 2012-09-10
Great link.  Thanks!

You are right.  What I posted is not comprehensive.  I posted it as a future note to myself on this hardware.

---

