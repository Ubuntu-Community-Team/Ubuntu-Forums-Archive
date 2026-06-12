---
title: "VDPAU - Not working in Ubuntu?"
date: 2014-11-02
forum: Multimedia Software
---

### Post by DJonsson2008 on 2014-11-02
We have tried on several machines to determine if VDPau is working at all with H264 video files.
For these tests we have used Noveau and Nvidea drivers and see no indication that VDPau is
working after using multiple players in playback.

The chatter on the internet is confusing about this for instance this discussion 
which claims Ubuntu does not enable VDPau and will not do to distro size considerations.
[http://www.phoronix.com/scan.php?page=news_item&px=MTYwNzU](http://www.phoronix.com/scan.php?page=news_item&px=MTYwNzU)

* Is VDPau enabled on Ubuntu?
* If so what software utilizes it?
* Do any other distros have better VDPau support?

Please advise

---

### Post by sudodus on 2014-11-02
I run Ubuntu 12.04.5 LTS with xubuntu-desktop and the proprietary driver NVIDIA 304.88 for a GeForce GT 430 graphics card.

Then it works to use vdpau with mplayer2 (from the repositories). I use the following alias

```
 alias mplayervdpau='mplayer -vo vdpau -vc ffh264vdpau -lavdopts skiploopfilter=nonref -use-filename-title -fs'
```

so for example a file with 

```
VIDEO:  [H264]  1280x720  24bpp  50.000 fps  4125.5 kbps (503.6 kbyte/s)
```

runs with the command

```
mplayervdpau file.mp4
```

and uses

```
VO: [vdpau] 1280x720 => 1280x720 H.264 VDPAU acceleration  [fs]
```

instead of

```
mplayer file.mp4
```

This means that a lot of work is moved from the CPUs to the GPU. You will notice a bigger difference in performance with 1920x1080-50p video clips.

---

### Post by SeijiSensei on 2014-11-02
VDPAU is not a feature of the operating system but of the NVIDIA driver suite.  If you install the proprietary NVIDIA driver, it will be used by the kernel for the video display.  One way to tell if it's loaded is to run the command "lsmod" like this:
```

$ lsmod | grep nvidia
nvidia              10675249  71 
drm                   303102  2 nvidia

```
That says that the driver is loaded (and occupies about 10 MB of memory) and that the related DRM kernel object uses the NVIDIA driver.

Beyond simply using NVIDIA for the overall display, programs need to have support code to take advantage of off-loading the video decoding task.  As sudodus notes, all the mplayer-based programs can use VDPAU.  I use SMPlayer which is a terrific GUI front-end for mplayer.  In Options > Preferences > General > Video you can select the output driver for the player to use.  On machines with the NVIDIA driver, you'll see vdpau in the list.

---

