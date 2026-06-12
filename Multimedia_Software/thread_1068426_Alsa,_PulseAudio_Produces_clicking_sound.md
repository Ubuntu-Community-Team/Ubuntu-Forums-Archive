---
title: "Alsa, PulseAudio Produces clicking sound"
date: 2009-02-12
forum: Multimedia Software
---

### Post by OSX@Linux on 2009-02-12
In Ubuntu 8.10, The Alsa and PulseAudio configurations both produce a clicking sound and nothing else. The only configuration that works is OSS. Using a Nvidia Board with Realtek HD Audio. Any help greatly appreciated

---

### Post by peppergrower on 2009-03-26
I'm suddenly experiencing the same problem (apparently).  To clarify: in Ubuntu 8.10, when I try to play back audio (e.g., from Amarok) I get instead only a clicking noise.  When I go to Preferences -> Sound, and test the various output options, the only options that *don't* produce the clicking sound when I hit "test" are the ones that use OSS.  ALSA or PulseAudio just produce a series of clicks.

In my case, this seems to coincide almost exactly with installing kde-desktop and trying KDE 4.2 out.  (Sound worked fine before this.)  Sound in KDE works just fine, but under GNOME it's broken.  I switched back to using gdm rather than kdm, but this is still broken.

Does anyone have any ideas?

---

### Post by Reeman on 2009-03-26
> **peppergrower said:**
> I'm suddenly experiencing the same problem (apparently).  To clarify: in Ubuntu 8.10, when I try to play back audio (e.g., from Amarok) I get instead only a clicking noise.  When I go to Preferences -> Sound, and test the various output options, the only options that *don't* produce the clicking sound when I hit "test" are the ones that use OSS.  ALSA or PulseAudio just produce a series of clicks.

In my case, this seems to coincide almost exactly with installing kde-desktop and trying KDE 4.2 out.  (Sound worked fine before this.)  Sound in KDE works just fine, but under GNOME it's broken.  I switched back to using gdm rather than kdm, but this is still broken.

Does anyone have any ideas?

See what sound deamons are running. esd and artsd  are most likely playing around in /dev/hell. I hate add on sound servers!

---

### Post by markbuntu on 2009-03-26
Well, KDE4 uses the new Phonon sound api which is currently using the xine backend. You need xine and the xine plugins for it to work. Though you can select gstreamer it is not working and the sound defaults to xine anyway. Amarok2 uses Phonon so......

I use pulseaudio with both KDE4 and Gnome in Intrepid and don't have any problems. If you are using KDE4 you might want to read this

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

---

### Post by ashen on 2009-04-29
I have this same problem!

I didn't install KDE, and I can't really pinpoint the exact moment it stopped working (it would have been ~ a month a go).  All I've done is the updates the update manager through at me.

I've got onboard sound - but I couldn't tell you the exact motherboard at the moment.

Any help would be gratefully received!

Cheers,

Alex

---

