---
title: "Poor Audio Capture Quality when using gtk-recordmydesktop with ALSA"
date: 2010-05-13
forum: Multimedia Software
---

### Post by diablo75 on 2010-05-13
A while back I decided I wasn't going to use Pulse Audio because it doesn't play nice with the surround-sound outputs on my Creative Labs Audigy 2 sound card.  So what I've done is simply do a "sudo apt-get remove pulseaudio" and have been fine with my sound output since then.

But today I tried to record a little video with gtk-recordmydesktop.

The first thing I had to do was change the audio capture settings because "DEFAULT" just wasn't working.  Using Audacity, I determined the name of the correct capture device to be "hw:0,1", so that's what I typed into gtk-recordmydesktop and it worked.  Except it sounds like the sample rate is really low, like 11Khz, even though it was set to record at 22050 Hz.  I even tried to change that to 44100 Hz but it didn't make a difference.

Was wondering if anyone might have a suggestion about how to get the quality of my microphone back up.

---

### Post by diablo75 on 2010-05-13
Figured it out.

With a little more experimenting using Audacity, I found that if I used hw:0,0 things sounded MUCH better.

---

