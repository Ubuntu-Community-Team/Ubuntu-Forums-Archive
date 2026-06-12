---
title: "mplayer fails to use VDPAU device"
date: 2010-05-23
forum: Multimedia Software
---

### Post by gizmocan on 2010-05-23
Hi!

I have a Zotac IONITX-F-E motherboard (Intel Atom Dual Core 1.6 GHz +  Nvidia ION) -based box with Ubuntu 10.04 64-bit installed. My goal is to  play back 1080p video.

I have mplayer installed (which I compiled from source with --enable-vdpau). I try to run mplayer with this command:

```
mplayer -vo vdpau -vc ffh264vdpau path/to/myfile.mkv
```I get the following message in my terminal:

```
Error opening/initializing the selected video_out (-vo) device.
```I have libvdpau-dev and libvdpau1 installed.

After Googling this problem, I found a post that suggested the following steps:

```
sudo add-apt-repository ppa:nvidia-vdpau
sudo apt-get update
sudo apt-get install nvidia-glx-195 nvidia-195-modaliases
```It turns out that I had already added the nvidia-vdpau repository. However, despite that, I get:

```
E: Couldn't find package nvidia-glx-195
```The same problem exists for the nvidia-195-modaliases package.

Before doing all this, I was able to get the nvidia 195.36.24 driver installed, but [I am still having some trouble]("http://ubuntuforums.org/showthread.php?t=1488320"), which may or may not be related.

Any thoughts are appreciated!

---

### Post by gizmocan on 2010-05-31
I've resolved my desktop display problems by changing my Desktop Effects setting to None.

This had no impact on my problem with mplayer.

Can anyone help?

---

