---
title: "get sound from multiple programs"
date: 2009-06-18
forum: Multimedia Software
---

### Post by kilgore9 on 2009-06-18
Hey there.  I'm on Jaunty, really loving it!  One thing that bugs me though it that sounds only seems to work in one application at a time.  For example, when I'm watching a video, skype sounds will not play.  Sound for some programs also will only work when other audio programs are turned off.

any way to set it up so that I can have multiple open programs and have all sounds working?

---

### Post by kilgore9 on 2009-06-25
really?  no one knows a way to do this?

---

### Post by dayers on 2009-06-25
Is this the kind of thing you are experiencing?

I'm running Kubuntu Jaunty on a Dell workstation. If I am listening on Amarok, stop what's playing to listen to, say, a video on YouTube, the video will have no sound. Same for a video on Wall Street Journal Online. Same for opening a VMware VM. No sound. It seems that the first app I use with sound locks up sound, even after I quit the app.

I have to log out and log back in to release the death grip on /dev/dsp.

---

### Post by Nubi505 on 2009-06-25
I'm having the same problem using Ubuntu 9.04 and would like to know the same thing.

---

### Post by kilgore9 on 2009-06-26
yes dayers, thats pretty much what I'm experiencing.  Usually just quitting the program (or dong a pkill) will take care of the "death grip", though a few times I have had to restart to get the sound back to a particular program.
It seems like there should be a way to tell the system to allow multiple programs to use the same sound device.  In my non-programmer mind it seems really simple...

---

### Post by lovinglinux on 2009-06-26
Open "System >> Preferences >> Sound" an change the audio settings to "ALSA" also open gstreamer-properties and do the same. This might help.

Some tutorials that might help:

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)
[PulseAudio Fixes & System-Wide Equalizer Support](http://ubuntuforums.org/showthread.php?t=789578)
[Multiple Sound Solution (ALSA w Pulseaudio)](http://ubuntuforums.org/showthread.php?t=843012)

---

