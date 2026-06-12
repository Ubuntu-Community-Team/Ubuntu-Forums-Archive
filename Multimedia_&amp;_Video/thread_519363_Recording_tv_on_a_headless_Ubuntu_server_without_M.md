---
title: "Recording tv on a headless Ubuntu server without MythTV"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by rml00 on 2007-08-06
Hi all,

I have a Hauppage WinTV-PVR-USB2 capture card that does hardware encoding. I have put it on an old computer (700Mhz, 256Mb RAM) with the command line version of Ubuntu (no X server). I am trying to find a way to record TV shows directly to disk (no display) and to schedule the recordings using cron. The only reference I could find is to do a "cat /dev/video0 >> tvshow.mpg" but you need to manually stop the recording which is not very practical. Is there a way to stream the card's stream to disk and stop it automatically.  I believe mencoder can do it but I was not able to find to proper flags to use with an already encoded stream. I do not want to transcode as the computer is not powerfull enough and the stream is already encoded using MPEG2 directly on the capture card. Also, I do not wish to use MythTV because it is overkill for what I want to do.

Thank you very much.

---

### Post by tbroderick on 2007-08-07
Take a look at streamer.

---

### Post by MMoudry on 2007-08-07
Install dvb tools I think the package name is dvb-tools or dvbtools) and use dvbstream command to record. There is a nice DVB wiki at [www.linuxtv.org](www.linuxtv.org)

MM

---

### Post by dougfractal on 2007-08-07
> mencoder -sws 2 -oac copy  -ovc copy  dvb://five -o batmanreturns.mpg  dvb://Five   -endpos 7200

record Five for 2 hours, mpeg2 stream, ~1GB per hour


> mencoder -sws 2 -oac mp3lame -lameopts mode=2:cbr:br=128:vol=0 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800:vhq  -vf scale=352:288 -ffourcc XVID  dvb://five -o batmanreturns.avi -endpos 7200

record Five for 2 hours, xvid vid, mp3 audio , scaled 352x288   ~400MB per hour

---

### Post by rml00 on 2007-08-07
Thank you all for you answers.

tbroderick: I have tried streamer but I get no image nor sound. I used: ```
streamer -t 0:30 -f mjpeg -F stereo -o test.avi
``` I will look into it further.

MMoudry, dougfractal: I do not have any dvb drivers installed. I think it is v4l. I used the instructions [here]("http://www.isely.net/pvrusb2/pvrusb2.html") to build the driver. I will look further into the wiki suggested. Though I must say I am a bit confused about this dvb and v4l thing. What is the best way to go?

Thanks again.

---

### Post by dougfractal on 2007-08-07
v4l is for TV capture cards
dvb-tools  is for dvb streams.


