---
title: "Help with video playback!"
date: 2008-11-28
forum: Multimedia Software
---

### Post by Silentzor on 2008-11-28
Hello!
Whenever i launch a video with vlc or any other program, it flickers between the video and a black screen very rapidly, making the video not watchable. It's like viewing an image every 0.1sec and viewing a black screen every 0.1sec again. Hope someone can help?

---

### Post by cariboo on 2008-11-28
Have you installed the ubuntu-restricted-extras meta package?

Jim

---

### Post by Silentzor on 2008-11-28
Just installed it and nothing has changed

---

### Post by c_riggan on 2008-11-28
> **Silentzor said:**
> Hello!
Whenever i launch a video with vlc or any other program, it flickers between the video and a black screen very rapidly, making the video not watchable. It's like viewing an image every 0.1sec and viewing a black screen every 0.1sec again. Hope someone can help?

I am having the very same problem...  Hope somebody can help

---

### Post by Silentzor on 2008-11-30
bump

---

### Post by mc4man on 2008-11-30
The first thing to try is change your video output module.( and sometimes sound also effects video quality)
 In vlc 0.9.x go tools -> preferences -> and in the 'simple sittings' click video and from the 'output' drop down choose smething specific. The preferred is "XVideo ..." you can try that though it may not help. If not try "X11 .." and then finally "OpenGl".

Don't forget to click save between setting changes.

You may also want to do the same for audio, move it off of default, the best choice usually is 'alsa'.

In vlc 0.8.6  same idea, go settings -> preferences and click "show advanced options".
Then expand the Video tree and highlight 'Output modules', on the r. side will be your drop down. Same for audio

In both cases you can revert to the default if needed with the 'Reset ...'  button.


Gstreamer apps and system wide is usually adjusted in System -> Preferences -and in both "Sound" and "Multimedia Systems Selector"

---

### Post by darksideforge on 2008-11-30
mc4man,
regarding sound, here is a screenshot of my current settings:

[IMG]http://i38.photobucket.com/albums/e129/diveclint/Screenshot-SoundPreferences.png[/IMG]

And here is a screenshot of my options:

[IMG]http://i38.photobucket.com/albums/e129/diveclint/Screenshot-SoundPreferences-2.png[/IMG]


Where is vlc?

---

### Post by mc4man on 2008-12-01
As i mentioned to you I never had onboard sound so don't know much about.

Personally I wouldn't have any problem with changing the setting, both in there in and in individual apps where possible. You can always change them back and you can't get any worse than the no sound you have now.

In what you show I'd try test, if no sound then switch. My inclination would be to try "ALSA...."

Then good or not, I'd try changing in vlc's settings and seeing how vlc worked. If still no good, i'd probably go back to above screen, change and then back to vlc, ect. ect.

At some point I'd ck. in multimedia system selectors also. (probably no effect on removable media, movies, and music.

If none of that worked I'd do some searching using your specific sound device as keyword.

Also i think the guide you followed has a thread, have you tried there?

---

