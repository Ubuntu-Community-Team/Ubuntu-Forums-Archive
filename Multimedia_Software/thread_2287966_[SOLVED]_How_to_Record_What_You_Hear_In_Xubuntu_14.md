---
title: "[SOLVED] How to Record What You Hear In Xubuntu 14.10?"
date: 2015-07-23
forum: Multimedia Software
---

### Post by lambdafox on 2015-07-23
Can anyone point me to a how-to that explains how to do this with Xubuntu, Alsa, etc?

[Here is a web page]("http://www.howtogeek.com/217348/how-to-record-the-sound-coming-from-your-pc-even-without-stereo-mix/?PageSpeed=noscript") that shows how to do it in Windows. I am a linux noob; so, I am looking for similar stoopid-proof instructions for Xubuntu 14.10...

Thank you.

---

### Post by kostkon on 2015-07-23
Install the PulseAudio Volume Control utility (pavucontrol). You can use Audacity to do the recording.

Start recording in Audacity then open pavucontrol, click on Recording and set the device for the Audacity input stream to the Monitor of your soundcard.

---

### Post by lambdafox on 2015-07-24
> **kostkon said:**
> Install the PulseAudio Volume Control utility (pavucontrol). You can use Audacity to do the recording.

Start recording in Audacity then open pavucontrol, click on Recording and set the device for the Audacity input stream to the Monitor of your soundcard.

Thank you.  That is the easy kind of answer I was looking for!:p

Sadly, when I run pavucontrol, I get an error message:confused::

```
Connection to PulseAudio failed.  Automatic retry in 5s

In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is miscofigured.

This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window.

If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulse-audio-x11 manually.
```

echo $PULSE_SERVER returns a blank line.

You can see in /etc/pulse/client.conf default-server is not set to anything:

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

## Configuration file for PulseAudio clients. See pulse-client.conf(5) for
## more information. Default values are commented out.  Use either ; or # for
## commenting.

; default-sink =
; default-source =
; default-server =
; default-dbus-server =

; autospawn = yes
; daemon-binary = /usr/bin/pulseaudio
; extra-arguments = --log-target=syslog

; cookie-file =

; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB

; auto-connect-localhost = no
; auto-connect-display = no

```

I do not know what I should put there...

---

### Post by Dennis N on 2015-07-24
Here is how I set Audacity and Pulse Audio Volume Control to record what is playing through my speakers:

[http://ubuntuforums.org/showthread.php?t=2234397&p=13073700#post13073700](http://ubuntuforums.org/showthread.php?t=2234397&p=13073700#post13073700)

As to the file you show, mine is the same. It's all comments, and therefore not being used. So it is probably not the problem. If I think of any further suggestions, I will post back.

---

### Post by mörgæs on 2015-07-24
Before wasting time on 14.10 which is out of support as of yesterday I recommend a fresh install of 14.04.2 or 15.04.

---

### Post by Dennis N on 2015-07-24
In moving to 15.04 or 14.04 - Remember that pulse audio and pulse audio volume control are installed by default in both (Xubuntu), so all that's necessary is installing Audacity to give you a fresh start. Follow my linked guide and all will be well.

Good luck.

---

### Post by monkeybrain20122 on 2015-07-24
A very easy solution [https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder](https://launchpad.net/~osmoma/+archive/ubuntu/audio-recorder)

---

### Post by lambdafox on 2015-07-27
> **lambdafox said:**
> ...

Sadly, when I run pavucontrol, I get an error message:confused::

```
Connection to PulseAudio failed.  Automatic retry in 5s

In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is miscofigured.

This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window.

If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run start-pulse-audio-x11 manually.
```

...

With a little googling, I discovered that PulseAudio was creating a file, ~/.config/pulse/cookie, with the wrong permissions.

It made me the owner and gave me rw permission, but set no group or other permissions.  Allowing others read permission on this file fixed the problem.

Thank you all for your help

---

### Post by Dennis N on 2015-07-27
> **lambdafox said:**
> With a little googling, I discovered that PulseAudio was creating a file, ~/.config/pulse/cookie, with the wrong permissions.

It made me the owner and gave me rw permission, but set no group or other permissions.  Allowing others read permission on this file fixed the problem.

Thank you all for your help
Wow, that's great that you discovered a solution, but also puzzling why it worked. When I look at that file on my system it has the same permissions, and there are no problems.
```
dmn@Sydney:~/.config/pulse$ ls -l cookie
-rw------- 1 dmn dmn 256 Nov 13  2014 cookie

```
Maybe changing permissions here serves as a workaround for some other problem? But, glad you were able to solve it.

---

### Post by lambdafox on 2015-07-27
it may have to do with the fact that my install is a little bizarre.  I used xubuntu-core because just about every app i prefer is not the standard w xfce.  i also have synaptic set to not install recommends by default.

---

