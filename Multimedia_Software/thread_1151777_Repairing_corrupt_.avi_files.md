---
title: "Repairing corrupt .avi files?"
date: 2009-05-07
forum: Multimedia Software
---

### Post by Scruffynerf on 2009-05-07
Ok, I have some video files, specifically .avi & .xvid.avi

File properties report "video/x-msvideo" Codec is XVID MPEG-4 @ 24 Frames/sec and Audio Codec AC-3 audio

Whenever I try to play the files, the following things happen:

MPlayer: window cycles continuously between MPlayer and "Error! [AO_ALSA] Unable to find simple control 'PCM",0. "

VLC: Launches a Qt subroutine that "Repairs" the movie file, and the movie plays fine. However it doesn't save the state - each time that the file is opened, it "repairs" the file.

Can anyone suggest an app that could repair the files and save the repaired state?

Ubuntu Jaunty, NVidia 6600GT (256MB), NVidia driver version 180.44

cheers

Scruffy.

Edit:

Googling the error message in MPlayer yields advice from the Fedora forums to switch from the ALSA audio to PulseAudio. This indeed fixes the problem in MPlayer, however VLC still "repairs" the files each time, even with VLC defaulting to Pulse drivers.

Edit 2: 

Globally changing the drivers to Pulse Audio via System -> Preferences -> Sound has a slight effect - VLC still repairs the file, but it is much faster at doing it - from perhaps a minute to 15 seconds.

Edit 3:

Found an app called DivFix++ in the repos. Played around with it, seems to create another copy of the video when 'repairing index'. That new version has the identical problem to the original - ie: It seems to do absolutely nothing.

---

