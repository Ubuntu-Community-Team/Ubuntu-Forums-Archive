---
title: "Speaker and Headphones BOTH play after installing kubuntu"
date: 2011-09-18
forum: Multimedia Software
---

### Post by theWrkncacnter on 2011-09-18
Hey everybody, I have an HP pavillion dm3, dualbooting ubuntu 10.10 and windows.

Recently I decided to try switching to kubuntu, so I have that installed. But the first time I played music, I found out that the speakers don't mute when you plug in headphones.

Strangely enough, there was nothing to be found on google when I searched for a solution.

Another thing of note is in "playback devices," the RS780 Azalia controller Digital Stereo (HDMI) slider does nothing, while the "Internal Audio Analog Stereo" is the slider that controls volume.

On a suggestion, I opened up alsamixer, but there was no option for "automute" in all settings.

Additionally, in alsamixer, if I mute the "speakers" column, it mutes everything -- speakers and headphones. If I mute the "headphones" column, it also mutes everything. However the volume sliders operate independently: "speakers" controls the speakers, and "headphones" controls the headphones.

I'll take this as an opportunity to learn more about sound under kubuntu, but what is a way of getting the speakers to mute when headphones are plugged in?

---

### Post by philipballew on 2011-09-18
What version of Kubuntu are you trying to install?
How is Ubuntu 10.10's overall performance?

---

### Post by lidex on 2011-09-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by theWrkncacnter on 2011-09-19
Hello, it looks like I solved the problem in a way I didn't expect.

When I installed kubuntu-desktop, dpkg asked me if I wanted to keep gdm installed or use kdm. I went with gdm.

When I switched to kdm last restart, not only did that fix the sound problem I described here, it also gave me a shutdown button which was missing before. I don't know what else was fixed when I switched to kdm.

I might report a bug in the installer, because it seems that not having kdm seriously degrades the quality of kubuntu.
(i'm uploading the sound diagnostics anyway: [http://paste.ubuntu.com/693344/](http://paste.ubuntu.com/693344/))
Thanks for your help and support! Also if you have any theories as to why breakage occurred, that would be cool too. Thanks

---