from [http://www.linuxtv.org/v4lwiki/index.php/Mencoder](http://www.linuxtv.org/v4lwiki/index.php/Mencoder)
> 
 Mencoder usage on a slow x86

This is the command line I use for recording PAL (UK), using a simple capture card, and an old PC (PIII 700mhz):

 sudo nice --10 mencoder tv:// -v -tv \
 driver=v4l2:width=576:height=576:input=1:device=/dev/video0:immediatemode=0:forceaudio:outfmt=yv12 \
 -o outfile.avi -ovc lavc -lavcopts vcodec=mjpeg:aspect=4/3 -aspect 4:3 -noautoexpand -oac pcm \
 -endpos 00:30:00


ffmpeg also good
>  FFmpeg can grab video and audio from devices given that you specify the input format and device.

ffmpeg -f audio_device -i /dev/dsp -f video4linux2 -i /dev/video0 /tmp/out.mpg

Note that you must activate the right video source and channel before launching FFmpeg with any TV viewer such as xawtv ([http://bytesex.org/xawtv/](http://bytesex.org/xawtv/)) by Gerd Knorr. You also have to set the audio recording levels correctly with a standard mixer.

---

### Post by dougfractal on 2007-08-07
OK i've just looked at [http://www.isely.net/pvrusb2/usage.html](http://www.isely.net/pvrusb2/usage.html)

can you try 
> ffmpeg -i /dev/video0 out.ffmpeg.mpg

and 
> mencoder /dev/video0 -oac copy -ovc copy -o out.mencoder.mpg

apparently  the tv option may playup because it a  mpg2 stream not video frames.

---

### Post by MMoudry on 2007-08-08
From what I gathered v4l is the older standard and DVB is the new standard. It's merely a question on how the drivers that manage your card communicate with the tools that you use to exploit your card (ie a video player). On the [www.linuxtv.org](www.linuxtv.org) site most of the drivers are both v4l and DVB. Anyways.... I'd suggest to use DVB, I dunno how to do it under v4l ;-)


MM

---

### Post by rml00 on 2007-08-08
> **dougfractal said:**
> OK i've just looked at [http://www.isely.net/pvrusb2/usage.html](http://www.isely.net/pvrusb2/usage.html)

can you try 


and 


apparently  the tv option may playup because it a  mpg2 stream not video frames.

Works great. Thanks. 

I can change channels using v4lctl. I also want to change the encoding parameters. Searching Google I found v4l2-ctl in the ivtv-utils package. I think it can work since the driver I build is v4l2 (isn't it?). I don't know about ivtv, though. Would you suggest another app to change resolution, bitrate, etc.

I am also mixed up with all these types of video drivers (v4l, v4l2, dvb, ivtv). Which type of driver would you suggest I use if i am to work only from the command line?

Thanks again for all your help. It is much appreciated.

---

### Post by dougfractal on 2007-08-08
I might get this wrong.

v4l : original video for linux,  webcams, tv capture
v4l2 : ditto  version 2
ivtv :  a layer ontop of v4l2 . Linux Open Source driver implementation for video capture cards based on the iCompression iTVC15 or Conexant CX23415/CX23416 MPEG Codec. Examples of such cards are the Hauppauge PVR 250/350 series of MPEG video capture cards

dvb : digital tv receiver.   receives mpeg2 streams 
ivtv : receives analog and converts to a  mpeg2 stream

xawtv and ivtv just don't get along!xawtv does not understand mpeg. Use a player that understands mpeg, such as mplayer or xine

ivtv is designed for your card

[http://ivtv.sourceforge.net/FAQ.html](http://ivtv.sourceforge.net/FAQ.html)
> Alternatively, if you want things to just happen automagically, edit /etc/modules.conf and add the following lines:

alias char-major-81 videodev
alias char-major-81-0 ivtv
options ivtv debug=1
options tuner type=2
options msp3400 once=1 simple=1
add below ivtv msp3400 saa7115 tuner

With the above changes to modules.conf, all the required modules will be automatically loaded when accessing /dev/video0 or when doing a modprobe ivtv. Thanks to Jake Page for suggesting the above changes to modules.conf

Next go into the .../utils directory and type make to create the test_ioctl utility. Before you can capture you must set the video resolution and possibly the video standard and video input. Pick and choose from the following commands as appropriate or change the values to suit:

Set PAL video standard

[root@host]# ./test_ioctl -u 0xff

Set NTSC video standard

[root@host]# ./test_ioctl -u 0x3000

Select tuner input

[root@host]# ./test_ioctl -p 0

Select composite video input

[root@host]# ./test_ioctl -p 5

Set full PAL resolution

[root@host]# ./test_ioctl -f width=720,height=576

Set full NTSC resolution

[root@host]# ./test_ioctl -f width=720,height=480

Finally, try to capture some video:

[root@host]# cat /dev/video0 > first_capture.mpg

Press ctrl-c to stop the capture.


have you seen this
[https://help.ubuntu.com/community/Install_IVTV_Feisty](https://help.ubuntu.com/community/Install_IVTV_Feisty)
[https://help.ubuntu.com/community/Install_IVTV_Troubleshooting](https://help.ubuntu.com/community/Install_IVTV_Troubleshooting)

---

### Post by rml00 on 2007-08-12
Thank you all for your help. With all the info you gave me I was able to build a very simple pvr which does exactly what I wanted. I will try to post a HowTo when I get some time.

Thanks again.

---

