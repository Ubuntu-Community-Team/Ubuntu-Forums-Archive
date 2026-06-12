---
title: "No Sound + System Freezing (Ubuntu Gnome 12.10/13.04)"
date: 2013-05-04
forum: Multimedia Software
---

### Post by DoubleFacepalm on 2013-05-04
Hello,

Every time I sign into Gnome shell the system freezes and I have to wait a couple of minutes before it becomes responsive. Then it randomly lags again for a minute or so during normal operation. Also, I have no sound and there are no devices in System Settings / Sound.

The system was OK after clean install but then the problem appeared somwhere after installing nVidia drivers / updates / webcam. I have tried this with Ubuntu Gnome 12.10, Ubuntu Gnome 13.04 and various nVidia drivers but it's always the same.

I managed to find a command that sometimes fixes the problem until the next restart: sudo alsa force-reload

This command usually brings sound back and the lags disappear. It also brings back sound devices into System Settings (Analogue Output-Buildin Audio and Webcam Microphone but no nVidia HDMI!). 

Is there a way to troubleshoot this?

Here's my system info:
ASRock 960GM/U3S3, AMD FX4300, nVidia Geforce 650 Ti
Audio: Realtek ALC662
Logitech C270 Webcam
Ubuntu Gnome 13.04
nVidia Drivers 319.12

Thanks a lot in advance for your help.

---

### Post by cancerkid09 on 2013-11-09
I am having a very similar issue, that started with changing my nvidia driver from an open source driver to Nvidia 319

started at:
"Nouveau display driver from xserver-xorge-video-nouveau (open source)"
     audio worked fine at this point until changed to a non open source driver
"Nvidia binary Xorg driver, kernel module and VDPAU library from nvidia-319 (proprietary, tested)"
realizing the damage that had been done i tried changing it back only to get scratching audio that seems to stem from the audio switching from my speakers to the headphone jack, very rapidly at the high points of all my music. this has nothing to do with volume.
When i go into sound settings i can see "headphone jack" flashing (appearing and disapearing) under my output audio device.  I fixed the scratching by running 
```
alsamixer
```
pressing the right arrow key to "Auto-Muted" and pressing down to change to disabled. I am now only stuck with the rapidly flashing volume manager.

I have and a couple of hard freezes that only allowed me to move my mouse. These were close to or right after bootup. Physical shutdown button is unresponsive, only reset or pulling the plug with undo this.

To any one with future issues DO NOT uninstall pulseaudio completely, i have reinstalled only to find no audio devices and no sound applet in gnome shell.

Seeing as how doublefacepalm has very similar problems but very different hardware i can only assume the driver is to blame.
I get this error from running banshee, possibly because i nuked pulseaudio.

> [Error 21:34:53.076] GStreamer library error: Shutdown
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
AL lib: alsa_open_playback: Could not open playback device 'default': Connection refused
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
AL lib: alsa_open_playback: Could not open playback device 'default': Connection refused



My Specs:
Motherboard: Intel DG41BI
CPU: intel core 2 quad Q8300
GPU: Geforce 210
Audio: HDA something...

---

