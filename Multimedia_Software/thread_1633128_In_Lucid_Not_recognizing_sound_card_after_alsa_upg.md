---
title: "In Lucid Not recognizing sound card after alsa upgrade"
date: 2010-11-28
forum: Multimedia Software
---

### Post by excetara2 on 2010-11-28
I upgraded using the alsa upgrade script just fine but decided to try the driver snapshot to see if my hdmi would work after this. In the mean time I had installed ffmpeg which caused the installation to fail because used the wrong libavcodec.a. I removed ffmpeg and re-compiled and installed it and everything went just fine. Now, it won't recognize my analog card. It only recognizes the HDMI output which still doesn't work.

I've looked up in the sound troubleshooting how to reinstall alsa drivers to base config. Should I run this and then try to reinstall with alsa-upgrade.

Any help would be great.

Here is my alsa-info script information:
[http://www.alsa-project.org/db/?f=e039a15887fd5d59a3c684a8713cab32aa4b3f02](http://www.alsa-project.org/db/?f=e039a15887fd5d59a3c684a8713cab32aa4b3f02)

---

### Post by excetara2 on 2010-11-28
Here was the alsa info script after the first time when it had worked:

[http://www.alsa-project.org/db/?f=adf0af63234ba8a40a356111d98ce0013cc4cf6e](http://www.alsa-project.org/db/?f=adf0af63234ba8a40a356111d98ce0013cc4cf6e)

---

