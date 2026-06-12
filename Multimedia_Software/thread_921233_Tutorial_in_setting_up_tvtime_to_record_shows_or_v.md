---
title: "Tutorial in setting up tvtime to record shows or video camera input."
date: 2008-09-16
forum: Multimedia Software
---

### Post by Cresho on 2008-09-16
I'm reposting this up because I have had quite a few requests and am not able to bump up the tvtime tutorial I posted months ago....long ago.  I am going to assume that you already have TVtime installed and it is configured and you have all the channels working as well.  So all that we need to do is install


If you did not modify your software sources from system->administration and changed your download server to "main server", then I suggest you in terminal enter these one line at a time.....

sudo apt-get update
sudo apt-get install transcode

start of tutorial
-----------------

We are going to create 3 buttons (4th one is for video cam or pc cam recorder using rca input into your television tuner card if it has one).  All are very necessery so do not skip any of them the buttons we are about to create!!!!!


create a folder in your "home" directory called "tvtime-buttons"(no spaces please).  In this folder create 4 files by right on desktop, clicking->create document->empty file (we need 4 of these).  Each one will be named tvtime.sh, tvtime-record.sh, tvtime-stop-recording.sh, tvtime-camcorder-recorder.sh.

on each of those files created, you will need to right click on each and one of them, go to properties->permissions-> put a check mark on "execute" on each and one of them.

we need to find out where your video card lives!! So open up a terminal and do a...
ls -l /dev/video0
and you should then see something like this
crw-rw----+ 1 root video 81, 0 2008-09-15 21:41 /dev/video0

if you change the last digit 0 to a 1 or 2, then you may have more so keep notes of these.

on my pc, i have 
crw-rw----+ 1 root video 81, 0 2008-09-15 21:41 /dev/video0
crw-rw----+ 1 root video 81, 1 2008-09-15 22:03 /dev/video1

the other ones to not say anything at all.  In my pc,
dev/video0 is the television tuner
dev/video1 is the rca input from video camera.
if I had a pc cam, it would be video3. but this can vary between users so be aware of this.


Now we are ready to edit the scripts!!!!!

updated scripts as of 05042010
OKAYYYY!!!!
------------------------------------------------------------------------------------------------------------
it's done.

Lil history here...short version.

I created these sets of commands for my hardy heron....worked great!  Flash forward into the future.  They suck and will probably suck for others.

issues?
transcode
ffmpeg
pulseaudio
new drivers
new kernel

So what was fixed?  Nothing really.  the new software includes pulseaudio fixes and they work.  Previous attempts was futile.

So what does the script look like?  I have a set of 4
1.  launches tvtime
2.  or records line in
3.  records tvtime
4.  closes transcoder and shuts down or mutes line in.

here they are and adjust them accordingly.

They specifically work for lucid lynx under UBUNTU and not KUBUNTU.  I barely got this working here but you can give it a whirl.

tvtime launcher
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute;
```
tvtime launch video in
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=1 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute;
```
tvtime records in
```
#!/bin/sh
killall tvtime
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
sleep 4 && amixer -q set "Line" 100% unmute
sleep 1 && amixer -q set "Analog Mix" 100% unmute
#####################################################################
gnome-terminal --execute transcode -x v4l2,v4l2 \
-M 2 \
-i /dev/video0 \
-p /dev/dsp \
-w 6000 \
-y ffmpeg \
-F mpeg4 \
-g 720x420 \
-f 0,4 \
-I 1 \
-J resample,levels,smartyuv,pv \
-u 100 \
-Q 3 \
-Z 640x480,fast \
-E 48000,16,2 \
-o ~/-${TODAY}-${NOW}.avi \
#####################################################################

```
tvtime stop recording
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute
```






Here is an interesting thing.  create a bash script and put this in

```
#!/bin/sh
killall tvtime
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
sleep 4 && amixer -q set "Line" 100% unmute
sleep 1 && amixer -q set "Analog Mix" 100% unmute
#####################################################################
transcode -x v4l2,v4l2 \
-M 2 \
-i /dev/video0 \
-p /dev/dsp \
-w 6000 \
-y ffmpeg \
-F mpeg4 \
-g 720x420 \
-f 0,4 \
-I 1 \
-J resample,levels,smartyuv,pv \
-u 100 \
-Q 3 \
-Z 640x480,fast \
-E 48000,16,2 \
-o ~/-${TODAY}-${NOW}.avi \
#####################################################################
```

create a test.sh and paste the above.  open a terminal and cd into the directory of the file.  execute in terminal like this "./test.sh" and see the output.  paste output here.

make sure the sh script is executable.  We can see what is conflicting.  I must of spent tons figuring out what was going on.  It wasn't a problem.  It was 4 plus different issues including pulseaudio which I assumed was broken in lucid lynx but its working fine and they must of compiled transcode to work with it.  my tv recording now works and also my line in video works and also svideo line in works...not created a script...yet but its easy.

issues?  never got these working in karmic or jaunty.  I went from hardy streight to lucid lynx
--------------------------------------------------------------------------------------------------------------------
TVTIME LAUNCHER!!!!!
open up "tvtime.sh" in a text editor (this one is in your applications->accessories) and paste this next info into it and save it.
```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video1 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```
The only part that I want you to modify is this line and you can do the rest later
"tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video1"
this line says, launch tvtime in a window of 480x360 and I want video1.  Remember that video1 could not be your tuner.  you may need to change this to video0 if you dont see anything.  change video0 to 1 or 2 or 3 in this order and save document.  Then double click on the script to see if it launches by clicking on run on the pop up.  If it does, keep note of which video so you can use it on the next step to add on the record script.

TVTIME RECORDER!!!!!!!!
now open up tvtime-record.sh and paste this into it.
```
#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )

gnome-terminal --execute transcode -x v4l2,v4l2 \
           -M 2 \
           -i /dev/video1 \
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
           -o /Multimedia/myfiles/My_Videos_Projects/tvtime-recorded/-${TODAY}-${NOW}.avi \




amixer -q set "Line" 0% mute &
```
now pay close attention to...

-i /dev/video1 \
and
-o /Multimedia/myfiles/My_Videos_Projects/tvtime-recorded/-${TODAY}-${NOW}.avi \

-i is the input so you can change video1 to video0 if that is where your card is at after the past experiment.
-o is the output to the directory of where you want your video recorded so it could say
-o /home/myusername/Videos/-${TODAY}-${NOW}.avi \

once you finished editing this, save the document.

NOW TO STOP THE RECORDER BUTTON!!!!!
```
#!/bin/sh

killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video1 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute;
```
this one tells the recording to stop recording and then reopens the tvtime.

Ill let you guess at the 4th or 5th button since the above gives you alot of clues.

If you have any questions, Feel free to ask!

Now to associate the buttons.
go to system->preference->main menu
choose sound and video, then remove a checkmark on the original tvtime and create a new one.select new item and name it tvtime-play under name and in the command, direct it to the tvtim.sh.  then "ok" and do the same for tvtime record and tvtime stop record.  if you want to see you can choose custom icons like the ones I use which has a play, record, stop icons.  Once these are costumized or if you dont care for them, you can drag and drop these icons to the desktop so you can have access to them easily.  If you setup a drawer in gnome bar, you can drag and drop the custom  launchers into it directly and you can launch it from there.

So this is how it works, I turn on tvtime, change channels.  After I have what i want to see, i just click on record button.  After I am done recording, I just click on stop recording.  These steps are necessery because it turns off line in and turns it on as necessery since most tv-timer cards use line in.  if your card is digital, then you may need to adjust amixer to use digital.

Here is a picture of my final product.

---

### Post by lovinglinux on 2008-09-16
I have incorporated some of your instructions on my "Firefox Media Center" tutorial, since my previous recording method output a single file name.

I have modified the code, so it won't launch the terminal. Nevertheless, it will launch TVTime before recording, so you can choose channel and the recording will start only after closing TVTime window. My method is for a silent recording. Please tell me what you think about it. It is in the section 8.2 of my tutorial (link in the signature).

---

### Post by Cresho on 2008-09-16
Hey!  that's pretty cool how you got the silent record to work and view the video file like a pvr. :popcorn:

I frankly have 2 television tuners with 1 being single and the other being dual.  I like having 2 windows, 1 analog tv, 1 high definition television and the pvr would be perfect on a home theater system.  But this one is my desktop so I like having 2 televisions running while I have a third for dvd or browsing the net or what ever else.  I sometimes like recording my high definition or analog at the same time when i can't make my mind up on what show to watch!

I have one question, How is the recording compared to the old way you did it?  I am curious because I tweaked it to my liking and have not updated it since then.  I was wondering if you like the setting or if you found a different way of making the recording look better.

---

### Post by lovinglinux on 2008-09-16
> **Cresho said:**
> Hey!  that's pretty cool how you got the silent record to work and view the video file like a pvr. :popcorn:

Thank you.

> **Cresho said:**
> I frankly have 2 television tuners with 1 being single and the other being dual.  I like having 2 windows, 1 analog tv, 1 high definition television and the pvr would be perfect on a home theater system.  But this one is my desktop so I like having 2 televisions running while I have a third for dvd or browsing the net or what ever else.  I sometimes like recording my high definition or analog at the same time when i can't make my mind up on what show to watch!

You must have a very good system. Since my TV card is analog, I can't put a higher resolution without boosting CPU usage to the top. Can't even imagine recording two things simultaneously. 

> **Cresho said:**
> I have one question, How is the recording compared to the old way you did it?  I am curious because I tweaked it to my liking and have not updated it since then.  I was wondering if you like the setting or if you found a different way of making the recording look better.

I didn't changed my old settings for the transcoder command, except for the output file name. I was saving with the same file name every time, so each recording was replacing the previous one.

Unfortunately I'm still having issues with the audio. When I record from microphone the recorded sound is fine, but when recording from Line (audio from the tv card), I get a very weird accelerated sound. Looks like everyone is the Disney's Donald Duck character. Do you have any idea how to fix this?

I will try your settings, but my TV card i so lame that I guess it won't make any difference.

Edit: I get better results without overloading the CPU using "-g 640x480 \" and "-Z 320x240,fast \"

---

### Post by lovinglinux on 2008-09-16
You should take a look at my PVR tutorial section again. I have included new features like moving the file to another directory after recording, playing the recorded file automatically and displaying a notification icon in the gnome-panel while recording (with file info) that you can click to stop the recording :popcorn:

---

### Post by Cresho on 2008-09-16
-E 48000,16,2 \
           --lame_preset medium \


those lines above!  I am assuming your pc is struggling so you can probably change these to

           -E 44100,16,2 \
           --lame_preset large \

or


           -E 44100,16,2 \
           --lame_preset small \

or

           -E r[,b[,c]] [44100,16,2] \



If you have a cellphone, or a zaurus or even a pda, you can convert these files into something much better for "on the road"  I basically use this step when I record my VHS movies into ubuntu using the top method and then use these methods to put them on my zaurus or cellphone to view.
[http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27](http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27)

just ignore the xacti part.  I use my xacti high definition camcorder to record high definition movies and edit them in ubuntu.  so you really need to look at winff and avidemux section better or even the mandvd section which has a fix for slideshow.

---

### Post by Cresho on 2008-09-16
> **lovinglinux said:**
> You should take a look at my PVR tutorial section again. I have included new features like moving the file to another directory after recording, playing the recorded file automatically and displaying a notification icon in the gnome-panel while recording (with file info) that you can click to stop the recording :popcorn:

You know what, I have it bookmarked to see where you are heading with this.  It has interesting stuff.  But I like looking at the terminal.  That is why i added it because i can see if it drop files or has any errors that develops.  When I get a little free time, I will definitely use the pvr trick you have setup on a new record button.  That's why I posted the tricks because I wanted to get an idea of how far I can take it and here you are with new information.  I was very surprised.

---

### Post by lovinglinux on 2008-09-16
> **Cresho said:**
> -E 48000,16,2 \
           --lame_preset medium \


those lines above!  I am assuming your pc is struggling so you can probably change these to

           -E 44100,16,2 \
           --lame_preset large \

or


           -E 44100,16,2 \
           --lame_preset small \

or

           -E r[,b[,c]] [44100,16,2] \



If you have a cellphone, or a zaurus or even a pda, you can convert these files into something much better for "on the road"  I basically use this step when I record my VHS movies into ubuntu using the top method and then use these methods to put them on my zaurus or cellphone to view.
[http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27](http://forums.steves-digicams.com/forums/view_topic.php?id=594710&forum_id=27)

just ignore the xacti part.  I use my xacti high definition camcorder to record high definition movies and edit them in ubuntu.  so you really need to look at winff and avidemux section better.

Thanks. I will try these settings. My pc is not actually struggling, like not being able to do anything else while recording, but I don't like to have the recorder using so much of the CPU. Really don't know if this is bad on long term.

> **Cresho said:**
> You know what, I have it bookmarked to see where you are heading with this.  It has interesting stuff.  But I like looking at the terminal.  That is why i added it because i can see if it drop files or has any errors that develops.

Hehehe. Sorry if I'm hijacking your thread and spamming it with these messages. I won't post any reminders now that you have bookmarked my thread :biggrin: I guest I'm that kind of Linux newbie that can't control himself every time he discover new cool stuff :)

---

### Post by Jesua on 2008-11-14
Im going to check out this tutorial.. and see if it works...

---

### Post by Cresho on 2008-11-15
ffmpeg is not needed since transcoder uses something else.  I just cant modify the tutorial anymore because it wont let me.  Never mind.  I just updated it.

---

### Post by xunilevol on 2008-12-21
how do you think i could get this to work with a usb input device to record tv.  i got tvtime working with video and audio which is piped in through svideo of a dazzle av to usb. when i did list for video i only found(i left off the o after trying 12and3)
crw-rw----+ 1 root   video    81,   0 2008-12-21 16:45 video0
crw-rw----+ 1 root   video    81, 224 2008-12-21 16:45 vbi0
 i guess i need to search for usb,but not sure what the command is. 
 ls -l /dev/usb said no such file or directory

---

### Post by Cresho on 2008-12-21
post your lsusb

---

### Post by xunilevol on 2008-12-24
ok i got it to work with vlc,pain in the butt to figure out though.i made a video to show how i recorded with vlc instead.
[http://www.youtube.com/watch?v=biQ8FXxoXN8](http://www.youtube.com/watch?v=biQ8FXxoXN8)

Bus 007 Device 004: ID 2304:0207 Pinnacle Systems, Inc. [hex] Dazzle DVC90 Video Device
Bus 007 Device 002: ID 0d49:3210 Maxtor 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Cresho on 2008-12-24
This is very good work.  Thanks for sharing.  I also record from VCR especially the ones from my grandparents which they aren't around to see anymore.

I use model "averTV Stereo"  9 dollars at amazon.com

I use the built in tv tuner for cable and the s-video or rca input with left and right in to capture audio.  output is usually dvd resolution or 4:3 aspect ratio stereo audio using transcoder xvid dvd quality bitrate with smooth 30fps.  I think ill give vlc a try..something new.  Also, I have a high definition television tuner that I might give a swing at for hd recording via inputs.  I wish i had your usb input device to try it out.  I did a few searches regarding your unit but I came out short.  Your Kernel seems to identify the device just fine.  It's now about searching for those channels for audio since you mentioned you have no audio.  in a script, you can easily open up the video and audio but its just knowing what it is.

here!  i read up on this which I found interesting
[http://forum.videohelp.com/topic341837.html](http://forum.videohelp.com/topic341837.html)

---

### Post by megamania on 2009-03-03
I managed to get your scripts to work, but just need some help sorting out an audio problem (I'm using a Hauppauge HVR 1110 card). In order to have audio on TVtime, i need to use SOX:
```

padsp sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
soxpid=$!
sleep 0.5
tvtime --device /dev/video0
kill $soxpid

