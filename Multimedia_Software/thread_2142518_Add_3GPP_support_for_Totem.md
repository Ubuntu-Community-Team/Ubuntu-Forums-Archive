---
title: "Add 3GPP support for Totem?"
date: 2013-05-06
forum: Multimedia Software
---

### Post by Roasted on 2013-05-06
In prior versions of Ubuntu I had Totem working without issue with certain MP4 files of mine. Some of them I can see have the 3GPP codec, which is looking like it's an issue in this case. Any time I try to open an MP4 with the 3GPP codec in Totem it says "This file is corrupt and can not be played." Even if I run Totem from terminal, same error, but absolutely nothing in terminal.

A user in IRC indicated that I can run "file video.mpg" in terminal to find a little bit of into out on the file. That's where we saw the 3GPP link. I'm just curious as to how I can get these videos working with Totem like I once had on 12.04, except this time with 13.04. Restricted-extras are installed.

Note: I know VLC is a great media player and would be a sweet alternative, but I am specifically trying to get this working with Totem since VLC is giving me some extensive headaches due to [this bug.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1176379")

---

### Post by Yellow Pasque on 2013-05-06
Is gstreamer1.0-libav installed?

---

### Post by Roasted on 2013-05-06
$ sudo apt-get install gstreamer1.0-libav
[sudo] password for jason: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer1.0-libav is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Yep. :(

---

### Post by mc4man on 2013-05-06
Out of curiosity - there are 2 3gpp sample clips here you can download, unzip & try. Can you play them in totem?
If so, then it would be good if a sample of an unplayable one was available for others to test.
[http://support.apple.com/kb/HT1425](http://support.apple.com/kb/HT1425)

---

### Post by Roasted on 2013-05-06
Both of those work. :(

This video here is one I was unable to get working. It's a 60 second clip from my video surveillance system:

[http://skynetcore.zapto.org/public/video/](http://skynetcore.zapto.org/public/video/)

(note - that server will be offline in a few hours due to me upgrading the OS HDD to an SSD)

EDIT - When I run "file video.mp4" it gives me some basic info on the file. Here's what I got for these videos:

Test 1:
:~/Downloads$ file sample.3gp 
sample.3gp: ISO Media, MPEG v4 system, 3GPP

Test 2:
:~/Downloads$ file sample_3GPP2.3g2
sample_3GPP2.3g2: ISO Media, MPEG v4 system, 3GPP2

My Video Surveillance Clip:
:~/Desktop$ file 01.mp4 
01.mp4: ISO Media, MPEG v4 system, 3GPP

---

### Post by mc4man on 2013-05-06
The file you uploaded is - 
Format                                   : MPEG-4
Format profile                           : 3GPP Media Release 5
Codec ID                                 : 3gp5

made on a Vivotek device which is known to create files with issues.
ffmpeg & libav have no real issue with the file, so vlc, mplayer will play ok. Seems that totem or gstreamer does though and have for some time. (easy to test for that, when I get back.

While you may not wish to if you use ffmpeg or avconv to copy the file it then will work fine in totem (they must create a new header or something.
Can be seen in screens, 2.mp4 is thumbnailed & plays fine in totem
(the copy takes a couple of sec.'s

Ex. command using repo avconv (install libav-tools
```
avconv -i /home/doug/Documents/01.mp4   -c:v copy  /home/doug/Documents/2.mp4
```

---

### Post by Roasted on 2013-05-06
Yes indeed I'm using Vivotek cameras.

In short, are you basically saying that this will be problematic with Totem due to the way Vivotek packages the MP4s? I know with 12.04, Totem worked fine with these files from the camera system. This is insanely disappointing. Part of the reason I wanted Totem to work was largely due to it being my backup plan, which I'd like to use right now. At the present time there's an issue with FUSE or something on the backend of VLC that causes it to freeze in 13.04 when playing videos over SMB/GVFS. Having Totem working, which like I said, it did work on 12.04, was nice because then I could utilize that to still view my feeds back if need be.

---

### Post by Yellow Pasque on 2013-05-06
You may want to file a bug with gstreamer (giving an example file that doesn't work).
> In short, are you basically saying that this will be problematic with Totem due to the way Vivotek packages the MP4s?
Yes, but mc4man's command should be useful to you to "convert" the files into a format that opens without fuss.

---

### Post by mc4man on 2013-05-06
If filing a bug with gstreamer then you may want to supply a smaller file, can't use ffmpeg or avconv to cut a small sample as they 'fix' the problem

Definitely gst  issue - 
```
gst-launch-1.0 -v playbin uri=file:///home/doug/Documents/01.mp4 
clipped ...
/GstPlayBin:playbin0/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstQTDemux:qtdemux0.GstPad:sink: caps = application/x-3gp, profile=(string)basic
ERROR: from element /GstPlayBin:playbin0/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstQTDemux:qtdemux0: This file is corrupt and cannot be played.
Additional debug info:
qtdemux.c(7644): qtdemux_parse_trak (): /GstPlayBin:playbin0/GstURIDecodeBin:uridecodebin0/GstDecodeBin:decodebin0/GstQTDemux:qtdemux0
ERROR: pipeline doesn't want to preroll.
```

---

### Post by Roasted on 2013-05-06
Bug reported:

[https://bugzilla.gnome.org/show_bug.cgi?id=699791](https://bugzilla.gnome.org/show_bug.cgi?id=699791)

Thanks everyone for your help with this! I'll post back here if anything monumental with the issue changes.

Oh, and I did end up uploading a different file (even though it shares the same 01.mp4 name as the ~60MB one I posted earlier). I shared it through my DropBox and linked it to the report. Thanks again!

---

### Post by mc4man on 2013-05-06
Also just to note - the same error is seen when using gst-1.1.x (current dev, 1.1.0.1+git20130503.abdfb8d4 to be exact

---

