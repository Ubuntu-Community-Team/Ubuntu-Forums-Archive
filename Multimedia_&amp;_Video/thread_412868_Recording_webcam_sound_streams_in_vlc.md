---
title: "Recording webcam sound streams in vlc?"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Milamber_Cubed on 2007-04-18
Okay, 

So I got my eyetoy working with Ubuntu pretty easily using the ov51x-jpeg driver following the module-assistant method described here:

[http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Install_debian_module_package](http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall#Install_debian_module_package)

I can see the images from my camera  by running 

```
xawtv -nodga
```

so far so good.

I used the device manager to find out that the audio input contained within the eyetoy is mapped to /dev/dsp1. Also good :)

After some playing, I got VLC to show me on the screen  with audio, albeit with a slight lag by using the following v4l uri (?)

```
v4l:// :v4l-vdev="/dev/video" :v4l-adev="/dev/dsp1" :v4l-norm=3 :v4l-frequency=-1 
```

The problem comes when I try to get VLC to save this stream to disc. Video records fine provided I have the correct codec installed but audio simply refuses to work. I always see the following output in the terminal:

```
[00000487] v4l demuxer error: cannot open device (No such file or directory)
[00000487] v4l demuxer error: cannot open audio device (No such file or directory)

```

I am struggling to get my head around this since VLC plays back the audio perfectly well, but when it comes to trying to record, it all goes wrong.

Any ideas?

---

### Post by Milamber_Cubed on 2007-04-20
Seriously, I'm no closer to figuring this out... anyone have any ideas?

I guess posting this so close to Feisty's release wasn't such a good idea :confused:

---

### Post by bruno.vitorino on 2007-12-12
In my case i had to set the audio device to /dev/audio1 in order to have sound.

---

