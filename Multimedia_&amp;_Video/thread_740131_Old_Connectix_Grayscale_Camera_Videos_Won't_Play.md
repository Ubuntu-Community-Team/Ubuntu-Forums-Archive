---
title: "Old Connectix Grayscale Camera Videos Won't Play"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by sanitycheck on 2008-03-30
I have a collection of ancient, 10+ year-old black-and-white videos made with the first-generation Connectix Grayscale parallel port (Windows 9x) camera.  To my surprise, MPlayer and VLC will not play the videos.  The files will open and sound will play, but the screen is either black or flashing colors.  I do have the Win32 codecs installed, and I can play every other video format I know except these Connectix files.

This must be a codec issue, but which codec?  In MPlayer I tried changing the various Codecs and Demuxer (tab) settings, and Video (tab) settings, but the changes didn't help.  I did restart playback each time so the settings changes I made would be applied before replaying the video.

My system is i386 Gutsy, so this isn't a 64-bit problem.

The files have an AVI extension.  From what I can tell, the format is uncompressed 4-bit grayscale.  The size is 320X240 or smaller.  The files play fine in Windows Media Player with no special codecs installed.

If I can get them to open, I'll probably convert them to a normal format using Avidemux, which can't currently open the files either.

Thanks in advance.

---

### Post by xc3RnbFO8P on 2008-03-30
In terminal:
mplayer /home/... your avi file > return
and post the output

---

### Post by kostkon on 2008-03-30
> **sanitycheck said:**
> If I can get them to open, I'll probably convert them to a normal format using Avidemux, which can't currently open the files either.

Good thinking, converting them to an open format (like Ogg) will make your videos last longer. You can see that even now you have problem playing them.

If you still have Windows, try to convert them from there, maybe you will have better chances finding an application that will recognize them.

---

### Post by sanitycheck on 2008-03-30
Here's the output:

```
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
gnome_screensaver_control()The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
Frame too small! (9600<38400) Wrong format?
```

I don't know what that joystick message is all about, but I think I'd like to clean that up, too.

I did consider converting them in Windows.  However, I'm not familiar with Windows conversion tools, and I'd rather do this in Kubuntu if at all possible.  I'll use the Windows conversion as a last resort.

---

### Post by xc3RnbFO8P on 2008-03-30
Do it like kostkon suggested, you could try free program like [Virtualdub]("http://prdownloads.sourceforge.net/virtualdub/VirtualDub-1.7.8.zip?download")
[http://www.virtualdub.org/]("http://www.virtualdub.org/")

---

