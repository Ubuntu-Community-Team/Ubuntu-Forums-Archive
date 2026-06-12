---
title: "Surround Sound in Lucid Lynx"
date: 2010-06-10
forum: Multimedia Software
---

### Post by quequotion on 2010-06-10
I never got very far with the thread for Karmic Koala before upgrading, but I'm still determined to get this done.

In Lucid, getting 5 of the 5.1 channels to work is not so hard, but I still think the rear channels are a little weak. LFE support is still weak if present at all. There's another thread about this in the forum.  Not hearing anything useful from the subwoofer.

Changing the volume with pulseaudio still causes a ringing sound through all audible channels. Since pulseaudio likes to change all channels together, this also makes the sound unbalanced in some setups (like mine, where I have an amped center channel (monitor speakers) that should be at half volume compared to the left and right channels) Changing the volume with alsamixer is ok, but I can't use the media keys on my keyboard because they link to pulseaudio.

I'd be a lot happier if I could find some way to upmix stereo all the way to the rear speakers. at the moment only Center and Front-Left/Right are used by stereo audio. There are settings on my card (in alsamixer) for "Surround Depth" and "3D depth" which seems to affect the Center and Left/Right mixing, but neither option makes any significant sound come from the rear speakers.

---

### Post by quequotion on 2010-08-20
So I posted [this thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1539887") while i was upset about this.

The sound quality of surround sound in Lucid is terrible. It seems for those lucky enough to have a 7.1 capable sound card, the problem is not so bad. My card only goes up to 5.1 and sounds good only at full volume. Changing the volume outside of alsamixer makes horrible distortion (lets call it a "hisstle" = hiss + whistle)

The subwoofer doesn't output anything audible still yet... Perhaps it is necessary to amp that channel. the others seem to work without amps, although the rear channels are weak.

There are still some issues with SDL applications and pulseaudio (the same ones that gave everyone headaches in karmic) and still no solution...

---

### Post by ratcheer on 2010-08-20
I am using a Soundblaster Audigy ZS in 5.1 mode with Lucid and Maverick and everything is working just fine.

There is an "Unlock" button in the Pulse Audio volume control applet that lets you "ungang" the volume sliders to each output, i.e, allows you to set each channel's volume, separately. Have you tried that?

Tim

---

### Post by quequotion on 2010-10-22
> **ratcheer said:**
> I am using a Soundblaster Audigy ZS in 5.1 mode with Lucid and Maverick and everything is working just fine.

There is an "Unlock" button in the Pulse Audio volume control applet that lets you "ungang" the volume sliders to each output, i.e, allows you to set each channel's volume, separately. Have you tried that?

Tim


Thank you Tim!

Yes I have tried that, but it doesn't stop the hisstling. Also, it's very easy to forget as it seems to reset itself from time to time (unless pavucontrol is always open, which crashes some progams).

Sounds like you have a very similar card, but perhaps the higher-quality version of it. Min's a "Live! Value" which is just about the same design but made with lowest-bid, substandard parts.

Is your card also using the emu10k1 driver?

I have recently found a workaround though, with pulseaudio-equalizer. It never worked for me in Karmic or Lucid, but after upgrading to Maverick it seems to work quite well and minimalises (not quite nullifies) the hisstling sounds PA was making before. Strangely, I am still using the version from Lucid in Maverick.

---

### Post by ratcheer on 2010-10-22
> **quequotion said:**
> Thank you Tim!

...

Is your card also using the emu10k1 driver?

I have recently found a workaround though, with pulseaudio-equalizer. It never worked for me in Karmic or Lucid, but after upgrading to Maverick it seems to work quite well and minimalises (not quite nullifies) the hisstling sounds PA was making before. Strangely, I am still using the version from Lucid in Maverick.

You're welcome.

Yes, mine is also using emu10k1.

And, ***since*** upgrading to Maverick, I have noticed a sound from at least one speaker that sounds like a combination of hissing and whistling. It is very annoying and I don't recall ever hearing it before Maverick.

Tim

---

### Post by quequotion on 2010-10-23
> **ratcheer said:**
> ***since*** upgrading to Maverick

Oh no....

---

### Post by Chrykal on 2010-10-26
Have a similar "Hisstle" problem since upgrading to maverick, it seems to be caused when pulseaudio sets the PCM above 70%-ish.

Even after sorting all my other pulseaudio issues this is stubbornly hanging around, and seems to be independent of hardware as I experienced it with an Audigy 2ZS and my on-board VIA.

edit: not the most elegant solution, but dropping to 4.0 channels fixed it for me.

---

### Post by ratcheer on 2010-10-29
> **Chrykal said:**
> Have a similar "Hisstle" problem since upgrading to maverick, it seems to be caused when pulseaudio sets the PCM above 70%-ish.

Even after sorting all my other pulseaudio issues this is stubbornly hanging around, and seems to be independent of hardware as I experienced it with an Audigy 2ZS and my on-board VIA.

edit: not the most elegant solution, but dropping to 4.0 channels fixed it for me.

I finally figured out what you were talking about. Not in Pulse Audio, I went into alsamixer and saw that the PCM levels were jacked all the way up. I lowered them all to 60% and the "histle" sound immediately ceased.

But, as soon as I touched the Pulse Audio volume control, it came back. I did not increase the PA volume to 100, and changing it again did not correct the problem. So, back to alsamixer and, sure enough, some of the PCM levels were back to 100. Lowering them fixed the problem, again.

Apparently, Pulse Audio is actively changing the alsamixer settings. I did not know this could happen. Is it a bug? I thought PA just "rode on top of" alsa. I knew the alsa settings affected PA output, but I didn't know it could also be vice versa.

Could someone enlighten me on this? If I cannot make a simple volume change in PA without messing up the alsa settings, what good is PA?

Tim

---

### Post by quequotion on 2010-11-26
> **ratcheer said:**
> I finally figured out what you were talking about. Not in Pulse Audio, I went into alsamixer and saw that the PCM levels were jacked all the way up. I lowered them all to 60% and the "histle" sound immediately ceased.

But, as soon as I touched the Pulse Audio volume control, it came back. I did not increase the PA volume to 100, and changing it again did not correct the problem. So, back to alsamixer and, sure enough, some of the PCM levels were back to 100. Lowering them fixed the problem, again.

Apparently, Pulse Audio is actively changing the alsamixer settings. I did not know this could happen. Is it a bug? I thought PA just "rode on top of" alsa. I knew the alsa settings affected PA output, but I didn't know it could also be vice versa.

Could someone enlighten me on this? If I cannot make a simple volume change in PA without messing up the alsa settings, what good is PA?

Tim

It rides on top of ALSA the way you'd ride on top of a **[thought not appropriate for this forum]**.

Pulseaudio does not only actively change the settings, it attempts to exceed the values defined in them. That's why 70% sounds terrible. Pulseaudio seems to think that about 140% of alsa's maximum volume is a safe and reasonable thing to consider 100% of general audio volume, regardless of the lack or presence of an amplifier.

You may also find that after dropping the settings in alsamixer a little, raising them back up to max (in alsamixer) *does not* cause the hisstle to return.

Meanwhile, once hisstling, you will not be able to correct the problem by changing the volume in any direction with pulseaudio (though I occasionally found full volume to sound reasonably good, and a few certain levels have less hisstle than others)

Only pulseaudio causes the problem and it doesn't really matter what percentage of volume it's pushing. Something is unnatural and wrong with the way pulseaudio changes the volume.

I suspect, rather than simply turning the virtual knobs on the card, pulseaudio is attempting some very poor preamp to effectively exceed the volume level dictated by the card. This may even work on some cards...

I have found that using Pulseaudio Equalizer (check google, check launchpad) ended my struggles with the hisstle. I don't know exactly how or why, but as long as I have it enabled the sound quality is good at nearly all volume levels weather changed by pulse or alsa. It also includes a preamp that works.

---

### Post by lidex on 2010-11-27
Some of this may help. 'Volume Range Anomalies' on this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

'Surround Sound' and 'Pulseaudio Modules' here:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

Bugs?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441195](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441195)
[http://pulseaudio.org/ticket/874](http://pulseaudio.org/ticket/874)

---

### Post by alecz20 on 2011-07-21
> **ratcheer said:**
> I finally figured out what you were talking about. Not in Pulse Audio, I went into alsamixer and saw that the PCM levels were jacked all the way up. I lowered them all to 60% and the "histle" sound immediately ceased.

But, as soon as I touched the Pulse Audio volume control, it came back. I did not increase the PA volume to 100, and changing it again did not correct the problem. So, back to alsamixer and, sure enough, some of the PCM levels were back to 100. Lowering them fixed the problem, again.

Apparently, Pulse Audio is actively changing the alsamixer settings. I did not know this could happen. Is it a bug? I thought PA just "rode on top of" alsa. I knew the alsa settings affected PA output, but I didn't know it could also be vice versa.

Could someone enlighten me on this? If I cannot make a simple volume change in PA without messing up the alsa settings, what good is PA?

Tim


The problem is not that PCM or any other sliders are way up.

Simply changing ANY of the sliders returns control of the sound to ALSA mixer which fixes the ringing sound. When using PulseAudio volume slider, the control goes to Pulseaudio which causes the ringing-hissing sound.

In my case the SUB is way too loud. Even with all SUB controls at minimum, the SUB is still very loud. (I have a Logitech 5.1 speaker system - very cheap ~$40).
Not only this but the surround slider directs some sound to the SUB as well.

So to reduce most of the low frequencies I have to reduce both LFE and Surround sliders.  If I want sound from the rear speakers I will get a lot of sound from the SUB (as well as the rear speakers).


EDIT: Problem with ringing/hissing does go away in 7.1 configuration.

---

