---
title: "VLC jumps to beginning and sound goes off"
date: 2009-11-14
forum: Multimedia Software
---

### Post by themusicalduck on 2009-11-14
While playing certain videos in VLC (it's been only MKV files so far), after a few minutes the video will cut back to the beginning and the sound will go off. It seems like this happens when the titles of an episode of something come up after the initial preview bit.

I'm not sure if there's some kind of chaptering in place embedded in the mkv file, but if there is, it could be what's causing the problems. Is there a workaround or fix for this?

I have Ubuntu 9.10 and vlc 1.0.2.

---

### Post by themusicalduck on 2009-11-15
This is the output I get from the messages window when it happens:

```
mkv debug: seek got 0 (0%)
qt4 debug: Title 1
qt4 debug: Chapter: 5
qt4 debug: Title 1
qt4 debug: Chapter: 5
mkv debug: seek got 0 (0%)
main warning: clock gap, unexpected stream discontinuity
main warning: feeding synchro with a new reference point trying to recover from clock gap
mkv debug: seek got 0 (0%)
qt4 debug: Title 1
qt4 debug: Chapter: 5
qt4 debug: Title 1
qt4 debug: Chapter: 5
qt4 debug: Title 1
qt4 debug: Chapter: 5
qt4 debug: Title 1
qt4 debug: Chapter: 5
main warning: audio drift is too big (-123439), clearing out
main warning: mixer start isn't output start (-54056)
main debug: End of audio preroll
main debug: audio output is starving (301112), playing silence
main debug: End of video preroll
main debug: End of audio preroll
main warning: mixer start isn't output start (-57984)
main debug: End of audio preroll
main debug: End of audio preroll
```

---

### Post by themusicalduck on 2009-11-15
bump

---

### Post by alexfish on 2009-11-15
do you have vlc-plugin-pulse installed

---

### Post by themusicalduck on 2009-11-15
Yeah, and I'm using pulseaudio as the audio output too in preferences.

---

### Post by alexfish on 2009-11-16
Hi try this from the terminal and post the results if possible

$ aplay -l

$ gedit /etc/pulse/daemon.conf

other links here

[http://en.wikipedia.org/wiki/PulseAudio](http://en.wikipedia.org/wiki/PulseAudio)

[http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages](http://en.wikipedia.org/wiki/Adobe_Flash#Video_in_web_pages)

added

if you go to system admin users and groups click the box click to make changes
enter your password  and click on manage groups click do you see any entries for pulse
if there click each one in turn and then click on properties the boxes user and root need to be checked

---

### Post by themusicalduck on 2009-11-16
aplay -l says:

> **** List of PLAYBACK Hardware Devices ****
card 0: Audiophile192 [M Audio Audiophile192], device 0: ICE1724 [ICE1724]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Audiophile192 [M Audio Audiophile192], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


/etc/pulse/daemon.conf:

```
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

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
; default-sample-channels = 2
; default-channel-map = front-left,front-right

default-fragments = 8
default-fragment-size-msec = 10
```

I looked through the users and checked my name and root for any items with pulse in the name, but it hasn't helped.

---

### Post by alexfish on 2009-11-16
try looking at this thread
[http://ubuntuforums.org/showthread.php?t=1308235&page=5](http://ubuntuforums.org/showthread.php?t=1308235&page=5)

---

### Post by alexfish on 2009-11-20
Hi managed to get vlc working not 100% abit crackly at first but settles down 
 I am  going to check setting in the 

/etc/pulse/daemon.conf file


installed most via synaptic

 vlc

gstreamer010-pulse audio

libsdl1.2.debian-all

vlc-plugin-pulse

libdvdcss 

had play around with the audio settings in the vlc tools preferences / to match the setting in pulse

 ie my pulse settings are dolby 5.1

 and force detection of dolby suround sound   in vlc

its working on intel atom330 with an old hercules sound card pci  lists as CM8738

found link relating to the crackling  Listed as [SOLVED]

**Re: Penumbra Collection on Karmic - horrible crackly audio**

[http://ubuntuforums.org/showthread.php?t=1309691&highlight=pulse+crackly](http://ubuntuforums.org/showthread.php?t=1309691&highlight=pulse+crackly)

---

### Post by themusicalduck on 2009-11-20
I installed all of the packages you mentioned, but it hasn't helped :(

To be honest, I don't think the problem is to do with Ubuntu's way of handling sound but is down to a bug in VLC not handling chapters properly. I've done plenty of searching on it, and a few people have had the same problem but there doesn't seem to be a fix anywhere in existence yet.

Thanks for all your suggestions and trying to help though.

---

### Post by alexfish on 2009-11-23
hi

do you have the pulse audio device chooser installed

padevchooser     in synaptic .........  this can help a great deal 

 follow this link

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

step 6 if you have pulse

read from start 

 this can help to configure the system

---

### Post by alexfish on 2009-11-23
Knock Knock    can any one else help here

**VLC crashes.**

 Increase the verbosity level (either in the preferences or with a -vv command line option) and look at the debug messages (in the terminal or in the Messages window).
  If you are convinced that it is a bug in VLC, have a look at the [bug reporting page]("http://www.videolan.org/support/bug-reporting.html").

**VLC has a strange behavior...**

 The first thing to do is to reset the VLC preferences in the preferences dialog of the application and restart VLC. If VLC doesn't even start anymore, delete VLC's configuration file (see the previous question to know about its location). Then restart VLC. If it does not get any better, read the following questions! 
  [B]
[/B]

---

### Post by alexfish on 2009-11-23
Bump Bump

---

### Post by mrdek11 on 2009-11-30
Has anybody ever found the answer to this? I'm experiencing the same problem on Jaunty while running:
```
cvlc 2038_20091117103000.mpg --sout '#transcode{width=320,height=240,vcodec=h264,vb=960,acodec=mp4a,ab=128,channels=2}:standard{access=http,mux=ts,url=:8080}'
```

---

### Post by themusicalduck on 2009-12-03
I'm not sure if there's a fix for it. Eventually I got smplayer to work properly and I'm using that instead. Subtitles even display properly with it.

---

### Post by demis1 on 2009-12-03
I would agree with that. VLC has problems went handling chapters. Its is the way that it handles interframes. I believe that the team are aware of it and they are going to fix it at some point. 
Cheers

---

