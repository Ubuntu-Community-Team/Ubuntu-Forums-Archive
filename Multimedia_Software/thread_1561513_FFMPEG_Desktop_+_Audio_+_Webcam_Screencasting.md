---
title: "FFMPEG Desktop + Audio + Webcam Screencasting"
date: 2010-08-26
forum: Multimedia Software
---

### Post by clockworkpc on 2010-08-26
Hi,

This is my first post so I hope I don't annoy anyone.  Basically, I'm on the verge of having a single command that will enable me to record all three elements of a screencast -- desktop, audio, and webcam -- but it is falling at the final hurdle.

System:

[LIST]
[*]Ubuntu Lucid with updates
[*]Dell Inspiron 1520
[*]NVidia drivers
[*]Onboard webcam
[*]FFmpeg version SVN-r24872
[/LIST]

I have two scripts that work independently, but I can't get them to work simultaneously.  I have tried chaining the commands, but I get an error and I don't know how to solve it.  I hope someone can give me some pointers.

**Screencast: Desktop and Audio:/usr/bin/screencast:**

[INDENT][COLOR="Navy"]# Record The Screencast
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1440x900 -i :0.0 -qscale 1 -acodec alac -vcodec libx264 -vpre lossless_ultrafast -threads 0 ~/Videos/output.m4v 

# Move and Rename the Screencast
mv ~/Videos/output.m4v ~/Videos/Screencasts/Screencast_on_$(date +%F_%A_at_%H:%M:%S).m4v

## Talking Cow (XCowsay 1.2 installed from source file)

xcowsay --cow-size=large --time=3 --monitor=0 "Your video has been recorded :)"

exit[/COLOR]
[/INDENT]

On its own, this works absolutely wonderfully.

**Webcam: /usr/bin/webcamscript**

[INDENT][COLOR="navy"]#!/bin/bash

## Record from webcam in 320x240 resolution
ffmpeg -f oss -i /dev/dsp -f video4linux2 -s 320x240 -i /dev/video0 ~/Videos/recording.mpg

## Wait for video to be created
# sleep 5

## Move file to ~/Videos/Screencasts
mv ~/Videos/recording.mpg ~/Videos/Screencasts/Webcam_on_$(date +%F_%A_at_%H:%M:%S).mpg[/COLOR]
[/INDENT]

On its own it works perfectly too.

**[COLOR="Red"]PROBLEM: They do not work together![/COLOR]**

I have tried the following command without success:

(gnome-terminal -e screencast &);(gnome-terminal -e webcamscript)

The thing is that it opens two gnome-terminals, as I need in order to stop recording when I'm done, and *webcamscript* works perfectly, but my *screencast* (ffmpeg x11grab and audio) gives me the following output:


[COLOR="Navy"][INDENT]FFmpeg version SVN-r24872, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 23 2010 20:50:39 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.24. 0 / 50.24. 0
  libavcore      0. 6. 0 /  0. 6. 0
  libavcodec    52.85. 1 / 52.85. 1
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.37. 0 /  1.37. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[alsa @ 0xa9c9470] capture with some ALSA plugins, especially dsnoop, may hang.[/INDENT][/COLOR]


When I tried it initially, it actually did work.  I must have done something differently since then, but I can't figure it out.  Ideas, anyone?

---

### Post by gordintoronto on 2010-08-26
Interesting how different people approach things differently. It would never occur to me to try what you want to do. I would use Recordmydesktop to do the screen capture, then I would record video with Cheese, then I would use Cinelerra for video editing. Oh, I might do some video conversion using "video converter," a GUI front-end for ffmpeg.

---

### Post by clockworkpc on 2010-08-30
> **gordintoronto said:**
> Interesting how different people approach things differently. It would never occur to me to try what you want to do. I would use Recordmydesktop to do the screen capture, then I would record video with Cheese, then I would use Cinelerra for video editing. Oh, I might do some video conversion using "video converter," a GUI front-end for ffmpeg.

Hi,

Thanks for your response, but there are a few key reasons for my attempt to run everything through the command line, using ffmpeg for everything, with a single command that runs effectively three simultaneous processes.

