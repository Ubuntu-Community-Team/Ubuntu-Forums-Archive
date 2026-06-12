---
title: "VLC Trouble..."
date: 2009-09-15
forum: Multimedia Software
---

### Post by Thomas.Kast on 2009-09-15
I am having a little bit of trouble with my VLC player. I have a bunch of .avi files and vlc seems to pick and choose which ones to play and which ones to display error messages. I would post an error message, but the only thing it says is that it cant open.

I think I may have to uninstall and reinstall VLC...

---

### Post by andrew.46 on 2009-09-16
Hi Thomas,

> **Thomas.Kast said:**
> I am having a little bit of trouble with my VLC player. I have a bunch of .avi files and vlc seems to pick and choose which ones to play and which ones to display error messages. I would post an error message, but the only thing it says is that it cant open.

If the files are not actually damaged it could be that there is a codec in some of these avi files that vlc is not happy with. It would be nice to identify the codecs and if you were interested in pursuing this the best way is to use FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

The page above should give you a decent copy of FFmpeg and if you could then try the following syntax:

```
ffmpeg -i my_***[COLOR="Red"]problem_file.avi[/COLOR]***
```

and then post the full terminal output on this page. This should show the makeup of the difficult files and hopefully show a path to allow playback on your machine.

Andrew

---

