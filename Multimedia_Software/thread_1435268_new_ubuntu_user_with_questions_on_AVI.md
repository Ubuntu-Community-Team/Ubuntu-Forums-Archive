---
title: "new ubuntu user with questions on AVI"
date: 2010-03-21
forum: Multimedia Software
---

### Post by happy_camper on 2010-03-21
hello ubuntu world!

I am as green as they come and this is my first post, please be gentle

I have just installed 9.1 at home and I've managed to get much farther on my own than I ever thought possible.  I am slowly learning terminal talk, however I am becoming wary of just copying and pasting commands from the web into my terminal and running them

Problem statement:
As I'm importing all of our media files back onto the harddrive but of course my .AVI files won't play.  These are family movies taken on a digital camera, so I can't really do away with them.

First let me state that I've already spent my morning searching through the forums for answers and have come up empty.

Here is what I've figured out already


#1 Obviously, the Default Ubuntu Movie player doesn't work for AVI files

#2 the files aren't corrupted, they play fine on the flash memory card on the camera or on windows.

#2 I've Installed VLC 
VLC doesn't seem to like the files and asks to repair them (I'm not sure what this does)
VLC seems to like the files for a split second but then quits.

#3 Went here to do something with FFmpeg, but I'm not sure what I did
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
sudo apt-get install ffmpeg libavcodec-unstripped-52

#4 I've finally figured out how to launch the .AVI files from the command line and I can run ffplay filename.avi and i can see the video playing but there is choppy audio.

here is the output:

[I]user@ubuntu:~/Desktop/new_photos$ ffplay MVI_4026.AVI
FFplay version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1[/I]


#5 I'm not sure if its helpful to know, but I can't get DVDs to play either.  I'm sure this is useful to know but I'm not sure how it can help trouble shoot.

So community, where can I go from here?
My goal is to have the files just work.

What I've realized is that this single issue stands in the way of my girlfriend adopting Ubuntu into the family.

---

### Post by happy_camper on 2010-03-21
bump

---

### Post by dragonboss on 2010-03-21
Have you installed the ubuntu resrticted extras from the software center? Those should install the correct stuff and even it should ask to be installed when you just double click the avi, and check whether you have the universe, restricted and multiverse repositories selected in System > Administration > Software sources

---

### Post by happy_camper on 2010-03-21
dragonboss Thanks for the reply and for being gentle!

I thought I had already done that, but here is what I see when I look at the Software sources.

---

### Post by dragonboss on 2010-03-21
From the pics it looks like you have the correct sources enabled now try installing the ubuntu restricted extras from the software center

---

### Post by happy_camper on 2010-03-21
dragonboss, I REALLY appreciate you helping me out with this.

I've installed  the ubuntu restricted extras from the software center     

Under the AVI files, I open with ffplay and I can see the video but the audio is garbled.

Any recommendations on what I should trouble shoot next?

Would the output from the command line tell you anything?

---

### Post by dragonboss on 2010-03-21
Why did you do this? > #3 Went here to do something with FFmpeg, but I'm not sure what I did
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
sudo apt-get install ffmpeg libavcodec-unstripped-52 
Try uninstalling that and see if the audio is still garbled:

```
sudo apt-get remove ffmpeg libavcodec-unstripped-52
```

---

### Post by happy_camper on 2010-03-21
> Why did you do this?      I was trying to follow the advice in another thread to try to make it work myself.

I ran: 
```
sudo apt-get remove ffmpeg libavcodec-unstripped-52
```This is what I've ouputted.

```
user@ubuntu-desktop:~$ sudo apt-get remove ffmpeg libavcodec-unstripped-52
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-unstripped-52 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libuser-perl gdesklets-data python-numeric xdotool python-utidylib
  libtidy-0.99-0 python-soappy python-feedparser hddtemp libavfilter0
  libdate-manip-perl libwww-search-perl libfile-slurp-perl python-fpconst
  python-chardet libgtkglext1 libavdevice52
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ffmpeg
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 844kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136146 files and directories currently installed.)
Removing ffmpeg ...
Processing triggers for man-db ...
```the ffmpeg is now uninstalled and the video files don't play at all.

Next, step?

---

