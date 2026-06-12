---
title: "Chrome no sound issue - but not always!  HTML5?"
date: 2015-07-28
forum: Multimedia Software
---

### Post by Swell6 on 2015-07-28
I'm running Kodibuntu Isengard 15.0 which has a Lubuntu base.  I use Chrome Launcher within Kodi to run Netflix as well as other web-based packages which has worked fine up until now.  Last day or so Netflix plays video fine but there's no sound.  The same is true for YouTube clips.  This suggests its's an HTML5 issue.  I can stream mp3s I have hosted on a box.com site, but wavs won't play!  That seems strange.

Chromium works fine with none of the above issues so its specific to Chrome.

I have tried:
- uninstalling & reinstalling
- beta version
- installing ffmpeg codecs and the extra package
- changing ALSA sliders
- deleting profile info

I also tried to access the Pulse Audio volume control from command-line but that throws up an error.  Some have reported that has a volume slider specific from Chrome, but as I can't access it I can't check that.  Strange as I say above that mp3s stream fine through Chrome, so it's not a fundamental sound issue.

Can anyone suggest what else to try?

---

### Post by Swell6 on 2015-07-29
Just to add I completely uninstalled Chrome including profile and re-installed an earlier version 40.0.2214.115-1 just in case the issue is linked to an update.  No change at all which suggests that it's not a Chrome issue, and the same issue now exists in Chromium. Maybe driver or other system related?  Its an ASRock ION 330HT HTPC so will try updating the NVIDIA drivers.  Also as mentioned above Pulse Audio throws up the following error:
[I]"Connection to PulseAudio failed.  Automatic retry in 5s
In this case this is likely because PULSE_SERVER in the environment/X11 Root Window Properties or default-server in client.conf is misconfigured.
This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window Propserties.  If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually."[/I]
The error appears in a window which can't be resized & some of the text runs off the display, so not all words may be included here, but hopefully you get the idea.  Is there anything anyone can suggest to resolve the issue with PulseAudio?

---

