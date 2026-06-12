---
title: "Loud hissing/interference when audio is playing"
date: 2013-02-23
forum: Multimedia Software
---

### Post by Roboticexile on 2013-02-23
Good afternoon,

I updated my Xubuntu HTPC installation yesterday. and ever since have had an issue with interference whenever audio is playing. The audio/video can still be heard (albeit very quietly), with incredibly loud interference (much like you might hear with a badly tuned analog TV) over the top of it.

I currently have my system set up with Pulseaudio, providing analog 5.1, and before yesterday, this was all working fine (apart from the front left channel. This is probably unrelated, but I thought it might be worth mentioning). There are also two (unused) audio devices, an HDA Internal Audio, and an analog TV tuner (both muted)

I have so far tried re-installing pulseaudio, muting all inputs (line, mic etc.), and generally restarting, and messing with volume levels, but to no avail.

I have tried working through various forum posts, but I have had no luck. Would someone be able to please help me firstly identify the cause, and then rectify this problem?

Many thanks,

Roboticexile

---

### Post by Yellow Pasque on 2013-02-23
If your update installed a newer kernel, try booting into the one that last worked.
Also, try resetting the user's pulseaudio configuration files:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

### Post by Roboticexile on 2013-02-24
> **Temüjin said:**
> If your update installed a newer kernel, try booting into the one that last worked.
Also, try resetting the user's pulseaudio configuration files:
```
rm -r ~/.pulse*; pulseaudio -k
```

Thank you, Temüjin. I didn't think you could roll-back the kernel, nor that it would have such a dramatic effect. Rolling back to 3.5.0-21 solved the issue, although I did need to re-install my graphics drivers. Hopefully this thread should help anyone else out, who updates to 3.5.0-25, and encounters the same hissing issue.

Many thanks,

Roboticexile

---