```
With your script, I can finally record but I get no sound. How can I change it so that sound is recorded? I've been trying to do this for months!

Anyway, this is a great tutorial - thanks!

---

### Post by Cresho on 2009-03-03
your intrepid ibex is the problem  They dropped the ball for audio recording.

I went from hardy to intrepid and applied my patches to it and then realized pulseaudio was the issue.  Then I read this post...

Do this.  you need to unmute the analog mix and push them up on both "analog mix" and "analog mix capture"  Then try and record audio..if this failed, then in terminal do a "alsamixer"  use tab key to cycle to all and bumb up the mixer levels i suggested.  this should work, if it doesnt, then you do this last part.


Here is a fix
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I still use my hardy heron since it was somewhat affected.

The problem with intrepid ibex is it never left alpha (I call it that).  It is just and even kde4 software is dated.  Everything is supposedly going to be fixed in jaunty jackelope.  This is because of the transition from alsa to pulse audio.  Right now, Pulseaudio sucks bigtime if not configured.

if you have a mic, try recording your voice.  IF this fails, you definetly have a problem.

I stayed with my hardy heron because it is LTS, all works minus kdenlive for video editing but am using vegas video 8 on it just fine.

here is my fix for my audio problem in hardy heron which fixes analog and mic recording issues.

1.  "sudo apt-get install asoundconf-gtk"
2.  Then type "asoundconf-gtk" in terminal and set your audio card.
3.  forcing the sucker to bootfix at bootup.  Right click on the desktop and create a file and call it "asoundfix.sh" and then right click on it and give it permissions to execute.  Then paste this part into it.  Make sure you change "audigy2" to your card since audigy2 is my soundcard I am forcing to use.  I had 2 listed.  place this in a folder in your home user directory and call it fixes
open up session manager and ask it to boot the script up at startup.


```
#!/bin/bash
sleep 10 && asoundconf set-default-card Audigy2;
```

after a reboot in hardy, it all works, mixer and all and 5.1 audio is fine.

This part method does not work in intrepid ibex or jaunty jackalope.

---

### Post by megamania on 2009-03-03
> **Cresho said:**
> your intrepid ibex is the problem  They dropped the ball for audio recording.

First of all, thanks for your prompt reply.

Are you sure the problem is with 8.04 and 8.10? If you search the net for "tvtime audio sox" you'll see that it's not a problem limited to Ubuntu. It seems TVtime-related, at least for some video cards. See here, for example: [http://bbs.archlinux.org/viewtopic.php?pid=508405](http://bbs.archlinux.org/viewtopic.php?pid=508405)

I'm not having problems with audio, the mic works and even skype audio works fine. I think I used the same "pulseaudio fixes" link you gave me, when it was posted. 
Mplayer plays TV fine without a need for sox, but still I never succeeded in getting audio when recording. I also tried these scripts, which work but without audio: [http://ubuntuforums.org/showthread.php?t=338029](http://ubuntuforums.org/showthread.php?t=338029)

So my only big problem is recording analog tv or from a composite source with my card. It would be very handy and would allow me to get rid of my old videotapes.

In the end, since you look pretty expert I thought I'd ask before I apply your suggestions (I'm an expert at breaking things!). :-)


[EDIT: In case other users are interested, I finally amended the mplayer scripts and I recorded analog TV _with_ audio using an HVR 1110 card!  - I still would like to fix the audio issue with TVtime though]

---

### Post by Cresho on 2009-03-04
did you try my suggestion in keepin analog audio and the analog audio capture in the mixer open and on?  also in alsamixer?

---

### Post by sluggerjd on 2009-04-06
Hi I cannot get this to record...I have a pinnacle dazzle dvd recorder(thats literally what its called) and I have my xbox 360 plugged in and I can view it fine but I cannot record it at all and I religously looked at the guide.. So when I click on the tvtime-play button it starts up then I click on the record utton it opens for a brief moment and then closes... help please!

---

### Post by Cresho on 2009-04-06
are you running the ffmpeg from medibuntu?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

i get the same flash terminal opening and closing when my ffmpeg gets modified.  This version allowes to record.

or you can compile one with all options from source

---

### Post by gnorph on 2009-04-19
Hi
I got this one working only I can't seem to get the sound going.. Is there anyway I can check which is my default audiosource i the terminal and adjuste the settings to this? I seem to have 4 audiosources (dev/audio, audio1, audio2 and audio3)

---

### Post by Cresho on 2009-04-19
what operating system are you using?  hardy, intrepid, jaunty?

---

### Post by gnorph on 2009-04-20
8.04 Hardy

---

### Post by Cresho on 2009-04-20
The very little information I have about your hardware leaves me to believe your audio is digital.  If it was analog, I'm sure you would of figured out about the mixer and adjusted the recording level in pcm, analog mix, line in.  I have an audigy that works good with my setup.  If you have a newer soundcard with no audio mix, you could be in trouble.  Have you tried looking at your mixer and revealing all levels?

how about alsa mix?

do this, send me your from terminal
```
amixer scontents
```

---

### Post by rootedoddity on 2009-04-26
I'm having trouble recording with tvtime. I am using Jaunty and an ATI TV Wonder 200. When I go to record the program, tvtime closes, then flashes very quickly along with what appears to be a terminal window. Then when I stop recording, everything pops back up. Any advice?

---

### Post by Cresho on 2009-04-26
in terminal type tvtime and give me the text output here

---

### Post by rootedoddity on 2009-04-26
Running tvtime 1.0.2.
Reading configuration from / etc/tvtime/tvtime.xml
Reading configuration from /home/*username*/.tvtime/tvtime.xml

---

### Post by Cresho on 2009-04-26
Let me get this straight, your tvtime works but when you hit record, you get a quick flash and it wont record right?  but tvtime is working and audio as well right?

then you need to install medibuntu or change the codec you are using to something else.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Usually the quick flash of the terminal is due to the fact its not finding the codec.  Also, make sure you have the correct tv card chosen on that file you configured.

---

### Post by rootedoddity on 2009-04-26
That's correct, Tvtime work perfectly before I hit record. I'll give this a shot and let you know.

---

### Post by rootedoddity on 2009-04-26
I installed medibuntu, but it still isn't working. I was able to take a screenshot on the terminal flashing.
[[IMG]http://img408.imageshack.us/img408/2595/screenshotd.th.png[/IMG]](http://img408.imageshack.us/my.php?image=screenshotd.png)

---

### Post by Cresho on 2009-04-26
transcoder cannot open your input source as you see its in red.  give me both scripts here so i can view it.

---

### Post by rootedoddity on 2009-04-26
Record script

gnome-terminal --execute transcode -x v4l2,v4l2 \
           -M 2 \
           -i /dev/video0 \
           -p /dev/dsp \
           -w 6000 \
           -y ffmpeg \
           -F mpeg4\
           -c 02:30:00 \
           -g 720x480 \
           -f 0,4 \
           -I 1 \
           -J levels,smartyuv,pv \
           -u 100 \
           -Q 3 \
           -Z 640x480,fast \
           -E 48000,16,2 \
           --lame_preset medium \
           -o /home/rootedoddity/Desktop/tvtime-recorded/-${TODAY}-${NOW}.avi \

amixer -q set "Line" 0% mute &

Play script

#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;


I was playing around with different commands and I added the** x mplayer,mplayer** to the record script and the terminal stayed up. Here is what it said. 

transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=mplayer|A=mplayer)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x576  1.25:1  
[transcode] V: bits/pixel       | 0.579
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] warning : no option -o found, encoded frames send to "/dev/null"
[transcode] V: video buffer     | 10 @ 720x576
[import_mplayer.so] v0.0.5 (2003-03-10) (video) rendered by mplayer | (audio) rendered by mplayer
[export_null.so] v0.1.2 (2001-08-17) (video) null | (audio) null
[import_mplayer.so] mplayer -hardframedrop -vo null -ao pcm:nowaveheader -ao pcm:file="/tmp/mplayer2transcode-audio.0iUDaS"  "/dev/dsp" > /dev/null 2>&1

---

### Post by Cresho on 2009-04-28
well, I don't see you doing anything wrong.
change your play code like this


```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 -d /dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```



change your record code like this
```
#!/bin/sh
killall tvtime
sleep 4 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute &
sleep 1 && amixer -q set "Mic" 0% &
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
           -E r[,b[,c]] [44100,16,2] \
           -o /home/ranxerox/Videos/tvtime-recorded/${TODAY}-${NOW}.avi \




