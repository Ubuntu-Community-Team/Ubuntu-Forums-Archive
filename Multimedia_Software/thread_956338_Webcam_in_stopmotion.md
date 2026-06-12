---
title: "Webcam in stopmotion"
date: 2008-10-23
forum: Multimedia Software
---

### Post by okey666 on 2008-10-23
Now, I know that I will probably be told to put up with it as I am running BETA intrepid, but its only 7 days until the release so I thought I may as well post.

I am trying to get my Logitech Quickcam Pro 5000 to work on Ubuntu. I specifically want it to work in  Stopmotion (program for making animations). It used to work in Fiesty, but only in Cheese (capture software). Any other program would just come up with various errors. Now, in Intrepid it does not work at all. Cheese just comes up with a multicolored snowstorm screen and stopmotion just goes green. Looking at the terminal output of stopmotion I notice that it says (using vgrabbj):
```
Device doesn't support width/height
There was no map allocated to be freed..
```

Cheese gives:
```
libv4l2: error requesting 4 buffers: Device or resource busy

```

 lsusb gives:
```
oscar@key-oscar:~$ lsusb
Bus 007 Device 002: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1241:1503 Belkin Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and the file /dev/video0 is present.

Stopmotion seems to be using UVC Camera *Auto Detected v4l-device.

Can anyone help?

edit:
It did not work in Hardy either, cannot remember gutsy

---

### Post by okey666 on 2008-10-24
Woop! solved by
[http://ph.ubuntuforums.com/showthread.php?t=931208&page=1](http://ph.ubuntuforums.com/showthread.php?t=931208&page=1)

---

### Post by okey666 on 2008-10-24
new problem:
when I try to take a picture it dies with:
```
*** glibc detected *** stopmotion: free(): invalid next size (fast): 0x0000000002250570 ***

