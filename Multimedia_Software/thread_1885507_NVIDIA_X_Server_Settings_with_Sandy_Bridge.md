---
title: "NVIDIA X Server Settings with Sandy Bridge"
date: 2011-11-23
forum: Multimedia Software
---

### Post by Dan Again on 2011-11-23
I've been on a quest to mitigate the screen tearing I'm experiencing using an i3 Sandy Bridge processor. One of the most frequently proposed solutions is to open NVIDIA X Server Settings and manipulate the "sync to vblank" option. However, when I open the settings tool I get the following message...

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

So I run nvidia-xconfig as root and it completely breaks my system...I had to boot into my system using a live CD and remove /etc/X11/xorg.conf.

What's going on?

---

### Post by BicyclerBoy on 2011-11-23
You should not be using any nVidia utilities with the sandybridge graphics.

The only exception would be the Frankenstein's monster "Optimus"..& then you would use Ironhide or Bumblebee..

lsmod
You should see i965 driver
glxinfo | grep OpenGL
you should see Tungsten Graphics

The tool you would use with HD200/3000 is:
driconf

I would use the latest kernels & xorg-edgers launchpad ppa.
You could try VAAPI:
vainfo

Screen tearing has a bad history with nVidia & composite windows managers.

---

### Post by Dan Again on 2011-11-25
Thanks for the reply, Bicycle.

When I run lsmod, I do see the i965 driver. Here is output...


Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  0 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
i915                  566711  2 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
drm_kms_helper         42558  1 i915
snd_seq_midi_event     14899  1 snd_seq_midi
drm                   236330  3 i915,drm_kms_helper
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  1 i915
mei                    41480  0 
video                  19412  1 i915
psmouse                73882  0 
serio_raw              13166  0 
joydev                 17693  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
r8169                  52788  0 

However, when I run glxinfo |grep OpenGL, I get the following...


Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I installed and ran driconf and got the following error...

libGL is too old.

When I installed and ran vainfo, I got the following error...


libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

I'm not really sure what all this means. Any idea? Thanks again for all your help.

---

### Post by BicyclerBoy on 2011-11-25
If you look in the /var/log/Xorg.0.log file you will see that xorg is trying to load nvidia-glx driver & failing. This is caused by messed up symlinks.

I guess that you have:
1. tried to install the nVidia driver
2. have residual driver components from previous h/w..

Could try:
sudo apt-get remove --purge nvidia*
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

Your video driver comes in the xserver xorg package.
The best SNA performance probably comes from recent kernels & xorg-edgers ppa.

---

### Post by Dan Again on 2011-11-26
Purging NVIDIA enabled me to get into driconf (thanks), but I'm still having the screen tearing issue. I feel like I've tried everything. I read something about forcing video overlay, but I don't know how to do this with gstreamer, which is what I think I'm using. Any advice on what to do in driconf to mitigate screen tearing or how to overlay video?

---

### Post by BicyclerBoy on 2011-11-26
Synchronization with vertical refresh ..

There are a couple of video overlay methods..the ones that could work for you are:
XVideo
openGL
The video decode VA-API could be useful..
I believe all these use DRI..
gstreamer should just work with DRI.
There is a recent VA-API support in gstreamer (DIY build ?)

glxinfo
glxinfo | grep OpenGL   [check not s/w rasteriser]
glxgears

There are composite (ccsm) settings that can mess up unity..best not to touch unity settings.

---

