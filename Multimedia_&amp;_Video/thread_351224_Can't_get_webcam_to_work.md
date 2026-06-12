---
title: "Can't get webcam to work"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by psi36 on 2007-02-01
I plugged in my webcam and tried to get it to work via [EasyCam]("https://help.ubuntu.com/community/EasyCam"), but to no avail.
Easycam recognizes this:
Bus 004 Device 002: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
And proposes these drivers: ov511 or ov51x
I tried ov51x first, but got an error, so tried again with ov511.
It says the webcam is installed and I should check if it works. When I try to start Camorama, I get an error: "Could not connect to video device (/dev/video0). Please check connection".

Help! :confused:

---

### Post by scrooge_74 on 2007-02-01
Maybe this can help you [http://tldp.org/HOWTO/html_single/Webcam-HOWTO/](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/)

---

### Post by psi36 on 2007-03-31
I've done everything as explained on [http://tldp.org/HOWTO/html_single/Webcam-HOWTO/](http://tldp.org/HOWTO/html_single/Webcam-HOWTO/) but I can't make a picture:
```
$ streamer -c /dev/video0 -b 16 -o Desktop/outfile.jpeg
files / video: JPEG (JFIF) / audio: none
v4l2: open /dev/video0: Function not implemented
v4l2: open /dev/video0: Function not implemented
v4l: open /dev/video0: Function not implemented
no grabber device available
```

Although there don't seem to be any errors in the system log:
```
Mar 31 12:28:06 my-laptop kernel: [17189560.928000] drivers/media/video/ov511/ov511.c: USB OV518 video device found
Mar 31 12:28:06 my-laptop kernel: [17189560.932000] drivers/media/video/ov511/ov511.c: Device revision 1
Mar 31 12:28:06 my-laptop kernel: [17189560.944000] drivers/media/video/ov511/ov511.c: Compression required with OV518...enabling
Mar 31 12:28:07 my-laptop kernel: [17189562.340000] drivers/media/video/ov511/ov511.c: Sensor is an OV6630AF
Mar 31 12:28:07 my-laptop kernel: [17189562.548000] drivers/media/video/ov511/ov511.c: Device at usb-0000:00:1d.1-2 registered to minor 0
Mar 31 12:28:07 my-laptop kernel: [17189562.548000] usbcore: registered new driver ov511
Mar 31 12:28:07 my-laptop kernel: [17189562.548000] drivers/media/video/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver
```

Any other tips on what I could try to get my webcam working?

---

### Post by psi36 on 2007-03-31
BTW: I'm using a Philips ToUcam XS

---

### Post by psi36 on 2007-05-12
Strange thing is that the led on the camera is lit, so I'd expect it to work.

---

### Post by psi36 on 2007-06-24
I just upgraded to Feisty and tried the instructions on [https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x) and now my webcam works. I got a good image in xawtv.

I cant remember if I tried the instructions on that page before, maybe not. Or maybe it's because of the newer kernel in Feisty that it's working now. I don't know. But I'm glad I got it working anyway!

---

### Post by hetzz on 2007-09-06
Ive been searching so long for this :D (why didnt i search for the lsusb result earlier)

Bus 001 Device 008: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam


Now the computer recognizes the webcam but the picture is just a kaos with colours. Anyone got any ideas why? (it worked in windows a couple of weeks ago, havent moved the cam) 
Really happy i got any result at all but it aint doin what it supposed to do yet =/

---

