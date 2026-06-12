---
title: "Internet streaming audio/video skipping"
date: 2012-04-10
forum: Multimedia Software
---

### Post by Durn Whippersnapper on 2012-04-10
Every source of streaming audio or video is skipping all of a sudden. Music played from my machine is fine. The only thing I did recently is I changed my home directory using usermod. I purged and reinstalled alsa-base, alsa-utils, linux-sound-base, and flashplugin-nonfree-extrasound. The skipping happens on both Chrome and Firefox, and I switched to the HTML5 version of youtube, but that didn't help. Any ideas?

---

### Post by lovinglinux on 2012-04-10
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) or [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Lemuriano on 2012-04-14
Hi,

Besides flash aid, as a temporary solution, try to lower your screen resolution and limit the video quality.  After that I was able to play full screen videos on YouTube and Hulu without a problem. 

Hope this help,
Regards.

---

### Post by lovinglinux on 2012-04-14
> **Lemuriano said:**
> Hi,

Besides flash aid, as a temporary solution, try to lower your screen resolution and limit the video quality.  After that I was able to play full screen videos on YouTube and Hulu without a problem. 

Hope this help,
Regards.

This might be useful: [https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/](https://addons.mozilla.org/en-US/firefox/addon/low-quality-flash/)

---

### Post by BicyclerBoy on 2012-04-14
A Long Shot..
If this problem just started after your audio re-installing & user changes..the problem maybe your user is not in the audio group or some other required group.

The audio group could be needed for setting/changing buffers etc..

---