[COLOR="Blue"]
[LIST=1]
[*]Running it from the command line uses fewer system resources.
[*]Running it from the command line enables me to assign a keyboard shortcut to the command.
[*]What I want is raw video that is automatically saved in a folder and date-and-time stamped in a format that can be uploaded to youtube without editing or conversion. (And if I'm running ffmpeg from the command line, why would introduce a few superfluous steps by using an ffmpeg front-end?)
[*]Recordmydesktop is buggy and slow and its output even at high quality is poor.
[*]Cheese is OK for images but it is absolutely useless for webcam video.  It seems to be stuck on one frame per second and is completely unsuitable for webcasting.
**[*]And finally, I want the output to be in two separate simultaneously recorded files that I can put together in Openshot, which is a great video editor that allows me to position the webcam's talking head as I see fit.**[/COLOR][/LIST]

My goal is to show my Mac friends that whatever they can do with Camtasia:mac etc. I can do too, and the cumbersome method of using a collection of frankly second-rate GUI front-ends when we have an awesome tool in ffmpeg makes no sense.

[LIST]
[*][COLOR="blue"]When I record the webcam with ffmpeg it works beautifully at a high frame rate;
[*]When I record the desktop and audio with ffmpeg it works beautifully at a high frame rate;[/COLOR]
[COLOR="Red"][*]If I try to do all of these together I run into problems.[/COLOR]
[/LIST]

If someone can help me to record all three streams simultaneously and output to two separate files -- (webcam+audio and x11grab) OR (x11grab+audio and webcam) -- **from the command line with a single command**,  then I would be most grateful.

---

### Post by gordintoronto on 2010-08-30
I hope you can find an answer. The only thing you said above, which does not match my experience, is about Cheese. When I record video in Cheese, it's just fine, "full motion video." Perhaps it's because last year was "new computer" time, and I built a pretty fast system.

---

### Post by clockworkpc on 2010-08-31
OK, here is my script, which will undergo further refinement, but it works -- if anyone out there is interested...

############ The Clockwork PC Webcasting Script #################
#
# This script is the fruit of many hours of research into FFMPEG.
#
# You will need ffmpeg with x11grab, and a number of libraries that should be installed automatically.
#
# You will need a custom directory ~/Videos/Screencasts or change the output directory in the commands.
#
# You will also need to download and install the newest xcowsay from its homepage, 
# because the older xcowsay from the Ubuntu repositories (2010-08-31 at the time of writing) will not work with the --monitor option.
#
# The chained command creates THREE separate files: 
# x11grab for your desktop, 
# video4linux2 for your webcam, 
# alsa for your microphone or headset. 
# 
# This is very important to me because I use Openshot Video Editor, which cannot split audio and video yet, but can combine them very well.
# If this is not important to you, there are many fine commands that combine audio and video streams into a single file, so you don't have to use mine.
#
# However, this chained command will record everything synchronously, including webcam and audio.
#
# Enjoy! 
#
# Alexander,
# [email]linux@clockworkpc.com.au[/email]
#
#
#################################################################

# Working on saving all the files into date-stamped bins,
# but for now they just pile up in Screencasts.


gnome-terminal -x ffmpeg -f x11grab -r 30 -s 1600x900 -i :0.0 -sameq -vcodec libx264 -vpre lossless_ultrafast -threads 0 ~/Videos/Screencasts/bin_today/Screencast_on_$(date +%F_%A_at_%H:%M:%S).m4v ;

gnome-terminal -x ffmpeg -f video4linux2 -s 240x150 -i /dev/video0 ~/Videos/Screencasts/bin_today/Webcam_on_$(date +%F_%A_at_%H:%M:%S).mpg ;

gnome-terminal -x ffmpeg -f alsa -ac 2 -i pulse -acodec pcm_s16le ~/Videos/Screencasts/bin_today/Audio_on_$(date +%F_%A_at_%H:%M:%S).wav

############################################################
#
# Add a cute talking cow.  
#
# (Haven't worked out how to stop it from popping up before #  the videos have finished recording)
#
## xcowsay --cow-size=large --time=3 --monitor=0 "Your video has been recorded :)"
#
############################################################

---

### Post by gordintoronto on 2010-09-01
Perhaps you could use the Thread Tools to mark the thread "Solved"?

---

### Post by inteldesign258 on 2011-12-20
I read your post and fell in love with it! I haven't used ffmpeg since last summer! I like many others interested in doing screen-cast did it the conventional way like a few other users have outlined in their post to this thread!

This is the version of ffmpeg that is installed on my liveUSB:

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2

I do not plan on installing ffmpeg on my laptop hard drive so I am curious to see if your method that you say works will work for me! I will keep you posted in the future to let you know how things worked out for me!

---

### Post by nothingspecial on 2011-12-21
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

