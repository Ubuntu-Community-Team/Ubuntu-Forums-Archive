---
title: "VLC - no sound with some filetypes"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by silkstone on 2007-05-07
I've used the Media Player Connectivity plugin for Firefox to set VLC as the default player, and some streams work OK but others give video but no sound. The VLC plugin shows up in about:plugins. I've installed all the codec packages I can find.

Then I tried using VLC to play different file types from disk, and the results are strange. It works with most, but with some - for example .mov (Quicktime) files - it again gives video but no sound.

BUT... if I move the slider to go back and forth within the movie, I can hear the sound track (speeded up and garbled, of course) as I do this. As soon as I stop moving the slider, the sound stops. :confused: 

Any ideas please?

P.S. Totem plays these with both video and sound.

---

### Post by silkstone on 2007-05-08
Another curiosity...

With streaming video, if I move VLC's slider completely to the left hand side the slider bar disappears, then comes back and the movie restarts - with sound!

Also, if I click on the 'speed up' and 'speed down' arrows so I'm back to normal speed again, the sound comes on. :confused:

Unfortunately neither of the above work when playing .mov files - only with streaming video.

I'm getting the same problem with VLC on both the desktop (Edgy) and the laptop (Feisty), so surely I can't be unique???

I've tried installing mplayer, but I get an error message when it tried to play anything - it just says 'Error'.

---

### Post by silkstone on 2007-05-08
One last try with this!

When I get no sound in VLC, if I click on View > Stream and Media Info > Statistics > Audio it shows

Decoded blocks X
Played buffers X
Lost buffers X

The three figures (X) are the same. i.e. it's losing all the buffers.

If I jiggle the playback speed control so the audio comes back, the first two figures are the same and the last one is zero (or doesn't increase from where it stopped losing the sound).

So it's losing the buffers. Can anyone suggest how to solve this? Please?

---

### Post by John Rolando on 2008-03-08
I have the same problem my sound works fine in ubuntu 8.04 Alpha 5, but with MPlayer and VLC... the funny thing is that VLC says to me that there are no lossing from buffers... 

this is my output when I load a DVD movie...

jraristi@KNIFE:~$ vlc
VLC media player 0.8.6d Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: PAIS_PAISA
libdvdnav: DVD Serial Number: 363E0335C9C1FCCA
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jraristi/.dvdnav/PAIS_PAISA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: *** pgci_ut handle is NULL ***

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000166
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006729
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000337] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib pcm_dmix.c:866:(snd_pcm_dmix_open) unable to open slave
[00000338] jack audio output error: failed to connect to JACK server
[00000338] oss audio output error: cannot open audio device (/dev/dsp)

IF YOU CAN HELP ME YOU WILL HAVE MY ETERNAL GRATITUDE!

thanks!

---

### Post by zedlander on 2008-04-09
Try playing with the settings under Settings -> Preferences -> Audio -> Output Modules -> OSS and ALSA.  It worked for me.

---

### Post by harmck on 2008-05-12
Thanks Zedlander, 

I upgraded to 8.04 shortly after its release and sadly I've seen the same problem with Mplayer and VLC. But your setting change worked a treat. 

Har

---

### Post by bodhi.zazen on 2008-12-26
> **zedlander said:**
> Try playing with the settings under Settings -> Preferences -> Audio -> Output Modules -> OSS and ALSA.  It worked for me.

This thread comes up on google search so ...

Thanks zedlander, Setting to OSS worked for me on Ubuntu 8.10

I am frankly shocked with this and never would have guessed.

---

