---
title: "Issues with Audio drivers ..."
date: 2011-05-12
forum: Multimedia Software
---

### Post by ItBala on 2011-05-12
Hi All,

I'm new to Ubuntu forums and this is my first post.

I'm running Kubuntu 10.10 and sound is not working properly...I went through alot of posts here but nothing is working for me .. 

Problem : Sound is not working suddenly in the middle of the video playback via vlc player or via you tube...

Below are the ways which I have tried to resolve but in vain.

1.Installed Pulseaudio Volume controller and increased the pcm volume.

2.Removed pulseaudio driver packages and configured ALSA driver and changed my audio o/p option in vlc player to ALSA driver.

Neither ways are not working .. and the problem persists.

So someone ... Please help me on this issue.

Thanks
Bala

---

### Post by lidex on 2011-05-14
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ItBala on 2011-05-28
Hi,

Please find detailed information in the below link and help me on this issue..

[http://www.alsa-project.org/db/?f=b54aa6cc6bb261c1c765f51d7b573cf5d9669bc1](http://www.alsa-project.org/db/?f=b54aa6cc6bb261c1c765f51d7b573cf5d9669bc1)

---

