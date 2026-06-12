---
title: "Pulse Audio questions"
date: 2012-05-25
forum: Multimedia Software
---

### Post by mckeja on 2012-05-25
I don't really have any problems playing audio from the unity desktop.  Rhythmbox works, game audio works, etc.  However, I have a wine game that refuses to play nice with a dual-monitor desktop.  So I created another X session with only one monitor configured (DISPLAY = :3) to run the game there. 

However, since upgrading to 12.04, any time I leave the Unity desktop, I lose all audio.  If I swap to another virtual display, either a console or my second X session, then I no longer hear any audio.  In fact, if I play an MP3 from the console, I do not hear it until I switch back to the Unity desktop.

My question, then, how do I change this behavior to allow audio no matter which local display I have decided to use?

---

### Post by mckeja on 2012-05-25
I read through all the Pulse Audio documentation.  I've tried a variety of searches, but found nothing useful.  

By default, gnome 3/unity/lightdm/whatever are all on virtual console 7 (CTRL-ALT-F7).  Sound played from any other virtual console is only audible if I'm currently displaying console 7 on my monitors.  So, the sound through PulseAudio is working, I just can't hear it when I'm at any console other than 7.

My second X session, which I called DISPLAY :3, is on CTRL-ALT-F8.  I've run a variety of applications from it, and they all work just fine. In particular, I can control the volume levels and see the applications plugged into PulseAudio, etc. However, I can't hear anything at all until I hit CTRL-ALT-F7 and can see the primary unity desktop again.

So, the audio is clearly working, it just isn't audible unless I'm on console 7, no matter which console it is playing on.  I want it to be audible reguardless of the console I'm currently displaying on my monitors.  Its all local.  The only other time I've encountered something like this was with a Windows XP application that would only output sound if it was the currently focused window.

---

### Post by mckeja on 2012-05-25
I may have found a workaround.  There are a lot of warnings against this, so it may not be the best solution, but.. it works.

sudo pulseaudio --system

Anyway, it points me at this page: [http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode](http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode)

But, I can now hear audio from any other X sessions or virtual consoles.  Does anyone have any advice on this subject?

---

