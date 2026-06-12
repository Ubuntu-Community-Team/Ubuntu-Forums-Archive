---
title: "Stuttering sound issues, any help appreciated."
date: 2014-07-01
forum: Multimedia Software
---

### Post by Noki0100 on 2014-07-01
Hi, I'm having general sound issues running  through simple HDMI on my desktop with Ubuntu 14.04. Using the browser, or XBMC for example is generally fine. I get full 5.1 audio to my amp without issue. NVidia GTX 670 > amp > TV.

The problem usually occurs when I play games, such as Planetary Annihilation through steam. I get stuttering sound which makes it unplayable, even though the games itself is running smoothly. My PC is powerful enough to run and I don't get these issues when I boot to Windows 7 and play games.


[LIST]
[*]I have stock Ubuntu aside from installing things like preload
[*]I have blacklisted a number of unused drivers, with no positive or negative effect
[*]I have manually set prealloc to 0 for that port with no effect. I used 'sudo gedit /proc/asound/NVidia/pcm7p/sub0/prealloc' to alter the setting before testing(not sure if thats correct)
[*]Tested with pulseaudio both disabled and removed with not effect.
[/LIST]

Unsure what to try next, this seems like such a simple problem. I would appreciate any help at all on what I should try next.

Thanks, Noki

---

### Post by Noki0100 on 2014-07-01
Or for that matter why ALSA seems to have no bug tracker at them moment, [https://bugtrack.alsa-project.org/alsa-bug/](https://bugtrack.alsa-project.org/alsa-bug/)

---

### Post by lidex on 2014-07-02
Try one of these:
[https://www.google.com/search?q=hdmi+audio+stuttering&sitesearch=ubuntuforums.org&gws_rd=ssl]("https://www.google.com/search?q=hdmi+audio+stuttering&sitesearch=ubuntuforums.org&gws_rd=ssl")

---

### Post by Noki0100 on 2014-07-02
Thanks for the reply. After digging around I think the problem is with the NVidia drivers. I have switched to Optical out and the stuttering is gone.

Now I can't seem to enable 5.1 output over optical, the only options I have are for Digital Stereo. I think my motherboard supports it, but I can't find a way to do this.

Any help in this regard would be appreciated. I have an AsRock Z77 Extreme motherboard.

---

### Post by lidex on 2014-07-02
I think you'll need hdmi for 5.1:
[http://ubuntuforums.org/showthread.php?t=1770348&p=10876211#post10876211]("http://ubuntuforums.org/showthread.php?t=1770348&p=10876211#post10876211")

---

