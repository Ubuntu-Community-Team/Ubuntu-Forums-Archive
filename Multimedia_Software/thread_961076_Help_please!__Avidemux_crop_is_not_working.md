---
title: "Help please!  Avidemux crop is not working"
date: 2008-10-28
forum: Multimedia Software
---

### Post by DavidVS on 2008-10-28
When I try to crop with Avidemux it does not work!  The file that is saved has only one frame.

What might I be doing wrong?

---

### Post by xc3RnbFO8P on 2008-10-28
It could be codec problem,
what are you trying to encode?

---

### Post by DavidVS on 2008-11-11
I am trying to edit a video I recorded with a Flip Mino camcorder.

Telling you my Avidemux settings is probably unhelpful, since they are undoubtedly wrong or improperly supported with missing packages.  If I were to record a tiny video and put a link to it in this forum thread, would someone whose Avidemux works well double-check they can crop it and then share his or her settings?

---

### Post by xc3RnbFO8P on 2008-11-11
> If I were to record a tiny video and put a link to it in this forum thread, would someone whose Avidemux works well double-check they can crop it and then share his or her settings?
Yes do that.

---

### Post by DavidVS on 2008-11-21
Okay.  My sample Flip video is here:
  [http://davidvs.net/crop-me.avi](http://davidvs.net/crop-me.avi)
I'll take it down after I receive a helpful reply.

My Avidemux GTK+ settings (which do not work) are:
  
[Audio]
 Local Playback: Pro Logic
 Volume Control: PCM
 Audio Output: OSS
 ALSA Device: (the option is grayed out)

[Video]
 Video Display: GTK+ (slow)
 Default Postprocessiong: Horizontal Deblocking, Vertical Deblocking
   (no Deringing), Strength 3

[Output]
 (no boxes checked), Split every 790 MB

The laptop is an Extensa 4620Z.

Thank you for any help!

---

### Post by DavidVS on 2008-11-24
Okay.  It works well enough for me.  Here is what I did:

[Audio]
Local Playback: Pro Logic
Volume Control: Master
Audio Output: ALSA
ALSA Device: default

[Video]
Video Display: XVideo (best)
Default Postprocessiong: none
Strength 3

[Output]
(no boxes checked), Split every 790 MB

Then, **not in preferences** but in the options on the left hand side of the Avidemux window...

Video: Copy
Audio: MP3 (LAME)
Format: AVI

I'm not sure if **any** of the preferences matter.  I think that changing the "Audio" setting on the left hand side was the big deal.

---

### Post by shirilover on 2008-11-24
The preferences really don't effect cropping. I also assume you tried Video->Filters and selected crop from the list. Although the resolution of your sample is 640x480, so I'm not quite sure what you want to crop.

If, on the other hand, you meant cutting a selection out. You should have been able to choose the start and end frames that you wanted to remove and deleted the frames with the Del key.

---

