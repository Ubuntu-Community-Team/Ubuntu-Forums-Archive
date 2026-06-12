---
title: "Webcam no longer works in Cheese"
date: 2008-12-22
forum: Multimedia Software
---

### Post by subluminal on 2008-12-22
I'm using an Acer 5920 Laptop with an integrated Crystal Eye webcam. It works just fine in Skype, but not in Cheese. At startup, I get a blank screen (no black, just default window color). Here are the errors I get when starting from the terminal.

```
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:11725): WARNING **: could not generate thumbnail for /home/*****/Videos/Webcam/2008-12-20-141957.ogv (video/ogg)


(cheese:11725): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:11725): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:11725): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small
```

---

### Post by wolfen69 on 2008-12-22
try ```
gstreamer-properties
``` to configure.

---

### Post by subluminal on 2008-12-22
> **wolfen69 said:**
> try ```
gstreamer-properties
``` to configure.
Good thought, but I've still got zilch after trying all the available options.

---

### Post by beyboo on 2008-12-25
I have an acer 5920. Facing same problem on intrepid. Funny thing - this worked great in Hardy and also works well when you boot from intrepid live CD and install cheese. 

It seems that cheese does not work on resolution higher than 160x120 which is very very coarse.

Any ideas - I am gonna report it in bugs at launchpad.

---

### Post by BigDamnHero on 2008-12-26
I'm having the same problem with the Crystal Eye webcam on an Acer Aspire 5730z.  Cheese only works at 160x120, gstreamer-properties gives me zilch on all setttings, and the same goes for Xsane and Camorama.  It works fine with luvcview, but gives me two identical low-res side by side images in GyachE Improved 1.1.59.  

Everything worked fine until I thought that I had re-installed 8.10, but I have a sneaking suspicion that I previously had 8.04 installed accidentally.  I would hate to have to wait until 9.04 Jaunty to fix this...

---

### Post by HDave on 2008-12-28
I have the same problem.  Webcam worked with 8.04 and doesn't work now.

gstreamer-properties works, skype works, but xsane and cheese do not.

