---
title: "Hardware Encoding Support (Intel QSV) in OBS Studio"
date: 2020-12-08
forum: Multimedia Software
---

### Post by skipbarker on 2020-12-08
It took a bit of doing to get hardware encoding working on my Intel based laptop. Here are the quick steps to get it working. If there is interest, I'll make a video tutorial.
[B]
1. Add the OBS PPA[/B]
```
sudo add-apt-repository ppa:obsproject/obs-studio
```
**2. Install OBS**
```
sudo apt install obs-studio
```
**3. Install intel-media-va-driver-non-free**
```
sudo apt install intel-media-va-driver-non-free
```
**4. Reboot**
**5. Open OBS goto** *File > Settings > Output > Advanced > Streaming / Recording > Encoder FFMPEG VAAPI*

---

