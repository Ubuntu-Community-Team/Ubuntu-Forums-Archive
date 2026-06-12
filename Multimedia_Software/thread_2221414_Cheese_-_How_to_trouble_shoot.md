---
title: "Cheese - How to trouble shoot?"
date: 2014-05-02
forum: Multimedia Software
---

### Post by suomalainen on 2014-05-02
Ubunteros,

I have two laptops. Both are running 12.04LTS with MATE desktop 1.6.0.

Laptop A has kernel version 3.5.0-49-generic
Laptop B has kernel version 3.2.0-60-generic

On both laptop "A" & "B" I'm using an EasyCap USBTV007 video grabber. The drivers were downloaded and installed from here:

[https://github.com/mwelchuk/usbtv](https://github.com/mwelchuk/usbtv)

On laptop "A" Cheese is working. VLC is working. 

On laptop "B" Cheese IS NOT WORKING. VLC is working.

Question:

1) Could the kernel version be effecting why cheese is not working?
2) Is there a way to compare the settings and files between both machine in order to try and isolate the issue as to why Cheese does not work on laptop "B"???

Thank you!!

---

### Post by dannyboy79 on 2014-05-02
easy way is to launch cheese from the command line and see what the output is. have you tried guvcview? i find it superior to cheese as far as no frills just work type of webcam software.

---

### Post by suomalainen on 2014-05-03
Thanks for helping dannyboy79!

When launching Cheese I have two devices I would like to use. Device #1 is a EasyCap Video Grapper and Device #2 is a webcam. Both these devices failed to open when launching Cheese from terminal. As an FYI, the video grapper does work under VLC. The web cam does work under Gvucview.

Here is the reported error messages reported by Terminal when attempting to launch Cheese using the Video Grabber. I need this to be working more than the web cam.

```
me@me-CF-29CTKGHGS:~$ cheese

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:14:62: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:25:74: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:53:73: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:64:73: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:75:73: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:86:73: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:59:15: Horizontal and vertical offsets are required

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:305:60: Junk at end of value

(cheese:1894): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:327:60: Junk at end of value

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1894): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (cheese:1894): WARNING **: Could not negotiate format

```

Here is the reported error messages reported by Terminal when attempting to launch Cheese using the Web Cam.

```
me@me-CF-29CTKGHGS:~$ cheese

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:14:62: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:25:74: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:53:73: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:64:73: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:75:73: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:86:73: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:59:15: Horizontal and vertical offsets are required

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:305:60: Junk at end of value

(cheese:1980): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:327:60: Junk at end of value

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:1980): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (cheese:1980): WARNING **: Could not negotiate format


```

Here is the reported error messages reported by Terminal when attempting to launch Gvucview using the Video Grabber.

```
me@me-CF-29CTKGHGS:~$ guvcview
guvcview 1.5.3
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround71
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib setup.c:565:(add_elem) Cannot obtain info for CTL elem (MIXER,'IEC958 Playback Default',0,0,0): No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:14:62: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:25:74: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:53:73: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:64:73: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:75:73: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets-img.css:86:73: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:59:15: Horizontal and vertical offsets are required

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:305:60: Junk at end of value

(guvcview:1885): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:327:60: Junk at end of value
video device: /dev/video0 
Init. usbtv (location: usb-0000:00:1d.7-1)
{ pixelformat = 'YUYV', description = '16 bpp YUY2, 4:2:2, packed' }
VIDIOC_ENUM_FRAMESIZES - Error enumerating frame sizes: Inappropriate ioctl for device
  Unable to enumerate frame sizes.
: Inappropriate ioctl for device
{ pixelformat = 'RGB3', description = 'RGB3' }
{ ?GSPCA? : width = 720, height = 480 }
fmtind:2 fsizeind: 1
{ pixelformat = 'BGR3', description = 'BGR3' }
{ ?GSPCA? : width = 720, height = 480 }
fmtind:3 fsizeind: 1
{ pixelformat = 'YU12', description = 'YU12' }
{ ?GSPCA? : width = 720, height = 480 }
fmtind:4 fsizeind: 1
{ pixelformat = 'YV12', description = 'YV12' }
{ ?GSPCA? : width = 720, height = 480 }
fmtind:5 fsizeind: 1
vid:1b71 
pid:3002 
driver:usbtv
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
Segmentation fault (core dumped)
me@me-CF-29CTKGHGS:~$ 
```


Thank you for any advice you can offer in trouble shooting this issue.

Suomalainen

---

### Post by suomalainen on 2014-05-04
Bump...

---

### Post by suomalainen on 2014-05-10
Bump....

---

