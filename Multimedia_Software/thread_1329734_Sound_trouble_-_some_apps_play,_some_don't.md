---
title: "Sound trouble - some apps play, some don't"
date: 2009-11-17
forum: Multimedia Software
---

### Post by centos on 2009-11-17
Hello, I've been having strange problems for last two or three days. Everything was fine before and I was happy that Karmic was first distro that had stable pulseaudio..
But now - it starts with launching AWN Manager on startup. It shows an error icon instead of volume control and error window pops up(screen as a attachment) with this traceback:
```
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/awn/extras/awnlib.py", line 1580, in init_start
    applet_class(applet)
  File "/usr/share/avant-window-navigator/applets/volume-control/volume-control.py", line 68, in __init__
    self.backend = ALSABackend(self)
  File "/usr/share/avant-window-navigator/applets/volume-control/volume-control.py", line 294, in __init__
    self.channels = filter(self.filter_channels, alsaaudio.mixers())
ALSAAudioError: No such file or directory
```

I have two sound cards (external SB Live and internal inside my laptop) so i use pulseaudio volume control to switch between them when I need it. Some applications works fine (SMPlayer, Rhythmbox, Totem..), but some, especially flash in browsers (FF, Chromium and Opera), and also Minitube, are muted. AND, I don't even see it in the Playing tab in Pulse Vol. Ctrl.
I'm not aware I've changed something since the time it was working.

aplay -l shows this:
```
**** Seznam PLAYBACK Hardwarových za&#345;ízení ****
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory
karta 1: External [SB Live! 24-bit External], za&#345;ízení 0: USB Audio [USB Audio]
  Podza&#345;ízení: 0/1
  Podza&#345;ízení #0: subdevice #0
```

It's strange that internal sound card is not listed there. But when I run e.g SMPlayer, I can move stream into it so it plays from internal speakers.

I'm also sometimes having problems with wifi and usb ports - like that it wasn't there. Right now I'm connected via ethernet, wifi is not active. It seems to me that my laptop is going to die soon. :/ Maybe it has something to do with my sound troubles, maybe it does not.

Thank you for any help.

---

