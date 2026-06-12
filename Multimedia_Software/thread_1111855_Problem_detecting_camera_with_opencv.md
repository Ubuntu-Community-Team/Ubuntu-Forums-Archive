---
title: "Problem detecting camera with opencv"
date: 2009-03-31
forum: Multimedia Software
---

### Post by Uldrer on 2009-03-31
Hi
I'm pretty new at ubuntu but the last couple of weeks i've come to like it more and more. I have this video-capturing project in school atm and I'm using the latest OpenCv snapshots with ffmpeg and xine. My programs work fine with .avi files but now I have received the camera intended for the project and OpenCv can't detect it. It's a JVC, GR-D860E which connects through firewire. I've been troubleshooting it the last couple of days (and nights) and I've manage to capture from it using Kino. OpenCv still refuses to find it though. Last night I tried it on my windows PC which also has OpenCv and it worked perfectly...

I really want to keep working on ubuntu but I have a tight schedule with school so if I can't find the reason soon I'll probably have to go back to windows :( 

Any help in the matter would be greatly appreciated!

//Martin

---

### Post by rrfx on 2009-05-05
What error messages are you getting when trying to open the camera?

I am using OpenCV 1.1pre on Jaunty. To use my DC1394 firewire camera (unibrain) I had create some symlinks in the /dev folder after plugging the camera in: 

```
sudo mkdir /dev/video1394
sudo ln -s /dev/video1394-0 /dev/video1394/0
sudo chmod 777 -R /dev/raw1394 /dev/video1394-0 /dev/video1394 
```

It appears OpenCV or libdc1394-13(-dev) is now looking for the block device in the wrong place. It worked fine on Intrepid.

Hopefully that helps someone else!

---

