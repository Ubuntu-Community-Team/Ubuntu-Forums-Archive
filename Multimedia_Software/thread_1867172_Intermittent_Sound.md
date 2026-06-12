---
title: "Intermittent Sound"
date: 2011-10-22
forum: Multimedia Software
---

### Post by Tri_X_Troll on 2011-10-22
I upgraded to 11.10 last night and discovered that my sound intermittently works. The issue first appeared when listening to pandora with pianobar. I can listen to a few songs at a time  before the sound just stops. A reboot seems to solve the issue.

At first I thought this was an issue with pianobar, until I realized that it was also affecting youtube.

I went ahead and did a fresh install on my Dell Mini 9 and am still having the issue.

---

### Post by Toz on 2011-10-22
When the sound quits, is anything being logged to ~/.xsession-errors?

You might be getting affected by: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/841308"). What is the contents of your **/etc/modprobe.d/alsa-base.conf** file?

---

