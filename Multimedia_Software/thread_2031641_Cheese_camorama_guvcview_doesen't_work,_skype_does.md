---
title: "Cheese camorama guvcview doesen't work, skype does with cam"
date: 2012-07-22
forum: Multimedia Software
---

### Post by firekage on 2012-07-22
Hi.

I would like to ask for Your help. I have Logitech C270 cam but it doesen't work with cheese and camorama. Cam works in skype and in gstreamer-properties.

As soon as i start cheese i have the following output:

```
firekage@deusex:~$ cheese

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkGrid to a GtkToggleButton, but as a GtkBin subclass a GtkToggleButton can only contain one widget at a time; it already contains a widget of type GtkLabel

(cheese:19671): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel

** (cheese:19671): CRITICAL **: cheese_camera_device_get_uuid: assertion `CHEESE_IS_CAMERA_DEVICE (device)' failed
**Naruszenie ochrony pami&#281;ci**
firekage@deusex:~$ 

```The one that is bolded in english should be like: **segmentation fault.** Cheese with Ubuntu 12.04 upgraded fro 11.10 doesen't start at all even when i try to run it from terminal.


As soon as i start camorama i have following output:

```
firekage@deusex:~$ camorama

(camorama:26644): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
```I see control panels from camorama but there is no video, no sound. 

```

firekage@deusex:~$ guvcview
guvcview 1.5.3
ALSA lib pcm_asym.c:106:(_snd_pcm_asym_open) capture slave is not defined
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM hdmi
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.SB-XFi.pcm.modem.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: Nie ma takiego pliku ani katalogu
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: Nie ma takiego pliku ani katalogu
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM phoneline
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : B&#322;&#261;d wej&#347;cia/wyj&#347;cia(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : B&#322;&#261;d wej&#347;cia/wyj&#347;cia(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : B&#322;&#261;d wej&#347;cia/wyj&#347;cia(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : B&#322;&#261;d wej&#347;cia/wyj&#347;cia(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
video device: /dev/video0 
Unable to find parent usb device.Unable to find parent usb device.Init. UNKNOWN/GENERIC (location: PCI:0000:04:07.0)
{ pixelformat = 'GREY', description = '8 bpp, gray' }
VIDIOC_ENUM_FRAMESIZES - Error enumerating frame sizes: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
  Unable to enumerate frame sizes.
: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
{ pixelformat = 'RGBO', description = '15 bpp RGB, le' }
   { not supported - request format(1329743698) support at http://guvcview.sourceforge.net }
{ pixelformat = 'RGBQ', description = '15 bpp RGB, be' }
   { not supported - request format(1363298130) support at http://guvcview.sourceforge.net }
{ pixelformat = 'RGBP', description = '16 bpp RGB, le' }
   { not supported - request format(1346520914) support at http://guvcview.sourceforge.net }
{ pixelformat = 'RGBR', description = '16 bpp RGB, be' }
   { not supported - request format(1380075346) support at http://guvcview.sourceforge.net }
{ pixelformat = 'BGR3', description = '24 bpp RGB, le' }
{ ?GSPCA? : width = 480, height = 480 }
fmtind:2 fsizeind: 1
{ pixelformat = 'BGR4', description = '32 bpp RGB, le' }
   { not supported - request format(877807426) support at http://guvcview.sourceforge.net }
{ pixelformat = 'RGB4', description = '32 bpp RGB, be' }
   { not supported - request format(876758866) support at http://guvcview.sourceforge.net }
{ pixelformat = 'YUYV', description = '4:2:2, packed, YUYV' }
VIDIOC_ENUM_FRAMESIZES - Error enumerating frame sizes: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
  Unable to enumerate frame sizes.
: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
{ pixelformat = 'UYVY', description = '4:2:2, packed, UYVY' }
VIDIOC_ENUM_FRAMESIZES - Error enumerating frame sizes: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
  Unable to enumerate frame sizes.
: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
{ pixelformat = 'RGB3', description = 'RGB3' }
{ ?GSPCA? : width = 480, height = 480 }
fmtind:5 fsizeind: 1
{ pixelformat = 'YU12', description = 'YU12' }
{ ?GSPCA? : width = 480, height = 480 }
fmtind:6 fsizeind: 1
{ pixelformat = 'YV12', description = 'YV12' }
{ ?GSPCA? : width = 480, height = 480 }
fmtind:7 fsizeind: 1
vid:0000 
pid:0000 
driver:cx8800
checking format: 1497715271
Unable to set 1/25 fps
VIDIOC_S_PARM error: Niew&#322;a&#347;ciwy ioctl dla urz&#261;dzenia
fps is set to 1001/30000
drawing controls

NEXT_CTRL flag not supported
**Naruszenie ochrony pami&#281;ci**
firekage@deusex:~$ 

```Guvcview doesen's show at all, like cheese, and **there is segmentation fault again - bolded one.**


My camera works in gstreamer-properties, works in skype but i would like to have the ability of recording by 3-rd party software and be able to use it freely, not when i use skype as a skype chat cam.

Could you help me?

My internet cam is Logitech C270 and when i put lsusb in terminal i see it:

```

firekage@deusex:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 002 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270

```

---

### Post by firekage on 2012-07-27
Anybody?

---

### Post by gyurma on 2012-08-01
Mine dies with segmentation fault...
 cheese[4075]: segfault at 0 ip 00007f66a9376096 sp 00007fffd92d94b8 error 4 in libc-2.15.so[7f66a92ef000+1b3000]

---

### Post by firekage on 2012-08-05
Can anybody help? I've got still segmentation fault with Cheese.

---

