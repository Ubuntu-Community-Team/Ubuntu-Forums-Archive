---
title: "no sound, pulseaudio stuck, &quot;audio and video settings&quot; stuck, spinning cursor"
date: 2014-02-12
forum: Multimedia Software
---

### Post by chrisco23 on 2014-02-12
I had been running pulse with the jack sink setup, so I could try some linux audio with ardour, etc.

Everything was working fine but with this setup I could not use my headset, so I could not do work with skype or Google Hangouts.

Finally I decided to just do without jack for now and tried to go back to vanilla pulseaudio.

I purged and reinstalled numerous times following numerous threads I found in various places.

At this point, pavucontrol sits at "Establishing connection to PulseAudio.  Please wait..."

Going into systemsettings, then "Multimedia", is ok until I click "Audio and Video Settings".  Then I get some spinning cursor and it never makes progress.

I'm stumped.  Anybody have any suggestions here?


Thanks,
Chris

---

### Post by chrisco23 on 2014-02-12
[UPDATE]
OK, after another hour of battle I can now run pulse with "pulse -D", and I can play banshee.

The problem with systemsettings just giving spinning cursor for "audio and video settings" remains.

---

### Post by Bucky Ball on 2014-02-12
Switch off jack and try again. Close QJackctl if that's what you're using. Jack will 'take over' audio settings. That is what it is for.

---

