---
title: "Cannot get Surround Sound in 10.04"
date: 2010-07-16
forum: Multimedia Software
---

### Post by zillaxwafer@aim.com on 2010-07-16
Alsa says I'm using a HDA ATI SB audio card with realtek ALC662 rev 1. chip, I've set the default channels to 6 for 5.1 in /etc/pulse/daemon.conf but got only stereo.

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6
; default-channel-map = front-left,front-right

I would assume I have to do something with the channel map, but I don't know where to begin. I can say it is not a hardware issue as it works fine in windows 7 where my mic in is my sub-woofer/center out and my line in is my line in is my rear speaker out. I tried going into sound preferences to see if I could get it to use line in and mic in as sub-woof out and rear out , but there was no such option. All I was allowed was analog duplex 1 output / 1 input.

I'm new-ish to ubuntu and don't really know how to get this to work, I've scowered the forums but everything I've seen was for someone else's build and when i tried applying it I got nothing.

---

### Post by zillaxwafer@aim.com on 2010-07-16
Just occured to me this may be useful information:


zillaxwafer@Starscream:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

thanks in advance

---

### Post by zillaxwafer@aim.com on 2010-07-16
Also occurred you might need whole daemon.conf file:



; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = yes
; realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file =

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; rlimit-rttime = 1000000

; default-sample-format = s16le
; default-sample-rate = 44100
; default-sample-channels = 6
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10

---

### Post by lidex on 2010-07-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

You may find this helpful:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")
Scroll down to surround sound section.

---

### Post by zillaxwafer@aim.com on 2010-07-21
```
uname -a:
Linux Starscream 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dpkg -l | grep "alsa":
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                              0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                      1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 


head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI

```
This is pretty much just a custom built computer.

---

### Post by lidex on 2010-07-21
ASUS motherboard?
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by linuxyogi on 2010-08-04
> **lidex said:**
> ASUS motherboard?
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Same issue as zilla. Please visit my thread. I really need your help.

[http://ubuntuforums.org/showthread.php?t=1532400](http://ubuntuforums.org/showthread.php?t=1532400)

I just did what yo have mentioned above. After rebooting I found that the controls for the rear channels is missing from alsamixer.

My motherboard is ASUS too.

Please visit

[http://ubuntuforums.org/showthread.php?t=1532400](http://ubuntuforums.org/showthread.php?t=1532400)

There is detailed info about my sound hardware.

I am also providing the details you have asked for.

Thanks to both.

---

### Post by zillaxwafer@aim.com on 2010-10-04
So I added the line at the bottom of the daemon's conf file and played with alsa's settings and didn't get even a peep out of my rear or sub-woofer speakers. I know for a fact when I boot into windows I can use my line in as rear out and my mic in as sub-woofer out, but system> preferences >sound>hardware says i only have 1 output or 1 output/1 input. Not quite sure what to do here. Sorry it has been so long I've been using windows lately because I need music when I do _anything_ lolz. Figured I'd try taking another crack at it on Ubuntu and see if anyone has a solution yet.

---

### Post by lidex on 2010-10-05
> **zillaxwafer@aim.com said:**
> So I added the line at the bottom of the daemon's conf file and played with alsa's settings and didn't get even a peep out of my rear or sub-woofer speakers. I know for a fact when I boot into windows I can use my line in as rear out and my mic in as sub-woofer out, but system> preferences >sound>hardware says i only have 1 output or 1 output/1 input. Not quite sure what to do here. Sorry it has been so long I've been using windows lately because I need music when I do _anything_ lolz. Figured I'd try taking another crack at it on Ubuntu and see if anyone has a solution yet.

OK, you lost me. Did you add the line to alsa-base.conf?

---

