---
title: "Can't get VDPAU nor pulseaudio working in Lucid."
date: 2010-05-05
forum: Multimedia Software
---

### Post by thatsdaniel on 2010-05-05
Regarding video, xv works fine, however no VDPAU.
 I have seen -> [this thread]("http://ubuntuforums.org/showthread.php?t=1467952"). 

However, my mplayer log from smplayer error message is: ```
[vdpau] Error when calling vdp_device_create_x11: 1 Error opening/initializing the selected video_out (-vo) device.
```PPA's in use: medibuntu, nvidia-vdpau. 
Nvidia driver: nvidia-current. 

Any ideas, good Sirs? Thanks in advance! :)

---

### Post by mageus on 2010-06-16
Same initial problem.  I'm not very familiar with the internal workings of repositories, but it looks like the medibuntu version of mplayer superceded the vdpau ppa version.  This didn't happen in prior releases (pre-Lucid).

Adding the libvdpau1 package worked for me, but I haven't fully tested it on many videos.  If I have further problems, I'll post.

---

### Post by richardchu on 2010-06-16
adding libvdpau1 works for me too. anyone knows why?

---

### Post by thatsdaniel on 2010-07-18
SOLVED!

Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1505854](http://ubuntuforums.org/showthread.php?t=1505854)

 ```
sudo mv /usr/lib/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so") /usr/lib/libvdpau_nvidia.soOLD
sudo ln -s /usr/lib/nvidia-current/vdpau/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so") /usr/lib/[libvdpau_nvidia.so]("http://libvdpau_nvidia.so")
```

---

