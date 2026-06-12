---
title: "Microphone not working in Ubuntu 8.10"
date: 2008-12-18
forum: Multimedia Software
---

### Post by groundnut on 2008-12-18
I use the microphone for Skype.
Skype is working fine except for the microphone.
I am also not able to record a sound with the Ubuntu sound recorder.

With Ubuntu 8.04 I had no microphone problems on the same machine.

I have a C Media CM18738 soundcard.

What has changed between Ubuntu 8.04 and 8.10?

---

### Post by xc3RnbFO8P on 2008-12-18
> What has changed between Ubuntu 8.04 and 8.10?
I have to leave the Volume Control window open, or the Mic will be automatically  muted.

---

### Post by groundnut on 2008-12-18
> **Ringi said:**
> I have to leave the Volume Control window open, or the Mic will be automatically  muted.

This trick doesn't work for me.

Thanks anyway

---

### Post by xc3RnbFO8P on 2008-12-18
In Volume Control> Preferences , did you check all boxes Mic and Capture?
And in Option> Input Source, choose Mic or Front Mic?

---

### Post by groundnut on 2008-12-18
Now it works.

Many thanks!!

---

### Post by groundnut on 2008-12-18
Though I can record a faint signal with the Ubuntu sound recorder, the microphone does not work with Skype.

I got it working in Ubuntu 8.04, also in combination with a faint signal from the Ubuntu sound recorder.

Any ideas why the mic does not work in Skype?

---

### Post by xc3RnbFO8P on 2008-12-18
In option> Sound Devices> Sound In
what option do you have?

---

### Post by markbuntu on 2008-12-18
Skype has not yet figured out how to write a proper sound interface that actually conforms to the standards.

---

### Post by groundnut on 2008-12-19
> **Ringi said:**
> In option> Sound Devices> Sound In
what option do you have?

I have the following options for *Sound In* in Skype:

* Default device (default)
* pulse
* C-Media CM18738 (hw:CM18738,0)
* C-Media CM18738 (pluhhw:CM18738,0)
* C-Media CM18738 (hw:CM18738,1)
* C-Media CM18738 (plughw:CM18738,1)
* C-Media CM18738 (hw:CM18738,2)
* C-Media CM18738 (plughw:CM18738,2)
* hdmi
* headset

I selected **C-Media CM18738 (hw:CM18738,0)** (also for Sound Out and Ringing)

---

### Post by xc3RnbFO8P on 2008-12-19
> I selected C-Media CM18738 (hw:CM18738,0) (also for Sound Out and Ringing)
Use that,
then before starting Skype open Volume Control and unmute Mic and try test call.

Do have Mic and Front Mic in Volume Control?

---

### Post by groundnut on 2008-12-19
I tried to make test calls the way you described with the unmuted mic. However I could not record something. Most times there was no introduction after which I could do a recording test. One time the recording started, but was not played back.


The volume control has to Mic-In Modes:
* Mic-In
* Center/LFE Output

---

### Post by PlanetT on 2008-12-20
Hi!

I am struggling with the same problem with Ubuntu 8.10. Having unmuted the mic in volumen control I still cannot record anything (except some ugly noise). Somehow the "Capture" option is allways muted, even if I unmute it (see attached pic). I have a HDA NVidia sound card.

---

### Post by xc3RnbFO8P on 2008-12-21
> (except some ugly noise).
Do you have Mic Boost enabled?

---

### Post by groundnut on 2008-12-22
I have 2 choices:

* Mic Boost
* Mic Boost Capture(?)

When Mic Boost is enabled, I get positive feedback.
When Mic Boost Capture(?) is enabled the test recoding still does not work.

---

### Post by baxter42 on 2010-01-07
i'm using the netbook remix and i have none of the options referred to. i only have the sound preferences window. the microphone is unmuted. i turned up the input level. neither skype nor sound recorder records anything. in fact, there is a meter on the sound prefences window which i presume indicates the input level. it never displays anything.

thanks--

---

