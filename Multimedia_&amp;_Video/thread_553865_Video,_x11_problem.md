---
title: "Video, x11 problem?"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by otek on 2007-09-18
Hi,

Ive got a really irritating problem, you might remember my last thread, that problem is solved, kind-of.

Edit: My computer has an ati radeon 9700tx

I have a problem with video playback. Usually playing any type of video works perfectly, but sometimes out of the blue when i want to play a file the video is heavily pixelated and garbled. Vlc can still play video if i change output from default or x11 to open gl or something similar, but mplayer and totem still give me ****. The problem is solved by restarting the computer once or twice.

So, i start my computer, play 10 videos, leave the computer on, eat breakfast, and when i come back mplayer cant play anything, its just blank, even though it worked 1 hour ago. If i restart X (ctrl+alt+backspace) i get video, but its heavily pixelated and garbled. When this happends vlc and totem can still play the files without restarting X but its still pixelated and garbled. So i have to restart my computer to be able to play video again. Like i said, it works, then without me doing anything it just cant play video. Im thinking maybe this has something to do with the screensaver (which is the blank screen default).

Ive tried uninstalling the ati drivers (installed through envy) and restarting and installing the drivers again (in the command type thing i get since ubuntu cant load the graphical interface since i havent got any drivers), ive done this maybe 10 times now.

On my previous install i got garbled and pixelated video every time, and now i get it just sometimes. I get no artifacts and my card can still display 3d graphics when video playback crashes like this.

Yeah, on my first 4 installs of the ati drivers i only got 60hz refreshrate on my display and now i got 75hz (which it of course supports), and the first times the ati control center didnt start. 

On my last ubuntu install when i typed  "sudo aticonfig --overlay-type=Xv" i got "overlay on" or something similar, now i get

sudo aticonfig --overlay-type=Xv
Password:
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

Can anyone help me?

Thank you in advance, and sorry for my english.

---

