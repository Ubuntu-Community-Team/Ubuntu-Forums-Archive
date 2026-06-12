---
title: "Any audio equalizer in Ubuntu 17.10.1"
date: 2018-02-25
forum: Multimedia Software
---

### Post by calistoga1 on 2018-02-25
Hi! I'm having some troubles with Pulseaudio Equalizer, it's not working with Ubuntu 17.10, So i'm on a drifting of a good equalizer, if you know any, please answer this thread.

---

### Post by amino2111 on 2018-02-26
**Install the system-wide PulseAudio equalizer in Ubuntu or Linux Mint**


[B]To install the (unofficial) system-wide PulseAudio equalizer in Ubuntu, use the commands below:


[/B][COLOR=#000000][FONT=&amp]sudo add-apt-repository ppa:nilarimogard/webupd8
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=&amp]sudo apt-get install pulseaudio-equalizer

[/FONT][/COLOR][B]Tip from WebUpd8 reader MikeEx: if you get stuttering audio while using this equalizer, edit [I]/etc/pulse/default.pa as root with a text editor - I'll use Gedit below:

[/I][/B][COLOR=#000000][FONT=&amp]gksu gedit /etc/pulse/default.pa[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]And add "tsched=0" (without the quotes) to the "load-module module-udev-detect" and "load-module module-detect" lines - this is how it should look:

[/FONT][/COLOR]### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect **tsched=0**
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect **tsched=0**
.endif

finally visit my website to download softwares for windows: [https://www.topvoce.com](https://www.topvoce.com)

---

### Post by calistoga1 on 2018-02-27
Thanks, but that version via ppa it's not working in Ubuntu 17.10.1, because of gnome maybe ? In linux mint and another distros are working well.

---

### Post by Frogs Hair on 2018-02-27
The package is no longer available for 17.10 . Webup8 may update the PPA for 18.04 though they state the following.

> Please note that PulseAudio Equalizer is no longer maintained so if you  find a bug or if it doesn't work for you and the fix isn't trivial,  there's nothing I can do. 

---

### Post by calistoga1 on 2018-02-27
Oh well, i will just wait for the Ubuntu's update. Thanks!

---

### Post by DuckHook on 2018-02-27
I believe the webupd8 disclaimer is outdated.

Starting with Artful (and only with Artful), *pulseaudio-equalizer* is now included in Universe:```
duckhook@Zeus:~$  apt show pulseaudio-equalizer
Package: pulseaudio-equalizer
Version: 1:10.0-2ubuntu3.1
Priority: optional
Section: universe/sound
Source: pulseaudio
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Pulseaudio maintenance team <pkg-pulseaudio-devel@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 233 kB
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.9.14), libfftw3-single3 (>= 3.3.5), libpulse0 (= 1:10.0-2ubuntu3.1), pulseaudio (= 1:10.0-2ubuntu3.1), python, python-qt4, python-sip, python-qt4-dbus, python-dbus
Breaks: pulseaudio (<< 9.0-3~)
Replaces: pulseaudio (<< 9.0-3~)
Homepage: http://www.pulseaudio.org
Download-Size: 43.8 kB
APT-Manual-Installed: yes
APT-Sources: http://mirror.it.ubc.ca/ubuntu artful-updates/universe amd64 Packages
Description: Equalizer sink module for PulseAudio sound server
 PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
 WIN32 systems. It is a drop in replacement for the ESD sound server with
 much better latency, mixing/re-sampling quality and overall architecture.
 .
 This package provides an equalizer sink and an interface to configure the
 equalizer, qpaeq.
 .
 The module is called module-equalizer-sink.

N: There is 1 additional record. Please use the '-a' switch to see it
```
You should be able to install it without adding any PPA. Try disabling webupd8 PPA, then:```
sudo apt update && sudo apt install pulseaudio-equalizer
```**NOTE:** you *must* first disable the webupd8 PPA, then run *sudo apt update*.

---

### Post by cruzer001 on 2018-02-27
Nice find DuckHook, it is there.

[https://packages.ubuntu.com/artful/pulseaudio-equalizer](https://packages.ubuntu.com/artful/pulseaudio-equalizer)

---

### Post by DuckHook on 2018-02-27
@calistoga1

What do you mean by:> **calistoga1 said:**
> …it's not working with Ubuntu 17.10
This is very vague. Please explain in more detail. Is it giving poor output? Does it not launch? Mine seems to be working alright, although I do notice some lag with it, which sometimes desynchronizes audio from video in Youtube.

---

### Post by ukspreads on 2018-05-05
"There was an error importing needed librariesMake sure you have qt5 and dbus-python installed
The error that occured was:
	No module named PyQt5"
That's what I get when I try to run qpaeq :/

---

