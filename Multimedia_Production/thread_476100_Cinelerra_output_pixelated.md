---
title: "Cinelerra output pixelated"
date: 2007-06-16
forum: Multimedia Production
---

### Post by Dave Mason on 2007-06-16
Hi there any Cinelerra experts. I've been playing around with Cinelerra for a few months to achieve a particular video editting project. Cinelerra pretty well does everything I need but I'm hung up on a basic pixelation issue that I can't seem to overcome. I just recently updated my Ubuntu (to Edgy) and my Cinelerra (to 2.1cv) in the hope that my problem would go a way but it has not !

The problem:
I have an video input file that I wish to edit. (MPREG,720*576,Framerate 25fps,Codec MPEG/libmpeg2). This plays OK using Mplayer (0.99 +1.0pre7try2+cvs20060117). 
If I create a cinelerra project (specifying same Frame dimensions & framerate) and input my MPEG file as a resource then any 'playback' or 'rendered output' of bits of this video involving significant motion suffer from pixelation. I am not doing anything clever with my editing - in fact I get the pixellation effect just clipping a piece out of the input file and playing it back.

I have tried changing various 'playback' settings and tried rendering with different options and nothing I do seems to affect the basic problem.

Can anyone give me any reason why just running this file thru' cinelerra should result in this sort of loss of picture quality - and is there anything I can do to stop it happening ?
Dave

---

### Post by Rexbron! on 2007-06-18
Is the pixelation just on playback in Cinelerra or does it output this way as well?

In either case, make sure the project settings match your input video and possibly  you may need to right click on the clip and use the track resize option. 

If the pixelizaton is just on the render, check you project settings (resoultion, bitrate) and possibly use a different encoder.

---

### Post by Dave Mason on 2007-06-19
Hi,
Thanks for the reply !
Yes the pixelation is there when I render too. 
I have been careful to try to match the video parameters of the input file and my project. (That is the frame size & the frames per second) . I have played around with all of the video settings I could find in Cinelerra. Nothing I have done affects the playback much or how it renders. I guess there could be something odd about the input file - but it plays without a stutter in Mplayer !
One other thing I tried was to convert the MPEG to 'avi' using mencoder. This avi also plays OK in Mplayer but Cinelerra does not seem to like the .avi  (I can load it as a resource but when I try to move it to the 'Compositor' window it just fails to load). Do you know if I should be able to work with an 'avi' in Cinelerra ?
Dave

---

### Post by Rexbron! on 2007-06-19
Is it pixelated when you play it in the viewer or only when it is through the compositor?

Did you try resizing the video track after it is imported to the timeline?

---

### Post by Dave Mason on 2007-06-20
It's pixelated when I play back thro' in the compositor window. I tried resizing the video to about half size - this has no effect on the pixelation.
It is hard to say if there is a problem in the viewer window as the resource does not really play here in real time. When you play you hear the sound but the video is just a static image. If you move thro' the input clip using the 'slider' the image does change - this is how I have had to select my edited 'snips'. I have not worried too much about this as the overall process appears to work (except, of course, for the pixelation).
Dave

---

### Post by Rexbron! on 2007-06-20
hmm, ok try changing the video playback driver in setting or preferences and see if that makes a difference. Also, for pixelation, you want to resize the track to its native resolution, as if the project setting were changed after the clip was added to the timeline, it will retain those settings. 

Also consider playing around with the scaling equasion for  playback. 

If all else fails, attach a **short** clip and I will take a look at it.

---

### Post by Dave Mason on 2007-06-25
Thanks for your latest post - I've been on vacation for a few days with no access to the internet. I might just take you up on your offer to take a look at at a small clip. It might take me a while to work out how to snip out a minimal bit of the original file that exhibits the problem when I run it thro' Cinelerra.
Dave

---