Found this bug however:  [https://bugs.launchpad.net/bugs/260918]("https://bugs.launchpad.net/bugs/260918")

---

### Post by PhrankDaChickenGeek on 2008-12-28
> **HDave said:**
> I have the same problem.  Webcam worked with 8.04 and doesn't work now.

gstreamer-properties works, skype works, but xsane and cheese do not.

Found this bug however:  [https://bugs.launchpad.net/bugs/260918]("https://bugs.launchpad.net/bugs/260918")

Same problem

Bus 005 Device 004: ID 041e:4057 Creative Technology, Ltd Live! Cam Optia

---

### Post by RunLengthLimited on 2008-12-28
I'm seeing something similar.  I have a **Creative Live! IM** webcam and I'm running **Ubuntu 8.10**.  

**luvcview** displays the camera stream fine.  

Likewise, **xawtv** displays the cam video data just fine.  

**Cheese** shows a blank screen and gives the following error in the console:

```
(cheese:6021): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:6021): WARNING **: could not generate thumbnail for /home/jgloza/Videos/Webcam/2008-12-27-130007.ogv (video/ogg)


(cheese:6021): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:6021): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small

```

**camorama** gives the following error on startup:
```
Could not connect to video device (/dev/video0).  Please check connection.
```

**skype** exits silently during its initialization process.

**ekiga** is able to read and display the camera video.

Browser-enabled video chats (**icamonline**,**meebo**) do not recognize the video camera, but do find the microphone on the camera!

Hope this helps.

---

### Post by BigDamnHero on 2008-12-29
I downloaded a tarball called uvcvideo-7ec490a64a56.tar.gz and ran a "make" and "make install" and it didn't work.  But when I tried a "make all" for some reason it fixed Cheese upon reboot.  However GyachE and Kopete still don't work.  I hope that helps the Cheese users.  Be sure to read the readme file.  It gets a little confusing in there...

---

### Post by RunLengthLimited on 2008-12-30
What version of ubuntu are you running Hero?  Do you remember where you found that tarball?

---

### Post by BigDamnHero on 2008-12-30
> **RunLengthLimited said:**
> What version of ubuntu are you running Hero?  Do you remember where you found that tarball?

I am currently running 8.10, but the cam seemed to work just fine in 8.04.  :confused:

I completely forgot where I got that tarball, but I do have it saved locally.  Any suggestions where I could upload it that would be convenient for everyone?

---

### Post by BigDamnHero on 2008-12-30
> **RunLengthLimited said:**
> What version of ubuntu are you running Hero?  Do you remember where you found that tarball?

I am currently running 8.10, but the cam seemed to work just fine in 8.04.  :confused:

I completely forgot where I got that tarball, but I have it saved locally.  Does anyone know a good place to upload it where it would be convenient?  It's 3.57 megs, so I can't attach it here.

---

### Post by RunLengthLimited on 2008-12-31
Running **gstreamer-properties** and selecting the actual device on the Video tab seems to have fixed **cheese**.  **camorama** and several flash-based websites still do not work, though some flash websites do.

---

### Post by RunLengthLimited on 2008-12-31
I also downloaded the latest flash10 pluguin alpha from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) . Unpacking the libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz gets you a libflashplayer.so.  Quit your browser and copy the libflashplayer.so over all instances on your system to update.

---

### Post by PhrankDaChickenGeek on 2009-01-01
> **RunLengthLimited said:**
> Running **gstreamer-properties** and selecting the actual device on the Video tab seems to have fixed **cheese**.

This does not work for me. Running Ubuntu 8.10

---

### Post by subluminal on 2009-01-18
I enabled the proposed repository today to take care of a bug that is likely to shorten the lives of laptop hard disks. The new repo included a newer rev of Cheese, which fixed everything. Photos are captured and videos record at all resolutions. The live display only refreshes once every 750ms or so, but video records properly in sync. To add the 'proposed' repo, add the following line to /etc/apt/sources.list and run Update Manager.

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
```

---

### Post by zea_ on 2009-01-19
Hi there!

i just try the cheese included in the proposed repo but still not working at my laptop :(

the output:
```

zea@sendai:~$ cheese 
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:13093): WARNING **: could not generate thumbnail for /home/zea/Videos/Webcam/2009-01-19-134942.ogv (video/ogg)


(cheese:13093): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:13093): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps

(cheese:13093): GStreamer-WARNING **: pad video_source:src returned caps which are not a real subset of its template caps
libv4l2: error converting / decoding frame data: v4l-convert: error destination buffer too small


```

my kernel:
```

2.6.27-9-generic

```

my cam:
```

zea@sendai:~$ lsusb 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by skalka on 2009-01-19
Hey guys I've found [this solution]("http://forum.ubuntu-it.org/index.php/topic,239811.msg1660830.html#msg1660830") on the italian forum and it worked for me. Give it a try!

Skalka.

---

### Post by Hilko on 2009-01-22
> **subluminal said:**
> I enabled the proposed repository today to take care of a bug that is likely to shorten the lives of laptop hard disks. The new repo included a newer rev of Cheese, which fixed everything. Photos are captured and videos record at all resolutions. The live display only refreshes once every 750ms or so, but video records properly in sync. To add the 'proposed' repo, add the following line to /etc/apt/sources.list and run Update Manager.

```
deb http://archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
```

I tried this, but it didn't work. (I installed only 37 of the 66 updates because i thought the others were not related to cheese)

---

### Post by beyboo on 2009-01-24
This bug was addressed by a new version of cheese and V4L by way of updates in intrepid. This works OK now. If this is solved for the thread starter. can you please put [solved] and mod needs to  close this thread ?

---

### Post by HDave on 2009-01-24
Problem still exists for me in Intrepid...no change.

---

