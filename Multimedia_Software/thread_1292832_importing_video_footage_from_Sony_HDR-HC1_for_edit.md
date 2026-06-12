---
title: "importing video footage from Sony HDR-HC1 for editing"
date: 2009-10-16
forum: Multimedia Software
---

### Post by madmaze on 2009-10-16
Hello there,
I have a Sony HDR-HC1 and i cant find anywhere how i can get the footage I have on this camera on my ubuntu box so that i can edit it.

Is this possible?

Any help would be great. 

Thanks is advance

---

### Post by madmaze on 2009-10-26
Anybody every used a firewire camera over Ubuntu?

---

### Post by madmaze on 2009-10-26
Ok, NVM i found some things that worked.
dvgrab can cmd line capture for most dv cams 
and if you are brave enough you can try to setup Kino to do so if you prefer a GUI

quick run through:

run without your camera connected: 

```

# lsmod | grep 1394
ohci1394               33540  1 dv1394
ieee1394              104376  3 ohci1394

```

now connect and turn your camera to Video Playback
run the same command, if you get the following your all set.
```

# lsmod | grep 1394
dv1394                 28680  0 
raw1394                35592  4 
ohci1394               42164  3 dv1394
ieee1394              108288  3 dv1394,raw1394,ohci1394

```

make sure dvgrab is installed
```

# sudo apt-get install dvgrab

```

now try the following and see if it will capture,
you will prob have to sudo/ or change permissions for /dev/raw1394 (see links)
```

# dvgrab --autosplit --format dv2 --size 0 --opendml my_videofile-
Found AV/C device with GUID 0x0800460104a65128
Turning on OpenDML to support large file size.
Capture Started

```

If everything worked well youll be capturing.
to stop hit the stop button on the camera, dont ctrl+c otherwise youll probably get a screwed up video file.

Some good and simple editing programs:
Open Movie Editor-very easy to use very simple but i dont think it can capture video
Kino-good and simple editor, easy to use can capture video with a little tinkering
KdenLive - more advanced editor has some cool feature, setup similar to Adobe Premiere 

here are some links with more info:
[http://www.ubuntugeek.com/open-movie-editor-a-simple-non-linear-video-editor.html#more-1281](http://www.ubuntugeek.com/open-movie-editor-a-simple-non-linear-video-editor.html#more-1281)

[http://www.jennings.homelinux.net/video_camera.html](http://www.jennings.homelinux.net/video_camera.html)

---

