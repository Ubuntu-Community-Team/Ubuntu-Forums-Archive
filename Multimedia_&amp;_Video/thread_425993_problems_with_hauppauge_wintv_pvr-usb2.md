---
title: "problems with hauppauge wintv pvr-usb2"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by sepalo on 2007-04-28
hello

the tv card doesn't work for me (in kubuntu 7.04) .
tvtime says "videoinput: Card failed to allocate capture buffers: Invalid argument" on terminal and "pvrusb2: Invalid argument; cannot open capture device /dev/video0" on the screen
The device /dev/video0 does exist (appears whenever I plug the card in); the driver pvrusb2 is loaded, firmware is installed by default, but still it doesn't work. Does anybody know what to do?

I also tried xawtv; it says:
"/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway"

v4l-info prints all kind of info about the card, I don't see anything potentially bad except for 
"VIDIOC_G_FMT(VBI_CAPTURE): Invalid argument"
(but there are many similar things which are not "Invalid argument"s or anything else scary)

and kdetv 
"WARNING: Device does not support streaming interface or is not a V4L2 device
WARNING: [VBIDecoder::restart()] no permition to access device"

thanks for any hints!

---

### Post by fededs83 on 2007-05-03
have you installed mplayer? If not install it and give "mplayer /dev/video0" you should see a channel......
I think that kdetv and tvtime don't support our video card. You should try xawtv or mythtv.
Actually I'm running mythtv and I have only some little troubles but after all it works ok!
Let me no
Fede

---

