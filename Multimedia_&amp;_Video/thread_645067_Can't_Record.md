---
title: "Can't Record"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by EnglishOpeningc4 on 2007-12-19
Hello my gateway laptop won't record and i've tried most everything to fix it. 
Nothing is muted, playback is fine, my esd.conf file is as it should be.

When I try to test recording in system/preferences/sound i get this error message:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.

This is the output of aplay -l if it helps anyone

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have Feisty Fawn kernel 2.6.20-16-generic

I am a musician and I could really use linux sound software. Thank you for your time. All help is appreciated.

---

### Post by thebrotherofasis on 2008-04-30
Did you ever resolve this issue? I am having the same problem with Hardy.

---

### Post by soxs on 2008-04-30
You're way behind. 8.04 is out and since one year ago alsa/pulseaudio evolved _A_ _LOT_
Edit: Sorry, overread the second post, but it may still help to move to hardy.

---

### Post by thebrotherofasis on 2008-04-30
Well... it hasn't been fixed in Hardy, as far as I have tried recording in it.

Based on your post I assume it is working for you, is it right? Did it work out of the box? It would surprise me since I have a card that outputs the same as yours (if you still have it):

Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]

I'll wait for your response. Thanks.

---

### Post by soxs on 2008-05-01
Well, I am able to use mumble/ts, though I must add that my audio device is somewhat diffrent (but uses same driver ): 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

---

