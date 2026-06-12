---
title: "Installed OSS, lost all sound"
date: 2009-12-04
forum: Multimedia Software
---

### Post by LukeLinux on 2009-12-04
**BACKSTORY BEGINS HERE** (skip ahead if you want, but this might help you understand my problem): Yesterday I got my 360 controller and Tomb Raider: Legend running in Ubuntu 9.10, so I decided to give it a little run. Unfortunately, the audio was really laggy. It didn't lag at all the last time I tested out the game, so I figured it was just that WINE didn't take too well to ALSA, and I could save myself time by installing another sound driver rather than have to reboot all the time. I launched the WINE configuration and switched over to the Audio tab to see what else WINE could use. ALSA was the first option, and OSS was the second, and for that reason alone I decided to go with it.
[B]BACKSTORY ENDS HERE

[/B]Audio was working in everything using ALSA and PulseAudio running side-by-side, but after I installed OSS through apt-get, sound disappeared. In the sound preferences, my audio card ("Realtek ALC888" according to Windows, "nVidia Corporation MCP61 High Definition Audio (rev a2)" according to Ubuntu) no longer shows up. I've tried reinstalling ALSA and PulseAudio via terminal, but I can't seem to get OSS to uninstall/reinstall. Interesting thing is, audio in WINE works just fine through OSS. It's everything else that remains silent.

I've followed the comprehensive audio problem guide sticky (as well as other tutorials) with no luck. The thing is, they all seem to deal with a single audio system rather than two or three...I'm thinking maybe adding a third wasn't the best idea...

Anyone know how I could get sound back up for *everything? *Could I possibly even just reinstall some packages from the Ubuntu CD? If so, which ones?

---

### Post by swimfish on 2009-12-04
have a look at gstreamer-properties from a terminal, then set it system wide for OSS.  

also when you sudo dpkg-reconfigure linux-sound-base  that should be set to OSS as well.

i tried the mercurial checkout method of getting OSS to work under karmic, and could not get any sound, either through a optical IEC cable or analog cables.  the ubuntu wiki intstructs a person on how to do that, but it didn't work for me and my c-media Crystal HD card.

---

### Post by LukeLinux on 2009-12-04
> **swimfish said:**
> have a look at gstreamer-properties from a terminal, then set it system wide for OSS.  

also when you sudo dpkg-reconfigure linux-sound-base  that should be set to OSS as well.

i tried the mercurial checkout method of getting OSS to work under karmic, and could not get any sound, either through a optical IEC cable or analog cables.  the ubuntu wiki intstructs a person on how to do that, but it didn't work for me and my c-media Crystal HD card.

hmm....nope, still not working. The gstreamer-properties test functions check out ok, but even after setting OSS there, I still get no system sound. If I try to select ALSA it just gives me an error message ("could not open audio device for playback"), and PulseAudio just doesn't play sound. Audio in WINE is absolutely flawless now that OSS is the system default, but I use native Linux apps more than WINE, so this is definitely not a good enough fix :sad:

I hoped a reboot would maybe help, but no dice. System/Preferences/Sound Preferences still reports no sound hardware present, and the 'Output' tab is set to 'Dummy Output', no other choices available.

---

### Post by LukeLinux on 2009-12-04
Oh, by the way, I don't know if it makes much of a difference in this case, but I'm using the 64-bit edition of Ubuntu 9.10.

---

