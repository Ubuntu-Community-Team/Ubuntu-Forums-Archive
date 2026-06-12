---
title: "HD-PVR Washed Colors"
date: 2012-07-08
forum: Mythbuntu
---

### Post by miggl on 2012-07-08
Hi Everyone,

I just received my HD-PVR in the mail on Friday and went about getting everything set up. I have installed Mythbuntu 12.04, connected everything (I assume correctly), but am experiencing the following issues:

1. Audio only comes over as static.
2. Colors are all wrong on the HD-PVR, washed out and over-intensified (red is bright pink, for example).

As for the audio connections:
1. Optical connection between my STB and the HD-PVR.
2. USB connection between HD-PVR and Mythbuntu box.
3. Stereo (analog) connection between Mythbuntu box and (desktop) speakers.

Regarding the HD-PVR:
1. Model is HD-PVR 49101 LF rev F2.
2. Composite cable connection from STB to HD-PVR.
3. USB connection between HD-PVR and Mythbuntu box.
4. VGA cable from Mythbuntu box to monitor.

Any ideas how to resolve these issues?
Thanks!
~Mike

---

### Post by nickrout on 2012-07-08
> **miggl said:**
> Hi Everyone,

I just received my HD-PVR in the mail on Friday and went about getting everything set up. I have installed Mythbuntu 12.04, connected everything (I assume correctly), but am experiencing the following issues:

1. Audio only comes over as static.
2. Colors are all wrong on the HD-PVR, washed out and over-intensified (red is bright pink, for example).

As for the audio connections:
1. Optical connection between my STB and the HD-PVR.
2. USB connection between HD-PVR and Mythbuntu box.
3. Stereo (analog) connection between Mythbuntu box and (desktop) speakers.

Regarding the HD-PVR:
1. Model is HD-PVR 49101 LF rev F2.
2. Composite cable connection from STB to HD-PVR.
3. USB connection between HD-PVR and Mythbuntu box.
4. VGA cable from Mythbuntu box to monitor.

Any ideas how to resolve these issues?
Thanks!
~Mike

Is there audio in the file created? Can you play it through another player like mplayer or vlc?

---

### Post by miggl on 2012-07-08
> Is there audio in the file created? Can you play it through another player like mplayer or vlc?
Good point.
```
cat /dev/video0 > test.ts
```
produced video with clear sound. This means that it must be a configuration issue with MythTV frontend. Any ideas? (I will continue fiddling with this, as we have now narrowed the problem down.)

More importantly, what to do about the washed out colors?

---

### Post by miggl on 2012-07-08
Washed-out colors troubleshooting:
1. Connected STB using Composite cables directly to TV, produced good colors.
2. Upgraded firmware on HD-PVR to latest version on Hauppauge website (1.7.1.30059).
3. Reconnected to Mythbuntu box.
4. Resulted in same washed out colors.
5. Direct capture from HD-PVR results in washed colors as well.

My guess is that this has something to do with the HD-PVR driver in Mythbuntu. Thoughts?

---

### Post by miggl on 2012-07-08
I think I've figured out the colors issue:

1. Open MythFrontend, start watching live TV.
2. Press G to edit recording color, hue, saturation, brightness, contrast settings.
3. Keep fiddling until you got it just right.

---

