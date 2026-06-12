---
title: "Getting desktop screen capture to work well with or without 3d windows"
date: 2007-09-27
forum: Multimedia Production
---

### Post by djrobthaman on 2007-09-27
Hi everyone,

I am about to start recording my ubuntu desktop with a screen capture program.  So far I've installed and tried gtkrecordmydesktop.  It works in that a video file is created that somewhat resembles what was going on while I was recording, but it's kinda jerky.  I upped the frome rate from 15 (I think that was the default) to 30 and still it wasn't that great looking.  I must admit that I was running compiz fusion at the time, and that I haven't tried using it without compiz.  So I can't say whether it is better without it on.

But does anyone have any idea of a "best settings" for gtkrecordmydesktop so the video comes out as good looking as possible.

Also, I'm not averse to trying another program.  If you know of one that's better and will give me a better output could you let me know about that too?

Many thanks,
Douglas

---

### Post by eye208 on 2007-09-28
> **djrobthaman said:**
> It works in that a video file is created that somewhat resembles what was going on while I was recording, but it's kinda jerky.
I use gtk-recordMyDesktop to capture machinima clips from games. It works very well but requires a fast PC. There are some settings that may reduce CPU load for you:

[LIST]
[*]Always capture in 100% quality. The resulting files will be larger, but you can use MEncoder afterwards to compress them to H.264 which is more efficient than the default Ogg Theora codec anyway.
[*]Do not record sound unless you need it.
[*]Capturing a window results in less CPU load than capturing the whole desktop.
[*]Enable "quick subsampling".
[*]Disable "encode on the fly".
[*]Disable "full shots at every frame" unless you need it (i.e. when capturing from an OpenGL accelerated window/screen).
[*]If the recording is still jerky, enable "zero compression" as a last resort. The temporary file will be huge so make sure there is enough free space left on your HD.
[/LIST]

---

### Post by djrobthaman on 2007-09-28
Thanks,

will try adjusting those settings and hopefully I'll see a boost in quality.

---

