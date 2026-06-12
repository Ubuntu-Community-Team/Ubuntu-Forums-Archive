---
title: "video playback issues"
date: 2008-05-29
forum: Multimedia Software
---

### Post by BoardStupid on 2008-05-29
Initially, I didn't realise that my video playback was broken as I don't normally watch media on my laptop (Acer Aspire 5051AWXMi), but it is soon to become my sole computer and I would like to get it fixed. 

I used to be able to watch media on it running Gutsy and using Totem, but now after a brief flash the picture disappears and the video window turns black. The audio plays fine but without a picture it's a bit pointless.

So far I have tried removing all codecs and video playing apps through synaptic manager and reinstalling. 
I've also tried using VLC, mplayer, and even Kaffine in the hopes they would help.

Every time I tested one program, I would uninstall it before installing another to avoid any conflicts.

I have an ATI Radeon Xpress 1100 integrated GPU and have installed all drivers correctly (compiz works like a charm).

If any one has any ideas what could be causing the problem, or better yet, a solution, I would love to hear them.

Thanks for taking the time to wade through all this.

---

### Post by kpkeerthi on 2008-05-29
Does the video play OK with compiz turned off?

[http://ubuntuforums.org/showthread.php?t=729034](http://ubuntuforums.org/showthread.php?t=729034)

---

### Post by CameO73 on 2008-05-29
Hmmm ... could be a video driver or a codec problem. 

First check if you have the (restricted) ATI driver installed. This usually happens automatically after the first logon (popup saying you can enable a restricted driver). If not, try installing **xorg-driver-fglrx** with Synaptic.

For the codecs, try the following:

[LIST]
[*]Install Totem, and all gstreamer0.10-plugins-[good/bad/ugly]. This should normally play most movies.
[*]Install VLC (which will have no impact on Totem, btw). This one will play most of the stuff Totem has a problem with (but unfortunately misses the handy on-screen progress bar of Totem).
[*]The [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository has more multimedia stuff (recommended!)
[*]Install **ubuntu-restricted-extras** to get most of the cool multimedia stuff that can not be included in Ubuntu by default (because of licensing issues).
[*]You may want to enable more software (Synaptic -> Settings -> Repositories)  by checking all options in the Updates-tab. Warning: some of those updates (hardy-proposed and hardy-backports) are unsupported and could cause problems!
[/LIST]
If that fails, let me know!

---

### Post by BoardStupid on 2008-05-29
It appears that wording your problems can be the hardest part. I was having the same problem as Catalyst2Death in that other thread but I was obviously searching for the wrong keywords. A couple of preference changes and everything works perfectly. Thanks for the help guys

---

### Post by bgjmo on 2008-06-18
what did you change boardstupid?  im having the same problem

---

### Post by mc4man on 2008-06-18
he probably changed his video output (-vo) to x11

edit: ck. here (link above)   [http://ubuntuforums.org/showthread.php?t=729034](http://ubuntuforums.org/showthread.php?t=729034)

---

### Post by bgjmo on 2008-06-18
> **mc4man said:**
> he probably changed his video output (-vo) to x11

edit: ck. here (link above)   [http://ubuntuforums.org/showthread.php?t=729034](http://ubuntuforums.org/showthread.php?t=729034)

yeah i cant find that setting

---

### Post by mc4man on 2008-06-19
> yeah i cant find that setting 
either run in terminal  ```
gstreamer-properties
``` or go system -> preferences -> multimedia systems selector and under video tab -> default output -> plugin choose as suggested  ...(no Xv)
For vlc see post 2 in that thread
 Note: though it makes no sense after switching to no Xv or in vlc to X11 after a few usages you could try switching back to Xv and sometimes it works right (Xv is preferred if your system can handle)
Possibly it's just switching from autodect to something specific that's helpful

---

### Post by bgjmo on 2008-06-20
the only difference it seems to make is that i can watch it fullscreen.  which is fine... thanks for the help.

---

