---
title: "GUVC viewer shuts off when i hit record"
date: 2011-11-21
forum: Multimedia Software
---

### Post by Stijnvanhees on 2011-11-21
[SIZE=2]what the title says.

I find a 2kb video file in the destination folder afer every try but that is corrupt. It seems this is a better app than cheese to record video from webcam so I'd like it to work. Cheese does the job but not very satisfactory. Making photo's works with GUVC. Can somebody help me?
[/SIZE]

---

### Post by htcrwn148 on 2011-11-21
i would also like to get help with this. i did a fresh install to check if it was something that i did, but no it is 11.10 that messed up. it worked fine in 10.10... hopefully we can get some help with this!!! anyone?

---

### Post by Stijnvanhees on 2011-11-22
I forgot to mention, but my machine works on 11.10 too. I never tried this app with another version of ubuntu.

On a semi-related note. Is it possible that Cheese actually works a bit better after I installed the Medibuntu package? Anyway I'd still like to use GUVC view too since so many people seem happy with it.

---

### Post by Stijnvanhees on 2011-11-27
apparently it's a known bug for this app in ubuntu 11.10

I found out about wxCam: [http://wxcam.sourceforge.net/index.php](http://wxcam.sourceforge.net/index.php) this one works, taking images as well as video capture.

---

### Post by no2498 on 2011-11-28
id like to know if dmesg loads a cam grabber for you
in a terminal type dmesg click enter
it will be close to the bottom if it does
if it loads one retry guvcview

---

### Post by solosister on 2012-02-18
Same problem as well with Dell D430 as thinkpad x60s both new Ubuntu 11.10 installations.


guvcview 1.4.5

(guvcview:10084): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2212:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1613:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
Init. Venus USB2.0 Camera (location: usb-0000:00:1d.7-6)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/15, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/15, 
vid:0ac8 
pid:3420 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls

Control 0x0fffffff failed to query
fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
[mp2 @ 0xa047de0] codec type or id mismatches
could not open codec
Segmentation fault

---

### Post by lisati on 2012-02-18
Old thread closed.

@solosister: please start a new thread, and use [noparse]```
 and 
```[/noparse] tags around the output you are quoting.

---

