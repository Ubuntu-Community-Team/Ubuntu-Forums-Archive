---
title: "Webcam Support"
date: 2010-12-26
forum: Multimedia Software
---

### Post by lonemangx on 2010-12-26
Is there support for the A4tech PK-7MAR? I used cheese and it always display a blank screen. The device is actually listed as /dev/video0. I also tried camorama, guvcview, wxcam and none worked. I also have a Creative PD1001 although I don't know how to install the drivers and where the original source is just the patch: [[COLOR="DarkOrange"]epcam[/COLOR]]("http://members.chello.nl/~j.vreeken/se401/").

Thanks,
Homer

---

### Post by xc3RnbFO8P on 2010-12-26
Try: Alt-F2 
copy7paste into window
> gstreamer-properties
run.

Video> Pipeline> Test

---

### Post by lonemangx on 2010-12-26
I have tried it a couple of times actually. The default output test shows a window of vertical colors and a smaller box of noise with a window message saying: Testing... Click Ok to finish. The default input just shows(using v4l2) the window message. I get a message in terminal when I run this:gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
Does this help?

Thanks

---

### Post by xc3RnbFO8P on 2010-12-26
Read this:
[http://ubuntuforums.org/showpost.php?p=9565512&postcount=1]("http://ubuntuforums.org/showpost.php?p=9565512&postcount=1")

---

### Post by lonemangx on 2010-12-26
I found out I already have the ffmpeg and the ugly. I just installed the bad set, but nothing has changed I still get a black screen output.

---

### Post by xc3RnbFO8P on 2010-12-26
> The default output test shows a window of vertical colors and a smaller box of noise with a window message saying: Testing... Click Ok to finish.
Did you try to change the output to: X Window system (no xv) or x11

---

### Post by lonemangx on 2010-12-26
Yeah, tried it has the same output with autodetect.

---

### Post by Syed75 on 2010-12-26
You need a [gspca]("http://packages.ubuntu.com/hardy/all/gspca-source/download")  driver probably.

---

### Post by lonemangx on 2010-12-27
> **Syed75 said:**
> You need a [gspca]("http://packages.ubuntu.com/hardy/all/gspca-source/download")  driver probably.

I installed it but nothing has changed, still a black screen output.

Thanks

---

### Post by no2498 on 2010-12-27
did you restart the computer that driver is in a kernel 

hope that helps

---

### Post by lonemangx on 2010-12-29
I did restart but it is still the same. I actually tested a Crunchbang LiveCD and the webcam works using VLC. Don't know what the problem with ubuntu.

---

### Post by xc3RnbFO8P on 2010-12-30
Try this:

> vlc v4l2:// :v4l-vdev="/dev/video0"
> vlc v4l2:// :v4l-vdev="/dev/video1"

---

### Post by no2498 on 2010-12-30
if your testing in vlc
open vlc click media 
open capture device
click play

---

### Post by lonemangx on 2010-12-31
> Try this:

Quote:
vlc v4l2:// :v4l-vdev="/dev/video0"

It gave this output:
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9897914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb74460d4, 0xb7446048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1293487306)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1813): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)

---

