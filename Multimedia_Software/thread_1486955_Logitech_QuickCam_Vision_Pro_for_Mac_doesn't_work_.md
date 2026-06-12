---
title: "Logitech QuickCam Vision Pro for Mac doesn't work in Skype"
date: 2010-05-18
forum: Multimedia Software
---

### Post by rootless on 2010-05-18
I am running Xubuntu Lucid 10.04 on a Sony Vaio.

I recently dropped $100 on a Logitech QuickCam Vision Pro for Mac, on the recommendation on the ubuntu wiki [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) that it would "work perfectly" in Skype.

In Skype, it did nothing. No Audio, no video, light wouldn't even come on. Essentially a $100 dollar paperweight. I really think someone should correct this misleading information on the wiki.

I followed the kludge listed here [http://ubuntuforums.org/showthread.php?t=1318506&page=5](http://ubuntuforums.org/showthread.php?t=1318506&page=5) to get the video to work. By executing Skype with the shell script listed in the first post, I could get the video test to work, but no audio, and when I tried to call someone, when I turned on video, Skype quit suddenly.

For the record, yes, I unmuted the device in the Sound Mixer in the top right corner.

Later on, I tested it with guvcview, and the cam worked perfectly in that program. It's only Skype that doesn't know what to do with it.

When I execute Skype in Terminal I get the following output repeating over and over again:

```
X Error, request 20, minor 0, error code 3 BadWindow (invalid Window parameter) 
X Error, request 15, minor 0, error code 3 BadWindow (invalid Window parameter) 
libv4l2: error setting pixformat: Input/output error
libv4l2: error setting pixformat: Input/output error

```

Copy of lsub:

```
rootless@boltbox:/usr/bin$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 054c:01b4 Sony Corp. 
Bus 001 Device 003: ID 046d:09a6 Logitech, Inc. QuickCam Vision Pro
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


The only reason I bought this webcam was Skype. Any help that anyone could give me would be greatly appreciated. 

At the very least, is there any way I can go back to a non-beta version of Skype? I've read about 20 threads, and apparently it is just Skype Beta 2.1 that breaks things.

---

### Post by no2498 on 2010-05-18
not picking on anyone but stop with all the skype first time up with a cam
type skype in the search box see what and how many come up
get the cam working first so you have something to work with

not sure if you have  gstreamer-properties on a mac
if you do set the dev's
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope the cam comes on good luck with skype

---

### Post by rootless on 2010-05-21
KK, will give this a try tomorrow. Currently writing finals. Even if this doesn't work, thank you for the help!

---

### Post by no2498 on 2010-05-21
good luck with the finals

---

### Post by rootless on 2010-05-21
Yeah, had to install gstreamer because xubuntu doesn't use it, but it detects the cam perfectly and gets picture when set on vl42.

Skype is still having the same problem though. When I perform the Video Test, the light on the Cam turns on, but Skype doesn't show any picture- the video test box stays black.

---

### Post by no2498 on 2010-05-22
type skype in the search box

try the cam in cheese webcam booth it should be loaded
look in sound & video

---

### Post by gordintoronto on 2010-05-22
If I read something that said a "Logitech QuickCam Vision Pro for Mac" would work fine, I would mentally append, "when installed on a Mac." Perhaps I'm wrong in suggesting this.

I wasn't aware that Skype would work in Xubuntu.

I use Skype on a high-performance system and it works perfectly. System monitor says both CPUs are running at more than 50%.

When I try to run it on a five-year-old computer, it fails miserably. I'm using a $10 webcam I bought in China.

---

### Post by no2498 on 2010-05-22
Logitech QuickCam Vision Pro for Mac/linux
put that in the search box

gordintoronto 
do what i told him too do but try changing the driver
look in the cheese help files, faq's, cheese has what you need to do

---

### Post by rootless on 2010-05-24
Thanks for the suggestion, but I already searched ubuntuforum and Google, and multiple other sites, otherwise I wouldn't have posted this.

Started a clean install of Ubuntu 10.04 just to test... it still doesn't do anything. If I click "test" in Skype, the cam light comes on, then immediately shuts off. There is never any picture. Gstreamer still works perfectly with the cam, and I suspect cheese would as well.'

Any thoughts?

---

### Post by no2498 on 2010-05-25
i have seen 32 bit and 64 bit have diff problems

i do not use skype so im no help

---

### Post by no2498 on 2010-05-26
try this for skype put it in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

if it works you need to do it every time before you start skype

---

