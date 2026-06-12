---
title: "PowerDVD intrepid issues"
date: 2009-03-14
forum: Multimedia Software
---

### Post by kumoshk on 2009-03-14
I just bought, downloaded and installed PowerDVD (the version for Ubuntu 8.10) for my new laptop. I downloaded and installed all the prerequisites. I put in a movie, and it started up to the menu screen, with the video introduction. However, the menu screen had no sound and would not respond to any key on the keyboard (I tested them all), or any click of the mouse in any location, except for where it came to turning the volume up and down. It wouldn't let me close PowerDVD, either&#8212;I'd have to use xkill to close it. It doesn't let me eject my DVD&#8212;not even after using xkill (maybe that's a hint as to what is wrong). There shouldn't be any problems with my video card. I have the driver installed, activated and everything; it's an nVIDIA GeForce 8200M G Video Card. My processor is an AMD Athlon Dual-core QL-62 (2 Ghz); I have 4GB of RAM.

Oh, I should note that after using xkill to close PowerDVD one time, I logged out and I could hear the menu screen music for a few seconds.

Any ideas on what to do?

I'm considering wiping my hard drive (there's nothing really on it, except Ubuntu and PowerDVD) and trying out the PowerDVD version for Hardy Heron (downloading the ISO now)&#8212;but I'd really like to stick with Intrepid Ibex if possible (the shut down, log-off menu is kind of nice at the very least).

---

### Post by kumoshk on 2009-03-14
Awesome, I found a way to make it work!—well, a whole lot better than not at all, at least.

The file associated with it to load the move is the wrong file, apparently (or it's not the one that works, anyhow).

The one you want instead is /opt/cyberlink/pdvd/PCM4/pdvdlinux.

I just went to the directory from the commandline and typed ./pdvdlinux. Then, it loads up something that does recognize my mouse and the DVD in the drive, and does play sound. However, I should note that the DVD I was using (To Live) still has some problems in the menu, sometimes (but you can circumnavigate the menu and turn subtitles on during the movie—or whatever). I don't know if it works well with other encrypted movies.

The file it loads with my default is pcm (in the same directory as pdvdlinux).

---

