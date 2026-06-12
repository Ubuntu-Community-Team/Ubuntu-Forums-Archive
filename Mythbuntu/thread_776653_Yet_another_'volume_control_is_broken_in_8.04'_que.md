---
title: "Yet another 'volume control is broken in 8.04' query"
date: 2008-04-30
forum: Mythbuntu
---

### Post by Scott Atkinson on 2008-04-30
Sorry - I've read thru' the other threads, tried what's been suggested and...it doesn't work.

I installed 8.04 today on a plain vanilla AMD box that's been running - without complaint - 7.10.

Everything works, except the volume up and down on my keyboard (I don't use a remote) and mute.

They worked perfectly in 7.10, and they (F10 + F11) work fine in VLC.

I tried going into setup---->general----->audio and doing several variations on the 'make it alsa: default and PCM (or not)' suggestions without success.

I'm outputting analog stereo to a pair of AudioEngines, so there's nothing fancy or tricky there.

Can somebody lay out the next steps for me, or send me where I need to go?

Tks,

Scott A.

---

### Post by garyedwardjohnston on 2008-04-30
[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)

hope it helps

---

### Post by Scott Atkinson on 2008-05-01
Well, I tried the following off the mailing list:

Audio Output Device => /dev/dsp
Mixer Device => /dev/mixer
Mixer Controls => Master

That restored 'mute,' but volume control still doesn't work, excepting that if I go all the way to zero the sound stops.

Thoughts? Anyone?

s.

---

### Post by superm1 on 2008-05-01
Is it just the special multimedia keys not working?  If so you may need to use xmodmap to remap them to different keys, or at least inside myth go and use mythcontrols to set myth to use those keys.

---

### Post by Scott Atkinson on 2008-05-01
> **superm1 said:**
> Is it just the special multimedia keys not working?  If so you may need to use xmodmap to remap them to different keys, or at least inside myth go and use mythcontrols to set myth to use those keys.

I should have been clearer. I'm using the default keys - F9 for mute, F10 for volume down and F11 for volume up.

Thanks,

s.

btw - They are set correctly in Myth.

UPDATE - I made some bad assumptions before my original post. It appears the volume controls don't work in either 8.04 or 7.10, contrary to what I wrote above.

(I confused this install with my other one...)

That said, I have tried every combination of ALSA/non-ALSA - mixer/PCM etc., etc. that I can come up with, with no luck. Mute works, as above, but volume up and down do nothing.

s.

---

### Post by jonno on 2008-05-05
Ditto the exact same behaviour for me (even the muting when I run the volume all the way down to 0).

---

