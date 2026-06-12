---
title: "Pulseaudio: mute mic output through speakers, but not mic input"
date: 2010-11-09
forum: Multimedia Software
---

### Post by ufugu on 2010-11-09
I have read dozens of sound how-tos and posts here and elsewhere but can't find instructions on how to do this.

I don't want to monitor my inputs.  In other words:

My microphone input plays through my speakers, adding a lot of undesirable noise from the mic.

I can mute the mic inputs in alsamixer and/or in the Pulse volume control. This works to get the mic out of the speakers--but it also mutes my mic entirely, so I cannot record audio or use Google Talk. 

I want the microphone muted in my output, but available to my apps.

Can anybody point me in the right direction?

(I try, try, try to get on the Pulse bandwagon but it is so hard--I thought this was exactly what it was supposed to do, give easy mixing control over inputs and outputs. But I have to search for "fixes" with every single Ubuntu release for two years now, ever since it was first included. Grrr!  OK, venting over, time to get it working!)

---

### Post by r0nni3 on 2010-12-05
I have exactly the same problem. If you want to use the mic you'll just have to listen your own pretty voice in the process :). Did you get a workaround for this ?
Thanks

---

### Post by lidex on 2010-12-05
Try muting the "Monitor of internal audio..." on the input devices tab in pavucontrol. If not visible make sure the "show" option down below is set to "All input devices"

---

### Post by ufugu on 2010-12-06
@lidex: been there.

@r0nni3: my solution was to buy a USB Samson Go mic when I saw one at half price, and to just mute the internal mic. 

Kind of a drag to have pull out an external mic when I want to voice chat, but the sound quality is fantastic, it's detected without issue, and I no longer feel the pain of not being able to get it to work. :P

---

### Post by lidex on 2010-12-06
> **ufugu said:**
> @lidex: been there.

@r0nni3: my solution was to buy a USB Samson Go mic when I saw one at half price, and to just mute the internal mic. 

Kind of a drag to have pull out an external mic when I want to voice chat, but the sound quality is fantastic, it's detected without issue, and I no longer feel the pain of not being able to get it to work. :P

Checked around some and according to one of the main pulse gurus
 - markbuntu - this worked in the past:
> PulseAudio Volume Meters
You should now have a PulseAudio Volume Meter (capture) you can use to test your microphone or other capture inputs available in your sound mixer or volume control. Once you have chosen your default device, you can open sound recorder and record it. If you choose a monitor device, you can record whatever is going through the comparable Output Device.
You can use the PulseAudio Volume Meter (Playback) for monitoring playback streams. The volume meters work on the default streams.

[COLOR="Red"]If you are using a microphone for recording and wish to not hear the microphone input to prevent feedback, you can just mute the microphone playback in the panel volume control or ALSA sound mixer. It is the Capture settings that are the only important ones for recording.[/COLOR]

---

### Post by Linus P Nuts on 2011-03-13
I had the same problem and it looks like i got it solved now.
The sound card in question is a Sound Blaster Live and i simply had to put the "AC97" slider down to zero, using the alsa-mixer.
Here a copy from the alsa-mixer:

Card: SB Live! Platinum [CT4760P]
Chip: SigmaTel STAC9721,23
View: F3:[Playback] F4: Capture  F5: All
Item: AC97 [dB gain: mute, mute]

I also have the internal sound card enabled and there the mic is initially not echoing. My system is the Ubuntu Lucid 64bit. Also I installed new a pulse-audio version 0.9.22 before i tried that ( actually i tried all sliders :P ), but i don't know if that makes any difference.

---

