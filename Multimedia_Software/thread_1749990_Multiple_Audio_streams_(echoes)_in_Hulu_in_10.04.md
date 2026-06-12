---
title: "Multiple Audio streams (echoes) in Hulu in 10.04"
date: 2011-05-05
forum: Multimedia Software
---

### Post by abid_naqvi83 on 2011-05-05
I recently upgraded from Ubuntu 9.10 to 10.04. Hulu worked flawlessly in the previous incarnation. Upon upgrading I discovered that if I ran a Hulu video (in either Chrome of Firefox) the ads would play normally to begin with and then suddenly audio from the actual video would appear in the background. Soon multiple audio streams (echoes) would appear.

Even when I paused the video some audio streams would continue until I closed the relevant tab of the browser.

Even for smaller videos without ads this phenomenon occurs. The video starts to play normally and then it might pause (or not) and echoes would begin to appear.

Any help would be appreciated. Thanks.

---

### Post by abid_naqvi83 on 2011-05-05
I forgot to mention that YouTube videos stream just fine so this is not necessarily a Flash issue and more likely a Hulu (or other internally ad-generated video issue).

---

### Post by frank cox on 2011-06-03
Try closing the tabs before you close the browser and if you save the settings be sure to cut off any tabs open to Hulu.
It worked for me.

---

### Post by abid_naqvi83 on 2011-06-03
Sorry, I am not sure I understand what you are suggesting. Would you be kind enough to elaborate?

---

### Post by configt on 2011-07-14
I am having the same problem with Hulu Desktop on 10.04 amd64 (the desktop package, not from a browser) where it sounds like 2 audio streams of the same stream are playing over each other like a canon, making it sound like an echo.  

Did anyone find a fix for it yet?

:popcorn:

---

### Post by randoker on 2011-10-12
Hey guys and gals,

I have windows XP and i *intermittently* have the same issue with IE, firefox, and chrome. When it happens, it happens on all three. I'm not sure what that means...

Anyway, just wanted to let you know it's not strictly an Ubuntu issue. Hope that helps narrow it down.

---

### Post by abid_naqvi83 on 2011-11-23
In the beginning I stopped watching Hulu (seeing as it was impossible). A few weeks ago I tested the Luakit micro-browser framework and it turns out the luakit was successful where Chrome and Firefox were failing miserably. I was able to play Hulu videos (both native window and fullscreen).

A few days ago the flash audio on my system started interfering with the Audacious and VLC audio - if flash audio was already playing (or the video had been played and paused) Audacious would refuse playback (the counter would stutter back and forth by a second) and VLC would play videos without sound. Conversely if VLC or Audacious were playing then newly opened flash videos would play  without sound.

I am uncertain as to what caused these problems, it might have been me fiddling with the Wine configuration or possibly the most recent Kernel update.

I despaired of solving this issue using Pulseaudio and ALSA and finally succumbed and installed OSS4 instead using the instructions provided in [http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html]("http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html"). I chose NOT to remove Pulseaudio but simply edit the necessary configuration file to pass streams to OSS4.

Not only did this move solve the flash vs VLC/Audacious audio issues but I discovered a few days later that the multiple audio streams (echoes) in Hulu problem (in Chrome and Firefox) had also been solved. I can now watch videos on Hulu in both the native Window and fullscreen mode.

However there are issues with the pop-out window in Hulu. The ads run just fine and then the actual video starts, stalls (the screen blacks out) and keeps starting and stalling without any significant headway. This problem appears in luakit as well, if I am sneaky and copy the pop-out window's html link directly in to luakit (normally luakit refuses to open up the pop-up window).

Any help on this latest problem is appreciated. In the mean time those of you who are having multiple audio stream problems in Hulu may wish to try out luakit and the OSS4 sound module.

---

### Post by abid_naqvi83 on 2012-09-12
Update: I still don't know what caused the initial problem and what exactly solved it but I am currently using Ubuntu 12.04 with Pulseaudio (I completely removed OSS4 and did a clean install of the audio software on the system) and haven't had problems with Hulu for a while. Hopefully this will remain the case.

---

