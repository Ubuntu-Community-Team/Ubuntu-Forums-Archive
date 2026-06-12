---
title: "Video Troubles (low frame rates) Ubuntu 10.10"
date: 2011-01-19
forum: Multimedia Software
---

### Post by daveco-inc on 2011-01-19
Hi!

I recently installed Ubuntu 10.10 (the newest stable release) and I am having video troubles. I have enabled the proprietary video driver for my video card, and the special desktop effects work great and very smoothly.

But when I try to play HD video, which using the same hardware on windows, used to play perfectly, have very low frame rates (1 frame every ten seconds). The change is evident on both videos streamed from youtube and locally stored videos.

I am using a standard Ubuntu set up, with totem and I am trying to play HD .mkv files.
[B]
Thanks in advance for anyone's help![/B]

---

### Post by BicyclerBoy on 2011-01-19
What's the video h/w ?
What driver ?

What other media players have you used for playback & how were they configured (video) ?

Do you have medibuntu repository enabled ?

---

### Post by daveco-inc on 2011-01-21
Video Hardware: Asus 1GB DDR3 GeForce GT220 with HDMI, VGA and DVI output.
Driver: (from Ubuntu Additional driver) NVIDIA accelerated graphics driver

On Windows: VLC, youtube
On Ubuntu: totem, youtube

I do not have the mediabuntu repository enabled, not that I know of anyway...

---

### Post by BicyclerBoy on 2011-01-21
Totem in Ubu10.10 now uses xine which isn't so good.

Ideally you wouild want to use a media player that utilises nvidia vdpau (purevideo).

AFIAK
VLC can do this natively only if built DIY or via the VA-API wrapper va-vdpau package.
You still have to configure the playback options.

mplayer (& any GUI frontend) could be a better bet.

I am surprised your h/w works so badly tho'.
An atom netbook intel GPU can play H264 720x576 just fine.
A core2duo can play H264 1080 on 50% CPU.

Maybe your video driver installation is bad.
Post your 
/var/log/Xorg.0.log
file..

In terminal run
glxgears
vdpauinfo

---

### Post by no2498 on 2011-01-21
try your videos in smplayer
type it in a terminal it tells you how to install it

---

### Post by daveco-inc on 2011-01-25
/var/log/Xorg.0.log file: [http://pastebin.com/LnLF0WRZ](http://pastebin.com/LnLF0WRZ)

glxgears: 17128 frames in 5.0 seconds = 3425.437 FPS

vdpauinfo: command not found

So I should install smplayer then?

Thanks so much for everyone's help, by the way! :-)

---

### Post by BicyclerBoy on 2011-01-25
run nvidia-xsettings (GUI)

turn off xinerama
check twinview is off

save to xorg.cong
exit
reboot

Install vdpauinfo & latest video driver etcfrom nvidia ppa or  from Ubuntu X team ppa

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

note: your PCIe video card is in a x1 slot, can you use the x16 or x8 slot ?

---

