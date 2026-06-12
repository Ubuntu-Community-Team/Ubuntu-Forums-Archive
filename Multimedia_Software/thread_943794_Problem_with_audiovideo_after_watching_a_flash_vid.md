---
title: "Problem with audio/video after watching a flash video from a browser"
date: 2008-10-10
forum: Multimedia Software
---

### Post by jess_lyn on 2008-10-10
Hi everyone.. 

I am using Ubuntu-8.04. I am not able to play any media files (v/a) after I visit any website with flash video . If i restart the Xserver [ctrl + alt + backspace] then I can play them.. But again if i visit youtube or others.. i wont be able to use mplayer or amarok.. i tried using different video and audio players... but none of them works after i visit  youtube...Please note only if I play a flash video from the firefox or any other browser, this problem occurs.  Any idea what might be the problem ?

- jess_lyn

---

### Post by minky311 on 2008-10-10
Open up synaptic package manager (system->administration->synaptic package manager) and search for **libflashsupport**. Install that package if it isn't installed.

---

### Post by jess_lyn on 2008-10-11
ok.. I found that libflashsupport was not installed. but I am able to play flash videos from the browswer though.. But even after installing libflashsupport,... situation is still the same.

I tried using mpg123 to play a mp3 file after playing a flash video from youtube.
```

# mpg123 some.mp3 
decoder: SSE
High Performance MPEG 1.0/2.0/2.5 Audio Player for Layers 1, 2 and 3
	version 0.67; written and copyright by Michael Hipp and others
	free software (LGPL/GPL) without any warranty but with best wishes
[../../../src/audio_oss.c:182] error: Can't open default sound device!
audio: No such file or directory

Playing MPEG stream 1 of 1: some.mp3 ...
Title:                                   Artist: 
Comment:                                 Album:  
Year:                                    Genre:  Other
MPEG 1.0 layer III, 128 kbits/s, 44100 Hz stereo
[../../../src/audio.c:267] error: Unable to set up output device! Constraints: 44100, 22050 or 11025Hz.

Audio device: <none>
Audio capabilities:
(matrix of [S]tereo or [M]ono support for sample format and rate in Hz)
        |  s16  |  u16  |  u8   |  s8   | ulaw  | alaw  |
 --------------------------------------------------------
  8000  |       |       |       |       |       |       |
 11025  |       |       |       |       |       |       |
 12000  |       |       |       |       |       |       |
 16000  |       |       |       |       |       |       |
 22050  |       |       |       |       |       |       |
 24000  |       |       |       |       |       |       |
 32000  |       |       |       |       |       |       |
 44100  |       |       |       |       |       |       |
 48000  |       |       |       |       |       |       |

```

When I straced the above command there were two lines lke this
```

open("/dev/dsp", O_WRONLY)              = -1 EBUSY (Device or resource busy)
open("/dev/sound/dsp", O_WRONLY)        = -1 ENOENT (No such file or directory)

```

Also when i straced "aplay" command
```

open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK) = -1 EBUSY (Device or resource busy)

```

Looks like some sound application is not releasing some locks!!
Any idea how to fix this ??

- jess_lyn

---

### Post by minky311 on 2008-10-11
Go to system->preferences->sound and make sure everything is set to ALSA.

---

### Post by jess_lyn on 2008-10-11
Most of them were default. When I try to test, I got this message
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

```

---

### Post by minky311 on 2008-10-11
Try using ALSA, PulseAudio, and OSS or anything else available there and see if any of them work. If any do post which ones did.
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Try following this guide it is very thorough.

---

### Post by jess_lyn on 2008-10-11
PulseAudio seems to work. Nothing else works!!! I got the same error message for OSS as ALSA,which i posted earlier.

---

### Post by jess_lyn on 2008-10-11
I guess the problem is in flash player which does not release locks on audio devices. Can anyone tell me which package in ubuntu-8.04 is the flash player and its associated firefox plugin ? is there any alternative i can try with ?

---

### Post by gandaran on 2008-10-11
you can try flash 10 [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
remove the flashplugin-nonfree (flash 9) and libflashsupport first
if it doesn't work, you'll have to try other fixes, there are many here in the forum just search for pulseaudio related threads

---

### Post by jess_lyn on 2008-10-12
I tried flashplayer 10, but result is still the same. But i found an interesting thing. if I move the libflashplayer.so file from $HOME/.mozilla/plugins and close my browser, I can play audio & video. But obviously I wont be able to watch flash videos in the browser. I tried other alternatives to flashplayer-10, like libflash and libflash-mozplugin, with no change in situation.

---

### Post by Ilek on 2008-10-16
I have exactly the same problem... Did you find any solution ?
Thank you :)

---

### Post by Starteck81 on 2008-10-16
I have this problem as well.

---

### Post by Starteck81 on 2008-10-16
I got mine to work!

I removed any trace of flash I could find.

Went into system > Preferences > sound and changed everything to ALSA and rebooted.

I then reinstalled Adobe's flash version 10 and it worked. :guitar:

---

