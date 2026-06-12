---
title: "Cinelerra not working properly"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by MONODA on 2008-01-27
I have just compiled cinelerra from source and kept on getting an error that said:
```
virtual int FileOGG::read_frame(VFrame*): Expecting a keyframe, but didn't get it
```
whenever I clicked somewhere on the video I had loaded. So I uninstalled it then added the repos for it and used apt to install it byt I am still getting the same error. This only happens with some videos and all my videos are .ogg theora.

---

### Post by MONODA on 2008-02-08
Im getting some more problems. Whenever I add an effect the video either stops to play while the sound continues or the video slows down while the audio remains at the same speed. Also when importing video i get and error saying:
> int FileOGG::ogg_seek_to_keyframe(sync_windows_t*, Long int, int64_t, int64_t*: Cannot find next page while seeking 
I get this error several time in a row in the same window. How can I fix this?

---

### Post by rofthorax on 2008-05-14
I'm getting the same error in cinelerra.. 
It's kinda pathetic that Cinelerra should fail on a 
open source format.. 

Anyhow, I used Ogg Convert to generate the ogg file.. 

They really need to set cinelerra so it doesn't output 
errors, especially if the program is working fine despite the error 
messages.. 

I get 

virtual int FileOGG::read_frame(VFrame *) : Expecting a keyframe, but didn't get it

Well I guess I will have to do my video editing in blender's sequence editor if cinelerra doesn't satisfy me. 

:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by rofthorax on 2008-05-14
Ohh

You can move that window to another workspace.. At least it doesn't keep popping up in view of cinelerra..

---

