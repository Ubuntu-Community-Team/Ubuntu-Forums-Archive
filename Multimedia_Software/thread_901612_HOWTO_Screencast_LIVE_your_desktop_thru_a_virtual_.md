---
title: "HOWTO: Screencast LIVE your desktop thru a virtual webcam"
date: 2008-08-26
forum: Multimedia Software
---

### Post by patrickballeux on 2008-08-26
Hi, 

**[COLOR="Red"]EDIT: See the [WebcamStudio for GNU/Linux]("http://webcamstudio.wiki.sourceforge.net/") as is it far more easier and fun to use...[/COLOR]**

Here is the solutions that I found to be able to screencast my desktop thru a virtual webcam so I can show my destop (or part of it) in aMsn or with Flash in sites like Stickam or BlogTV.

[SIZE="4"]**1 - Using recordMyDesktop as the X11 grabber**[/SIZE]

What you need is recordMyDesktop and ffmpeg from the repositories of Ubuntu:

> sudo apt-get install ffmpeg recordmydesktop

Then, download the source code for [Flashcam]("http://www.swift-tools.net/Flashcam")

> wget [http://www.swift-tools.net/Flashcam/flashcam-1.1.tgz](http://www.swift-tools.net/Flashcam/flashcam-1.1.tgz)

(Check is there is a new version...  Just in case...)

Extract, and compile the source code...  (See documentation for dependencies)

> ./configure
> make
> sudo make install

Actually, we only need the vloopback module from Flashcam.

When loading the vloopback module, it will tell you which device is the input and which is the output.  If you already have a webcam, it is probably already set at /dev/video0.  So loading vloopback will give you /dev/video1 as OUTPUT and /dev/video2 as INPUT.  The following script a pointing to /dev/video2 by default.  You can validate the information my manually loading the vloopback module and using "dmesg" command to find out the input device.

Next, download the utility mjpegtools_yuv_to_v4l from [http://panteltje.com/panteltje/mcamip](http://panteltje.com/panteltje/mcamip)

> wget [http://panteltje.com/panteltje/mcamip/mjpegtools_yuv_to_v4l-0.2.tgz](http://panteltje.com/panteltje/mcamip/mjpegtools_yuv_to_v4l-0.2.tgz)

Extract, compile and install as usual...

We are now ready to the big thing!  There are a lot of possibilities, but here is a small script that can automate the whole process in a single command from the console:

#************Script*******************
mkfifo stream.ogg
sudo modprobe vloopback
echo "CTRL-C to stop the capture"
sleep 5

# On a single line!
recordmydesktop -width 320 -height 240 -fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o stream.ogg & sleep 10 & ffmpeg -i stream.ogg -an -s 320x240 -r 15 -f yuv4mpegpipe - | mjpegtools_yuv_to_v4l /dev/video2
# End of single line

killall recordmydesktop
rm stream.ogg
#*************************************


Copy this script into a bash file (mine is called caputre.sh), and create a folder where to invoke this script.

What happens is
- A fifo file is created to pipe recordMyDesktop with ffmpeg
- The module vloopback is loaded and make sure that your "input" device is /dev/video2. If not, you will have to modify the script to use the correct device. If you already have a webcam on /dev/video0, you will have /dev/video1 as an output and /dev/video2 as an input.
- Then recordMyDestop is invoke and we use the fifo file to record the desktop. That video file in the fifo file will be read by ffmpeg as an input, converted to yuv4mpeg format and the converted file will by piped to the mjpegtools_yuv_to_v4l onto the input device /dev/video2.
- To stop the screencast, simply hit CTRL-C.

    * Make sure to start the script before opening you stickam viewer because Flash won't detect properly your new webcam "Vloopback".
    * Sometimes, the Flash player crashes and stays zombie in memory. It does not happen often, but when it does, it locks the video device and you have to reboot the computer to have access again to your webcam device.


You will require a good CPU because the whole process is CPU demanding but not too much.

The script will capture a square of 400x300 that will be converted into a 320x240 image for the webcam. This settings gives a good view of what you are doing with a good image quality without sacrificing all your CPU cycles. Capture at 5 fps, more than that does not seem to help in any way for the webcam...


[SIZE="4"]**2 - Using ffmpeg (from SVN) as the X11 grabber**[/SIZE]

Ok, while looking for other possibilities, I found out that FFMpeg is able to grab directly from X11 meaning that we can get rid of recordMyDestop in the process...

Download the source code from the SVN repositories:

> svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

Then you have to explicitly enable the X11 grabbing like this:

> ./configure --enable-gpl --enable-x11grab

*The --enable-gpl is mandatory for the x11grab...*

Then continue with the compilation...

> make

I did not install ffmpeg to keep the one from the repository of Ubuntu, so I did not executed "sudo make install".  What I did is copy the binary "ffmpeg" into a dedicated folder to invoke it with a script So I won't mess my Ubuntu setup..

Here is the script to use ffmpeg...  

# Loading the vloopback module
sudo modprobe vloopback
# executing the compiled ffmpeg binary with the x11grab enabled...
./ffmpeg -f x11grab -s 640x480 -r 5 -i :0.0 -pix_fmt yuv420p -s 320x240 -r 5 -f yuv4mpegpipe -an - | mjpegtools_yuv_to_v4l /dev/video2


[SIZE="4"]**3 - Using GStreamer as the X11 grabber and mixer...**[/SIZE]

After looking for different way to play with mjpegtools_yuv_to_v4l, I found out that it was possible to use gst-launch to capture the desktop and also to mix the stream of my webcam onto the main desktop stream.

What you need:
- Gstreamer, GStreamer-ffmpeg
- Flashcam (for vloopback)
- mjpegtools_yuv_to_v4l
- recordMyDesktop can be introduced also but is optional.

Here is the script that I started to build to automate que video capture...

##############################################
# WebcamStudio : Small script to             #
# create a virtual webcam for Flash or aMsn  #
# by mixing different video source           #
#                                            #
# Tools required                             #
# - mjpegtools_yuv_to_v4l                    #
# - gstreamer, gstreamer-ffmpeg              #
# - vloopback (from Flashcam)                #
#                                            #
# Created by Patrick balleux                 #
# [http://blog.patrickballeux.com](http://blog.patrickballeux.com)             #
#                                            #
# End resolution will be 320x240             #
#                                            #
##############################################


# Setting up a folder to work with...
#mkdir ~/.webcamstudio
#cd ~/webcamstudio
# So not, we are in the right folder to work...

# creating output fifo for use with mjpegtools_yuv_to_v4l
mkfifo output.yuv

# loading the vloopback module
gksudo modprobe vloopback

# set those value depending on your setup...
INPUTDEVICE=/dev/video2
OUTPUTDEVICE=/dev/video1
OUTPUTWIDTH=320
OUTPUTHEIGHT=240

# Creating a stream from the webcam
VIDEO1W=80
VIDEO1H=60
VIDEO1X=240
VIDEO1Y=0

# webcam UVCVIDEO
#VIDEO1GST="v4l2src device=/dev/video0 ! jpegdec ! videoscale ! video/x-raw-yuv,width=$VIDEO1W,height=$VIDEO1H ! ffmpegcolorspace"

# webcam EYETOY
VIDEO1GST="v4lsrc device=/dev/video3 ! videoscale ! video/x-raw-yuv,width=$VIDEO1W,height=$VIDEO1H ! ffmpegcolorspace"


# Creating a stream from the desktop
VIDEO2W=500
VIDEO2H=400
VIDEO2X=100
VIDEO2Y=100

# Using GStreamer for X11 capture
VIDEO2GST="ximagesrc use-damage=false show-pointer=true startx=$VIDEO2X starty=$VIDEO2Y endx=$VIDEO2W endy=$VIDEO2H ! videoscale method=0 !video/x-raw-rgb,framerate=15/1,width=$OUTPUTWIDTH,height=$OUTPUTHEIGHT ! ffmpegcolorspace"

# Using recordMyDesktop for X11 capture
mkfifo screen.ogg

#VIDEO2GST="filesrc location=screen.ogg ! oggdemux ! theoradec ! videoscale  !video/x-raw-yuv,framerate=15/1,width=$OUTPUTWIDTH,height=$OUTPUTHEIGHT ! ffmpegcolorspace"
#recordmydesktop --quick-subsampling --no-cursor -width $VIDEO2W -height $VIDEO2H -fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o screen.ogg & sleep 2 & 


# Virtual webcam...

# Mixing VIDEO1 and VIDEO2
gst-launch $VIDEO1GST \
! videobox border-alpha=0 alpha=1 left=-$VIDEO1X top=-$VIDEO1Y \
! videomixer name=mix ! ffmpegcolorspace \
! y4menc ! filesink location=output.yuv \
 $VIDEO2GST ! alpha alpha=1 ! mix. & cat output.yuv | mjpegtools_yuv_to_v4l $INPUTDEVICE

# Sending only VIDEO2
#gst-launch $VIDEO2GST ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l $INPUTDEVICE


# Live view...
#gst-launch $VIDEO1GST \
#! videobox border-alpha=0 alpha=1 left=-$VIDEO1X top=-$VIDEO1Y \
#! videomixer name=mix ! ffmpegcolorspace \
#! xvimagesink \
# $VIDEO2GST ! alpha alpha=1 ! mix.

rm output.yuv



*********************************

The three solutions work quite well with Flash web site like Stickam or BlogTV.  But beware of the CPU usage, Bigger the capture = bigger CPU usage.

Also the video quality of Gstreamer is not as good as the FFMPEG+RECORDMYDESKTOP combo.  But you can overlay a webcam in your desktop capture.

I am trying to find a way to had a third stream for images/logos/titles to show on the stream.  The GStreamer script is not fine-tuned, but it works ok.





Here are some tips:
- With recordMyDesktop, you have more options on the capture like having a square 400x300 that will follow your mouse.
- Using ffmpeg (with X11grab) is not really lighter than using recordMyDesktop + ffmpeg
- Do not capture more than 640x480 with ffmpeg(x11grab), because it will probably kill your CPUs...
- A framerate of 5 fps is more than enough for the capture.
- Some Flash sites enable live recording.  I found out that the recording works better if ffmpeg outputs at 15 FPS...
- Since ffmpeg from the source is able to capture from v4l(2) devices, you can use the same technic to foward from your webcam to a vloopback device.  Usefull when Flash does not recognize your webcam...
- If you want to share a video over your webcam, play it in Totem/Mplayer/VLC and simply point yo it with your mouse...
- I also found out that two Flash site can record from the same virtual webcam as the same time...  I did not think it was possible...


That's it, hope you will enjoy getting par with Windows users with Manycam of FakeWebcam...

Patrick Balleux
[http://blog.patrickballeux.com](http://blog.patrickballeux.com)

---

### Post by patrickballeux on 2008-08-30
Hi, 

Things are going great and a new sourceforge project will be created as I am begining a small project to have an easy virtual webcam setup under Ubuntu (or any other Linux...)

Keep looking for this thread as I will announce new developments here.

Currently, I am able to show:
- Any webcam supported by GStreamer (Cheese...) in a Flash Site
- The desktop (like vnc)
- A composite of webcam/webcam or desktop/webcam or webcam/desktop.
- Show text, clock, time
- Add special effects on the video stream (like Cheese or EffecTV).

Dependencies are : Gstreamer (all plugins), Flashcam (vloopback module) and mjpegtools_yuv_to_v4l and Java as the GUI is done in Java (Because I know more Java than anything else...)

What will be possible eventually:
- Show a local or remote (URL) movie 
- Customise text color
- Apply more filter on the video
- Stream an image
- Mix more than two video source
- Show you desktop and following your mouse


Here is a preview of my current work in attachement...

---

### Post by patrickballeux on 2008-08-31
I was testing the virtual webcam solution and I discovered that on my other AMD64 computer, Flash 9 was installed instead of Flash 10RC...  

It seems that version 10 works better with webcam than Flash 9.  So if you have some problems, try it out with Flash 10 RC as the is a better compatibility.

Also, there seems to be some instability with Firefox 3.0.1 and Flash (9/10).  Sometime, the Flash process will stick in memory as a zombie process.  You need to reboot to get rid of it.  Really stange but I must tell you that this is happening on 2 AMD64 PC (one is laptop, other is desktop).

While testing WebcamStudio (soon on sourceforge), I also discovered that is it possible in a wirtual webcam to show a big part of the desktop and at the same time a small part in one of the corner that has a better visibility. 

For example:  The webcam resolution is at 320x240, and you want to capture an area of 1024x768 of your desktop.  The problem is that it becomes impossible to read of see the small details because the image of 1024x768 is converted to 320x240.  But you can add a second area of the desktop of 160x120 size that will display in the webcam as 160x120.  So you will have a small magnifying glass in the corner that can be usefull when you want to show the details or the text.

I'll make a screen capture to show what it looks like.

Current  development now enables:
- Stream all or part of the desktop
- Stream any webcam compatible with GStreamer (Cheese)
- Stream an image (jpg or png).  PNG alpha channel is supported
- Stream a video (any supported by GStreamer) (no sound for now...)
- Add an image for watermark effect on the stream
- Different special effects are included
- Clock, Time, Text overlay
- Testing mode, to validate before creating the virtual webcam


Note: I tried to make things work with the original vloopback module and it does not work with Flash site.  So you really need the vloopback from the Flashcam project.

Note2:  If you would like to test, have the vloopback module from Flashcam installed, the mjpegtools_yuv_to_v4l installed and Java 6 (OpenSDK from the repos) as WebcamStudio is created in Java.  Uncompress the archive and run like this : java -jar WebcamStudio.jar

Make sure that you vloopback module is loaded...
If all goes well, it should work

This is pre-alpha work, so there can be some trouble...

Hint, sometime, the gst-launch and mjpegtools_yuv_to_v4l get stuck and wont die...  Simply execute : pkill gst-launch & pkill mjpegtools_yuv_to_v4l

Hope you enjoy it!

---

### Post by patrickballeux on 2008-09-03
Somes news...

I am currently working on the new version of WebcamStudio and things are going well.

I am using Java 6 for my development, cause I a java developper so, it is easier for me.  I am testing (and loving...) the library gstreamer-java to interface with the gstreamer libraries.  There are some minor bugs , but overall it works good and the performance is better than other solutions.

The only think that I had trouble with is to rewrite the mjpegtools_yuv_to_v4l in Java using the JNA library.  Is seems to be doable but my knowledge in C coding and the JNA library is not enough.  If someone could help, we could get rid of mjpegtools_yuv_to_v4l and a only a java application able to interact with the native libraries.

Actually, the gstreamer-java library is usin JNA to acces the native libraries...

For now, WebcamStudio is able to :
- Broadcast a V4L2 webcam
- Broadcast the desktop
- Broadcast a JPEG file
- Broadcast multiple sources (no more limited to 2...)
- Apply live the opacity on a running source
- Apply live a string of text at the bottom of a running source
- Output the streams to a Vloopback device
- Output the streams to a YUV4MPEG file
- Output the streams to a YUV4MPEG fifo file
- Add a special effect to a stream (like EffecTV)
- Add a new stream while broadcasting

There is a lot of work still to be done, but I have to wait a good 2-3 weeks before my sourceforge project will be open.

I'll try to post a pre-alpha version here in the next few days so you will be able to play with it.

---

### Post by patrickballeux on 2008-09-04
Hi,

Coding is going well and I can show you a preview at this URL: 
[http://www.stickam.com/member/viewMedia.do?mId=180829239]("http://www.stickam.com/member/viewMedia.do?mId=180829239")

(Sorry, text is in french, but you should understand by lookin...).

Soon to be available at Sourceforge.net...

---

### Post by patrickballeux on 2008-09-07
Hi all,

Here it is, WebcamStudio for GNU/Linux is now available on sourceforge.net at this url: [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")


This is a really Alpha version, so do not expect to much, but the test mode is working ok (display is a little slow...).  But with a virtual webcam, it works like a charm.

I still have to work on the documentation, but you should be able to get it to work quite easily.  

Hope you like it!

---

### Post by patrickballeux on 2008-09-15
Version 0.11 is out and is really cool!

Go download it on Sourceforge!

---

### Post by patrickballeux on 2008-09-18
WebcamStudio v0.12 is not released...  See the project on sourceforge.net for all the details...

---

### Post by lian1238 on 2008-10-14
This project is really cool. I will definitely try this out when I've got time. It'll come in handy when you want to show someone how to do something on the computer. I tried vyew.com but it's too slow, since it loads the whole desktop real-size, (even if it does show the whole desktop to the viewers), and refreshes impossibly slow. Keep this up! I want to see this project become an everyday software that everyone uses! :)

Does anyone know of how to broadcast webcam to multiple viewers? (like a conference video call)

---

### Post by patrickballeux on 2008-10-14
Have a look at Stickam.com or BlogTV.com.  You will have everything needed with an account to broadcast whatever you want to show.  The viewers will only need an access to the Internet and have Flash locally installed.

Could not be easier than that.

Also, on stickam.com, you can be up to 6 peoples broadcasting in the your room (video and voice).  BlogTV, you can have one co-host at a time...

There are other services like that, but I found those 2 to be the easiest to use.

Have fun! Project is currently at version 0.17...

---

### Post by calebk on 2009-03-01
Hi, i want to broadcast my desktop onto skype video call. I am having problems doing this! I can see my desktop on webcam studio but i am not sure how to get that onto skype. I tried a virtual cam but do not have an output device and i am not sure how to get one. Please can you make a guide for a beginner like me. Thanks:confused:

---

### Post by parson983 on 2009-03-15
I'm having the same problem as the guy above, i've searched madly, all over the web to no avail, ho do i get vloopback to run a "Virtual Webcam"? I am obviously a newbie, but any help would be apriciated, thanks.

---

### Post by MaindotC on 2009-06-24
I love WebCamStudio and thank you so much for supporting it :D  Is there a way to make the broadcast size larger than 320x240?  I can't seem to broadcast anything larger than that and I have 1600x1200 resolution.

---

### Post by patrickballeux on 2009-12-15
See the capture size in the desktop source menu...

---

### Post by MaindotC on 2009-12-15
It doesn't really matter because anything larger than 800 x 600 wouldn't logically fit into a broadcast window and I've yet to find a machine that can handle fluid screencasting at that resolution.

---

### Post by afrodeity on 2010-03-02
Really interested in the WebCamStudio Project. It doesn't seem to work with my SN9c1XX camera however which works fine with Cheese and Karmic. Just get a blank screen on preview. Any ideas>?

---

### Post by MaindotC on 2010-03-02
I think your first point of contact would be [WS4GL Forums](http://www.ws4gl.org/forums-and-help).  I've posted there and usually get rather prompt help from Patrick.

---

### Post by afrodeity on 2010-03-03
Thanks, may the ubuntu be with you too.

---

### Post by armanditox on 2011-04-22
hello,

webcamstudio give me poor quality image (images look like a Zebra) for screencast and sometimes don't detect correctly my C200 logitech webcam.

So i write a simple script to stream my webcam on ustream using flashcam but i have a problem with my script for the screencasting.

To simplify the case i unplugged the webcam. When i load vloopback :

```

sudo modprobe vloopback

```

I see this on dmesg :
```
dmesg | grep vloopback
[86934.459334] [vloopback_init] : video4linux loopback driver v1.3
[86934.459472] [vloopback_init] : Loopback 0 registered, input: video0, output: video1
[86934.459477] [vloopback_init] : Loopback 0 , Using 2 buffers

```

My understanding is that i have to used /dev/video1.

my user is part of the group "video" :
```
id
uid=1000(presentation) gid=1000(presentation) groupes=1000(presentation),4(adm),20(dialout),24(cdrom),44(video),46(plugdev),111(lpadmin),119(admin),122(sambashare)
```

and the authorization are good :

```
ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2011-04-22 11:42 /dev/video0
crw-rw----+ 1 root video 81, 1 2011-04-22 11:42 /dev/video1
```


then i used the usefull command of Patrick :


```
rm -f stream.ogg
mkfifo stream.ogg
recordmydesktop --width 320 --height 240 --fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o stream.ogg & sleep 10 & ffmpeg -i stream.ogg -an -s 320x240 -r 15 -f yuv4mpegpipe - | mjpegtools_yuv_to_v4l /dev/video1
```

here is the partial output :
```
mjpegtools_yuv_to_v4l-0.2 (c) Jan Panteltje 2008-always.
mjpegtools_yuv_to_v4l: failed to open output video device, aborting.Initial recording window is set to:
X:0   Y:0    Width:320    Height:240
Adjusted recording window is set to:
X:0   Y:0    Width:320    Height:240
Your window manager appears to be Metacity
```

well, why mjpgetools_yuv_to_v4l can't open output video device ?

the fifo files seems good :

```
ls -rtl stream.*
prw-r--r-- 1 presentation presentation       0 2011-04-22 11:49 stream.ogg
-rw-r--r-- 1 presentation presentation 1178161 2011-04-22 12:00 stream.ogg.ogv
```

I read this [thread]("http://ubuntuforums.org/showthread.php?t=1353347") but it was not useful for me.

Can somebody help me ?
(ubuntu 10.10 maverick meerkat)

---

### Post by alexan on 2011-09-05
After two years there's a simpler (and more secure) way to achive the result?

I see this thread is both on top of most google searches on the subject

---