```
and then prints out a memory map.

This happens which ever command I use to take the picture.

---

### Post by okey666 on 2008-10-25
I have now changed my capture program to motion. This gives fantastic frame rate stopmotion still crashes. It even crashed when frame rate is 2fps (slowest possible speed). Compiling (stopmotion) from source makes no difference. I don't know what to do!

---

### Post by okey666 on 2008-10-27
After reading around a little I have found that this could be a 64bit problem, anyone else having this?

---

### Post by Aearenda on 2008-10-27
I haven't seen this before, myself. Stopmotion relies on the grabber to successively place new images in .stopmotion/capturedfile.jpg in your home folder, overwriting the file each time. The first thing I would do is to look at that file with a viewer and see if it is sane. Assuming it was, I would try placing other small (640x480 for example) .jpg files there by hand and see if Stopmotion can work with them.

The next thing I would do is completely remove your home-compiled version and reinstall the repository version, since home-compiling didn't fix it and introduces more variables.

You mention 64-bits: I can't really help with that as all my computers are old, or installed as 32-bits only.

What size pictures are you generating from the webcam?

By the way, the recent Quickcams seem to produce pictures in a format that older programs can't recognise (MJPEG springs to mind - my memory may be playing tricks on me), which is why we have to use a more modern grabber than vgrabbj.

By the way, what parameters do you use with 'motion' in Stopmotion?

---

### Post by okey666 on 2008-10-27
I have attached my configuration file to the post as its very long (its in a tar). I have already got rid of the home compiled version as it did not fix it.

Motion definitely makes good pictures, I can look at them with eye of gnome. I will have a go with adding pictures manually, but I think stopmotion crashes what ever grabber I use (dv cam or otherwise).

You can look at motion here:
[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)
The deb does not work for me so I have to self compile.

Motion is configuration file only so I use...

start daemon:
```
motion
``` 
stop daemon:
```
killall motion
```

---

### Post by Aearenda on 2008-10-28
Thanks for that - I have it running successfully, with 640x480 frames from my Quickcam E3500, using the standard Hardy repo version. I never thought of using motion to feed Stopmotion, but of course it works! 

Alas for you, it does not cause Stopmotion to crash on my system (which is Hardy, not Intrepid). If the framerate is too high, it does cause grey images which happen (I guess) when Stopmotion tries to read a file that has not yet been fully written to by motion. It would be better to write to a temporary file and them move the finished file into place, but I don't see a parameter allowing that to happen.

EDIT: Yes there is: the 'on picture save' command! I have set it like this:
```
on_picture_save mv %f /home/steve/.stopmotion/
```
And I set the initial save to be to a temporary folder with the same filename. No more grey images! But it seems more laggy. Then again, my computer is just a Pentium-M, nothing too fast.

---

### Post by okey666 on 2008-10-28
Maybe a 32 bit hardy virtual machine would do the trick. I am going to try my dv-cam again.

My webcam seems to take "wide screen" pictures at 640 x 360 and they are 32.8 kb, could this cause a problem. Stopmotion takes the picture, just crashes while doing so, if you restart it and click recover the image comes up.

note: picture moving lags on mine using that second value, and I have a relatively good system. Intel core 2 duo over clocked to 3.2 ghz, with nvdia 8600GTS

---

### Post by jabooduu on 2008-11-09
on Ubuntu 8.10 fresh install, when trying to install the latest Motion 3.2.11-1, the install does not work ok.

I get complain: 
 Error: Dependency is not satisfiable: libavcodec1d

Using synaptic to search this package, does not give any matches.

I think that this libavcodec1d is part of ffmpeg library......

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Any hints on how to get motion installed??

---

### Post by Aearenda on 2008-11-09
The latest Motion in 8.10's repo is 3.2.9-7 - so you have to resolve the dependencies yourself, as you have a newer version. How have you got the later version?

---

### Post by okey666 on 2008-11-09
I myself compiled from source, as I remember having trouble with that.

---

### Post by Aearenda on 2008-11-09
I think you'll have to do the same with that library then. I've never tried doing that, so I'm afraid I can't help any further.

---

### Post by jabooduu on 2008-11-11
Hi Okey666,

So, did you manage to get motion 3.2.11-1 running on Ubuntu 8.10 ??

(the version 3.2.11-1 is available from Motion homepage: [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)   )

It seems that Motino 3.2.11-1 would have V4L2 support, instead of V4L.

---

### Post by okey666 on 2008-11-11
I have got:
> motion Version 3.2.11, Copyright 2000-2005 Jeroen Vreeken/Folkert van Heusden/Kenneth Lavrsen (or so "motion -help" gives)

To get this, I first tried the .deb on the motion website. This gave some error that it could not satisfy a dependency. I then compiled from source. It was a simple matter, I had most things on my system already. Anything else, I just used synaptic (remembering to add -dev at the end of the package name).

If you want a step by step guide (I don't know how advanced you are, probably more advanced than me), then just ask.

---

### Post by ksigler on 2009-06-07
Thank you. You saved my life with this tip.

Ubuntu 9.04 (Jaunty) on ThinkPad T61p

Stopmotion: Video Device "UVC Camera" autodetected
Video Input: add new. name: motion; start daemon: motion; stop daemon: killall motion

lsusb = Logitech, Inc. QuickCam Deluxe for Notebooks

motion Version 3.2.11 via apt-get

motion conf from this thread with /dev/video changed to my cam and path to .stopmotion changed to my home dir. I also removed the timestamp text.

 Works like a charm for 640x480!

---

### Post by StuartN on 2009-10-02
Many thanks for this thread.

I just installed motion, which worked straight off, and then the configuration in this thread. After that Stopmotion works fine and I can do some stop-motion animations.

---

### Post by bnelson2002 on 2010-02-01
I'm having trouble getting stopmotion to work with ubuntu 9.10 using the steps outlined in this forum.  I bought a logitech c200 webcam, which is UVC compliant, for skype video calls, and it works fine for that.  I installed motion with some of the configuration changes suggested above, but when I run stopmotion, the screen is constantly switching between black, solid green, me with faded green coloring, and me in a clear shot.  Motion is definitely capturing images and sending them to stopmotion, but not quickly or consistently enough to make stopmotion usable.  

I started with the  motion.conf file from post #7 and made the following changes:

videodevice /dev/video3  

width 640

height 480

framerate 30  (I've tried 2, 30, 60, and 100 with not much difference)

target_dir /home/brett/.stopmotion

on_picture_save mv %f /home/brett/.stopmotion/

It's a nice little program & is easy for kids to use, but it doesn't look like there has been any active development for well over a year.  Is there another alternative that everyone is switching to?  Anyway, any help would be geratly appreciated.

Brett

---

### Post by okey666 on 2010-02-01
Perhaps you have said this in the post above, but if you have a look at the pictures that are being captured by motion (with a slow framerate) using the file browser, are the images perfect, or similar to what stopmotion is displaying?

In terms of using another program, it is possible to capture the pictures manually (using cheese for example), and then make them into a video. Blender and gimp (with gap extension) can both do this. You could also use a command line tool such as fmpeg or mencoder (stopmotion uses these to export at the end anyway).

---

### Post by bnelson2002 on 2010-02-01
If I comment out the "on_picture_save mv %f /home/brett/.stopmotion/" line, I get a series of clear 640x480 pictures in thefolders in the .stopmotion folders.

Yes you can use a digital camera & monkey with command lines, but for working (playing) with kids, stopmotion is nice & simple and the onionskin feature makes it super easy to line things up and judge changes in the scenes.

Thanks!

Brett

---

### Post by Aearenda on 2010-02-01
bnelson2002, it sounds to me as if Stopmotion is trying to use a different grabber, ignoring what Motion is producing. Are you sure you have it set to use Motion in Settings->Configure Stopmotion?

See [this post for details]("http://ubuntuforums.org/showpost.php?p=6042382&postcount=7") and [section 2 of this post]("http://ubuntuforums.org/showpost.php?p=5869544&postcount=10") for background info (but not that the first one is an update to the second one, which uses a different grabber, but shows how you add a new grabber to the config).

---

### Post by bnelson2002 on 2010-02-01
Sorry for the delay; I didn't notice that your reply jumped to a new page & I kept looking at the bottom of page 2.  Anyway, I checked the video import settings for stopmotion and it looks right.

But there is something else that I noticed: when I first start up stopmotion and turn on the camera toggle, the screen alternates between solid green and black, and nothing else, until I move in front of the camera.  Once there is motion in front of the camera, the screen alternates between black, solid green, clear image, and fuzzy green image, as mentioned before.  This suggests that there is some kind of motion detection trigger set in the motion settings that is causing the problems.  I have to leave now for a few hours, but I will look into those settings later tonight.

Thanks again for your help!

Brett

---

### Post by Aearenda on 2010-02-01
'Motion' is indeed designed to be triggered by movement, yes - but if there is no movement in the scene, then the Stopmotion screen should be steady with the last image on display, and no change at all. This is fine for Stopmotion work. I don't understand why your screen is shifting from green to black, when there is no motion for 'Motion' to detect at all. IIRC when Motion does detect movement, the config file recommended for use with Stopmotion causes it to supply a series of images but then stop again.

When you do have movement detected, then 'Motion' places a clear image for Stopmotion to find, which it does, but then (it seems to me) it goes back to getting images from somewhere else - maybe you should check the output of the terminal command 'ps aux' for any other grabber that is inadvertently started as well.

BTW, you can check for forum replies using the User Control Panel - [http://ubuntuforums.org/usercp.php](http://ubuntuforums.org/usercp.php)

---

### Post by bnelson2002 on 2010-02-01
Bingo!  Looking at ps -aux I saw that vgrabbj was still running and killed it.  Then I started wondering what other programs I may have invoked over the last couple of days testing the webcam & trying to get output into various programs; I decided some housecleaning was in order.  I started with a fresh download of your motion.conf file, changing just what was needed to match my filesystem.  In stopmotion, I deleted every option in video import except for motion.  Then I shut everything down and rebooted.  Upon reboot, stopmotion worked as advertised!  Very nice...thank you for the help!

Motion is a pretty cool app...I'm glad I spent some time to become more familiar with it.  I can see where it may come in handy for other applications.

Brett

---

### Post by Aearenda on 2010-02-01
Great! Makes me wonder if there is some logic in Windows having to reboot so often............ not!

---

### Post by bdebruler on 2010-06-11
Revive thread in 3, 2, 1...

I have tried using stopmotion with the following motion.conf settings as suggested thus far in this thread

target_dir /home/username/.stopmotion/

snapshot_filename capturedfile

jpeg_filename capturedfile

on_picture_save mv %f /home/username/.stopmotion/


What is happening is stopmotion freezes since the photos are not ending up in the .stopmotion directory. They are ending up in my home/username directory still.

Any thoughts? I hope this isn't too old for your attention!

---

### Post by bdebruler on 2010-06-11
Also, the files are named with a date time string. Shouldn't this be overwriting the same file?

It got really bad until I turned it down to 2 frames / second.

---

### Post by StuartN on 2010-06-11
> **bdebruler said:**
> What is happening is stopmotion freezes since the photos are not ending up in the .stopmotion directory. They are ending up in my home/username directory still.

Does %f have the value /home/username/.stopmotion/capturedfile? If it does, then the move will not work.

I have 

```
target_dir /home/stuart/.stopmotion
snapshot_filename motion
jpeg_filename motion

on_picture_save mv ~/.stopmotion/motion.jpg ~/.stopmotion/capturedfile.jpg
```

---

### Post by bdebruler on 2010-06-11
Thanks.

The problem was found in another thread "The Motion conf file was set up without general read access, so I had to  run 'sudo chmod 644 /etc/motion/motion.conf' before I could get motion  to run."

The changes I made to motion.conf were being ignored (well, partly). Now I can fine tune the file to my liking.

---