amixer -q set "Line" 0% mute &\
```

I just upgraded to jaunty and am fixing some commands to accomodate for the new os, so i may be a little rusty since these commands are from way back.  I am thinking your audio is not working and causing the crash.  I'm thinking transcoder is not seing your video or audio but lets start with audio.  if you dont get a "no such file or directory" then we are okay.  for the video, we will get back to that.

on my pc, I do a
```
ls /dev/dsp
```

---

### Post by rootedoddity on 2009-04-30
OK, I Changed the code to what you had, but still the same problem. I was able to get another screenshot of the terminal. [[IMG]http://img164.imageshack.us/img164/4061/screenshot91.th.png[/IMG]]("http://img164.imageshack.us/my.php?image=screenshot91.png")
I also put the -x mplayer, mplayer back in and I got this from the terminal:
```

transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
[transcode] warning : unused command line parameter detected (37/38)
[transcode] warning : argc[37]=[44100,16,2] (unused)
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=mplayer|A=mplayer)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x480  1.50:1  
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: fast resize      | Using -B 0,10,8 -X 0,0,8
[transcode] V: new aspect ratio | 640x480  1.33:1 (-B)
[transcode] V: bits/pixel       | 0.652
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse3 (sse3 sse2 sse 3dnowext 3dnow mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] V: video buffer     | 100 @ 720x480
[import_mplayer.so] v0.0.5 (2003-03-10) (video) rendered by mplayer | (audio) rendered by mplayer
[filter_resample.so] v0.1.4 (2003-08-22) audio resampling filter plugin
[filter_resample.so] options=(null)
[filter_resample.so] Invalid settings
[transcode] warning : filter plugin 'resample' returned error - plugin skipped
[filter_levels.so]: v1.0.0 (2004-06-09) Luminosity level scaler #0
[filter_levels.so]: scaling 0-255 gamma 1.000000 to 0-255
[filter_levels.so]: post-processing filter
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[filter_pv.so] v0.2.3 (2004-06-01) xv only preview plugin
[filter_pv.so] preview window 640x480
Xv: ATI Radeon Video Overlay: ports 57 - 57
Xv: grabbed port 57
Using Xv for display
[export_ffmpeg.so] v0.3.16 (2007-10-27) (video) Lavc52.11.0 | (audio) MPEG/AC3/PCM
[import_mplayer.so] mplayer -hardframedrop -vo null -ao pcm:nowaveheader -ao pcm:file="/tmp/mplayer2transcode-audio.RNUgZw"  "/dev/dsp" > /dev/null 2>&1

```

---

### Post by Cresho on 2009-05-01
okay, lets test your hardware first!

first check your video like this (replace my command regarding to video and audio with yours.)

#transcode -i /dev/video0

and then check your audio like this.

#transcode -i /dev/dsp


if both these work, then its going to be a codec issue which we will fix.  let me know what your system says on each one.  close terminal as soon as  you see it working so you can avoid junk being written to your temp directory.

---

### Post by rootedoddity on 2009-05-02
I put those in, and still the same thing happens.

---

### Post by Cresho on 2009-05-02
Okay!  We are off to a good start.  We now Know that transcoder cannot detect your hardware!  What we need to do is see where your video is as well as audio.

From your script, it shows that
```

#this should work but you say the terminal blanks out huh
transcode -i /dev/video0
#this one blanks out as well huh.  you should see it counting down times
#transcode -i /dev/dsp

```

What you need to do is in the terminal do a ls /dev and pm me the output.  Ill probably suggest something.  now its about finding the devices.
here is one thread
[https://www.linuxquestions.org/questions/linux-general-1/ati-tv-wonder-mencoder-recording-vhs-tape-313853/](https://www.linuxquestions.org/questions/linux-general-1/ati-tv-wonder-mencoder-recording-vhs-tape-313853/)



Lets get started with detecting your correct devices.

#sudo apt-get install xawtv
#xawtv -hwscan


send me your hwscan output





this one is my example:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
looking for available devices
port 280-311
    type : Xvideo, image scaler
    name : NV17 Video Texture

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : Kworld ATSC110/115
    flags: overlay capture tuner 

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : BT878 video (AVerMedia TVCaptur
    flags: overlay capture tuner 

```

---

### Post by joni8.10 on 2010-03-15
I can't get the recording function to work. TVTime-play opens up OK, then when I select tvtime-record, the tv picture disappears until I stop-recording, then the tv picture comes back on. When I go to the video folder nothing is there. What am I doing wrong?

---

### Post by Cresho on 2010-03-15
okay, please let me know what flavor of linux you are using, version, and also tuner card and soundcard.

I'm in the same boat with you and since your asking, i think it's about time i setup my rig.  I am beta testing lucid lynx so I havent configured anything yet.

---

### Post by joni8.10 on 2010-03-15
> **Cresho said:**
> okay, please let me know what flavor of linux you are using, version, and also tuner card and soundcard.

I'm in the same boat with you and since your asking, i think it's about time i setup my rig.  I am beta testing lucid lynx so I havent configured anything yet.

I'm using Ubuntu 9.04 Jaunty, and my tuner card is Sabrent PCI TV tuner/video capture with fm and remote control (SBT-TVFM). 

I can get a TV picture+sound, and composite and s-video. I don't know how to determine what the soundcard is.

---

### Post by Cresho on 2010-03-16
lets forget about the recording part at the moment.

do a  "amixer" in the terminal and paste the info here.  I want to see what you can use.

---

### Post by joni8.10 on 2010-03-16
> **Cresho said:**
> lets forget about the recording part at the moment.

do a  "amixer" in the terminal and paste the info here.  I want to see what you can use.

:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 63
  Mono:
  Front Left: Playback 63 [100%] [0.00dB] [on]
  Front Right: Playback 63 [100%] [0.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%] [3.00dB] [on]
  Front Right: Playback 25 [81%] [3.00dB] [on]
Simple mixer control 'PCM Stream',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%]
  Front Right: Playback 31 [100%]
Simple mixer control 'Synth',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 25 [81%]
  Front Right: Playback 25 [81%]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [on]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 25 [81%] [3.00dB] [on] Capture [off]
  Front Right: Playback 25 [81%] [3.00dB] [on] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

---

### Post by Cresho on 2010-03-16
This is going to be tricky.  On my audigy gamer, I have an "analog mix" which I use to record line in.  It doesnt mean you don't have this capability, we just need to find the mixer channel which allowes line in record.

can you do an alsamixer in the terminal and try and just type what you see in the title of each lever>?  on the top, can you tell me what vbersion of alsamixer you are using?  i have 1.0.21

example

i have

master
headphone
tone
bass
trebble
etc like 20 more levers.


what I want to see is under view in the top left corner, HIGHLIGHT THE terminal mixer and tab through the "capture" and see what is available.  list those lever title here.  It could be the bash script will need a forced amixer command to auto execute the line in to auto open during recording.  if the screen blanks out, this is usually the case.  also, the incorrect video input could cause your window to temporaraly pop in and out without record.  It takes a bit of time to assemble it.

---

### Post by joni8.10 on 2010-03-16
> **Cresho said:**
> This is going to be tricky.  On my audigy gamer, I have an "analog mix" which I use to record line in.  It doesnt mean you don't have this capability, we just need to find the mixer channel which allowes line in record.

can you do an alsamixer in the terminal and try and just type what you see in the title of each lever>?  on the top, can you tell me what vbersion of alsamixer you are using?  i have 1.0.21

example

i have

master
headphone
tone
bass
trebble
etc like 20 more levers.


what I want to see is under view in the top left corner, HIGHLIGHT THE terminal mixer and tab through the "capture" and see what is available.  list those lever title here.  It could be the bash script will need a forced amixer command to auto execute the line in to auto open during recording.  if the screen blanks out, this is usually the case.  also, the incorrect video input could cause your window to temporaraly pop in and out without record.  It takes a bit of time to assemble it.

