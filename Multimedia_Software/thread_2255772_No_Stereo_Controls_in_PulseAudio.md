---
title: "No Stereo Controls in PulseAudio"
date: 2014-12-07
forum: Multimedia Software
---

### Post by KitchM on 2014-12-07
My information is at [http://www.alsa-project.org/db/?f=781314fb3f8a941ccdf66af04802aaaaeacd78e6](http://www.alsa-project.org/db/?f=781314fb3f8a941ccdf66af04802aaaaeacd78e6)

I am having the requisite frustration with PulseAudio.  ](*,)  I hope someone can help.

The PulseAudio volume control applet only shows mono on the Playback tab.  How does one configure the system to show the stereo output controls?

Also, which is the correct selection in the Configuration tab>Profile?

Thanks.

---

### Post by deadflowr on 2014-12-07
That's the default when nothing is running.What does it show when you are actually running a sound app?
Whenever I launch rhythmbox, I get a stereo setting for playback for rhythmbox, but only after the app is launched.

---

### Post by Dennis N on 2014-12-07
> The PulseAudio volume control applet only shows mono on the Playback tab.
Are you playing some stereo output? The playback tab > won't show stereo output unless the player is active.

> How does one configure the system to show the stereo output controls?
Use the Output Devices tab, where you can adjust the level in each channel.

> which is the correct selection in the Configuration tab>Profile?
For built-in Audio, I have profile set to Analog Stereo Duplex.
You may also have digital audio such as HDMI audio. Setting depends on the device. Right now, mine is off.

---

### Post by KitchM on 2014-12-08
I had VLC playing an Internet stream.  I could see the volume control applet in the background and it showed the sound meter bar being active in mono.  But even then, there was nothing coming thru the speakers.

---

### Post by KitchM on 2014-12-08
Opps.  Missed the reply notifications.  Odd forum system.

---

