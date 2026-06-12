---
title: "xawtv"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by dimas869 on 2007-07-28
Hello,
This is may be simple but i am having difficulties to figure  what i am doing wrong when i record a video from xawtv (capturing the image from my webcamera) and when i look for the file i only find a picture and not a video.

thanks for the help:rolleyes:

---

### Post by nzadLithium on 2007-07-28
when you press record a window should show up. right at the top it should say
movie driver     : multiple image files
click where it says multiple image files then select microsoft avi (riff) format. 

It should now record to an avi file. I'm having problems with the avi record though colours are messed up for some reason. When you finish recording the screen freezes for some reason. To get it to go again click on audi mode then do your audio mode and it will go again.

I have installed the xawtv-plugin-qt package.
This allows it to record in quicktime format.
When i use quicktime format the image on the xawtv screen freezes. 
Then when i look at the recording about the first second works perfectly no color probs or anything then that freezes too :(
clicking on audio mode and setting again seems to fix.

using both recording formats sound goes perfectly.

I'm gona play round with it see if i can get it to go properly. If i can i'll post here and explain how. Try recording in avi anyway it might go perfectly for you.

---

### Post by nzadLithium on 2007-07-28
k i figured it out :)

these are my settings:

use movie driver microsoft avi.
call it whatever you want

audio format : 16 bit of whichever you want.
sample rate : 48000
video format: mjpeg (AVI)
frames/sec: 30.0 fps
video size: 384x288 (i can't change)

i think all have to have though is 
movie driver: microsoft avi
video format: mjpeg avi

tell me if it don't go

---

### Post by dimas869 on 2007-07-28
> **nzadLithium said:**
> k i figured it out :)

these are my settings:

use movie driver microsoft avi.
call it whatever you want

audio format : 16 bit of whichever you want.
sample rate : 48000
video format: mjpeg (AVI)
frames/sec: 30.0 fps
video size: 384x288 (i can't change)

i think all have to have though is 
movie driver: microsoft avi
video format: mjpeg avi

tell me if it don't go

Hello nzadLithium!,
Thank you very much!!!...works for me!...i appreciate it though

:guitar:

---

### Post by MsChevyKat on 2007-07-28
I'm using motv, which is basicly an xawtv front-end.

I tried all those settings, still no sound with recorded video. :(

---

### Post by nzadLithium on 2007-07-29
Can you post what your command and parameters are to start motv?

Also post a screenshot of whatever screen comes up for recording.

If any errors come up post them too.

And post any recording settings on here.

---

### Post by MsChevyKat on 2007-07-29
> **nzadLithium said:**
> Can you post what your command and parameters are to start motv?

Also post a screenshot of whatever screen comes up for recording.

If any errors come up post them too.

And post any recording settings on here.


well, I just type "motv" and use the gui menus to set up to record. The video part is lovely.

I get this message when I fire up the program:

This is motv-3.95, running on Linux/i686 (2.6.20-16-generic)
Warning: Actions not found: Remote
Warning: Actions not found: Remote
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: WARNING: framebuffer size mismatch
v4l2: me=1280x1024 v4l=0x0


When recording, I get no type of messages at all.

I use the same settings the other person mentioned...no audio. :(

---

### Post by nzadLithium on 2007-07-29
has your card got any line out?
If you do is this plugged into your audio cards line in?

I have to start mine using a program called sox. Otherwise i get error [init] Sox is available in synaptic.
I put this in a script:

#!/bin/bash
sox -r 32000 -w -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp & pid=$!
xawtv -vbidev /dev/vbi0 -dspdev /dev/dsp -remote -global:filter "linear blend" -b 24 -gl
kill $pid

It starts up sox then starts xawtv. Then when xaw is closed it stops sox.
Maybe this will help?

---

### Post by MsChevyKat on 2007-07-29
> **nzadLithium said:**
> has your card got any line out?
If you do is this plugged into your audio cards line in?

I have to start mine using a program called sox. Otherwise i get error [init] Sox is available in synaptic.
I put this in a script:

#!/bin/bash
sox -r 32000 -w -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp & pid=$!
xawtv -vbidev /dev/vbi0 -dspdev /dev/dsp -remote -global:filter "linear blend" -b 24 -gl
kill $pid

It starts up sox then starts xawtv. Then when xaw is closed it stops sox.
Maybe this will help?

I have onboard sound.  The only place I found to plug the tv card in, so I got sound, it the plug on the moboard where the cdrom would be plugged in if needed.

---

### Post by nzadLithium on 2007-07-30
have you tried running it using sox?

---

### Post by sharris203 on 2008-04-27
> **nzadLithium said:**
> k i figured it out :)

these are my settings:

use movie driver microsoft avi.
call it whatever you want

audio format : 16 bit of whichever you want.
sample rate : 48000
video format: mjpeg (AVI)
frames/sec: 30.0 fps
video size: 384x288 (i can't change)

i think all have to have though is 
movie driver: microsoft avi
video format: mjpeg avi

tell me if it don't go

i get error[init] with any settings i use and the video does not record. any ideas?

---

