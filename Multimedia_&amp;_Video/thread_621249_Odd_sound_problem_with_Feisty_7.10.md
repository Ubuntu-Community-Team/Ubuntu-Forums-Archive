---
title: "Odd sound problem with Feisty 7.10"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by Cyclops_ on 2007-11-23
I'm not sure of everything that I'm going to need to give you, but here are the symptoms:

1) I sort of have sound for SOME things (a VERY select few)...  logging in music, Spam music played by a Thunderbird plugin, and maybe a few others, but that's it.  No other sound.

2) Sometimes I get a gstreamer error.  I am not getting it right now or I would post it.

3) I get an error from Movie Player saying that the sound device is busy.

4) I have gone through the comprehensive sound guide, and tried everything and nothing works, up until the uninstall --force of alsa-base alsa-utils linux-sound-base, and then reinstalling them and rebooting.  Then I get sound.  For a little while.  And then ??  I don't know. Maybe I do something that kills it again, or what?  I don't know.

5) This started happening (afaik) after I created a brand new profile (username, home dir, etc) for myself.  Suddenly sound was gone.

Here is what I get from  "lspci -v":

```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01da
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```
What other info can I provide to getting this fixed?

Thanks in advance for any help!

---

### Post by limac on 2007-11-23
first of all it's gutsy 7.10 (feisty 7.04). and try installing alsamixer, maybe the vilume is muted there.

---

