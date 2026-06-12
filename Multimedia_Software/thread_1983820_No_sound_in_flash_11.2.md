---
title: "No sound in flash 11.2"
date: 2012-05-20
forum: Multimedia Software
---

### Post by tatsujin on 2012-05-20
(exact version of flashplugin-installer is 11.2.202.235ubuntu0.12.04.1, but I'm not sure how relevant that is)

My problem is that **only** flash fails to produce sound (video is fine). 

All other apps I've managed to find work just fine, e.g.: audacity, aplay, wine, mpd, mplayer (both also and pulse output). The working apps show up in pavucontrol's "Playback" tab when playing, like they should. Flash, in any browser, however, does not.

I've browsed in [[SOLVED] Sound troubleshooting](http://ubuntuforums.org/showthread.php?t=1885240) a bit, but those problems seemed to be more of a sort where audio doesn't work altogether.

I've checked around on ye ole 'net for solutions, and basically tried them all. 
For example:
[LIST]
[*]defaulting using /etc/asound.conf
[*]adding my user to the pulse-access group (which obviously is not the problem as other apps work)
[*]Install missing packages related to flash, pulse or alsa.
[*]Disabled my users .asound* config files.
[/LIST]

I saw somewhere of a mention of a pulse-related flash package, but maybe this is old info, as it's mentioned on [http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PerfectSetup](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PerfectSetup) that "the new flash player" (where new is v10) supports pulseaudio.

Too bad it doesn't seem to do that in my case... :(

Anyone who's had similar situation? and found a solution?! :)

Xubuntu 12.04, 64bit.

edit: changed title prefix to "all variants". I'm pretty sure it's not directly related to xubuntu.

---

### Post by tatsujin on 2012-05-20
Aah!  The ancient truth strikes again: Just after posting about a problem, a solution was found!

I was trying to install an older version of flash, and I took note of where the flashplugin-installer was downloading its stuff. Turns out there's all kinds of interesting stuff there:

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin](http://archive.canonical.com/pool/partner/a/adobe-flashplugin)

On a whim I installed the adobe-flashplugin .deb-package I found there (same version I hade before)...

... wait for it...

Let there be sound!

I actually have no idea why this helped as I assume that the adobe-flashplugin .deb-package is the same as the .tar.gz the flashplugin-installer downloads...

And yes, this is not a good solution as the adobe-flashplugin package is not in the repository so I won't get any updates for it automatically.

edit: btw, flash player appears as "ALSA plug-in" in pavucontrol, so it does, infact, not support PulseAudio.
edit2: confirmed that the .so file is exactly the same in both .tar.gz and .deb (using diff).

---

### Post by tatsujin on 2012-05-21
Another update, at least I have lots of space to roam in here ;)

Since the .so files are identical in both packages and it worked after installing the adobe-flashplugin package, I figured it must be in the install script of that package that made it start working.

So, to test my theory, I uninstalled that and then reinstalled the standard package again (flashplugin-installer), and you know what... it still works!

Still having no clue of what was fixed by adobe-flashplugin I guess I'll chalk this one down in the "unsolved mystery" column for now...

---

### Post by ken78724 on 2012-07-22
moved

---

