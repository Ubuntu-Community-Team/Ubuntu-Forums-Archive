---
title: "White noise hissing static whenever audio starts"
date: 2015-01-24
forum: Multimedia Software
---

### Post by jacob57 on 2015-01-24
```
Machine: Lenovo U430 Touch
OS: Ubuntu 14.10
Sound card: HDA Intel PCH
Sound chip: RealTek ALC 3239

```

My headphones and stereo system both play constant static when plugged into my laptop. The static stops when I mute the audio and doesn't change with volume levels or plugging in to AC power.

I've tried:


[LIST=1]
[*]Muting everything but Headphones and Master in alsa-mixer 
[*]Purging and reinstalling pulseaudio and alsa-utils 
[*]Uninstalling pulseaudio, but then I couldn't get any audio. 
[*]Checked out the Sticky-ed guides, but they seem oriented to people with no sound whatsoever. Also, searched around to little avail. 
[/LIST]

Here is the output of "aplay -l".

```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3239 Analog [ALC3239 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I'm a noob, so let me know if there's more information needed. Thanks you very much for your help!

---

### Post by tgalati4 on 2015-01-25
It's possible you have a feedback loop.  Make sure your microphone inputs are muted and any monitor switches are turned off.  It's also possible that the gain levels are set pretty high so that you are hearing the baseline noise of your system.  Headsets and stereo systems will bring that out.  Lenovo computers are not known for audio fidelity.  Do you hear the noise through the laptop speakers?  Is the volume level acceptable through the laptop speakers?

Make sure you have any "boost" switches turned off in sound preferences.

Read the reviews for your computer.  If others experience the same issue, then perhaps it is a design issue.

Is the noise the same while running on battery?  If it is quieter on battery, then perhaps you have some AC ripple (noise) in your power system.

---

### Post by jacob57 on 2015-01-25
Thanks for your reply! I checked all the microphone inputs in alsamixer, muted/zeroed everything I could. There's no audible noise through the laptop speakers and the volume level is fine.

Checked both alsamixer and pulseaudio for any boost switches etc.

I've found one [reviewer]("http://forum.notebookreview.com/ideapad-essential/724339-lenovo-u430-touch-14.html") with the same issue, but I suspect it's a Linux problem as the noise is quite noticeable and at least a few others would have posted complaints. I'm also not sure if this began on upgrade of kernel/OS, or I just hadn't noticed it previously since I wasn't using the audio system as much. I might try a live boot of another OS and see if things work better there.

---

### Post by tgalati4 on 2015-01-25
Yes, the reviewer is presumably using the default operating system (which would be Windows).  So if it is noisy with the default operating system, why would it be different under linux?  My guess is that the baseline gain (the first notch above mute) is loud enough to be noticeable.  All audio circuits have noise.  Better ones have less noise and more dynamic range.  The rest of the review is consistent with the overall build quality for this machine.  The audio noise is no worse than the screen quality and no worse than the touchpad, etc.

I have an IBM Thinkpad T43p and normally I would associate crappy sound with Thinkpads, but my laptop has a pretty decent sound quality.  It's the same basic Intel HDA sound chipset, but the circuit is quiet, yet it drives my headphones to a decent volume and even when plugging into a Nakamichi amplifier with Magnatone speakers, it sounds quite decent.

Either you have a defective sound circuit or that is how it was designed.  It's possible with a high noise floor that your upper sound levels are much louder and you can play concert level sound (120 dB) through your stereo system.

Record 1 minute of the static in *audacity* and perform a frequency analysis on it.  If the noise is equally distributed across the audio spectrum, then you can be pretty sure that your base gain level is set too high for your use.  If there are dominant frequencies, then it could be leakage from nearby circuits.

Does the noise get lower when running on battery only?  Does the noise change in pitch or frequency when running on AC or can you hear the disconnection of the power plug when switching to battery?

---

