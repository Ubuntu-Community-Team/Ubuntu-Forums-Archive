---
title: "intel onboard sound"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by hellospencer on 2006-09-22
Hallo,

I got a probelem with the onboard sound of my Dell OptiPlex 260:

> armin@pet:~$ lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

On the top right the volume control symbol got a red mark and by double clicking it says:

> No volume control GStreamer plugins and/or devices found.

In the System/Preferences/Sound the Default Sound Card field is empty.

Following sound modules are loaded:

> armin@pet:~$ lsmod | grep snd
snd_intel8x0           33692  0
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

Anybody knows what's going on in my machine? Thanks for help and comments!

---

### Post by moore.bryan on 2006-09-22
*you could try reinstalling the gstreamer libs...*

---

### Post by hellospencer on 2006-09-27
I choose to reinstall gstreamer0.10-alsa, sinceI got the problem here:

> armin@pet:~$ gedit
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave

But unfortunately it didn't work.

Here a complete list of my installed gstreamer packages:

> armin@pet:~$ sudo dpkg -l gstreamer*
Password:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gstreamer0.10- 0.10.7-0ubuntu GStreamer plugin for ALSA
un  gstreamer0.10- <none>         (no description available)
un  gstreamer0.10- <none>         (no description available)
ii  gstreamer0.10- 0.10.3-0ubuntu GStreamer plugin for ESD
ii  gstreamer0.10- 0.10.1-0ubuntu FFmpeg plugin for GStreamer
ii  gstreamer0.10- 0.10.3-0ubuntu GStreamer plugin for OpenGL output
ii  gstreamer0.10- 0.10.7-0ubuntu GStreamer plugin for GnomeVFS
un  gstreamer0.10- <none>         (no description available)
un  gstreamer0.10- <none>         (no description available)
un  gstreamer0.10- <none>         (no description available)
ii  gstreamer0.10- 0.10.3-0ubuntu GStreamer plugins from the "bad" set
ii  gstreamer0.10- 0.10.3-3       GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10- 0.10.7-0ubuntu GStreamer plugins from the "base" set
ii  gstreamer0.10- 0.10.7-0ubuntu GStreamer helper programs from the "base" se
ii  gstreamer0.10- 0.10.3-0ubuntu GStreamer plugins from the "good" set
ii  gstreamer0.10- 0.10.3-0ubuntu GStreamer plugins from the "ugly" set
ii  gstreamer0.10- 0.10.3-2       GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10- 0.10.6-0ubuntu Tools for use with GStreamer
un  gstreamer0.10- <none>         (no description available)
ii  gstreamer0.10- 0.10.7-0ubuntu GStreamer plugins for X11 and Pango
un  gstreamer0.8-m <none>         (no description available


---

