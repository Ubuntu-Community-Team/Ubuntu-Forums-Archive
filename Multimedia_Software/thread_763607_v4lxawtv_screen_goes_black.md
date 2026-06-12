---
title: "v4l/xawtv: screen goes black"
date: 2008-04-23
forum: Multimedia Software
---

### Post by chochem on 2008-04-23
I'm tryingt to use xawtv with my webcam. Running: 'xawtv -c /dev/video0' results immidiately in  the screen turning black and the computer not repsonding to anything other than a switch to a text terminal (ctrl+alt+f1-6). From there I can then go back to X (ctrl+alt+f7) which will clear the screen and show my desktop again.

... where xawtv has printed out the following error message: 
/dev/video0 [v4l]: no overlay support
and then soliders on ("trying to continue anyway"), managing to start a window with webcam capture (working flawlessly).

Since the error seemed to come from video4linux, I tried running v4l-conf which results in exactly the same problem, only here I get a bonus error:
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Invalid argument
/dev/video0 [v4l]: no overlay support

Can anybody tell me what this overlay support is or how I can get xawtv to skip fishing for it and just give me the webcam window without the black screen? I at first thought it was trying to go fullscreen and failing but there is an explicit fullscreen argument to xawtv that I'm not using... Any ideas?

---

### Post by disraeli on 2008-07-06
I also have this problem

---

### Post by chochem on 2008-07-06
Sorry to say, I never found a solution. With xawtv, anyway. However, I was already using VLC for video, so I was pleased to discover that it could easily be used to mirror the webcam including taking snapshots and taping video. Mind you it doesn't have the settings and the silliness of Cheese but IMO far more lightweight, stable and reliable.

I don't knwo why the wiki doesn't suggest using it...

EDIT: It does now :)

---

