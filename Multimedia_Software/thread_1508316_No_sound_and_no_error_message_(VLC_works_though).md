---
title: "No sound and no error message (VLC works though)"
date: 2010-06-12
forum: Multimedia Software
---

### Post by pieroxy on 2010-06-12
Since about a day, mplayer and youtube (flash plugin) don't output any sound anymore. when playing a MP3 with mplayer it plays really fast (like 5x) and no sound is heard. whan playing a video (flash of mplayer) the video is ultra fast and no sound is played.

VLC is working fine...

```
pieroxy@pieroxy-linux:~/Music/OK/Air/Talkie Walkie$ time mplayer 01\ Air\ -\ Venus.flac.mp3 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 01 Air - Venus.flac.mp3.
Audio only file format detected.
Clip info:
 Title: Air - Venus.flac
 Artist: Air
 Album: Talkie Walkie
 Year: 2004
 Comment: 
 Track: 1
 Genre: Electronic
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 320.0 kbit/22.68% (ratio: 40000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 244.3 (04:04.3) of 246.0 (04:06.0)  0.5% 

Exiting... (End of file)

real	0m43.916s
user	0m1.392s
sys	0m0.216s
pieroxy@pieroxy-linux:~/Music/OK/Air/Talkie Walkie$ 

```

Any help will be appreciated.

---

### Post by dan335 on 2010-06-13
I'm having a similar problem! I can't get audio on any MPEG-2 videos with MPEG Streamclip or Quicktime Player, VLC is fine though. I just installed an update for Quicktime Player after being prompted by my Mac, that's when the audio disappeared - only on MPEG-2 videos. I've tried re-installing the MPEG-2 codec but that didn't help.

---

### Post by lidex on 2010-06-13
Try changing your audio output device in MPlayer preferences.

---

### Post by pieroxy on 2010-06-13
Hi lidex

Thanks for the tip, and it did the trick !

Now, I'm back to my problem with flash. After trying around different -ao options, it turns out ALSA is broken on my system - so I'm using oss and everything is fine. This is probably why all the trouble. I'm going to try to look around for a fix.

Thanks again!

---

### Post by lidex on 2010-06-13
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

---

### Post by pieroxy on 2010-06-14
I actually got my sound back, but I have to do the same tweak every time I boot up so it is very annoying. I click the sound level icon -> Sound Preferences -> Output. In there I see only the HDMI output from the ATI GC... So I go to Hardware and select my "Internal Audio Analog Stereo Output" card, then back to Output I can now see the "Internal Audio Analog Stereo" which I can select. From then on it works until reboot where I have to do it all over again.


```
pieroxy@pieroxy-linux:~$ uname -a
Linux pieroxy-linux 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
pieroxy@pieroxy-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pieroxy@pieroxy-linux:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                            14.3.0-1.1build1                                SoX alsa format I/O library
pieroxy@pieroxy-linux:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

---

### Post by lidex on 2010-06-14
> **pieroxy said:**
> I actually got my sound back, but I have to do the same tweak every time I boot up so it is very annoying. I click the sound level icon -> Sound Preferences -> Output. In there I see only the HDMI output from the ATI GC... So I go to Hardware and select my "Internal Audio Analog Stereo Output" card, then back to Output I can now see the "Internal Audio Analog Stereo" which I can select. From then on it works until reboot where I have to do it all over again.


```
pieroxy@pieroxy-linux:~$ uname -a
Linux pieroxy-linux 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
pieroxy@pieroxy-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pieroxy@pieroxy-linux:~$ dpkg -l | grep "alsa"
ii  alsa-base                                  1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                 1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                 4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                         0.10.28-1                                       GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transition
rc  libsdl1.2debian-alsa                       1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
ii  libsox-fmt-alsa                            14.3.0-1.1build1                                SoX alsa format I/O library
pieroxy@pieroxy-linux:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```
Here's what I would do. Install these:
```
sudo apt-get install alsa-oss gnome-alsamixer
```
An alsa upgrade is optional if this next doesn't work.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel probe_mask=1 
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

### Post by pieroxy on 2010-06-17
So... For the last three days I've been trying to reproduce the issue but I can't. I don't know what I did except play with the sound settings dialog (accessible from the sound icon in the dock) It means that it does work now on my system...

I will keep this thread around in case it breaks down again. Thanks for your help in any case.

---

