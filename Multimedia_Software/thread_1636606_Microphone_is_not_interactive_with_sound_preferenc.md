---
title: "Microphone is not interactive with sound preferences"
date: 2010-12-03
forum: Multimedia Software
---

### Post by trelozakinthinos on 2010-12-03
Hello!
I have a strange problem(i think)
I recently manage to make my microphone "work".
I open the alsamixer and i unmuted the mic.
Easy!!!
But as i can hear my voice through the speakers i can't record.
Actually i compare the alsamixer with the sound preferences.
And what I notice is:

i)When i mute the output volume from the sound icon in the alsamixer is also muted.
ii)The same when I increase or decrease the volume.
iii)But in the input tab if I mute increase or decrease the volume nothing happens!

I can only mute unmute and change volume trhough the alsa mixer!

Any ideas???

Thank you in advance

P.s. My English are not the best so if you do not understand something ask me!!

I use an Fujitsu siemens amilo pa 1510 with ubuntu 10.10 which I install from a pendrive.

---

### Post by trelozakinthinos on 2010-12-05
Someone please???
:(

---

### Post by lidex on 2010-12-05
Try pulseaudio volume control (pavucontrol). On the 'Input Devices' tab you should see element for "Monitor of Internal Audio....". If not, make sure 'All Input Devices' are selected below, where it says 'Show'

---

### Post by trelozakinthinos on 2010-12-05
Thank you for your reply but still the same problem! Other ideas???

---

### Post by trelozakinthinos on 2010-12-05
Thank you for your reply but still the same problem!!
:(
Other ideas???

---

### Post by lidex on 2010-12-05
Did you try muting that?

---

### Post by trelozakinthinos on 2010-12-05
Yes i tried but it is not responding to alsamixer. 
Maybe you can tell me some commands to see what's going on???
It seems really stupid problem!
:(

---

### Post by lidex on 2010-12-05
I was referring to muting in pavucontrol; "Monitor of Internal Audio....". There isn't a corresponding setting in alsamixer as this is a pulse routing stream.

EDIT:
I may have jumped too soon. Checked around some and according to one of the main pulse gurus
 - markbuntu - this worked in the past:
> PulseAudio Volume Meters
You should now have a PulseAudio Volume Meter (capture) you can use to test your microphone or other capture inputs available in your sound mixer or volume control. Once you have chosen your default device, you can open sound recorder and record it. If you choose a monitor device, you can record whatever is going through the comparable Output Device.
You can use the PulseAudio Volume Meter (Playback) for monitoring playback streams. The volume meters work on the default streams.

[COLOR="Red"]If you are using a microphone for recording and wish to not hear the microphone input to prevent feedback, you can just mute the microphone playback in the panel volume control or ALSA sound mixer. It is the Capture settings that are the only important ones for recording.[/COLOR]

---

### Post by trelozakinthinos on 2010-12-06
No the input volume meter is dead.
The microphone is only muted by the alsamixer.
I tried to record but nothing..

---

### Post by lidex on 2010-12-06
You should probably file a bug report. This should get you started.
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by trelozakinthinos on 2010-12-07
Sorry but I do not understand what I must do.
Can you explain me please?

---

