---
title: "Webcam not working with Cheese"
date: 2009-08-03
forum: Multimedia Software
---

### Post by RogerD on 2009-08-03
Hi 

Having real problems getting Cheese to work. It shouldn't be a problem, I've got a Logitech QuickCamPro 9000 webcam, video works in Skype and I've also had guvciview working perfectly.

What generally happens is that Cheese starts, the orange light on my webcam comes on briefly,but then goes off, and there's no image in the Cheese window. However, occasionally the light comes back on again, and I do get an image, although the response is very slow.

The settings on the video tab of my multimedia systems selector are:

Default Output
Plugin: X Window System (Xaa/XShm/Xv)
Device: Default

Default Input
Plugin: Vdieo for Linux 2 (v4|2)
Device UVC Camera (046d:0990)

I've played around with these a bit, but it doesn't seem to make any difference

Running cheese from the terminal gives:

roger@roger-desktop-new:~$ cheese-verbose
bash: cheese-verbose: command not found
roger@roger-desktop-new:~$ cheese --verbose
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/roger/.gnome2/cheese/media/0003.ogg'
Reason: Stream contains no data..

** (cheese:11082): WARNING **: could not load /home/roger/.gnome2/cheese/media/0003.ogg (application/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/roger/.gnome2/cheese/media/0012.ogg'
Reason: Stream contains no data..

** (cheese:11082): WARNING **: could not load /home/roger/.gnome2/cheese/media/0012.ogg (application/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/roger/.gnome2/cheese/media/0009.ogg'
Reason: Stream contains no data..

** (cheese:11082): WARNING **: could not load /home/roger/.gnome2/cheese/media/0009.ogg (application/ogg)

Detected webcam: UVC Camera (046d:0990)
device: /dev/video0
video/x-raw-yuv 1600 x 1200 num_framerates 1
5/1 
video/x-raw-yuv 960 x 720 num_framerates 2
10/1 5/1 
video/x-raw-yuv 800 x 600 num_framerates 5
25/1 20/1 15/1 10/1 5/1 
video/x-raw-yuv 640 x 480 num_framerates 6
30/1 25/1 20/1 15/1 10/1 5/1 
video/x-raw-yuv 352 x 288 num_framerates 6
30/1 25/1 20/1 15/1 10/1 5/1 
video/x-raw-yuv 320 x 240 num_framerates 6
30/1 25/1 20/1 15/1 10/1 5/1 
video/x-raw-yuv 176 x 144 num_framerates 6
30/1 25/1 20/1 15/1 10/1 5/1 
video/x-raw-yuv 160 x 120 num_framerates 6
30/1 25/1 20/1 15/1 10/1 5/1 
v4l2src name=video_source device=/dev/video0 ! video/x-raw-yuv,width=1600,height=1200,framerate=5/1 ! identity

Any ideas please?

Roger D

---

