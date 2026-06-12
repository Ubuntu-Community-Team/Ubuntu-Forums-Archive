---
title: "Avidmux too clunky is Cinerra for me?"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by ftwig on 2007-01-17
I have in the past used various video editing systems such as Avid,
Final Cut Pro, SpeedRazer).  I wanted something to chop out adverts of
xvid .avi files I have created on my MythTV box (a linux system for
recording TV).

I have been using avidemux which works but is very fiddly.  The good
thing about it is it is very quick to save the final .avi (it douse
not have to re-encode the whole thing, it can simply copies from the
original).  It is possible to 'scrub' to roughly find the begining/end
of the adverts but then you can only either play at normal speed (not
backwards), go forward/back 1 frame or forward/back to next key-frame.
 In all the other systems I have used it is possible to play
forward/reverse and speed up/slow down from between 1/10 times of
actual speed.  This means it is fairly quick to get to the frame you
want and if you overshoot this can be corrected easily.    You can not
even use the cursor key to move forward back, you have to click on the
buttons with the mouse.

So I was wondering if Cenerra was the answer.  I guess it has the
standard 1/10 times forward reverse and allows you to use the cursor
key to go back/forward.  The question is how quick it is to load/save
avi files.  Douse it have to convert to load then transcode to save?

Regards,
Ben

---

### Post by loell on 2007-01-17
i think it depends on the processor, better processor faster results,

i tried loading an avi file in cinellera and took too long to process.

---

### Post by ftwig on 2007-01-17
I feared this.  If avidmux had key binding for next/previous frame/keyframe and could play in reverse it would be so much better.

---

### Post by CompShrink on 2007-03-02
AVIDemux's "smart copy" is a godsent in my opinion. I don't know why more encoders don't implement something like it.

A little technical, but the following paragraph describes why you probably won't find the feature in other programs.

You can't just "copy" the data if you don't cut on keyframes. Keyframes hold the entire image data, and the other frames just describe how the image has changed since the last key frame. So if you want any of the video between keyframes, you need the previous keyframe, or to remake a keyframe. Remaking a keyframe is *not* copying, obviously. AVIDemux will reencode only the section not belonging to a keyframe with the same video codec, if you have that codec available for encoding as well as decoding. Thus, all but a tiny bit is exactly copied, which saves time and quality.

Cinerra I'm sure has a direct copy mode, but like every other video editor I've used or heard of, you need to cut on the keyframes. Or, you have to reencode the whole thing, which takes a lot more time, and loses quality.

Bottom line:
The creator of AVIDemux seems like a pretty cool guy. Just ask in the forums for what you want:
[User interface and Usability]("http://www.avidemux.org/admForum/viewforum.php?id=7")
Whine here if there is some improvement needed concerning usability / interface

---

