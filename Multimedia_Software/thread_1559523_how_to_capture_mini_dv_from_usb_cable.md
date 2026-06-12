---
title: "how to capture mini dv from usb cable?"
date: 2010-08-23
forum: Multimedia Software
---

### Post by dioxholster on 2010-08-23
there doesnt seem to be a software in linux that allows that and the mim dv doesnt get recognized at all.

---

### Post by dalmeida on 2010-10-24
Wrong. Yes, there is a way to capture minidv footage via usb in linux using dvgrab. Just install dvgrab using sudo apt-get install dvgrab (you might need to adjust your apt.sources if apt doesn't find it). Once dvgrab is installed, plug your camera to your laptop, and run the following:

dvgrab -v4l -input /dev/video0 -a -t -f raw

A quick read of dvgrab man pages tells us this:

"dvgrab also supports UVC (USB Video Class) compliant DV  devices  using
Linux  kernel  module  uvcvideo,  which is a V4L2 driver.

-a --> Try  to  detect whenever a new recording starts, and store it into a separate file. Autosplit is off by default.

-t -->  Put information on date and time of recording into file name.

-f, -format --> Specifies the format of the output file(s). File  format  can  also  be  determined  if you include an extension on the base
name.(dv1 | dv2 | avi | raw | dif | qt | mov | jpeg | jpg | mpeg2 | hdv)


These are the options I've used and they worked for me, check out dvgrab for more options if you wish, but this should be able to get you going. I use this tool to grab all my vids from my camera and then use cinelerra for the editing. Hope this helps you out.

---

### Post by Geremia on 2011-07-01
> **dalmeida said:**
> dvgrab -v4l -input /dev/video0 -a -t -f rawMy system doesn't have a video0 device. I'm hoping that after following [the instructions here]("https://help.ubuntu.com/community/UVC") I'll get it to work.

EDIT: After trying those instructions, running this command```
dvgrab -V -input /dev/video0
```produces this error:```
Error: v4l2reader.cc:66: In function "virtual bool v4l2Reader::Open()": "m_fd = open( m_device, O_RDWR | O_NONBLOCK, 0 )" evaluated to -1
v4l2reader.cc:66: errno: 2 (No such file or directory)terminate called without an active exception
Abortado
```

---

