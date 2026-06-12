---
title: "Combine Video with no Audio with Video that Has Audio"
date: 2013-12-30
forum: Multimedia Software
---

### Post by gerowen on 2013-12-30
I have 3 video files I need to combine.  Two of them have audio, and one of them I sped up with mencoder and the "noaudio" option since it runs at 360fps to speed through a portion of what I was recording.  However, when I try to join the sped up video with the two normal ones, mencoder tells me:
```

Cannot mix video-only files with audio and video files. Try -nosound.

```

After speeding up the video with no audio, I re-sampled the video so it actually runs at 30 fps so it matches up with the other two videos.

I strung them together with OpenShot, except every time I use OpenShot the video/audio sync gets way off after a minute or two, and AVIDemux crashes constantly, all you can do is edit one video file and cut/edit parts out of it, but appending a video, opening a menu, anything but editing one video causes it to crash with no output if ran from the terminal.

---

### Post by FakeOutdoorsman on 2013-12-30
1. You should get a [recent ffmpeg build](http://ffmpeg.org/download.html#LinuxBuilds). If you're lazy you can do:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
tar xzvf ffmpeg.static.32bit.$(date +"%F").tar.gz

```
or [compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

2. Then show some information about your inputs (notice the **./** for using the static build):
```
./ffmpeg -i input0.mp4 -i input1.mp4 -i imput2.mp4
```
Please show the complete ffmpeg console output.

---

### Post by gerowen on 2013-12-30
Thanks for your reply, :-)
I figured out before your reply that I could just open the video in OpenShot, then export it with a silent audio track, and that allowed it to be joined with the other videos.  That way it had an audio track mencoder detected, it was just a silent one.

---