I have v1.0.18
Card: Cirrus Logic CS4201
Chip: Cirrus Logic CS4297A rev 4
View: [Playback] Capture All
Item: Master [dB gain=0.00, 0.00

<Master
<Master M
<Headphone
<3D Control ---3 bars, 2 long empty ones & 1 small with MM inside
<PCM
<PCM Stre
<Synth
<Line
<CD
<Mic
<Mic Boos
<MIc Sele
<Video
<Phone

I'm not sure what you mean by HIGHLIGHT the terminal mixer and tab thru capture? BAsically, I'm looking at a bar graph which I totally don't understand.

---

### Post by Cresho on 2010-03-16
ya, just upen up the terminal and type alsamixer.  hit the Tab key and cycle through the interface till it reads capture in bold on upper left hand corner.  I want to see if you have a virtual recording lever.

another thing, you you have medibuntu installed? also transcoder or transcode>?

---

### Post by joni8.10 on 2010-03-16
> **Cresho said:**
> ya, just upen up the terminal and type alsamixer.  hit the Tab key and cycle through the interface till it reads capture in bold on upper left hand corner.  I want to see if you have a virtual recording lever.

another thing, you you have medibuntu installed? also transcoder or transcode>?

OK I've highlighted capture and this is what I get:

3D Contr
3D Contr
Line --capture L  R
CD
Mic
Video
Phone
Aux
Capture L R
Mix
Mix Mono


I installed medibuntu yesterday, and transcoder too, I think...is there a way to know for sure if it's installed properly if at all?

---

### Post by joni8.10 on 2010-03-17
Hey Cresho, what's happening? Have you given up on me already?

---

### Post by Cresho on 2010-03-17
No, I had a latenight duty.  I'm doing another session tonight.  Tomorrow, I'm getting my tv up and running to refresh.  Like said, I'm beta testing lucid lyn and my tv tuner isn't hooked up since I been doing lots of jobs.  I'm actually typing this from my android.  Tomorrow we will gp through the motions.  you seem to have your stuff together and now its just a matter of creating a script launcher to auto initiate process.  That's all.  Talk to you tomorrow.

---

### Post by Cresho on 2010-03-18
CAN YOU POST your script your using to launch?

---

### Post by joni8.10 on 2010-03-19
> **Cresho said:**
> CAN YOU POST your script your using to launch?

How do I get the script I use to launch?

---

### Post by joni8.10 on 2010-03-19
> **Cresho said:**
> CAN YOU POST your script your using to launch?

OK I got it:

#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;

---

### Post by joni8.10 on 2010-03-22
bump

---

### Post by joni8.10 on 2010-03-28
I just installed ubuntu 6.10 and have tvtime working on it. When I follow the instructions here on setting up the tvtime-buttons, the one named tvtime.sh will launch the tvtime program but will not allow me to change the video input (tv,composite,s-video). But if i launch tvtime from Applications>Sound&Video>tvtime, I can change the video input. 

I have determined that my sabrent tvtuner is supposed to be located at /dev/video0, which is what I put in tvtime.sh to launch it, but it's not working. I've tried changing the video0 to 1,2,3 but no go.

Can anyone help me locate where exactly my sabrent tvtuner is and how to get this thing working so that I can record with it?

---

### Post by Cresho on 2010-04-05
wow, wonder Why I never got email notification.  Hardy heron works with this just fine as well.  I wont be able to help you with this for a bit.  I am running kde lucid lynx at the moment and cannot do any debugging until the final release LTS by the end of this month.  I'm beta testing.

try using hardy heron if you are installing operating systems and try the scripts.  If it works, then it's a pulseaudio issue and I can't do anything about it.  We would need to wait for the final release of lucid lynx to figure out what is going on.  I am waiting on it.  I can't really help at the moment and I'll be posting an update to this.  You can try kde as it works since it has no pulseaudio.

There is no way for me to help at the moment till the final release.  Try hardy heron since that works fine.  you may need to tweak the audio system a bit to foce the audio to work since it has a handicaped pulseaudio.

---

### Post by Cresho on 2010-04-05
> **joni8.10 said:**
> I just installed ubuntu 6.10 and have tvtime working on it. When I follow the instructions here on setting up the tvtime-buttons, the one named tvtime.sh will launch the tvtime program but will not allow me to change the video input (tv,composite,s-video). But if i launch tvtime from Applications>Sound&Video>tvtime, I can change the video input. 

I have determined that my sabrent tvtuner is supposed to be located at /dev/video0, which is what I put in tvtime.sh to launch it, but it's not working. I've tried changing the video0 to 1,2,3 but no go.

Can anyone help me locate where exactly my sabrent tvtuner is and how to get this thing working so that I can record with it?

When ever you install tvtime, there is a permission issue.  you will need to adjust permission problem like this.

```
sudo chmod -R 777 ~/.tvtime
```

then play around with it and see if something works.. let me know whats going on

---

### Post by Cresho on 2010-04-05
```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```

try this after you fixed permission and was able to adjust your settings through the tvtime normal launcher in that order.  to get your svideo and your rca input working, use --input= 0 or 1 or 2.  this is how you get your inputs working.  So you might want to create 3 shortcuts.  you would leave video0 alone.  I have 2 tuners so I use video1 for analog and video0 for HDTV

after you get this part launching your tvtime, message me or post here, i resubscribed to this thread.  Then we will get your audio/video recording and all working.

---

### Post by Cresho on 2010-04-05
```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```

try this after you fixed permission and was able to adjust your settings through the tvtime normal launcher in that order.  to get your svideo and your rca input working, use --input= 1 or 2 or 3.  this is how you get your inputs working.  So you might want to create 3 shortcuts.

after you get this part launching your tvtime, message me or post here, i resubscribed to this thread so i should get the messages a bit faster.  Then we will get your audio/video recording and all working.  Remember I'm doing this off the top of my head because I don't have a working environment.  I'm beta testing and waiting for lucid lynx and ill update this thread with kubuntu and ubuntu..both different since Pulseaudio is so crazy and not consistent with kubuntu.

please post your recording script..not your launching script so i can see whats going on.

---

### Post by joni8.10 on 2010-04-25
> **Cresho said:**
> ```
#!/bin/bash
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 100% mute;
```

try this after you fixed permission and was able to adjust your settings through the tvtime normal launcher in that order.  to get your svideo and your rca input working, use --input= 1 or 2 or 3.  this is how you get your inputs working.  So you might want to create 3 shortcuts.

after you get this part launching your tvtime, message me or post here, i resubscribed to this thread so i should get the messages a bit faster.  Then we will get your audio/video recording and all working.  Remember I'm doing this off the top of my head because I don't have a working environment.  I'm beta testing and waiting for lucid lynx and ill update this thread with kubuntu and ubuntu..both different since Pulseaudio is so crazy and not consistent with kubuntu.

please post your recording script..not your launching script so i can see whats going on.

OK I reset the permission, then changed the launch script as you said to above, and tvtime will now launch BUT no sound. There's no sound when I try to launch it from Applications>Sound&Video either. So I tried to change the input to 1,2,3 and I do get *some* sound but it's very weak and has interference.

My recording script is this:

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
           -o /joni/Videos/-${TODAY}-${NOW}.avi \




amixer -q set "Line" 0% mute &

I've been playing around with my input=1,2,3 and have discovered a sort of issue in that I can view my TV on both composite and tv. This might be because I'm viewing my television through a wireless audio/video sender/receiver which is attached to my pc tvtuner (there are both coaxial and composite connections). And I have to manually switch both the tvtime input and my television input to tv in order to get the sound and video from the tv.

---

### Post by Cresho on 2010-04-25
at this point, it will be pulseaudio.  As I have issues recording audio.  Wait a few days.  I am going to test out the ubuntu LTS.  I now remember having issues with audio recording with pulseaudio.  In kubuntu, I have none.

right now, I am downloading the lts lucid lynx ubuntu and kubuntu and going to test both.  I am going to test out both gnome and kde versions and determine which is best for me.  I will try find both solutions.  The older ubuntu releases has been a pain in the neck minus hardy heron...though i did force audio to record since it also had an issue.  Expect an answer by the may 2 or 3rd since it will take me a few days to figure out what's going on.

They are saying pulseaudio is fixed in this version and that Is what I am hoping for.

---

### Post by joni8.10 on 2010-04-26
> **Cresho said:**
> at this point, it will be pulseaudio.  As I have issues recording audio.  Wait a few days.  I am going to test out the ubuntu LTS.  I now remember having issues with audio recording with pulseaudio.  In kubuntu, I have none.

right now, I am downloading the lts lucid lynx ubuntu and kubuntu and going to test both.  I am going to test out both gnome and kde versions and determine which is best for me.  I will try find both solutions.  The older ubuntu releases has been a pain in the neck minus hardy heron...though i did force audio to record since it also had an issue.  Expect an answer by the may 2 or 3rd since it will take me a few days to figure out what's going on.

They are saying pulseaudio is fixed in this version and that Is what I am hoping for.
 
Cresho,

I forgot to mention that I'm using ubuntu 9.04 now (Jaunty).
(I have 2 hard drives, one has 6.10 on it and this second HD  has 9.04 which I'm using:roll:). Should I still be having this pulseaudio problem with Ubuntu 9.04?

Another issue with sound, which I don't know if you can help with, is that when I turn off the tvtime video viewer, the sound from the tv station stays on, and keeps coming through my speakers. Is that normal, or is the sound supposed to turn off along with the video?

---

### Post by Cresho on 2010-04-27
ya, you need to tell amixer to shut down line in.  THat is what I added to my script.

Here is an update.  I just finished configuring my high definition tuner and also tuner priority and also installed my television tuner and also the tvtime software.  I now have everything working minus the recording part.

The recording portion is what I am going to work on tomorrow.  I needed to get this done so i can see how pulseaudio interacts with everything.  I know its the problem and I have a solution/theory that you can try while i dable with it tomorrow to make the scripts work on my pc...then we get yours situated.

do this.

Here do this

gedit ~/.pulse/client.conf

and paste this

autospawn = no

reboot.

now at this at the start of the script
killall pulseaudio

and at the end 

pulseaudio

then see if the audio works.  I'll be working on this tomorrow.  I'm just happy i finalized my video hardware but posting this so you can dable with it.  ill help tomorrow as soon as i get my recording going.  I am curious if you can resolve this this way myself. :P

---

### Post by Cresho on 2010-04-28
Here is a quick update.  I started messing with the recording option.  I usually use this to record my vhs tapes through my card into my pc.

What I can gather from the error codes using the newer OS, ffmpeg is having issues and as of right now, I'm experimenting with the script figruing out what works.  Nothing as of right now.  I still have a tons of codecs to go through and also will work around the pulseaudio issue.

I never had this problem in hardy heron.  I also made some changes to the script to reflect the new issues.  I'm about 80 percent done.

---

### Post by Cresho on 2010-04-28
I'm stopping today and will continue in 3 days.  The ffmpeg is missing some things and I'll use the full version of the latest ubuntu to get this working.  I don't feel like building a fresh ffmpeg today...lol

it's about 90 percent done.

---

### Post by Cresho on 2010-04-28
DONE!

I wont post script up until the release of lucid lynx and also fish through the 10 plus files worth of scripts i used to figure out what happened and what works.

I'm going to streamline the script and eliminate depreciated portions.

recording and everything works in lucid lynx.  I think I spent 3 hours today figuring out what happened.

The reality is my post worked for the hardy heron.  Wasn't updated until now.  So expect a post in a few days.

---

### Post by joni8.10 on 2010-04-29
> **Cresho said:**
> ya, you need to tell amixer to shut down line in. 

Is there a way to go into the tvtime program itself and tell amixer to shut down line in?



> **Cresho said:**
> 

now at this at the start of the script
killall pulseaudio

and at the end 

pulseaudio

then see if the audio works. 

I'm assuming you're talking about the tvtime.sh script here, right?

---

### Post by Cresho on 2010-05-04
OKAYYYY!!!!

it's done.

Lil history here...short version.

I created these sets of commands for my hardy heron....worked great!  Flash forward into the future.  They suck and will probably suck for others.

issues?
transcode
ffmpeg
pulseaudio
new drivers
new kernel

So what was fixed?  Nothing really.  the new software includes pulseaudio fixes and they work.  Previous attempts was futile.

So what does the script look like?  I have a set of 4
1.  launches tvtime
2.  or records line in
3.  records tvtime
4.  closes transcoder and shuts down or mutes line in.

here they are and adjust them accordingly.

They specifically work for lucid lynx under UBUNTU and not KUBUNTU.  I barely got this working here but you can give it a whirl.

tvtime launcher
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute;
```
tvtime launch video in
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=1 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute;
```
tvtime records in
```
#!/bin/sh
killall tvtime
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
sleep 4 && amixer -q set "Line" 100% unmute
sleep 1 && amixer -q set "Analog Mix" 100% unmute
#####################################################################
gnome-terminal --execute transcode -x v4l2,v4l2 \
-M 2 \
-i /dev/video0 \
-p /dev/dsp \
-w 6000 \
-y ffmpeg \
-F mpeg4 \
-g 720x420 \
-f 0,4 \
-I 1 \
-J resample,levels,smartyuv,pv \
-u 100 \
-Q 3 \
-Z 640x480,fast \
-E 48000,16,2 \
-o ~/-${TODAY}-${NOW}.avi \
#####################################################################

```
tvtime stop recording
```
#!/bin/sh
killall transcode
sleep 1 && amixer -q set "Line" 100% unmute;
sleep 1 && amixer -q set "Analog Mix" 100% unmute;
tvtime --g 480x360 --vbidevice=/dev/vbi0 --device=/dev/video0 --frequencies=us-cable --input=0 --norm=NTSC
sleep 1 && amixer -q set "Line" 0% mute
```






Here is an interesting thing.  create a bash script and put this in

```
#!/bin/sh
killall tvtime
TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
sleep 4 && amixer -q set "Line" 100% unmute
sleep 1 && amixer -q set "Analog Mix" 100% unmute
#####################################################################
transcode -x v4l2,v4l2 \
-M 2 \
-i /dev/video0 \
-p /dev/dsp \
-w 6000 \
-y ffmpeg \
-F mpeg4 \
-g 720x420 \
-f 0,4 \
-I 1 \
-J resample,levels,smartyuv,pv \
-u 100 \
-Q 3 \
-Z 640x480,fast \
-E 48000,16,2 \
-o ~/-${TODAY}-${NOW}.avi \
#####################################################################
```

create a test.sh and paste the above.  open a terminal and cd into the directory of the file.  execute in terminal like this "./test.sh" and see the output.  paste output here.

make sure the sh script is executable.  We can see what is conflicting.  I must of spent tons figuring out what was going on.  It wasn't a problem.  It was 4 plus different issues including pulseaudio which I assumed was broken in lucid lynx but its working fine and they must of compiled transcode to work with it.  my tv recording now works and also my line in video works and also svideo line in works...not created a script...yet but its easy.

issues?  never got these working in karmic or jaunty.  I went from hardy streight to lucid lynx

---

### Post by joni8.10 on 2010-05-10
> **Cresho said:**
> OKAYYYY!!!!


create a test.sh and paste the above.  open a terminal and cd into the directory of the file.  execute in terminal like this "./test.sh" and see the output.  paste output here.

make sure the sh script is executable.  We can see what is conflicting.  I must of spent tons figuring out what was going on.  It wasn't a problem.  It was 4 plus different issues including pulseaudio which I assumed was broken in lucid lynx but its working fine and they must of compiled transcode to work with it.  my tv recording now works and also my line in video works and also svideo line in works...not created a script...yet but its easy.

issues?  never got these working in karmic or jaunty.  I went from hardy streight to lucid lynx

Cresho,
I'm using ubuntu 9.04 and still can't get this thing to record. It is launching properly now:)
Could you explain for a beginner how to cd into the directory of that bash file above so as to see what's conflicting? 
Thanks.

---

### Post by Cresho on 2010-05-10
cd ~/          

or cd /home/"username"/ no quotes.


ls
./test.sh

then post output here.  this will give me all the errors you are having.

---

### Post by joni8.10 on 2010-05-11
> **Cresho said:**
> cd ~/          

or cd /home/"username"/ no quotes.


ls
./test.sh

then post output here.  this will give me all the errors you are having.

Cresho,
I created a test.sh on my desktop and put that script in it, now I don't know what steps to do next. When I open the terminal and type cd /home/username/desktop/test.sh it says there's no such file. What am I doing wrong here?

---

### Post by Cresho on 2010-05-11
> **joni8.10 said:**
> Cresho,
I created a test.sh on my desktop and put that script in it, now I don't know what steps to do next. When I open the terminal and type cd /home/username/desktop/test.sh it says there's no such file. What am I doing wrong here?

cd ~/Desktop

./test.sh

---

### Post by joni8.10 on 2010-05-11
> **Cresho said:**
> cd ~/Desktop

./test.sh

Thanks Cresho! Here's what I got:

tvtime: no process killed
amixer: Unable to find simple control 'Analog Mix',0

transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
[transcode] auto-probing source /dev/video0 (failed)
[transcode] V: import format    | unknown  (V=v4l2|A=v4l2)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x420  1.71:1  
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: fast resize      | requested but can't be used (W or H mod 8 != 0)
[transcode] V: zoom             | 640x480  1.33:1 (Lanczos3)
[transcode] V: bits/pixel       | 0.652
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG layer-3 [48000,16,2]  128 kbps
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse (sse mmxext mmx asm C)
[transcode] V: IA32/AMD64 accel | using sse memcpy
[transcode] V: video buffer     | 100 @ 720x480
[import_v4l2.so] v1.3.5 (2005-03-11) (video) v4l2 | (audio) pcm
[filter_resample.so] v0.1.4 (2003-08-22) audio resampling filter plugin
[filter_resample.so] options=(null)
[filter_resample.so] Frequencies are too similar, filter skipped
[transcode] warning : filter plugin 'resample' returned error - plugin skipped
[filter_levels.so]: v1.0.0 (2004-06-09) Luminosity level scaler #0
[filter_levels.so]: scaling 0-255 gamma 1.000000 to 0-255
[filter_levels.so]: post-processing filter
[filter_smartyuv.so] (MMX) 0.1.4 (2003-10-13) Motion-adaptive deinterlacing
[filter_pv.so] v0.2.3 (2004-06-01) xv only preview plugin
[filter_pv.so] preview window 640x480
Xv: NV Video Blitter: ports 57 - 88
Xv: grabbed port 57
Using Xv for display
[export_ffmpeg.so] v0.3.16 (2007-10-27) (video) Lavc52.11.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so]: v4l2 audio grabbing
[import_v4l2.so]: v4l2 video grabbing
[import_v4l2.so]: resync disabled
[import_v4l2.so]: video grabbing, driver = saa7134, card = Sabrent SBT-TVFM (saa7130)
[import_v4l2.so]: Pixel format conversion: YVU420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so]: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[import_v4l2.so]: checking colour & framerate standards: [PAL] 
[import_v4l2.so]: receiving 25 frames / sec
[import_v4l2.so]: frame size: 720x420
[import_v4l2.so]: cropcap bounds: 720x578 +0+46

