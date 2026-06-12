---
title: "composie and audio; dsp vs dsp1"
date: 2008-10-07
forum: Mythbuntu
---

### Post by MartinusEx on 2008-10-07
Hi,
now I have the composite input grabbing running, but the audio issue comes up:

Grabbing composite video with mythbuntu 8.04.1 with hauppauge nova-s plus
I set the tv card to 
v4l-card 
video device : /dev/video0
audio device : /dev/dsp

In this case mythbuntu uses the mic input of the onboard sound chip
(The sound ist very bad but available, so no broken cable again :oops: )
Line in on the onboard and on the hauppage gives no sound at all

I changed the audio device to /dev/dsp1, believing this would switch to one of the line inputs but this is not true.

In this case , none of the inputs works.

there are some further settings wether the sound device is ALSA or something different which I didn't fiddle with.

Is there a way to find out where /dev/dsp1 looks at and how to gain control over the line input (which one)

thnx a lot in advance

Martinus

---

### Post by MartinusEx on 2008-10-07
Update:
I had a look at alsamixergui and GNOME ALSA-Mixer

I could activate the line input of the onboard sound chip
ALSA-Mixer GUI sais that the onboard SIS Chop is dsp0 and CX88 (TV-Card) DSP1.

I went to the mythbuntu backend and set the audio device of the v4L card to /dev/dsp1

I grabbed a video and replayed it. No Sound.

Still there is in the general settings of the frontend  a possibility to set a mixer and a mixer1 but I suspect this is only for replay not for recording.

So my question is still open:
why doesn't mtyhbuntu grab the sound from dsp1 when I do a recording of a video from composite.

still something to try.

rgds
Martinus

---

