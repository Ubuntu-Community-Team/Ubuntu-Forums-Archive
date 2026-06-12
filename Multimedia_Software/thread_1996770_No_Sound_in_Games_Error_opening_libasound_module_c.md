---
title: "No Sound in Games: Error opening libasound_module_conf_pulse.so - Ubuntu 12.04"
date: 2012-06-04
forum: Multimedia Software
---

### Post by Routhinator on 2012-06-04
ia32-libs: Installed
libasound2: Installed
libasound2-plugins: Installed

Affected: All native 32-bit games.
Test samples: Loki Games (Majesty, HMM3), Osmos, Braid, World of Goo, Aquaria

Error Produced:

```
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
InitDriver [cglib/src/linux/cylinuxsnd.cpp:1285]: ***ERROR***: SDL_mixer error: ''

```

I have found a few forums and 'Ask Ubuntu' posts related to this, but the fixes are either game specific, or do not work on every system. I believe we should get a forum going with a fix that will correct the issue for all games.

Here's what I've found so far:

Fix specific to World of Goo: [http://ubuntuforums.org/showthread.php?p=11806027](http://ubuntuforums.org/showthread.php?p=11806027)

Fix for HMM3 attempting to preload the missing library (Does not work for all users):

[http://askubuntu.com/questions/142956/installing-old-loki-games-on-12-04-64-bit-results-in-no-audio/145570#145570](http://askubuntu.com/questions/142956/installing-old-loki-games-on-12-04-64-bit-results-in-no-audio/145570#145570)


======

Has anyone fixed this or does anyone know of a way to fix this system-wide? Or does it look like something we need to report to the ia32=libs devs?

---

### Post by satbunny on 2012-07-02
Not that this helps but it broadens:

> tomzunder@Inspiron-530-n:~$ pasuspender ~/majx
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
InitDriver [cglib/src/linux/cylinuxsnd.cpp:1285]: ***ERROR***: SDL_mixer error: ''


Using pasuspender is the option that LGP recommend, and indeed I remember that it worked fine on an earlier Ubuntu (that had Pulse Audio) but not, no sound.

Any suggestions on what to install, tweak or otherwise mess around with ?

In the meantime I'll frig my system so my SCSI scanner is recognised..

---

### Post by sol-invictus on 2012-09-18
i have the same problem!

is there any solution for that problem? using pasuspender is not working for me too...

> user@computer:/opt/majesty-gold$ ./majesty 
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
InitDriver [cglib/src/linux/cylinuxsnd.cpp:1285]: ***ERROR***: SDL_mixer error: ''

---

