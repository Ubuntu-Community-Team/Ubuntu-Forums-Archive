---
title: "Smplayer tearing with Geforce 410M"
date: 2012-03-12
forum: Multimedia Software
---

### Post by bbb13 on 2012-03-12
I'm using kubuntu 11.10 on a sony vaio laptop with a NVIDIA Geforce 410M, 295.20 graphic drivers and vdpau on sm player. i get tearing in .avi files but not in HD mkv's. Sync to VBlack is activated in nvidia settings. any solution?

here's smplayer's config file:

# Write your default config options here!

[vo.vdpau]
vc=ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau,ffh264vdpau,


thnx

---

### Post by bbb13 on 2012-03-25
so noone has an answer?

---

### Post by SeijiSensei on 2012-03-25
What happens if you use xv or gl as the video output driver rather than vdpau?  vdpau is good for H.264 encodes, but offers no advantage for XviD or DivX encodes, which are the most common codecs in AVI containers.

Have you tried playing these files directly with mplayer from the command prompt?  Perhaps you'll see something in the mplayer output that will give you some additional hints.

---

### Post by bbb13 on 2012-03-29
xv and gl also produce tearing

---

### Post by WasMeHere on 2012-03-29
Hi bbb13,

My computers are barely powerful enough to run high definition video. My best graphics card is a Geforce GT 430. I have seen a substantial improvement with Lubuntu Precise 12.04 beta with LXDE. It is partly due to the graphics driver and partly due to the light-weight desktop environment.

You already have a new graphics driver. Maybe your computer doesn't have enough horsepower for Kubuntu and those avi video clips. It would not cost much to install LXDE and select it from the login screen and have a try, or download the Lubuntu Precise 12.04 beta iso file and test it live.

Have fun finding out :-)
Olle

---

### Post by SeijiSensei on 2012-03-29
Sounds like a CPU horsepower problem.  As I said above, VDPAU only works for H.264-encoded video.  Other codecs like XviD must be decoded by the computer's CPU.  What's the result of:

```
cat /proc/cpuinfo | grep 'model name'
```

---

### Post by bbb13 on 2012-03-29
i seriously doubt that the cpu is the problem...

result:

model name      : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
model name      : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
model name      : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
model name      : Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz

---

### Post by SeijiSensei on 2012-03-29
What happens when you run mplayer from the command line?  Does it give any evidence of reasons for the problems you're having?  How about this:

```
mplayer -msglevel all=6 /path/to/file.avi
```

---

### Post by WasMeHere on 2012-03-29
In your situation I would do one of the following things:

1. Try a desktop environment with a smaller footprint: ***LXDE***.

2. Convert the avi video clips to a format your computer can manage, for example mp4 or mkv encoded with a 264 codec. You can do that with ***ffmpeg***.

---

### Post by cuyo01 on 2012-03-29
@bbb13

try these:

1) disable desktop effects: i know looks ugly but disabling compositing solves tearing. >system setting>desktop effects>general>activate desktop effects on start.

dont like that?

2) disable desktop effects in fullscreen windows: this disables the compositing while any windows is in fullscreen. >system settings>desktop effects>advanced>suspend desktop effects in fullscreen windows.

or

3) configure smplayer: in smplayer>option>configuration>general>video change the video output to gl_nosw and check the direct rendering option on: with this i have tearfree playback with desktop effects enabled but sometimes other window/program may cause tearing so while watching video miniminze all other windows.

also it helps to use the latest smplayer from ppa [http://smplayer.sourceforge.net/downloads.php](http://smplayer.sourceforge.net/downloads.php) the latest mplayer from [https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily), this one updates frequently so disable it after mplayer is installed. and of course the latest nvidia driver from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by WasMeHere on 2012-03-31
There are some good tips how to 'make kubuntu blazing fast' in the following link. I hope it helps you!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1889034_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1889034")

---

### Post by bbb13 on 2012-05-10
the only solution unfortunately was to disable desktop effects, even in Kubuntu 12.04. thnx everyone for their help

---

