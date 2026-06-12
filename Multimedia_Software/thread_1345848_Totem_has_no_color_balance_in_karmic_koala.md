---
title: "Totem has no color balance in karmic koala"
date: 2009-12-04
forum: Multimedia Software
---

### Post by lcn_mustard on 2009-12-04
I just installed ubuntu a karmic koala pcchips A15G (Use nvidia) and everything
is ok with the exception of the totem, the brightness and contrast has no
effect.

sudo apt-get remove totem-gstreamer
sudo apt-get install totem-xine

In player xine it works ok. In ubuntu 8.4 was in / home / sillas / .config /
totem / xine_config and put what I wanted. In Karmic this file does not exist,
but it includes no avail. Any idea?

I'm positive, the monitor is fine. This problem started after I installed the
karmic koala (installation by the live-cd). Before, I used the Hardy Heron and
was ok. Everything was working in totem. In hardy I was able to uninstall the
totem-gstreamer and switch to totem-xine, the karmic even following the same
steps it does not. Already removed with apt-get and reinstalled and nothing
changes.!? The gstreamer-properties does not help. Not even know what to do ...

in the gstreamer-properties > Video > default output plugin > custom line:
videobalance hue=-1 ! autovideosink and my video turns to red...

I try videobalance hue=0 saturation=50 contrast=-50 brightness=1500 !
autovideosink
Only shows me hue efects and not exist the colour balance in
Edit->Preferences->Display

This problem only happened in totem and always hapenned in ubuntu
(7.10-8.04-9.10) but i was able to fit it and had compiz and cairo-dock with no
error . Now I am using xine player (ugly) but is works.
I really prefer totem and I hope fix to fix it.


~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"
    number of ports: 32
    port base: 355
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x22
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
    number of attributes: 3
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_ITURBT_709" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SYNC_TO_VBLANK" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 2046 x 2046
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
  Adaptor #1: "NV05 Video Blitter"
    number of ports: 32
    port base: 387
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x22
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
    number of attributes: 2
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_SYNC_TO_VBLANK" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2046 x 2046
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x3
        guid: 03000000-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff

---

### Post by xouns on 2009-12-05
The saturation bar worked for me. Don't know whether this will hold after reboot, but it works for now. Thanks, guys!

---

### Post by mc4man on 2009-12-05
Depending on your video adapter you may or may not have color balance settings available in the edit -> preferences for totem as seen in your screen
> number of attributes: [COLOR="Blue"]3[/COLOR]

In your case they're not, we have 3 setups, all on karmic with nvidia and the 185 driver. Two are the same as you ( no color balance avail.) one has it.
>     number of attributes: [COLOR="Blue"]7[/COLOR]
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_ITURBT_709" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SYNC_TO_VBLANK" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)


Try making adjustments in nvidia Xserver settings if need be.

The settings can also be changed in gconf-editor -> totem, though the values aren't intuitive and may cause more trouble then worth ( default values equaling the middle slider are 32768

There is no working totem-xine package anymore in karmic, it's just a dummy.
While it's possible to build and run a real totem-xine in it's place, if you've upgraded to totem 2.28.2 then it won't work as well as with the totem-common from 2.28.1, for the most part you can consider it dead and almost buried

---

### Post by lcn_mustard on 2009-12-05
> **mc4man said:**
> Depending on your video adapter you may or may not have color balance settings available in the edit -> preferences for totem as seen in your screen


In your case they're not, we have 3 setups, all on karmic with nvidia and the 185 driver. Two are the same as you ( no color balance avail.) one has it.


Try making adjustments in nvidia Xserver settings if need be.

The settings can also be changed in gconf-editor -> totem, though the values aren't intuitive and may cause more trouble then worth ( default values equaling the middle slider are 32768

There is no working totem-xine package anymore in karmic, it's just a dummy.
While it's possible to build and run a real totem-xine in it's place, if you've upgraded to totem 2.28.2 then it won't work as well as with the totem-common from 2.28.1, for the most part you can consider it dead and almost buried

It was very explanatory. Thank you. Pitty had removed the totem-xine. The xine player works very well with the output xshm but I'm using mplayer and it fits well with the work output to gl as x11, but really do not like its interface. I'm trying to use the gmplayer it but the color setting is not saved, if you close the program I have to adjust the colors again. weird. Maybe go back to Hardy Heron does not know. Thanks anyway.[IMG]http://www.google.com/images/cleardot.gif[/IMG]

---

### Post by lcn_mustard on 2009-12-09
Do not install it nothing, nothing removed.
I haven't changed the xorg.
I haven't changed the nvidia x server settings tools.
In gstreamer-properties -> video output-> custom-> pipeline:
tried several commands, which ran:
videobalance hue=-0 saturation=1 brightness=1 ! videoscale ! ffmpegcolorspace ! ximagesink
 [[...]]("javascript:void(0);")
--
videobalance hue=-0 saturation=1 brightness=0.25 ! xvimagesink
--
videobalance hue=-0 saturation=1 brightness=0.25 ! autovideosink
--
The best command was "videobalance hue=-0 saturation=1 brightness=0.25 ! autovideosink"
For the internet I found some tips to "videobalance hue =- 1 ! Autovideosink" or "videobalance hue =- 100 ! Autovideosink" I decided to include the parameters you wanted, saturation and brightness using whole numbers and it worked. 
 The totem ran all night without problems, videos wmv, flv, avi and mp4 and mp3 with effects.
 We do not understand why removed the totem-xine, which I personally think better and easier to configure. In ubuntu 8.04 xshm used, configured in / home / folder User / .config / totem / totem_config with everything ok. Pitty
This setting doesn't affect the players xine (xshm ) or mplayer, both are still working (saturation and brightness, etc.).
 Hope that helps.

---

### Post by lcnrj on 2010-07-15
nobody knows solve that problem. I think is not the video driver but the payer because in xine ui its not happen

---

