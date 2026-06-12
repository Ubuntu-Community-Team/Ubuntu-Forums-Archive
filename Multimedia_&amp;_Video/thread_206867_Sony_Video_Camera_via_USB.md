---
title: "Sony Video Camera via USB"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by richbarna on 2006-06-30
Hi everyone,
I'm trying to capture from a Sony DCR-TRV140E Video Camera and would really appreciate any help at all.

This is what I've done so far :-

1. Installed Kino
2. Downloaded and Installed the drivers from here:-
3.[http://www.linux1394.org/view_device.php?id=810]("http://www.linux1394.org/view_device.php?id=810")
4. Have given /dev/1394 r/rw permissions
5. Loaded the 1394 module
6. Added 1394 module to start at boot
7. Rebooted and Plugged camera in, tried kino and no go.
8. Tried an lsusb and it sees the Sony Camera
9. Tried an lsmod and 1394 is loaded
I still get no device on kino :-
[ATTACH]12008[/ATTACH]

So I did this again :-
> richbarna@richbarna-desktop:~$ sudo modprobe raw1394
Password:
richbarna@richbarna-desktop:~$ ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2006-07-01 01:35 /dev/raw1394
richbarna@richbarna-desktop:~$ sudo chmod 777 /dev/raw1394
richbarna@richbarna-desktop:~$

Still no device.

I have been "Googling" and searching forums all day for the information that I have, and was hoping that maybe someone else could give me a hand as I don't know what to do next.

Thanks in advance.

---

### Post by richbarna on 2006-07-02
*bump*

---

### Post by otherdave on 2006-11-02
I have a sony video camera and I was able to pull videos over using a firewire cable and dvgrab.

Are you sure it's possible with a USB cable?

I just read [this thread](http://ubuntuforums.org/showthread.php?t=229181&) and the Kino developer said that USB cables weren't supported.

This is just a guess:
When you pull video from a video camera, the camera plays the video and the computer just captures it. USB doesn't support a consistent high throughput so they won't allow it, that's why you have to use firewire, it'll sustain the speed consistently so your video comes over correctly.

---

### Post by vraetorian on 2008-03-12
Aparently This guy was able to record video through a usb webcam connection...
I've just gotten sound to work so far, video's another thing all together...



Anyways, here's the quote and the link:
[http://ubuntuforums.org/showthread.php?t=495243](http://ubuntuforums.org/showthread.php?t=495243)

" Smile  Re: USB Video Capture
I have just set up webcam video capture on my machine. It all went fairly easily.

Machine: Asus M2N-MX-SE, 1GB RAM, AMD 3800+ CPU.

Webcam: Logitech Quickcam Orbit via USB. Its a 3 or 4 year old cam.
lsusb: Bus 001 Device 002: ID 046d:08b5 Logitech, Inc.

Ubuntu 7.10, plus added VLC, Camorama and Ekiga Softphone. All these apps recognise the webcam automatically. None seem to offer to do pan or tilt though. Perhaps the driver cannot support this anyway, I dont know.

To make an mpeg:
In VLC, "Open Capture Device", change the video to /dev/video0, audio to /dev/audio1, and set the Stream/Save on, then in the Settings button:

- Set Output to local and to a file (set [filename].mp4)
- Set Encapsulation Method to MP4, both Transcoding Options video and audio on.
- Later you might also want to fiddle with the the video bitrate and Scale to suit how much bandwidth vs size and clarity you want.

I used VLC to make an mp4, uploaded it to Utube.
__________________
The last great frontier is In Your Mind!
Last edited by DavidTangye : January 29th, 2008 at 05:36 AM.
Thanks"

---