[import_v4l2.so]: cropcap defrect: 720x576 +0+48
[import_v4l2.so]: cropcap pixelaspect: 54/59
[import_v4l2.so]: default cropping: 720x576 +0+48
[import_v4l2.so]: 9 buffers available
[export_ffmpeg.so] Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).
[export_ffmpeg.so]: WARNING: Interlacing parameters unknown, use --encode_fields
[export_ffmpeg.so]: INFO: No profile selected
[export_ffmpeg.so] Neither './ffmpeg.cfg' nor '~/.transcode/ffmpeg.cfg'
[export_ffmpeg.so] found. Default settings will be used instead.
[export_ffmpeg.so]: INFO: Starting 1 thread(s)
[export_ffmpeg.so]: INFO: Set display aspect ratio to input
Audio: using new version
Audio: using lame-3.98
[import_v4l2.so]: VIDIOC_DQBUF: Input/output error0:00:01, (98| 1| 0) 
recover DQBUF: Input/output error
recover DQBUF: Input/output error
recover DQBUF: Input/output error
recover DQBUF: Input/output error  3.75 fps, EMT: 0:00:01, (97| 1| 0) 
recover DQBUF: Input/output error  3.73 fps, EMT: 0:00:01, (96| 1| 0) 
recover DQBUF: Input/output error  3.73 fps, EMT: 0:00:01, (94| 1| 0) 
recover DQBUF: Input/output error  3.71 fps, EMT: 0:00:01, (92| 1| 0) 
recover DQBUF: Input/output error  3.72 fps, EMT: 0:00:01, (90| 1| 0) 
^Ccoding frames [000000-000143],   3.78 fps, EMT: 0:00:04, ( 0| 0| 0) 
[transcode] (sighandler) SIGINT received

