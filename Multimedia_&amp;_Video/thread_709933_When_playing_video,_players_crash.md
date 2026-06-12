---
title: "When playing video, players crash"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by juanm on 2008-02-27
Hello everybody,
I hope someone can help me.
I have two videos that I need to see, both in wmv. All the info about them is pasted below, extracted with MediaInfo. The problem is when I try to play them, the player immediately shuts down. It doesn't matter if it's xine, vlc, totem or Mplayer, I have tried everything. I have also tried uninstalling and then reinstalling w32 codecs, transcoding the files into other containers and with other codecs, and nothing, the same thing  always happens: as soon as I click play the player tries, but immediately shuts down. The only thing out of the ordinary is that the videos have a higher resolution than the one I usually handle. Could that be the problem? And if it is, how should I handle it?
Thank you.

These are the properties of the first video.
Format               : Windows Media
File size            : 907 MiB
PlayTime             : 1h 15mn
Bit rate             : 1672 Kbps
Movie name           : 001
Performer            :
Copyright            : 
Comment              :
Rating               : 
Date_Created         : UTC 1930-03-05 
VBR Peak             : 7000000
Buffer Average       : 28096

Video #0
Codec                : WMV3
Codec/Info           : Windows Media Video 9
Bit rate             : 1510 Kbps
Width                : 1280 pixels
Height               : 720 pixels
Aspect ratio         : 16/9
Resolution           : 24 bits

Audio #0
Codec                : WMA2
Codec/Info           : Windows Media Audio 2
Bit rate             : 128 Kbps
Channel(s)           : 2 channels
Sampling rate        : 44 KHz

And these are the properties of the second video

Format               : Windows Media
File size            : 582 MiB
PlayTime             : 48mn 38s
Bit rate             : 1672 Kbps
Movie name           : 002
Performer            :
Copyright            : 
Comment              :
Rating               :
Date_Created         : UTC 1930-08-16 
VBR Peak             : 7000000
Buffer Average       : 33421

Video #0
Codec                : WMV3
Codec/Info           : Windows Media Video 9
Bit rate             : 1510 Kbps
Width                : 1280 pixels
Height               : 720 pixels
Aspect ratio         : 16/9
Resolution           : 24 bits

Audio #0
Codec                : WMA2
Codec/Info           : Windows Media Audio 2
Bit rate             : 128 Kbps
Channel(s)           : 2 channels
Sampling rate        : 44 KHz

---

### Post by jan quark on 2008-02-29
please start the player via the terminal and post the error messages that will be displayed

just type into the terminal 
```
vlc
```

and run the movie.

---

### Post by eye208 on 2008-02-29
You are using desktop effects (Compiz) and these make your XVideo overlay non-functional.

This problem has been discussed here probably a thousand times. Use the search function.

---

### Post by juanm on 2008-03-01
Thanks jan quark, as soon as I was able to see what was the problem I was able to solve it. It was bad allocation. I changed the output device from default to X11.
eye208, I've never used compiz because it downgrades performance. I'm not very into gadgets.

---

### Post by Izek on 2008-06-25
> **juanm said:**
> Thanks jan quark, as soon as I was able to see what was the problem I was able to solve it. It was bad allocation. I changed the output device from default to X11.
eye208, I've never used compiz because it downgrades performance. I'm not very into gadgets.

And how would I do that? gstreamer isn't a valid terminal function, so how would I configure that?

---

### Post by Tomatz on 2008-06-25
You can only switch to x11 in vlc or mplayer, not gstreamer (there are probably others).

Install them via synaptic (or apt)

;)

---

### Post by Izek on 2008-06-25
> **Tomatz said:**
> You can only switch to x11 in vlc or mplayer, not gstreamer (there are probably others).

Install them via synaptic (or apt)

;)

Sorry, but I'd rather stick with totem/Windows Media Player. =/ Guess I'll just have to wait until Vista/Seven becomes low in price, or when I get a new PC with more RAM and stuff and/or when ReactOS becomes stable for real hardware.

Also...

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Error running pipeline 'X Window System (X11/XShm/Xv)': Could not initialise Xv output [xvimagesink.c(1333): gst_xvimagesink_get_xv_support (): /pipeline0/xvimagesink2:
No port available]
```

---

