---
title: "No sound in LiveTV"
date: 2009-03-22
forum: Mythbuntu
---

### Post by NuSkooler on 2009-03-22
I am unable to hear any sound while watching LiveTV, but watching external pre-recorded content such as downloaded AVI's works fine.

Some things I've tried:
[LIST]
[*] cat someaudio.au > /dev/dsp plays the sound.
[*] Ensured that the audio device in myth-setup is /dev/dsp 44k as well as that in the frontend setup
[*] Via Gnome volume control, checked that nothing is muted/etc. Volumes are up -- same with alsamixer
[*] Tried other settings in mythfrontend such as ASLA:surround. None of these seem to output any "cannot open"/etc. errors in the console (mythfrontend -v audio)
[/LIST]

I've tried numerous things on various lists / Google searches with no luck :(

aplay -l
```
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Ubuntu 8.10
Linux nubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

```

MythTV Version   : 20205
MythTV Branch    : branches/release-0-21-fixes
Library API      : 0.21.20080304-1
Network Protocol : 40
Options compiled in:
 linux profile using_oss using_alsa using_jack using_backend using_dbox2 using_dvb using_firewire using_frontend using_hdhomerun using_iptv using_ivtv using_joystick_menu using_libfftw3 using_lirc using_opengl_vsync using_opengl_video using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmcw using_xvmc_vld using_glx_proc_addr_arb using_bindings_perl using_bindings_python using_opengl using_ffmpeg_threads using_libavc_5_3 using_live
```


Please help! I can provide any output upon request, just not sure what to post here right now.

EDIT: Something I've noticed with my current settings is that when I start LiveTV I do hear a very slight pop as if the audio is going to kick in, but there is no output. It's as if it's playing audio, but it has nothing to play.

---

### Post by NuSkooler on 2009-03-23
No ideas on this one? I've been banging my head on this for about 4 days now with no luck. Everything I've looked at seems OK, yet no sound only in Live TV :(

---

### Post by newlinux on 2009-03-24
what type of tuner card do you have? What type of content are you playing back with liveTV (analog, digital - I'm guessing digital because of the audio device you are trying to use)? Can you playback your liveTV recordings with mplayer and get any sound (you need to make sure your tuner card is capturing sound first before assuming it is a sound output problem - some tuner cards require a direct connection to the sound card for analog audio to work)? If not what error messages does mplayer output? Which audio output on your computer are you wanting to use?

post your logs with 

mythfrontend -v all

Maybe we'll see something that helps troubleshoot.

---

### Post by NuSkooler on 2009-03-26
OK, this is embarassing. The reason all my settings "checked out" is because they were correct. I did not have the analog cable plugged from my pcHD5500 -> line in. Thank you newlinux for brining something so simple to my attention :D

---

