---
title: "vokoscreen with black  frame"
date: 2021-01-26
forum: Multimedia Software
---

### Post by Freiklite on 2021-01-26
Hi,
Vokoscreen doesn't record the frame only the sound.
I didn't find one solution in the forum posts.

Some informations:```
 [vokoscreen] Version: "2.5.0"
 [vokoscreen] Locale: "fr_FR"
 [vokoscreen] Qt version:  5.12.8
 [vokoscreen] Operating system: "ubuntu 20.04"
 [vokoscreen] Desktop: "ubuntu:GNOME"
 [vokoscreen] asoundlib version: "1.2.2"
 [vokoscreen] current icon-theme: "breeze"
 [vokoscreen] Qt-PluginsPath:      "/usr/lib/x86_64-linux-gnu/qt5/plugins"
 [vokoscreen] Qt-TranslationsPath: "/usr/share/qt5/translations"

 [vokoscreen] Qt-LibraryPath:      "/usr/lib/x86_64-linux-gnu"
   
 [vokoscreen] ---Begin Search external tools---
 [vokoscreen] Search ffmpeg     ..... found "/usr/bin/ffmpeg" Version: "ffmpeg version 4.2.4-1ubuntu0.1 Copyright (c) 2000-2020 the FFmpeg developers"
 [vokoscreen] Search pactl      ..... found Version: "pactl 13.99.1"
 [vokoscreen] Search xdg-email  ..... found Version: "xdg-email 1.1.3"
 [vokoscreen] Search lsof       ..... found Version: "revision: 4.93.2"
 [vokoscreen] ---End search external tools---
   
 [vokoscreen] ---Begin search Screen---

 [vokoscreen] Number of screens: 1
 [vokoscreen] Primary screen is: Display 1
 [vokoscreen] VirtualDesktop: false
 [vokoscreen] DevicePixelRatio: 1  (Normal displays is 1, Retina display is 2)
 [vokoscreen] "Display 1:  1600 x 900"
 [vokoscreen] ---End search Screen---
   
 [vokoscreen] ---Begin Environment---
 [vokoscreen] runs on DISPLAY ":0"
 [vokoscreen] ---End Environment---
   
 [vokoscreen] detect codecs with "/usr/bin/ffmpeg"
 [vokoscreen] ---Begin search formats---
 [vokoscreen] find Format "mkv"
 [vokoscreen] ---Begin search video codec---
 [vokoscreen] find Videocodec "libx264"
 [vokoscreen] find Videocodec "mpeg4"
 [vokoscreen] find Videocodec "huffyuv"
 [vokoscreen] ---End search video codec---
   
 [vokoscreen] ---Begin search audio codec---
 [vokoscreen] find Audiocodec "libmp3lame"
 [vokoscreen] find Audiocodec "libvorbis"
 [vokoscreen] find Audiocodec "pcm_s16le"
 [vokoscreen] not found Audiocodec "libvo_aacenc"
 [vokoscreen] find Audiocodec "aac"
 [vokoscreen] ---End search audio codec---
   
 [vokoscreen] find Format "mp4"
 [vokoscreen] find Format "gif"
 [vokoscreen] ---End search formats---
   
 [vokoscreen] ---Begin search Videoplayer---
 [vokoscreen] Find Videoplayer : "/snap/bin/vlc"
 [vokoscreen] Find Videoplayer : "/usr/bin/totem"
 [vokoscreen] Find Videoplayer : "/usr/bin/dragon"
 [vokoscreen] ---End search Videoplayer---
   
 [vokoscreen] ---Begin search GIFplayer---
 [vokoscreen] Find GIFplayer : "firefox"
 [vokoscreen] ---End search GIFplayer---
   
 [vokoscreen] ---Begin Pulse unload Module---
 [vokoscreen] ---End Pulse unload Module---
   
 [vokoscreen] ---Begin search devices---
 [vokoscreen] find device "x11grab"
 [vokoscreen] ---End search devices---
   
 [vokoscreen] ---Begin search Alsa capture device---
 [vokoscreen] Find CaptureCard: "[hw:0,3] HDA ATI HDMI"
 [vokoscreen] Find CaptureCard: "[hw:1,0] HD-Audio Generic"
 [vokoscreen] ---End search Alsa capture device---
   
 [vokoscreen] ---Begin search PulseAudio Capture Devices---
 [vokoscreen] Find CaptureCard: "Monitor of Audio interne Stéréo analogique" with device: "alsa_output.pci-0000_00_14.2.analog-stereo.monitor"
 [vokoscreen] Find CaptureCard: "Audio interne Stéréo analogique" with device: "alsa_input.pci-0000_00_14.2.analog-stereo"
 [vokoscreen] ---End search PulseAudio Capture Devices---
   
  
```

