---
title: "Capturing analog CAM recorder mplayer sync sound"
date: 2010-07-18
forum: Multimedia Software
---

### Post by klaas.holwerda on 2010-07-18
Capturing S-video from analog CAM recorder with mencoder and syncing sound using avifix.

I finally succeeded to capture my Analog CAM Hi-8 videos, and to sync sound afterwards.

Of course you need a capture card, which captures. I found xawtv helpful at getting that far.
When i managed to see video using xawtv, it took me a while to discover that S-video (which is on input channel of my capture card), does not contain sound.
Simple because S-video is only the video signal. Therefore the sound needs to come from the CAM recorder with a separate cable to your sound card, via the line or mic input.

So how does mencoder capture the sound and join it into the output AVI file encode with mpeg4? The important thing is to find the right input from the alsa sound system. The next gives you a list of what you have, and eventually will lead you to something like adevice=hw.0,0 on the mencoder command line.

```

aplay -l

```But the most important thing is to set the line input from your sound card as being capctured. The microphone input is to sensitive, which result in distortion, better us line in. After playing a bit with commands like this:
```

amixer sset Line mute cap 

```I found that alsa-mixer is one of the view mixer tools which show my line in, and gives me the option to capture from it. All the others (gnome-alsamixer, ubuntu its own sound preferences, really don't work for me).
So in the alsamixer,  you have so called views (F3 for the playback view, and F4 for the capture view). In the capture view, i see two capture input sliders, and next to them (input source, input source 1) there you can set which inputs ( mic ,line, CD  should  be used for those capture inputs. This approach made me get sound from my Line input. Also good to know that capture levels are independent from the playback levels. So your capture level for the line input, is what defines the level of the recorder sound on the encoded video, and the playback line level settings is what you hear directly.

With mplayer you can test if al is set right:

```

mplayer tv:// -tv driver=v4l2:norm=PAL:input=3:amode=1:width=640:height=480:device=/dev/video1 -v

```With mplayer using its mencoder i capture with this line:

```

mencoder tv:// -tv driver=v4l2:norm=PAL:input=3:amode=0:width=640:height=480:device=/dev/video1:alsa:forceaudio:amode=0:adevice=hw.0,0 -fps 25 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=6000 -vf crop=624:464:6:4,pp=lb -oac mp3lame -lameopts cbr:br=64:mode=3 -mc 2.0  -o myOutput.avi

```Important in here is to know that PAL is 640x480, and that a vbitrate=6000 is needed to not end up with squares in the output mpeg4 encode AVI result.
The clipping and de-interlacing is done with -vf crop=624:464:6:4,pp=lb. With out the crop, you end up with black/flickery sides in the video. With out de-interlacing quality is bad too. The crop setting width end height must be divide-able by 16 (mpeg needs it). The -mc 2.0 is to have mencoder do its best to sync audio with video.

Oke i now had a myOutput.avi file, containing sound and video. And could simply play it with ```
mplayer  myOutput.avi.
```But at the beginning of the video, the sound is in sync, and at the end the sound is seconds out of sync. After a long search and trial on problems with mplayer and audio sync and delay, i found no cure. Using mencoder to add audio delay, or to change frame per second, all did not solve it. Audio delay only works if its constant along the whole video. Trying to change -ofps with 
```
mencoder -ofps 24.995 -oac copy -ovc copy input.avi -o output.avi
```throws away/adds frames, but does not solve it, and results in a bad video.
Then i found avifix ( [http://www.transcoding.org/](http://www.transcoding.org/) ), with that tools you can change the header information of the AVI file, where the frames per second is store too. It does not change the video or sound itself, only the AVI container parameter. 

For example: 
   - if your sound is seconds ahead of your video signal, you must increase the FPS (e.g from 25 to 25.005).
   - if your sound is seconds after of your video signal, you must decrease the FPS (e.g from 25 to 24.995). 

Using avifix, you can experiment until you have the sound in sync:
The next id set it to 24.87 frames per second.

```

avifix -i reits-parijs.avi -f 2487,100

```To conclude: somehow the captured audio  getting out of sync, is related to not having exactly 25 fps, and adjusting it will get the sound in sync. Why and how the sound is not kept in sync by mencoder, is not clear to me.

---

### Post by no2498 on 2010-07-18
id like to ask you to re start this as a

s video how to and mark it solved 

have seen a few asking how to do it

thank you

---

