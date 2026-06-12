---
title: "avi's etc won't play"
date: 2009-01-27
forum: Multimedia Software
---

### Post by agazzard on 2009-01-27
HELP!!!

I have just installed 8.10 and my avi's won't play.

I have tried mplayer, smplayer, and vlc, and have installed w32codecs etc. but whenever I open an avi, wmv, or mov file the application just closes itself.

Any advice?

Thanks

---

### Post by taurus on 2009-01-27
Try the ubuntu-restricted-extras package.

---

### Post by agazzard on 2009-01-27
Sorry, installed that as well.

Have followed all the steps I can find, including this.

---

### Post by geirha on 2009-01-27
If that still doesn't help, open a terminal and type in **mplayer** followed by a space, but don't hit enter. Then drag and drop an avi over to the terminal window (which will insert the full path to the avi after mplayer) and hit enter.

The output mplayer produces should be helpful to determine the problem. Post the output here if the problem is not apparent.

---

### Post by XanTrax on 2009-01-27
You could also try opening a terminal and typing

```

cd <directory_of_avi>
vlc <video.avi>

```

Where <directory_of_avi> is the directory where your avi is and <video.avi> is the name of the avi you want to open.

Please post the output of that.  I am guessing somewhere in there it will say 

> 
SEGMENTATION FAULT



EDIT:

Also, please try this

Open a terminal or press alt+f2 and type

```

gstreamer-properties

```

Click the video tab and where it says "Plugin:", open the drop down menu and select "X Window System (No Xv)".  Then, open the avi in totem by either right clicking it and selecting "Movie Player" (not mplayer) or opening a terminal and typing

```

cd <directory_of_avi>
totem <name_of_avi.avi>

```

Where, <directory_of_avi> is the directory of the avi and <name_of_avi.avi> is the name of the avi

---

### Post by agazzard on 2009-01-27
OK, the initial output is:

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Then it seems to get into a loop with the error:

X11 error: BadAlloc (insufficient resources for operation) 2.1% 0 0

Any ideas as I have none?

Thx

---

### Post by geirha on 2009-01-27
Try disabling compiz (visual effects) and see if video will play then. To temporarily disable compiz you can open a terminal and run
```
metacity --replace &
```

I've noticed problems playing video when compiz is used, especially with the desktop cube enabled.

---

### Post by XanTrax on 2009-01-27
> **agazzard said:**
> OK, the initial output is:

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Then it seems to get into a loop with the error:

X11 error: BadAlloc (insufficient resources for operation) 2.1% 0 0

Any ideas as I have none?

Thx

As it says here:

[https://bugs.launchpad.net/fedora/+bug/111257](https://bugs.launchpad.net/fedora/+bug/111257)

Changing to "No Xv" will most likely fix the problem.  Please try my suggestion above using totem and then I will guide you on how to fix it with VLC and Mplayer.

---

### Post by agazzard on 2009-01-27
vlc did produce an error similar to before, but changing the plugin in gstreamer-properties has got everything working.

Totem will certainly do for playing the files, but if you want to explain how to fix vlc etc. please do. I'll be very interested.

Thanks for all your help. Much appreciated.

Ade

---

### Post by XanTrax on 2009-01-27
> **agazzard said:**
> vlc did produce an error similar to before, but changing the plugin in gstreamer-properties has got everything working.

Totem will certainly do for playing the files, but if you want to explain how to fix vlc etc. please do. I'll be very interested.

Thanks for all your help. Much appreciated.

Ade

Will do.

- Open up VLC player
- Click Tools
- Click Preferences
- Click the button at the bottom to show "All" settings
- Drop down the "Video" selection on the left
- Click Output modules
- On the right, drop down the menu where it says "default" and select "X11 video output"

---

### Post by agazzard on 2009-01-28
Thanks everyone, all sorted now.

---

