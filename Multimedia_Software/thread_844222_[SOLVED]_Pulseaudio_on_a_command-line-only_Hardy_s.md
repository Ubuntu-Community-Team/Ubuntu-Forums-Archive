---
title: "[SOLVED] Pulseaudio on a command-line-only Hardy system"
date: 2008-06-29
forum: Multimedia Software
---

### Post by dominiquec on 2008-06-29
Hi, all,

I installed Hardy using the command-line-only option of the alternate installation disk.  Intention was to load OpenBox as its windowing system.

Problem is I can't get sound to work.  I think the problem might be with pulseaudio.

Anyway, here is what I've done, post-installation:

1) Installed openbox, slim, firefox, abiword, and other applications.  All working okay.

2) Installed alsa-base and alsa-utils.  Ran alsamixer, unmuted the controls and maxed out all the volume settings.

3) Installed the following packages:

pulseaudio
gstreamer0.10-pulseaudio
libasound2-plugins
pulseaudio-esound-compat
pulseaudio-module-hal
pulseaudio-module-x11
pulseaudio-utils
padevchooser
paman
paprefs
pavucontrol
pavumeter

4) Installed vlc.  Tried running a test sound file but it complains that it can't contact the pulseaudio server.

Now, the problem is that pulseaudio daemon won't start and run in the background as it should in a normal Ubuntu installation.  I've tried following the steps in [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) (added my user account to the pulseaudio groups, created /etc/asound.conf), but all to no avail.

If I do start the pulseaudio server manually, VLC runs fine.  But still...no sound.

Can anyone with a similar setup show me how to get sound working?

Thanks in advance.

---

### Post by sisco311 on 2008-06-29
Is vlc-plugin-pulse installed?

I have a similar installation.
mplayer works fine with alsa.

aptitude show vlc-plugin-pulse:
>  
Package: vlc-plugin-pulse
State: not installed
Version: 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3
Priority: optional
Section: multiverse/graphics
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 49.2k
Depends: libc6 (>= 2.4), libpulse0 (>= 0.9.8), libvlc0 (>=
         0.8.6.release.e+x264svn20071224+faad2.6.1), vlc-nox
Conflicts: vlc-pulse (< 0.5.0)
Replaces: vlc-pulse (< 0.5.0)
[B] Description: Pulseaudio audio output plugin for VLC
 This plugin adds support for the Pulseaudio to the VLC media player. To
 activate it, use the `--aout pulse' flag or select the `pulse' audio output
 plugin from the preferences menu. [/B]
 
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4, DivX,
 MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia streams
 from various network sources.


---

### Post by dominiquec on 2008-06-29
Yes it was.  It was pulled in as part of the vlc package installation.

VLC itself isn't so critical for me.  Even mplayer would do.

Could you give me the list of packages and configuration steps to get your system set up?

Thanks in advance.

---

### Post by sisco311 on 2008-06-30
Try to select alsa  from vlc or
 
install mplayer-nogui (or mplayer if you prefere the gui version) package and try it
from the  terminal:
```
mplayer -ao alsa -vo xv /path/to/file.avi
```
If you have problems with the video select the -vo x11, gl or gl2 

If this works edit the ~/.mplayer/config file:
> ao=alsa
vo=xv

In the gui right click -> Preferences -> audio and make sure alsa is selected.

---

### Post by dominiquec on 2008-06-30
It works now!  Thanks, Sisco!

Just some observations:

I had previously purged all the audio related files (listed in the original post).  This time, I just installed alsa-base and alsa-utils.  (I also deleted the /etc/asound.conf I created.)

I maxed out all the audio controls.

I installed mplayer, as per your suggestion.

During my first attempt with mplayer, I didn't get any sound :(  But then I had to reboot because mplayer and X11 went crazy (don't know why).

After reboot, I tried mplayer again and it worked!

I found I don't actually need to specify alsa.  mplayer will try pulse first, and when it doesn't find that, it defaults to alsa.

Thanks again, sisco!

---