### Post by dragonboss on 2010-03-21
sudo apt-get install ubuntu-restricted-extras

---

### Post by dragonboss on 2010-03-21
If there are still problems try these in addition

sudo apt-get install gstreamer0.10-ffmpeg libavformat52 libxine1

I think its the libavformat52 you need

---

### Post by happy_camper on 2010-03-21
Dragon Boss, thanks for sticking with me on this!

I installed both of these successfully

```
 sudo apt-get install ubuntu-restricted-extras     
``````
sudo apt-get install gstreamer0.10-ffmpeg libavformat52 libxine1
```Now that I have all of those packages installed, what program should I use to actually play the AVI files and what steps do I need to take from the desktop to run this?

---

### Post by dragonboss on 2010-03-21
You can use totem, its installed by default. So there is no sound garbling?

---

### Post by happy_camper on 2010-03-21
when I click on a file from the desktop, Totem opens for a split second then shuts down.

If I already have the movie player open and try to open it from the program menu via Movie>Open> file.AVI

It also shuts down.

However, when I run from the terminal I get this... but I have not idea what it means

```


user@ubuntu-desktop:~/Desktop/new_photos$ totem MVI_4028.AVI
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by dragonboss on 2010-03-21
Well it says what it means: The error was 'BadAlloc (insufficient resources for operation) but try vlc and see if it plays

---

### Post by happy_camper on 2010-03-21
Thanks for sticking with me on this.

it doesn't play in VLC either..... :(.

But it does give me the option to repair or not to repair before it shuts down.

---

### Post by fremantle on 2010-03-21
i dont know what happened in your case, but i was also a new (but experienced) ubuntu user when i got 9.10 Karmic. i had like 20 .avi movies and knew they wouldnt work out of the box with ubuntu (NOT even windows). What i did was just activate 3rd party softwares, opened synaptic and got vlc. thats it. u dont need any other audio/video codecs or anything. the video and audio works just fine with vlc player (even slightly better then xp). So in your case, as you are a new and have little experience with linux, i recommend u install SuperOS. its completely based on ubuntu, but created for an Out-Of-The_box experience for beginner linux users. Meaning: u can play your video, dvd and everything else (youtube,flash,java...) as soon as u boot up and login for the first time. 
> check their wiki and download [http://hacktolive.org/wiki/Super_OS](http://hacktolive.org/wiki/Super_OS)let us know what happens:KS

---

### Post by happy_camper on 2010-03-21
It it helps, I do get this output from the terminal when I try to run VLC with the AVI

```

user@ubuntu-desktop:~/Desktop/new_photos$ vlc MVI_4028.AVI
VLC media player 1.0.2 Goldeneye
[0x9337140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x96a6ee0] pulse audio output: No. of Audio Channels: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  195
  Current serial number in output stream:  196
Segmentation fault


```

---

### Post by fremantle on 2010-03-21
> **fremantle said:**
> i dont know what happened in your case, but i was also a new (but experienced) ubuntu user when i got 9.10 Karmic. i had like 20 .avi movies and knew they wouldnt work out of the box with ubuntu (NOT even windows). What i did was just activate 3rd party softwares, opened synaptic and got vlc. thats it. u dont need any other audio/video codecs or anything. the video and audio works just fine with vlc player (even slightly better then xp). So in your case, as you are a new and have little experience with linux, i recommend u install SuperOS. its completely based on ubuntu, but created for an Out-Of-The_box experience for beginner linux users. Meaning: u can play your video, dvd and everything else (youtube,flash,java...) as soon as u boot up and login for the first time. 
let us know what happens:KS

[IMG]http://hacktolive.org/w/images/thumb/Super_OS_9.10_Video.png/800px-Super_OS_9.10_Video.png[/IMG]
[IMG]http://hacktolive.org/w/images/thumb/Super_OS_9.10_playing_DVD.png/800px-Super_OS_9.10_playing_DVD.png[/IMG]

---

### Post by dragonboss on 2010-03-21
Ok this is now beyond me. So put the things you uninstalled back

```
sudo apt-get install ffmpeg libavcodec-unstripped-52
```

And see if anything new happens. Other than that I'm stumped. :sad:

---

