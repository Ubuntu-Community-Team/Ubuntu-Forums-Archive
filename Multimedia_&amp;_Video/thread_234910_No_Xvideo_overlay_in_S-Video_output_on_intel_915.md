---
title: "No Xvideo overlay in S-Video output on intel 915"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by DrSpirograph on 2006-08-12
Hi,
I've got Dapper installed on a Compaq Presario M2000. XVideo playback of DVD's and Videos normally works fine, but yesterday I tried plugging into a TV via the S-Video out, and the X-Video overlay is not filled - I just get the blue colour-key inside the window on the TV-screen.

Does anyone know how I can get video playback going through S-Video?
I tried switching to the other output modules (I'm using xine, I tried, xshm, sdl and opengl) OpenGl didn't display at all, and with Xshm and opengl I get the video, but my CPU is too slow and so the video is choppy (with XVideo playback is smooth)

I've just been using the laptop's Fn-<Monitor> key combo to change the output to S-Video. Should I be setting up a second monitor in X.org instead?

Some info on my system:

$ lspci | grep Graphics 
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 9
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is -5)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 48)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 16777215)
    maximum XvImage size: 1440 x 1080
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
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

Thanks for any help.
Chris

---

### Post by rykeelty on 2007-10-08
I have the same problem on my Presario V2000 - svideo output on my television seems to work fine until I start a DVD, then no picture in movie player.  I altered the xorg.conf file to allow for svideo output, and I read in another forum that the problem could be that overlay needs to be turned on (whatever that means). I tried the following option in the device section (under identifier "svideo," the only device I have in the file that contains the i810 driver section):

         Option "OverlayOnCRTC2" "1"

This changed nothing when playing DVD in totem-gstreamer. It turned DVD output to blue screen (like you described above) in vlc. Still no picture when playing movie. It sounds like the same problem. Someone please help.

---

