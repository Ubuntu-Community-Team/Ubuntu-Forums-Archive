---
title: "[SOLVED] trouble with tvtime recording"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by Cresho on 2008-04-11
Hello!  I been at this all night.  I basically have 2 video cards.  the first one is the pctv115 by kworld which works fabulously and can record easily with me-tv.  the second one is a avermedia stereo and I use tvtime.  tvtime was having a hardtime running the audio and video so i put this script up to force tv time to work fine.

```
#!/bin/bash
amixer -q set "Line" 100% unmute
amixer -q set "Analog Mix" 100% unmute
tvtime --device=/dev/video1 --frequencies=us-cable --input=0 --norm=NTSC
amixer -q set "Line" 100% mute
```


NOW!  it all works fine....minus one thing.

I can record video through my mencoder like this

#!/bin/bash

OUTPUT="/home/myusername/Desktop/pvr/`date +%y%m%d-%H%M.xvid`"

mencoder tv:// -tv driver=v4l2:device=/dev/video0:input=2:width=640: height=480:alsa \
-of avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=3500 -oac \
mp3lame -lameopts cbr:br=128 -vf pp=lb -o test.avi -endpos 119:00

while [ ¨$(pidof mencoder)¨ != ¨¨ ]; do sync; sleep 15; done

sync

exit 0


I make the sh file executable and I run it in terminal so I can ctrl+c to close it after (easier way to close it?)

it records it fine but ill tweak the settings later for quality.

MY REAL QUESTION IS..

is there a way to record and view video at the same time?

---

### Post by Cresho on 2008-04-12
OKAY!  I GOT IT!

anyway, I spent 4 more hours today working my settings out.  I still have not configured the quality and I hope someone can help me record good quality video incase I want to go from DV camera into my linux box for video editing.

THis is how it works.  I have created 3 buttons and one folder.  Each button does something specific.  one opens tvtime, one records the show while you are watching it, and the last one stops it with the killall command.

this is the script i use to launch my tvtime.
```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```

this next code I use to record the show.
```
#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

gnome-terminal --execute transcode -x v4l2,v4l2 \
           -M 2 \
           -i /dev/video0 \
           -p /dev/dsp \
           -w 6000 \
           -y ffmpeg \
           -F mpeg4 \
           -c 02:30:00 \
           -g 720x480 \
           -f 0,4 \
           -I 1 \
	   -J resample,levels,smartyuv,pv \
           -u 100 \
           -Q 3 \
           -Z 640x480,fast \
           -E 48000,16,2 \
           --lame_preset medium \
           -o ~/tvtime-recorded/tvrecord-${TODAY}-${NOW}.avi \




amixer -q set "Line" 100% mute &
```

when you want to kill it, just highlight the terminal and ctrl+c or you can use this next script to kill it for you.  If you dont want to see the terminal information, just remove "gnome-terminal --execute"

this last one kills the transcode and reopens tvtime

```
#!/bin/sh

killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```


you will be fine if  you just install transcode in the terminal.  sudo apt-get install transcode

if you are going to try the above, make sure you have installed, well in my case, i installed all the gstreamers, mplayer, xawtv, xine, all codecs and etc for compatability.  but the main one is transcode from synaptic.
before you start modifying the scripts, you should do a "ls -l /dev/" and pay close attention to the            -i /dev/video1 \       and     -p /dev/dsp1 \  pay close attention to my script above when recording.  first timers will need to launch it from terminal (just cd into directory and sh tv-record.sh{this is my sh file name with execute permission enabled in properties} and look at the output for errors)  I changed my video to video0 and audio from dsp1 to dsp.  This fixed my problem and looking at the output from "ls -l /dev/" helped me out a bit.

to kill the transcode, just grab the terminal and on the keyboard do a ctrl+c to close it.  or in terminal do a killall transcode.

here is the result!  Look closely to the avant window navigator.  It has tvtime with all the buttons.  It integrates very well into my system.

[http://ubuntuforums.org/g/images/279277/1_realubuntu.jpg](http://ubuntuforums.org/g/images/279277/1_realubuntu.jpg)


all refferenced from here
[http://www.transcoding.org/cgi-bin/transcode?Video4linux_Examples](http://www.transcoding.org/cgi-bin/transcode?Video4linux_Examples)


I have a few more questions.  If anybody can help me use ffmpeg transcode to achieve a better encoding.  I got tired figuring this out and ill probably pick it up again next week.  Pointers are welcomed.

---

### Post by Cresho on 2008-04-12
im adding this here incase someone needs help with 2 tv card switching problems

[http://ubuntuforums.org/showthread.php?p=4706126#post4706126](http://ubuntuforums.org/showthread.php?p=4706126#post4706126)

---

### Post by Cresho on 2008-04-18
I just updated the scripts above.  It makes the tvtime load more snappier while controlling the line in.  The transition between tvtime and transcode is improved as well.  Just a hint for anybody else who asks me, if you want to use this method to record your video games or vhs tapes or video recorder onto your pc, just change

tvtime --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC

the input part 0 can be changed to 1 or 2.

so it would look like this

tvtime --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=1 --norm=NTSC

I forgot which one is for svideo and the other for video in.  anyway,   good luck

and I am looking for a ffmpeg script or settings that allowes me to use xvid instead of the current codec it uses.

---

### Post by Cresho on 2008-04-20
I just updated the above transocode to use mpeg4 instead of the msmpeg4 or what ever that was.  Appearantly, if I uploaded the recorded video to windows, it would not work, access, nor was I able to delete the file unless I use ubuntu to delete.  It does require a free codec available. "xvid"  [http://www.xvid.org](http://www.xvid.org)

I am still looking at recording mpeg2 or dvd compliant video I tried various methods but appearantly i get no sound.  So far, I am content with this method.

---

### Post by ferossan on 2008-05-21
Thank you Cresho! Great info.
I used to use streamer to record some TV Shows from tvtime but many times I ended up with corrupted files (specially in long recordings).
Now transcode seems to work better, still testing but looks fine by now.
This should be converted to a HowTo somewhere. Very useful.

---

