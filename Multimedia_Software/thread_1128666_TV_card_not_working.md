---
title: "TV card not working"
date: 2009-04-17
forum: Multimedia Software
---

### Post by wb8976 on 2009-04-17
Hello. I recently went back to Ubuntu with the 9.04 beta and later upgraded to the RC. I have a Generic BT878 chipset based TV card, and only today did I get around to seeing if it was configured properly.

I had XawTV installed, my preferred TV application. When I run the program however, I don't get any video in the viewing window, only black. Running XawTV in the terminal gives me these errors:

```
hazel@hazel-desktop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-11-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
libv4l2: error turning on stream: Device or resource busy
ioctl: VIDIOC_STREAMON(int=1): Device or resource busy
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
libv4l2: error turning on stream: Device or resource busy
ioctl: VIDIOC_STREAMON(int=1): Device or resource busy
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Device or resource busy
libv4l2: error dequeuing buf: Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Invalid argument

```

I get similar errors when running TVTime or Zapping. I can run other video applications like Xine or VLC Media Player with no issues, so I know it's not my graphics card. My graphics card is an ATI Radeon 9200SE using the open source ATI drivers as the official proprietary drivers no longer support my card.

Can someone help me get my BTTV card working?

---

### Post by wb8976 on 2009-04-18
Sorry if I am bumping this, but I do need my TV card up and running soon.

---

### Post by wolfen69 on 2009-04-18
see [this]("http://www.linuxtv.org/wiki/index.php/Bttv_devices_(bt848%2C_bt878)").

---

### Post by wb8976 on 2009-04-18
> **wolfen69 said:**
> see [this]("http://www.linuxtv.org/wiki/index.php/Bttv_devices_(bt848%2C_bt878)").

I looked at that, and I can't find a use for it. Im not an advanced user.

---

### Post by wb8976 on 2009-04-18
Sorry if I seemed a little blunt, but even though I have been using Linux for awhile, I still need to learn some things about it, like advanced configuration.

As for the TV Card, I decided to do a reinstall using the 9.04 Jaunty RC CD (I previously installed the beta version). Now for some reason, it works. Both XawTV and TVTime output video from the TV card.

---

### Post by wb8976 on 2009-04-19
And...after running Update Manager and rebooting the computer, the TV card doesn't work again. I assume the newer kernel provided in the updates somehow kills the TV card. Same issues as before.

I probably need help again.

---

### Post by alexkp on 2009-04-21
Hi, I was having the same problem with xawtv and came across your post.  I had better luck using mplayer:

```

sudo mplayer -tv driver=v4l2:noaudio:width=640:height=480:norm=ntsc:device=/dev/video0 tv://
```

---

