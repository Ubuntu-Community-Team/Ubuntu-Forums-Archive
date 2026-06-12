---
title: "USB Video Capture"
date: 2007-07-07
forum: Multimedia Production
---

### Post by zaffod on 2007-07-07
Hi All.

I have made the switch to an Ubuntu desktop. Almost everything works and I'm almost done with Windows.

The one remaining issue I have is with capturing video from my DV cam. It only has USB output. I have found that linux is unable to capture video from USB, only from ieee1394.

Can any one advise how I can capture from USB in linux? USB 2 is as fast as firewire, so I'm not sure why apps like Kino still do not support this.

Any help is welcome, or I'll have to install VMware and capture video from a virtual Windows machine. Would rather not have to do this.

My hardware:
JVC DV Cam GR-DX77AA
asus m2n-mx (no ieee1394)
AMD64 x2 2800+
2GB JetRam 667
	
Output from lsusb:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 04f1:000a Victor Company of Japan, Ltd GR-D72 Digital Video Camera
Bus 001 Device 004: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 001 Device 001: ID 0000:0000


Output from ls /dev/ | grep dv:

dvd
dvdrw

Thanks, karl

---

### Post by Ivo2406 on 2007-10-02
Maybe Video4Linux(v4l) detects your device, then you may Capture it with the VLC player

Look here  [COLOR="Blue"][http://www.linuxtv.org/v4lwiki/index.php/Main_Page]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page")[/COLOR]

and here [http://www.videolan.org/]("http://www.videolan.org/")

---

### Post by eye208 on 2007-10-02
> **zaffod said:**
> Can any one advise how I can capture from USB in linux? USB 2 is as fast as firewire, so I'm not sure why apps like Kino still do not support this.
Does the camera show up as a USB mass storage device if you insert an SD card? Some JVC camcorders from the GR-Dxxx series are known to work that way.

---

### Post by wasmuthk on 2007-11-09
Has anyone had any success wit this? I, too, am fully converted to Ubuntu except for my video capture from my DVC 150. I guess I could go buy a firewire card, but it seems foolish if I don't need to.

---

### Post by nutter78 on 2007-11-21
bump bump - i too would greatly appreciate a heads up on this!!

---

### Post by miserabledutchman on 2008-01-01
Has anybody tried dvGrab off kino's website, i think it's kinodv.org.  downloading now.

---

### Post by zaffod on 2008-01-22
If you can get a firewiwre card, do so. 
I ended up finding a 'hidden' ieee1394 port on my dvcam, and the quality of the captured video is far better than that captured via USB on my old windows machine. 
This may well be why no one has bothered to set up USB video capture on linux.

---

### Post by DavidTangye on 2008-01-29
I have just set up webcam video capture on my machine. It all went fairly easily.

Machine: Asus M2N-MX-SE, 1GB RAM, AMD 3800+ CPU.

Webcam: Logitech Quickcam Orbit via USB. Its a 3 or 4 year old cam.
lsusb: Bus 001 Device 002: ID 046d:08b5 Logitech, Inc.

Ubuntu 7.10, plus added VLC, Camorama and Ekiga Softphone. All these apps recognise the webcam automatically. None seem to offer to do pan or tilt though. Perhaps the driver cannot support this anyway, I dont know.

To make an mpeg:
In VLC, "Open Capture Device", change the video to /dev/video0, audio to /dev/audio1, and set the Stream/Save on, then in the Settings button:

 - Set Output to local and to a file (set [filename].mp4)
 - Set Encapsulation Method to MP4, both Transcoding Options   video and audio on.
 - Later you might also want to fiddle with the the video bitrate and Scale to suit how much bandwidth vs size and clarity you want.

I used VLC to make [an mp4, uploaded it to Utube]("http://www.youtube.com/watch?v=qiuz0bDFKkg")[.]("http://www.youtube.com/watch?v=qiuz0bDFKkg")

---

### Post by vraetorian on 2008-03-12
Hi DavidTangye,
I got audio to record from my camera, though the video isn't yet showing up.

Any recomendations?

lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 010: ID 054c:00c0 Sony Corp. Handycam DCR-30
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  


In VLC I used /dev/video0  and /dev/audio1
mp4 encapsulating with video codec .mp4v

Could it possibly be something other than /dev/video0 , in VLC?
If a webcam can bring in usb video, I'm sure this camera can as well.
Any help is much appreciated.
-V

---

### Post by DavidTangye on 2008-03-26
I cant help much, sorry, unless we agree for the blind to lead the blind :-).

Perhaps the key is in knowing if/how Bus 001 Device 010 maps to /dev/video(n)? I think I have seen that sort of info around here, or somewhere on the net. Try googling something like 'linux usb device mapping'

---

