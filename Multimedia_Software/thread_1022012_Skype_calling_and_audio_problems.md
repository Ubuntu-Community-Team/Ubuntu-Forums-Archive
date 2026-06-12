---
title: "Skype calling and audio problems"
date: 2008-12-26
forum: Multimedia Software
---

### Post by ExemplarUbuntu on 2008-12-26
I've upgraded a miniITX machine to 8.04 Heron and installed Skype with a Logitech E3500 webcam

I can get it to work but it's not right. There are a few issues.

1. When making a call I get "Problem with audio playback" but if I open the Skype Options dialogue and play the test sound and start a call before the sound stops playing then the call will work.

2. Skype is able to pick up the microphone but the Sound Recorder doesn't work. Not helped by Sound Recorder freezing/crashing quite a lot.

I've tried lots of settings and this is what I have in Skype at the moment:

Sound In:  USB Device 0x49d:0x9a4(hw:0x49d:0x9a4,0)
Sound Out: Default Device (default)
Ringing: Default Device (default)

In System Sound preferences it has:

Autodetect for the first 3 settings and ALSA for Sound Capture
with VIA 8237 (Alas mixer) for Default Mixer Tracks: Device

In the Alsa Mixer itself, Master, PCM, Line-in, CD and Mic are all on and at full setting.

---

### Post by xc3RnbFO8P on 2008-12-26
> Sound In: USB Device 0x49d:0x9a4(hw:0x49d:0x9a4,0)
Sound Out: Default Device (default)
Ringing: Default Device (default)

Try to change **default** to **(HW?-0)**

---

### Post by ExemplarUbuntu on 2008-12-26
That didn't make a call despite fiddling with the make test sound.

However, I tried changing Sound Out to "VIA 8237 (hw:?....)" and it makes
the test call.

Thanks.

One down, one to go. :)

---

### Post by Linda Kelpie on 2008-12-26
Hi!

It still not working.. no such option in sound in.. could someone help?

Kelpie

---

### Post by xc3RnbFO8P on 2008-12-26
> It still not working.. no such option in sound in.
What option do you have?

In Volume Control> Preferences> check all capture and mic boxes
in Volume Control> Recording, unmute the mic
in Volume Control> Option use front mic or mic 
leave the Volume Control window open or it will automatically mute the mic.

---

