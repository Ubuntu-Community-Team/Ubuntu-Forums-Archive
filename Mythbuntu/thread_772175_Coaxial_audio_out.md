---
title: "Coaxial audio out"
date: 2008-04-28
forum: Mythbuntu
---

### Post by gazlang on 2008-04-28
Hi,
I have just installed mythbuntu, but cannot seem to get any sound out.

I have my surround sound amp connected via digital coaxial from my on board sound (Asus M2N-SLI Deluxe mother board with intel HDA audio chip)

I have opened alsamixer from the terminal and activated and increased the volume of the ic??? level (cant remember the exact name, but I know it controls the spdif out). In alsamixer also, my sound device is correctly named, so has been detected by alsa.

I used to run LinuxMCE on my system with no problems getting sound out via coaxial, so I know it is not a hardware problem.

I have fiddled around with the sound settings in myth a bit, but no luck getting sound.

Can anyone suggest what settings I should have in myth?

Also (slightly off topic I know) is there a way to get 1080p video out via dvi to hdmi cable?

Cheers

---

### Post by volkswagner on 2008-04-28
A few things to get spdif working in mythtv.

[LIST=1]
[*]Create text file ~/.asoundrc
[*]Make sure you unmute iec958 in Alsamixer, if you see "mm" it is muted hit "m" to unmute, you should see "00"
[*]Your settings for General in mythtv page 3 should be similar to below.
[/LIST]

/home/youreusername/.asoundrc

```
pcm.!default {
    type plug
        slave {
        rate 48000
        pcm "spdif"
    }
}
```

Here are my settings for mythtv general settings


AUDIO OUTPUT DEVICE = ALSA:default
PASSTHROUGH OUTPUT DEVICE = ALSA:iec958:{ AES0 0x02 }
MAX AUDIO CHANNELS = 5.1
UPMIX = passive
X=Enable AC3 to SPDIF Passthrough
X=Enable DTS to SPDIF Passthrough
_=Aggressive Sound Card Buffering
X=Use internal Volume Controls
MIXER DEVICE = ALSA:default can also try default
MIXER CONTROLS = PCM


what is the output of

```
aplay -l
```

---

