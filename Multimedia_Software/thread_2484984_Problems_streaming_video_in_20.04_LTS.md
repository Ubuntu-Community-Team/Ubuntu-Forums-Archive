---
title: "Problems streaming video in 20.04 LTS"
date: 2023-03-16
forum: Multimedia Software
---

### Post by vector3 on 2023-03-16
I find have found most attempts to stream anything futile. Some YouTube video's will work as desired but anything else does not seem to. How can I resolve this? I have a few Ubuntu machines but none of them run 22.04.2 LTS. The primary laptop in question regarding this issue is a ThinkPad T530.

Please advise or refer me to meaningful threads discussing problem solving strategies for this complication.

---

### Post by vector3 on 2023-03-16
I found a solution of my own efforts. This is:

sudo apt install ffmpeg

For reference see the ffmpeg website: [https://ffmpeg.org/](https://ffmpeg.org/)

---

### Post by naufrsb on 2023-03-16
Hi there, did installing ffmpeg solved your issue?
You can also try the following...

1. Update your video drivers. This can cause problems like yours with video playback.
2. Clear browser cache. Try clearing cache and cookies... 
3. And finally, install the necesary codecs. Try installing the "ubuntu-restricted-extras" packages which comes with common codecs.

---

### Post by TheFu on 2023-03-16
> **naufrsb said:**
> Hi there, did installing ffmpeg solved your issue?
You can also try the following...

1. Update your video drivers. This can cause problems like yours with video playback.
2. Clear browser cache. Try clearing cache and cookies... 
3. And finally, install the necesary codecs. Try installing the "ubuntu-restricted-extras" packages which comes with common codecs.

If you have an nvidia GPU, you can install the recommended drivers using 
```
sudo ubuntu-drivers autoinstall
```
For AMD or Intel GPUs, the drivers are built-into the kernel.  Some laptops have hybrid setups which I don't have any experience with, so if you have that, say something for people to know.
Do not visit nVidia's support website and get drivers from them, unless someone you trust says to do that. Canonical tests specific driver versions with specific kernels to avoid undesirable results.

Youtube generally sends video as vp8 or vp9 video codecs.  VP9 is the h.265 version of Google's video codecs, but it requires a fast CPU and/or hardware driver support in the GPU to work.  Depending on the GPU and age of the computer, this may not work.  Short of getting a better GPU, there isn't much that can be done. However, VP8 is similar to h.264 which is what nearly all streaming sticks and computers have supported with GPU hardware made since 2012. Even the lowest end chromebooks support it.

The easy way to see what GPU and which drivers are being used is with a command that isn't pre-installed on Ubuntu:
```
$ inxi -Gxx
```

I've removed all my nvidia GPUs, so I can't show what that look like, but here's two AMD systems - one with kernel driver support and the other without it:
With (20.04):
```
$ inxi -Gxxz
Graphics:  Device-1: AMD vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 0a:00.0 
           chip ID: 1002:1638 
           Display: server: X.Org 1.20.8 driver: **amdgpu** compositor: gnome-shell 
           resolution: 1920x1200~77Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 compat-v: 3.1 
           direct render: Yes 

```
Without (18.04):
```
$ inxi -Gxxz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Cezanne bus-ID: 08:00.0 chip-ID: 1002:1638
           Display Server: x11 (X.Org 1.20.8 ) drivers: **fbdev**,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 1920x1200@77.00hz
           OpenGL: renderer: llvmpipe (LLVM 10.0.0, 128 bits)
           version: 3.3 Mesa 20.0.8 (compat-v: 3.1) Direct Render: Yes
```
Those are identical computers, just running different versions of Ubuntu.

As for software support, not including drivers, I tend to avoid looking at videos using a web browser because .... let's just say I have reasons that most people wouldn't have.  To play back and watch most youtube videos, I'll use either **mpv** or **vlc**. Both are dependent on ffmpeg libraries and compile in pretty much any codec we'd want used.  mpv will use hardware drivers, if possible. I don't really if asking is needed or not.  mpv can have a GUI front-end - think that's called **smplayer**. I don't use it.  A file manager can be setup to send all video files to mpv in the application defaults, if you like.  If youtube-dlp is installed, mpv will playback youtube (and other websites') videos using normal URLs too.  Just an option.

```
sudo apt install mpv smplayer 
```
I have doubts that installing just ffmpeg will solve playback issues in a browser, but it might. I just wouldn't expect it will.  ffmpeg is a great tool. I use it multiple times a day. There's probably a video transcoding task running right now on one of my systems using ffmpeg. Good tool.

---

