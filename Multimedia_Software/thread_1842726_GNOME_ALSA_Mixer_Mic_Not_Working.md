---
title: "GNOME ALSA Mixer Mic Not Working"
date: 2011-09-12
forum: Multimedia Software
---

### Post by cessusbangy on 2011-09-12
Hi, I'm trying to stream my microphone in real-time.
I have a Logitech C300 Webcam which I'm using as my microphone, the mic is built-in and shows up as "Webcam C300 Mono" in hardware when in Sound Preferences.
When I untick the "Mic" tab in the program, the only thing I hear is a constant white noise.
I am trying to stream my mic through the speakers so that I can make 'Let's Play' videos, without recording 2 seperate tracks as this causes desync.
In the past, I have tried VLC, Mplayer, Aplay all to no avail (lag)
I have also tried RTP streaming with VLC (using the address rtp://234.5.5.5:1234), but there is STILL 1-2 second lag.
I have also tried to get this to work using Pavu control, but nothing happened.

Furthermore, I tried to use JACK as an alternative, but when I try to start  it, it says:

"[I]17:14:30.211 Patchbay deactivated.
17:14:30.212 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
17:14:30.225 ALSA connection graph change.
17:14:30.422 ALSA connection change.
17:14:32.076 Startup script...
17:14:32.076 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
17:14:32.477 Startup script terminated with exit status=32512.
17:14:32.477 JACK is starting...
17:14:32.477 /usr/bin/jackd -dalsa -r8000 -p1024 -n2 -D -Chw:2 -Phw:0 -H
17:14:32.480 Could not start JACK. Sorry.
17:14:36.827 JACK was stopped successfully.
17:14:36.828 Post-shutdown script...
17:14:36.828 killall jackd
jackd: no process found
17:14:37.234 Post-shutdown script terminated with exit status=256.
17:14:50.805 Startup script...
17:14:50.805 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
17:14:51.207 Startup script terminated with exit status=32512.
17:14:51.207 JACK is starting...
17:14:51.207 /usr/bin/jackd -dalsa -r8000 -p1024 -n2 -D -Chw:2 -Phw:0 -H
17:14:51.211 Could not start JACK. Sorry.
17:14:52.149 JACK was stopped with exit status=255.
17:14:52.149 Post-shutdown script...
17:14:52.150 killall jackd
jackd: no process found
17:14:52.556 Post-shutdown script terminated with exit status=256.
17:16:13.309 Startup script...
17:16:13.309 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
17:16:13.710 Startup script terminated with exit status=32512.
17:16:13.710 JACK is starting...
17:16:13.710 /usr/bin/jackd -dalsa -dhw:0 -r8000 -p1024 -n3 -H
17:16:13.715 Could not start JACK. Sorry.
17:16:14.524 JACK was stopped with exit status=255.
17:16:14.525 Post-shutdown script...
17:16:14.525 killall jackd
jackd: no process found
17:16:14.932 Post-shutdown script terminated with exit status=256.
17:16:21.454 Startup script...
17:16:21.454 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
17:16:21.855 Startup script terminated with exit status=32512.
17:16:21.855 JACK is starting...
17:16:21.855 /usr/bin/jackd -dalsa -dhw:0 -r8000 -p1024 -n3 -H
17:16:21.857 Could not start JACK. Sorry.
17:16:23.269 JACK was stopped with exit status=255.
17:16:23.270 Post-shutdown script...
17:16:23.270 killall jackd
jackd: no process found
17:16:23.676 Post-shutdown script terminated with exit status=256.[/I]

Here is my output from aplay-l

[I]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/I]

What am I doing wrong?

---

