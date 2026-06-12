---
title: "UVC webcam and Cheese not working, weirdly"
date: 2008-09-27
forum: Multimedia Software
---

### Post by cyran on 2008-09-27
I just got a UVC webcam that works out-of-the-box on Windows XP SP2 with Windows Movie Maker. I installed the 'cheese' and 'camorama' packages in Ubuntu (Hardy). The camera shows up in System->Preferences->Hardware Information just fine.
When I run Cheese under my usual account, nothing shows up at all, no video feed. When I run Cheese with sudo, I *can* see things, and take still pictures easily. When I created a new account for testing, it works the same as sudo. Both suffer from problems when trying to record video, though. Sometimes it works, sometimes it *starts* working, but then overwrites the video file and gives it a size of zero bytes.

Running camorama, with sudo, test account, or otherwise, gives "Could not connect to video device (/dev/video0). Please check connection."

Here's my first test session's output from the command-line (0001.jpg was created fine; 0002.ogg ended up with zero bytes; but 0003.ogg was created perfectly.)

```
test@me:~$ dmesg
[ 9743.217986] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 9743.451353] usb 5-2: configuration #1 chosen from 1 choice
[ 9743.451792] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
test@me:~$ cheese
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/test/.gnome2/cheese/media/0002.ogg'
Reason: Stream contains no data..

** (cheese:24456): WARNING **: could not load /home/test/.gnome2/cheese/media/0002.ogg (application/ogg)


** (cheese:24456): WARNING **: Changing the `location' property on filesink when a file is open not supported.

(cheese:24456): GStreamer-WARNING **: Element photo_save_bin is not in bin pipeline

(cheese:24456): GStreamer-WARNING **: Name video_save_bin is not unique in bin pipeline, not adding
test@nobled-T60:~$ cheese
** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/test/.gnome2/cheese/media/0002.ogg'
Reason: Stream contains no data..

** (cheese:24659): WARNING **: could not load /home/test/.gnome2/cheese/media/0002.ogg (application/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(742): gst_type_find_element_activate (): /play/decodebin0/typefind:
Can't typefind empty stream

** Message: Error: Could not determine type of stream.
gsttypefindelement.c(757): gst_type_find_element_activate (): /play/decodebin0/typefind

totem-video-thumbnailer couldn't open file 'file:///home/test/.gnome2/cheese/media/0003.ogg'
Reason: Stream contains no data..

** (cheese:24659): WARNING **: could not load /home/test/.gnome2/cheese/media/0003.ogg (application/ogg)

test@me:~$ 
```

---

