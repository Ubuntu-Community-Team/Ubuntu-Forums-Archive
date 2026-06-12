---
title: "avi File Conversion - brandless mp3/mp4 touch screen player."
date: 2008-07-15
forum: Multimedia Software
---

### Post by JuzzyDee on 2008-07-15
Hi all, 

Im hoping for some help regarding one of those new iClone touch things that seem to be all the rage at the moment. The supplied software is.. surprise surprise, windows only. I figured that would be ok though, since it appears to use xvid and mencoder to do the dirty work anyway. Figured I could just work it out. 

Problem is my video files don't play once placed on the player. I have tried to figure out why by using comparison of the vendor supplied demonstration .avi file that plays no problems on the player.

I am using the following to generate my avi file. 

 ```
 mencoder InFile.avi -ovc xvid -xvidencopts bitrate=700 -oac twolame -twolameopts br=128 -ofps 20 -vf scale=320:240 -aspect 4:3 -o OutFile.avi
```

The file either freezes the player if it's the only video file on the player, or skips and plays the demo file if both are in place.

Here is the output of idvid for each of the files:



```

/*   SKIPPING/FREEZING FILE   */

Analyzing file: 'TestFile.avi'. This may take several minutes...
=========================================================
               File: TestFile.avi
              Width: 320 pixels
             Height: 240 pixels
       Aspect ratio: 1.33:1
             Frames: 1000
           Duration: 00:00:50 hours/mins/secs
          Framerate: 20.000 frames per second
       Video format: XVID
      Video bitrate: 435328 bits per second
---------------------------
Audio track 1 (Stream 0.1, AID 0):
---------------------------
              Codec: mp2
            Bitrate: 0000 bits per second
      Sampling rate: 48000 Hz
=========================================================
Audio is compliant with the following formats:
  128000 bps 48khz MP2 DVD (MPEG audio)
Video is compliant with the following formats:
  Not compliant with (S)VCD or DVD
This video does not seem to be compliant with (S)VCD or DVD
standards. If you burn it to a video disc, it may not work.
=========================================================


/* WORKING FILE  */
Analyzing file: '2.8     .avi'. This may take several minutes...
=========================================================
               File: 2.8     .avi
              Width: 320 pixels
             Height: 240 pixels
       Aspect ratio: 1.33:1
             Frames: 4982
           Duration: 00:04:09 hours/mins/secs
          Framerate: 20.000 frames per second
       Video format: XVID
      Video bitrate: 598624 bits per second
---------------------------
Audio track 1 (Stream 0.1, AID 0):
---------------------------
              Codec: mp2
            Bitrate: 0000 bits per second
      Sampling rate: 44100 Hz
=========================================================
Audio is compliant with the following formats:
  2-channel 128000 bps SVCD
Video is compliant with the following formats:
  Not compliant with (S)VCD or DVD
This video does not seem to be compliant with (S)VCD or DVD
standards. If you burn it to a video disc, it may not work.
=========================================================
8 -ofps 20 -vf scale=320:240 -aspect 4:3 -o OutputVid.avi
```

The players themselves seem to be pretty popular on ebay and youtube alike using a term of '2.8" TFT touch screen' or similar. It's driving me mental so if anyone can help I would be very very appreciative.

---

### Post by JuzzyDee on 2008-07-16
well, after setting the -srate flag to 44100, the demo file and test file look identical in idvid output. Still nothing. Does anyone know how i can compare these files in depth tp find what's different?

---

### Post by Creative2 on 2008-07-16
hello , unlucky i have lost my data partition so.. i lost my newer version of fuoco with the new command line anyway on my forum i have recover this 

[http://fuocotools.byethost13.com/index.php?topic=126.msg142#msg142](http://fuocotools.byethost13.com/index.php?topic=126.msg142#msg142)

and because byethost is a **** free web hostin i have to write here :


mencoder INPUT -ofps 20 -vf-add scale=320:240 -vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=400:max_bframes=0:quant_type=h263:me_quality=4 -oac lavc -lavcopts acodec=mp2:abitrate=128  -o OUTPUT


you can add this command line manually to fuoco... it's very easy :)

---

### Post by JuzzyDee on 2008-07-16
Thankyou so much!!!! I will give this a go tonight and hopefully be in business

---

