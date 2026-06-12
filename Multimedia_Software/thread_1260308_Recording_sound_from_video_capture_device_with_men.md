---
title: "Recording sound from video capture device with mencoder"
date: 2009-09-07
forum: Multimedia Software
---

### Post by philstovell on 2009-09-07
I've recently bought a video capture card - a Kworld USB2800D. I'm trying
to convert some ancient VHS home videos.

I can record the video OK, but all I get is silence. I can record the
sound with gnome-sound-recorder OK.

When I play the recorded video with Totem, properties for the audio is
greyed out as N/A.

Here's the last mencoder command line I tried (from
[http://forum.videohelp.com/topic307679.html](http://forum.videohelp.com/topic307679.html) plus googling):

```
mencoder -tv
norm=PAL:driver=v4l2:width=720:height=576:input=1:fps=25:alsa:audiorate=128000
tv:// -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf
pp=lb/ha/va/dr,hqdn3d,harddup -srate 48000 -af lavcresample=48000
-lavcopts
vcodec=mpeg2video:vrc_buf_size=1500:vrc_maxrate=8000:vbitrate=7000:keyint=15:aspect=4/3
-oac lavc -srate 44100 -lavcopts acodec=mp3:abitrate=128 -o capture.mpg

```

Can anyone give me any suggestions?

Cheers, Phil.

---

### Post by spegru on 2009-11-20
I've just been doing this. For sound to work I had to make sure that the recording settings were correct within the ubuntu sound settings.
You may have to change preferences so that the recording tab is shown in order to do this properly
I started with Line-in but found the levels were much too high from my vhs machine (I think they may be intended to driver speakers directly), so I changed to the mic input and adjusted the level down to a sensible level.

---

### Post by philstovell on 2009-11-24
Thanks for the reply.

I'm going to try again shortly, after I've upgraded to Jaunty.

Could I ask what parameters you give to mencoder, please?

Cheers, Phil.

---

### Post by rich86 on 2009-11-28
i was having the same issue with the audio. Just to be clear how did you set mencoder to listen to the specific input?

Did you go through:  System > Preferences > Sound > Input  and then select connector?

---

### Post by philstovell on 2009-11-29
Yes, I did run through the hoops you suggested. I used the sound recorder application to check I had sound coming in. That worked, I couldn't get mencoder to record sound.

I think sound in Ubuntu needs a lot of work, it is very confusing with ALSA, OSS and PulseAudio and lots of options on the controls.

Thanks for the input.

---

