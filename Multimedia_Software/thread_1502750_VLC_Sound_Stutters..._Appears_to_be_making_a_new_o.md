---
title: "VLC Sound Stutters... Appears to be making a new output &quot;stream&quot;/&quot;sink&quot;"
date: 2010-06-06
forum: Multimedia Software
---

### Post by tropicalfish on 2010-06-06
VLC will repeatedly make stuttering sounds when playing music (I haven't tested with video yet).
I've tried all the solutions I could find off Google's search of this forum, including disabling Pulseaudio, switching to ALSA, OSS, etc. However, they all produce a stuttering/popping sound that happens intermittently.

When I look at the Sound Preferences-> Applications Tab, I can see that VLC (it says ALSA Plug-in or something), it will flash every time the stutter occurs.
Additionally, when I go to the PulseAudio manager and look at the devices/sink list, the number corresponding to the VLC playback will increase after each stutter. 


Any ideas?

I'm running Ubuntu 10.04 realtime kernel (Ubuntu Studio). This does not happen with any other application, including Flash.

---

### Post by tropicalfish on 2010-06-07
Bump...

---

### Post by Starfleet on 2010-06-07
I'm getting a similar problem in 10.04. VLC and Rythmbox both have the problem of the sound stuttering and even cutting out a third of the way through the track. I can't see anything obviously wrong and have the latest codecs, etc. System sound play ok. I run 5.1 surround sound too with Via 8235 onboard sound and chipset. I'm still digging around for a solution but if anyone has an answer or idea I'll be pleased to hear it, and if I find the answer I'll be posting back.

Ian

---

### Post by tropicalfish on 2010-06-07
A lot of people said disabling PulseAudio worked. However, disabling PulseAudio didn't work to solve my stuttering problem.
I actually prefer to use PulseAudio instead of disabling it...

---

### Post by tropicalfish on 2010-06-07
Interestingly enough, the stutters go away if I configure VLC to output to JACK.

But I would still like it to work stutter free with PulseAudio/ALSA.

---

### Post by tropicalfish on 2010-06-09
Bump?

---

