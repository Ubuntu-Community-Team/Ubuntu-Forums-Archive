---
title: "record desktop with audio"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by jaysons on 2008-01-15
What program are people using to record there desktop with audio? (as seen on youtube)

---

### Post by rurinix on 2008-01-16
I have a similar questions.  I only want to record the content of a window. (i.e. me playing/beating a game on emulation).  I can't seem to find a Linux app which does that and WINE will not work right (instead of English I get random symbols).  There is a Windows tool call Fraps which basically does what I want (I am told).  I would like to find a Linux equivalent.

---

### Post by mondoUNC on 2008-01-16
you could try Wink, you can find it in synaptic.

---

### Post by rosemberg on 2008-02-13
[B]yeah, but it saves the files just in .swf and .exe 

i also need some program to record my desktop with sound.[/B]
[B]
i have tried this,
[/B]
root@Wuppie-Earth:~# recordmydesktop -x 200 -y 320 -width 425 -height 355 -device /dev/snd/seq

**but it gives the next error,**

-------------------------------------------------------------------------------------

Initial recording window is set to:
X:200   Y:320    Width:425    Height:355
Adjusted recording window is set to:
X:196   Y:314    Width:432    Height:368
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM /dev/snd/seq
Couldn't open PCM device /dev/snd/seq
Error while opening/configuring soundcard /dev/snd/seq
Try running with the --no-sound or specify a correct device.


-----------------------------------------------------------------------------------------------------

??????????

---

### Post by rosemberg on 2008-02-13
**i cant record the sound, even without errors!**


root@Wuppie-Earth:~# recordmydesktop -x 200 -y 320 -width 425 -height 355 -channels 2 -device default
Initial recording window is set to:
X:200   Y:320    Width:425    Height:355
Adjusted recording window is set to:
X:196   Y:314    Width:432    Height:368
Your window manager appears to be compiz


Detected 3d compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Opened PCM device default
Recording on device default is set to:
2 channels at 22050Hz
Capturing!
Broken pipe: Underrun occurred.
Saved 289 frames in a total of 288 requests
Shutting down.....
Encoding started!
This may take several minutes.
Pressing Ctrl-C will cancel the procedure (resuming will not be possible, but
any portion of the video, which is already encoded won't be deleted).
Please wait...
[100%] 
Encoding finished!
Wait a moment please...
   
Done.
Written 638062 bytes
(582704 of which were video data and 55358 audio data)

Cleanning up cache...
Done!!!
Goodbye!
root@Wuppie-Earth:~#

---

### Post by cozmicharlie on 2008-02-14
try gtk-RecordMyDesktop.  It is in Synaptic.

---

### Post by Dai777 on 2008-02-14
[http://videotutes.blip.tv/#669639](http://videotutes.blip.tv/#669639)
if it doesn't have an intro screen then it was recorded with recordmydesktop

---