espacially```
[vokoscreen] ---Begin search Screen---

 [vokoscreen] Number of screens: 1
 [vokoscreen] Primary screen is: Display 1

 [vokoscreen] VirtualDesktop: false
 [vokoscreen] DevicePixelRatio: 1  (Normal displays is 1, Retina display is 2)
 [vokoscreen] "Display 1:  1600 x 900"
 [vokoscreen] ---End search Screen---
   
 [vokoscreen] ---Begin Environment---
 [vokoscreen] runs on DISPLAY ":0"
 [vokoscreen] ---End Environment---


```
We can read " Primary screen is: Display 1" and "runs on DISPLAY ":0"". Is this normal?

Ubuntu-wayland:```
$ uname -a
Linux SATELLITE-C70D-B 5.4.0-64-generic #72-Ubuntu SMP Fri Jan 15 10:27:54 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


```

Thank you very much for any suggestion,
Ciao

---

### Post by Holger_Gehrke on 2021-01-26
The 'Display 1:' and 'DISPLAY ":0' refer to different things. The all caps "DISPLAY" is an environment variable that holds the address for the display server (leaving off the hostname or IP address at the beginning of the value means it's a display server running on localhost; it's quite normal to run programs on one machine and have them display on another one, in that case you'd have to set DISPLAY on the machine running the program; it's also possible to have multiple display servers on one machine - I think vnc does something like that ...). 'Display 1:' is just a description of the first connected physical display. So yes, this is normal and probably right.

I'm not sure Vokoscreen can record from Wayland. Try logging into an X11 session and record from that.

Holger

---

### Post by Freiklite on 2021-01-27
Hi,
Thanks very much for your answer.
some information:
> 
[vokoscreen] "/usr/bin/ffmpeg" is running and is ready for reading and writing   
[vokoscreen] "/usr/bin/ffmpeg" is not running 

and also:
> [vokoscreen] ---Begin search devices--- 
[vokoscreen] find device "x11grab" 
[vokoscreen] ---End search devices--- 
.
I found at [HTML]https://samiux.blogspot.com/2018/04/howto-fix-vokoscreen-250-on-parrot.html[/HTML] 
```
wget http://linuxecke.volkoh.de/vokoscreen/ffmpeg-64bit.tar.gz
tar -xvzf ffmpeg-64bit.tar.gz
sudo mv /usr/local/bin/ffmpeg /usr/local/bin/ffmpeg-original
sudo cp ffmpeg /usr/local/bin/
```

but :
> Connexion à linuxecke.volkoh.de (linuxecke.volkoh.de)|213.133.104.62|:443&#8230; connecté.
requête HTTP transmise, en attente de la réponse&#8230; 404 Not Found
2021-01-27 13:22:10 erreur 404 : Not Found.

Vokoscreen is crashed by ffmpeg.

I do :
> **Installing FFmpeg 4.x on Ubuntu**

The FFmpeg version 4.x adds a number of new filters, encoders, and decoders.
The easiest way is to install FFmpeg 4.x on Ubuntu 18.04 is by using the [snappy]("https://snapcraft.io/") packaging system.
Open your terminal by pressing Ctrl+Alt+T and install the FFmpeg snap package, by typing:
sudo snap install ffmpeg
I reboot.

There is* no improvement *in sight.
Ciao

---

### Post by CelticWarrior on 2021-01-27
If you installed the ffmpeg snap then make sure to give it all the required permissions. The easy way is to open the snap store, the standard app store Ubuntu comes with, search for ffmpeg and click on its page. There you'll find a "permissions" button.

---

### Post by Holger_Gehrke on 2021-01-27
Vokoscreen 2.5 from the repositories works fine on XUbuntu 18.04 with ffmpeg 3.4.8 in an X11 session. So it's not the ffmpeg version responsible for your problems. Since I don't have Wayland installed (XFCE doesn't yet work with Wayland, a major rewrite of several components would be necessary to make it work ...) I can't check whether Vokoscreen works with Wayland. Since version 2.5 of Vokoscreen was published in 2016 (at least according to /usr/share/doc/vokoscreen/copyright, which seems right since work on vokoscreen-ng started in 2017), I rather doubt it does. You should really try running it in an X11 session. There should be a way to select the display-server on the login-screen.

Holger

---

### Post by Freiklite on 2021-01-27
Hi,
All is OK: sessions Gnome on Xorg, xfce, xubuntu, and Ubuntu.
Vokoscreen doesn't work: sessions Gnome et Ubuntu on Wayland.

Thanks very much for all,
Ciao.

---

