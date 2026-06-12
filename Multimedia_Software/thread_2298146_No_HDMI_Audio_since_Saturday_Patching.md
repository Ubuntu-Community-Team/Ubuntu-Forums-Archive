---
title: "No HDMI Audio since Saturday Patching"
date: 2015-10-09
forum: Multimedia Software
---

### Post by TheFu on 2015-10-09
This machine has been working for 6+ months.
It is a media center, NFS server, running Kodi and PlexMS.
Video over HDMI still works perfectly.
Analog audio works, but we need HDMI audio. HDMI audio worked great from the day the machine was built until about 6 days ago - I patch on Saturday mornings - though the media center only gets patched monthly to reduce issues like this.

Checked the mute. No muted. ;)

Spouse is about to kill me!

CPU is a Pentium G3258 using the onboard GPU and Intel Audio.

14.04.3 Server with openbox as the GUI.

$ uname -a
Linux istar 3.13.0-65-generic #106-Ubuntu SMP Fri Oct 2 22:08:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Alsa Info is here:
 [http://www.alsa-project.org/db/?f=e3b0a2add839bfedc0ede9a82c984e52258d6173](http://www.alsa-project.org/db/?f=e3b0a2add839bfedc0ede9a82c984e52258d6173)

$ id
uid=1000(thefu) gid=1000(thefu) groups=1000(thefu),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),126(libvirtd),128(hts)

alsamixer only shows 3 S/PDIF outputs and no other controls.  Trying to change to a different sound card in alsamixer crashes with a "17~" displayed.

TIA. Please save my relationship!

---

### Post by Yellow Pasque on 2015-10-09
If you boot into the previous kernel, does that help?

I'm curious why you have a custom asoundrc and why it references hw:0,0 when you don't have a hw:0,0.

> TIA. Please save my relationship! 
"Don't make us converse with each other!"

---

### Post by TheFu on 2015-10-10
Good question and nicely put too. ;) 

What was I thinking?  That was a quick attempt to fix the issue.  The file was added and removed - did try hw:0,3 too. 
~/.asoundrc has been deleted.  No joy.

Rebooted this morning using an older kernel 3.13.0-62-generic (was running -65). Didn't help - analog audio is working, but HDMI.

A fresh alsa-info run: [http://www.alsa-project.org/db/?f=e38658bd1210cbe7e5a582fd76326921df21a358](http://www.alsa-project.org/db/?f=e38658bd1210cbe7e5a582fd76326921df21a358)

BTW, I've checked the cables and that other HDMI video+audio sources work fine.

Thanks for looking at this and the suggestions.

---

### Post by Yellow Pasque on 2015-10-10
So if you try playing sound directly, does that work?
```
aplay -Dplughw:CARD=HDMI,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
```

Note: Your card may be something other than "plughw:CARD=HDMI,DEV=3". Use aplay to get names if that's t he case:
```
aplay -L
```

---

### Post by TheFu on 2015-10-10
Working now. Clearly, whatever the issue was, it was user error.

I tried 
$ speaker-test -Dplug:0,3 

Earlier.  Nothing happened.  The 
$ aplay -Dplughw:CARD=HDMI,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
didn't work either.  0,3 is the correct device.

Installed some Pulse-Audio utils and fiddled with those settings some. Audio started working. Wish I knew what I did. Need to purge all pulse* stuff - guess the patch session last weekend re-installed it.  I purge all pulse-audio stuff during initial system setup due to stuff like this.  I am not a fan.

Found this PulseAudio command to check for muted pulse stuff.
```
$ pactl list sinks | grep Mute
        Mute: no
        Mute: no
```
I need to remember that. If pulse is on any of my machines, time to purge it.
Anyway, it is working with Kodi now and I'm out of  the dog house for today. UT vs OU game on.

Thanks for the 2nd set of eyes!  It really does help.

---

