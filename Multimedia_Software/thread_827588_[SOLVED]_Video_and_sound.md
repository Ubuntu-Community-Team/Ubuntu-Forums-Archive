---
title: "[SOLVED] Video and sound"
date: 2008-06-12
forum: Multimedia Software
---

### Post by pitchdiesel on 2008-06-12
So video and sound were working fine, but now they lag and stutter a really impressive amount, it sounds like my computer is possessed. I'm running Hardy Heron with all updates. I really have no idea. When trying to test pipelines in system > preferences > sound, nothing seems to work properly and here's the error message I get with an ALSA test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

What a pain... I'm considering reinstalling and hoping it doesn't happen again, but there has to be a fix.

---

### Post by mastermindg on 2008-06-13
What app are you using to play audio?

---

### Post by AndThenWhat on 2008-06-13
Maybe try switching to something besides ALSA ?

---

### Post by markbuntu on 2008-06-13
You get that message because pulseaudio has hijacked your sound from alsa. I went around in circles with this by following all the helpful guides and all they did was make things worse and worse until I stopped pulseaudio from loading at boot and got the alsa-utils loading again instead.

I stopped pulseaudio by using bum (Boot Up Manager) to deselect it at startup.
and renabled the alsa-utils in Sytem/Adminstration/Services

Then I set my default alsa sound card to my sound card and changed all the sound settings everywhere to alsa. You may need to get some of these to help this work if you don't already have them:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)

libasound2-plugins (jack, OSS, pulseaudio)

libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

the firefox flash sound hijacking problem will be fixed with the new libasound2 and flash 10b that are not yet available in the repos.

---

### Post by Cruciatum on 2008-10-17
markbuntu, that fixed my same problem perfectly! Thank you!

---

### Post by SlickRick on 2008-11-05
Having same problem. I kept getting that error, so I did what markbuntu suggested. Don't get the error anymore but there's still no sound. Movie player doesn't play anything, vlc plays but I don't hear any sound, rhythmbox crashes when I try to play something and ALSA player doesn't play either. When I go to system>preferences>sound and click 'test' THAT crashes too! I feel like I'm using Windows again.:mad: What can I do? I think I might of messed up my alsa configuration file somehow.

---

### Post by SlickRick on 2008-11-06
never mind. I fixed it. Must be getting good at this linux thing ;}
thx markbuntu for that last post, that's probably what fixed it, I just needed to fiddle around a bit extra.

---

### Post by kfenton on 2009-03-11
markbuntu i think i love you.... now fix my video card as well....:D

---

### Post by markbuntu on 2009-03-11
It was a long time ago that I wrote that and I have since figured out how to get pulseaudio set up and working properly which is a better solution than the one above. The post is here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

A condensed version is here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