---

### Post by Cresho on 2010-05-12
video for linux cannot see your video0 to start.  Do you see an image when you run it?

Also, you dont have analog mixer so this is just your soundcard.  We may need to switch mixer setting.

try video1 or 2 or 3 to start.  Your tuner may be digital and this could be a problem.

[transcode] auto-probing source /dev/video0 (failed)
this tells me this isnt going to work for your tuner.  if you can resolve this part, then we can move on to your other problem.  i dont know what yourt videocard uses.

here look at this

[http://www.linuxquestions.org/questions/linux-general-1/recording-from-video-card-with-transcode-no-sound-490143/](http://www.linuxquestions.org/questions/linux-general-1/recording-from-video-card-with-transcode-no-sound-490143/)




hmmm...try playing with these functions

-x v4l2,v4l2 -i /dev/video32 \
 -p /dev/video24 \
 -y ffmpeg -F mpeg4 \

---

### Post by joni8.10 on 2010-05-12
> **Cresho said:**
> video for linux cannot see your video0 to start.  Do you see an image when you run it?

Also, you dont have analog mixer so this is just your soundcard.  We may need to switch mixer setting.

try video1 or 2 or 3 to start.  Your tuner may be digital and this could be a problem.

[transcode] auto-probing source /dev/video0 (failed)
this tells me this isnt going to work for your tuner.  if you can resolve this part, then we can move on to your other problem.  i dont know what yourt videocard uses.

here look at this

[http://www.linuxquestions.org/questions/linux-general-1/recording-from-video-card-with-transcode-no-sound-490143/](http://www.linuxquestions.org/questions/linux-general-1/recording-from-video-card-with-transcode-no-sound-490143/)




hmmm...try playing with these functions

-x v4l2,v4l2 -i /dev/video32 \
 -p /dev/video24 \
 -y ffmpeg -F mpeg4 \

Cresho,
--I don't see an image when I run it from the terminal, but, the very first time I ran it just by double clicking test.sh on my desktop and briefly there was an image for about 5 seconds that was mostly covered with a green layer.

--Thanks for that link to linuxquestions but it's way too complicated for me. 

--I'd try playing with those functions you wrote about in your last post but I don't have a clue as to how to "play" with them. Like do I run them as commands in a terminal or what?

--Cresho, is xawtv very much different from tvtime? I can at least get xawtv to record video but not both video and sound together.:confused:

---

### Post by Milos_SD on 2010-05-17
I tried script from the page 7 named test.sh, it records video and sound, but sound is just a static and if I turn the volume up, I can hear a very weak sound. 
Here is the output that test.sh shows:
```
./test.sh 
amixer: Unable to find simple control 'Line',0

amixer: Unable to find simple control 'Analog Mix',0

transcode v1.1.5 (C) 2001-2003 Thomas Oestreich, 2003-2009 Transcode Team
[transcode] V: auto-probing     | /dev/video0 (OK)
[transcode] V: import format    | (null) in  (module=v4l2)
[transcode] A: auto-probing     | /dev/dsp (OK)
[transcode] A: import format    | PCM in  (module=v4l2)
[transcode] V: AV demux/sync    | (2) initial MPEG sequence / enforce frame rate
[transcode] V: import frame     | 720x420  1.71:1  encoded @ UNKNOWN
[transcode] V: de-interlace     | (mode=1) interpolate scanlines (fast)
[transcode] V: fast resize      | requested but can't be used (W or H mod 8 != 0)
[transcode] V: zoom             | 640x480  1.33:1 (Lanczos3)
[transcode] V: bits/pixel       | 0.652
[transcode] V: decoding fps,frc | 29.970,4
[transcode] V: video format     | YUV420 (4:2:0) aka I420
[transcode] A: import format    | 0x1     PCM          [48000,16,2]
[transcode] A: export format    | 0x55    MPEG ES Layer 3 [48000,16,2]  128 kbps
[transcode] V: export format    | unknown (module dependant)
[transcode] V: encoding fps,frc | 29.970,4
[transcode] A: bytes per frame  | 6408 (6406.400000)
[transcode] A: adjustment       | -1600@1000
[transcode] V: IA32/AMD64 accel | sse3 sse2 sse mmx cmove asm 
[transcode] V: video buffer     | 10 @ 720x480 [0x2]
[transcode] A: audio buffer     | 10 @ 48000x2x16
[import_v4l2.so] v1.6.2 (2008-10-25) (video) v4l2 | (audio) pcm
[filter_resample.so] v0.1.6 (2007-06-02) audio resampling filter plugin using libavcodec
[filter_resample.so] resampling: 48000 Hz -> 48000 Hz
[filter_resample.so] critical: Frequencies are identical, filter skipped
[transcode] warning: Initialization of filter resample failed, skipping.
[filter_levels.so] instance #1
[filter_levels.so] v1.2.0 (2007-06-07) Luminosity level scaler
[filter_levels.so] scaling 0-255 gamma 1.000000 to 0-255 (post-process)
[filter_smartyuv.so] (MMX) 0.1.6 (2007-05-31) Motion-adaptive deinterlacing
[filter_pv.so] v0.2.3 (2004-06-01) xv only preview plugin
[filter_pv.so] preview window 640x480
[pv.c] Xv: NV17 Video Texture: ports 361 - 392
[pv.c] Xv: grabbed port 361
[pv.c] Using Xv for display
[export_ffmpeg.so] v0.3.18 (2008-11-29) (video) Lavc52.20.0 | (audio) MPEG/AC3/PCM
[import_v4l2.so] warning: bad pixel format conversion: YUV420 [planar] -> YUV420 [planar] (no conversion)
[import_v4l2.so] warning: bad pixel format conversion: YVU420 [planar] -> YUV420 [planar]
[import_v4l2.so] warning: bad pixel format conversion: YUV422 [planar] -> YUV420 [planar]
[import_v4l2.so] warning: bad pixel format conversion: YUV411 [planar] -> YUV420 [planar]
[import_v4l2.so] warning: driver does not support setting parameters (ioctl(VIDIOC_S_PARM) returns "Invalid argument")
[export_ffmpeg.so] Using FFMPEG codec 'mpeg4' (FourCC 'DIVX', MPEG4 compliant video).
[export_ffmpeg.so] No profile selected
[export_ffmpeg.so] warning: Error opening configuration file ./ffmpeg.cfg: No such file or directory
[export_ffmpeg.so] Starting 1 thread(s)
[export_ffmpeg.so] Set display aspect ratio to input
[export_ffmpeg.so] warning: Usage of this module for audio encoding is deprecated.
[export_ffmpeg.so] warning: Consider switch to export_tcaud module.
[transcode] Audio: using lame-3.98.2
^C[transcode] (sighandler) SIGINT received0:00:13,  ( 9| 0|11) 
[decoder.c] cancelling the import threads
[import_v4l2.so] Totals: sequence V/A: 393/402, frames C/D: 0/0

[transcode] encoded 392 frames (0 dropped, 0 cloned), clip length  13.08 s


```

---

### Post by Cresho on 2010-05-21
Milo, yours seems to be working fine.  I am guessing you have are using pulseaudio and also your onboard audio card.  You need an audio card that can grab audio mixed or analog mix.  or audio that can grab audio from none specific input.  most prefferably analog mix.  what I suggest is.

1. start recording.  open up your mixer or "alsamixer" in terminal and play with the slides.  play back your video recording and just listen if any audio was grabbed.  I can't give you specifics on anything.  TUtorial are for people who have the hardware and operating system setup properly.

2. open pulseaudio and play with the line in.  You probably don't have the mixer setup properly in the interface.  It is still buggy you know so you need to play with pulseaudio mixer as well.

I have mines totally disabled and am running it directly from alsamixer.

---

### Post by Milos_SD on 2010-05-22
My TV Card have audio cable attached to motherboard "CD IN". Maybe that is the problem. Also look at this:

```
amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [on]
  Front Right: Capture 65536 [100%] [on]

```

---

### Post by Cresho on 2010-05-23
damn!  that is a problem.
I use an audigy 2 gamer pci card.  I never tried using my motherboard audio for sound.
this is mines

```
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Tone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Bass',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 19 [48%]
  Front Right: 19 [48%]
Simple mixer control 'Treble',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 40
  Front Left: 31 [78%]
  Front Right: 31 [78%]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 73 [73%] [-10.80dB] Capture 67 [67%] [-13.20dB]
  Front Right: Playback 73 [73%] [-10.80dB] Capture 67 [67%] [-13.20dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 80 [80%] [-8.00dB]
  Front Right: Playback 80 [80%] [-8.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 90 [90%] [-4.00dB]
  Front Right: Playback 90 [90%] [-4.00dB]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'Side',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100
  Mono:
  Front Left: Playback 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB]
Simple mixer control 'Synth',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958 Optical',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'IEC958 Optical Raw',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Aux2',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'Analog Capture Boost',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Audigy Analog/Digital Output Jack',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Audigy CD',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 0 [0%] [-99999.99dB]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
```

the ones I use in particular are these:

```

Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 0 [0%] [-99999.99dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
  Front Right: Playback 100 [100%] [0.00dB] Capture 100 [100%] [0.00dB]
Simple mixer control 'PCM',0
  Capabilities: pvolume cvolume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 100 Capture 0 - 100
  Front Left: Playback 73 [73%] [-10.80dB] Capture 67 [67%] [-13.20dB]
  Front Right: Playback 73 [73%] [-10.80dB] Capture 67 [67%] [-13.20dB]
Simple mixer control 'PCM Center',0
  Capabilities: pvolume pvolume-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB]
Simple mixer control 'PCM Front',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 100

```

---

### Post by Milos_SD on 2010-05-23
I compiled Alsa 1.0.23. My friend that has a lot older PC, and use integrated sound card, have a lot more amixer outputs/inputs. So maybe the problem is in compiled alsa?

---

### Post by Cresho on 2010-05-23
ya thats what I was suggesting.  Instead of using amixer to activate a channel, record a television show and use alsamixer in terminal to adjust the recording levels.  Find which one works that way.  play back the video file and listen for audio.  You just need to play with the mixers and figure out what works.

---

### Post by Cresho on 2010-05-23
try mencoder

[http://www.uluga.ubuntuforums.org/showthread.php?t=576656](http://www.uluga.ubuntuforums.org/showthread.php?t=576656)

in the meantime while i do a little homework.

---

### Post by Milos_SD on 2010-05-24
I made it work. This is how:

- edit /etc/pulse/clients.conf
- uncomment line autospawn=yes and change it to autospawn=no
- cut my custom .asoundrc file somewhere
- kill pulseaudio
- start recording
- after recording is done, I put everthing back as it was before, and start pulseaudio again. :)

---

### Post by Cresho on 2010-05-24
haha!

I should of known you didnt have it configured.

I have this as well on my system.

Glad you figured it out.
[http://kubuntuforums.net/forums/index.php?topic=3111692.0](http://kubuntuforums.net/forums/index.php?topic=3111692.0)

that above is my tutorial getting nvidia and audigy working under kde 4 perfectly.  You should try and script it so it works perfectly and without you needing to do all those crazy stuff.

---

### Post by themickeynick on 2011-06-27
When i ran the test.sh this is what happened. I'm such a noob. I would like some help plz
also the record button just shut the window.
```
amixer: Unable to find simple control 'Line',0

amixer: Unable to find simple control 'Analog Mix',0

[transcode] critical: Invalid filename "/dev/dsp": No such file or directory

```

---

### Post by BicyclerBoy on 2011-06-28
AFAIK
Changes with respect to v4l & v4l2 support in latest kernels *could *be to blame.
(Only could)

To get the analogue recording to work with the new kernels (natty) you may need the latest tvtime (from LinuxTV).

[http://www.kernellabs.com/blog/?p=1462](http://www.kernellabs.com/blog/?p=1462)

Are you trying to use TvTime for the first time ?
Are you using natty ?
Has this problem just occurred ?
Have you been using TvTime without problems before now ?

You could try to roll your kernel back by using the Grub boot menu..

---

