---
title: "Audio is playing but video is not.."
date: 2009-11-29
forum: Multimedia Software
---

### Post by timominous on 2009-11-29
Before, I was able to play all my video files. There was no problem at all.
Then, I installed Cairo Dock.
I tried both with OpenGL and no OpenGL.
I thought that everything was fine until I tried to play a video.
The video file open in both Totem and VLC but only audio is playing.
There is no video output.
I closed CD and restarted.
I tried to play videos but everything is still the same..

Can anybody please help me?
I'm desperate here..

UPDATE:
I uninstalled CD but the problem is still there.

---

### Post by timominous on 2009-11-30
I hate to do this but here goes..

BUMP!

---

### Post by gman16000 on 2009-12-02
I'm experiencing the same thing.  I will play around and see what I can figure out.

Here's my setup:
Karmic 64 bit.  Nvidia video without compiz/composite.  Everything is up to date.

What I see: 
VLC plays various ISOs fine **without** Cairo Dock installed.  Once Cairo is installed, I only hear audio.  Sometimes VLC crashes.  I get lots of error messages from VLC.

Once Cairo Dock is removed and I restart X, everything works fine. 

If I figure anything out, I'll post it here.

---

### Post by gman16000 on 2009-12-02
Here is a solution that worked for me.  

Open VLC.  Menu:Tools->Preferences->Interface (Show Settings=Simple)

There is a **Embed video in interface **checkbox.  Make sure it is unchecked.  

When I did this, I did not have to restart X or anything.  It worked from this point forward.

Hope this helps.

---

### Post by timominous on 2009-12-06
still did not work for me.. :(

---

### Post by mc4man on 2009-12-06
Have a read thru here, a few suggestions ( though maybe you've tried some

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/416294)

Note that it's been 'fixed' in the lucid vlc package set,

---

### Post by timominous on 2009-12-07
I'm relatively a new user.. A beginer..
I don't know how to use or what to do with the link that you gave me..

---

### Post by mc4man on 2009-12-07
Well the story there and in this thread seems to be that many setups will have video issues with vlc and possibly totem when cairo dock is installed.

A patch of sorts has been written and applied to a vlc 1.0.3 package  for lucid.
Whether it shows up in karmic I don't know, wouldn't hold breath there

For many, doing one or more of a few things may help, *for others there's only one choice atm in karmic, either vlc or cairo-dock*

Possibilities
Disable the "embedded video in interface" - vlc -> tools ->preference -> interface settings

Change the video output - same preferences -> click video tab, in output dropdown

Change from default to OpenGl or  if that's no good X11

Make sure after any changes to vlc to click save, closing and re-opening vlc won't hurt either.

If none of the above try either of the video outputs with just a command line vlc by entering in a terminal
```
cvlc /path/to/filename
```

Or if you find easier (I do), then 

Open a terminal, type cvlc and hit the space bar.
Then drag and drop your file onto the terminal, click anywhere in the terminal to return focus and press enter to run

---

### Post by timominous on 2009-12-12
I tried the all methods but nothing worked..
The one using the terminal gave this..

```
timominous@duhaylungsod-desktop:~$ cvlc /home/timominous/Videos/video.avi
VLC media player 1.0.3 Goldeneye
[0x890e108] main interface error: no interface module matched "globalhotkeys,none"
[0x890e108] main interface error: no suitable interface module
[0x8865140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x890e108] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /home/timominous/Videos/video.avi
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[0x8910978] access_file access error: cannot open file /home/timominous/Videos/video.avi (No such file or directory)
[0x8910978] main access error: File reading failed
[0x8910978] main access error: VLC could not open the file "/home/timominous/Videos/video.avi".
[0x890fa98] main input error: open of `/home/timominous/Videos/video.avi' failed: no suitable access module
[0x890fa98] main input error: Your input can't be opened
[0x890fa98] main input error: VLC is unable to open the MRL '/home/timominous/Videos/video.avi'. Check the log for details.

```

---

### Post by kortak on 2009-12-12
I had the same problem up to now.  No avi playback on any player.  Apparently it was related to X11.  So in VLC I changed the video output to "X11 video ouput" and it worked YUPIEEEEE.

I don't know what's going on exactly.

How can we set up this option for the other players ??

---

