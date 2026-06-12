---
title: "mpv backend doesn't prevent screen from dimming"
date: 2023-04-30
forum: Multimedia Software
---

### Post by kabirgandhiok on 2023-04-30
Hi,

While watching any video on mpv player (without an mpv frontend), the screen dims as per the system power settings. Mpv player does not prevent this behavior. The only workaround I have found is to use an mpv frontend like celluloid player.

From what I have read on other forums, mpv backend does not inhibit screen dimming on wayland, this problem does not happen on xorg.

Even after adding wayland in mpv.conf the behavior doesn't change:
```

save-position-on-quit
--geometry=1024x768+0+0
--gpu-backend=wayland

```

I would like to use mpv player without any front end, but it's not possible if it doesn't prevent the screen from dimming.

Any suggestions on how I could get it to work?

Thanks!

---

### Post by TheFu on 2023-04-30
It happens on X11 here.  To prevent it, I have a little script that disables dimming/blanking while mpv is use, then enables it when mpv is closed.  Or just move the mouse 1 pixel. That will prevent it too.

Really, I only so the screen blanking disable when I'm using a screen capture tool like SimpleScreenRecorder.
```
$ more ~/bin/ssr.sh 

xset s off &
xset -dpms &

# Disable the screensaver
/usr/bin/xscreensaver-command -exit

/usr/bin/simplescreenrecorder

# Enable the screensaver
/usr/bin/xscreensaver &

xset +dpms &
xset s on &
```

YMMV, especially if you use a different screen saver program.
I haven't any clue about Wayland.  It broke too many important workflows for my use at this point.  Perhaps in 2024, I'll check again.

---

### Post by #&amp;thj^% on 2023-04-30
TheFu suggestion used to work, currently, now use's:
GNOME Blank screen (Wayland)

mpv may not suspend GNOME's Power Saving Settings if using Wayland resulting in screen saver turning off the monitor during video playback. A workaround is to_add ** gnome-session-inhibit to the beginning of the Exec= line in mpv.desktop._**

In order to inhibit the screensaver only during playback, use mpv_inhibit_gnomeAUR. Alternatively, a mpv lua script based on gnome-session-inhibit may be used.
**Tip: The io.mpv.Mpv flatpak app already includes the mpv_inhibit_gnome plugin. **
There you go you have choices now.
I also don't think Wayland is ready for my use.:P
```
[Desktop Entry]
X-AppInstall-Package=mpv
X-AppInstall-Popcon=126
X-AppInstall-Section=universe

Type=Application
Name=mpv Media Player
GenericName=Multimedia player
Comment=Play movies and songs
Icon=mpv
TryExec=/usr/bin/mpv
Exec=/usr/bin/mpv --profile=pseudo-gui -- %U
Terminal=false
Categories=AudioVideo;Audio;Video;Player;TV;
MimeType=application/ogg;application/x-ogg;application/sdp;application/smil;application/x-smil;application/streamingmedia;application/x-streamingmedia;application/vnd.rn-realmedia;application/vnd.rn-realmedia-vbr;audio/aac;audio/x-aac;audio/m4a;audio/x-m4a;audio/mp1;audio/x-mp1;audio/mp2;audio/x-mp2;audio/mp3;audio/x-mp3;audio/mpeg;audio/x-mpeg;audio/mpegurl;audio/x-mpegurl;audio/mpg;audio/x-mpg;audio/rn-mpeg;audio/ogg;audio/scpls;audio/x-scpls;audio/vnd.rn-realaudio;audio/wav;audio/x-pn-windows-pcm;audio/x-realaudio;audio/x-pn-realaudio;audio/x-ms-wma;audio/x-pls;audio/x-wav;video/mpeg;video/x-mpeg;video/x-mpeg2;video/mp4;video/msvideo;video/x-msvideo;video/ogg;video/quicktime;video/vnd.rn-realvideo;video/x-ms-afs;video/x-ms-asf;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-wvxvideo;video/x-avi;video/x-fli;video/x-flv;video/x-theora;video/x-matroska;video/webm;audio/x-flac;audio/x-vorbis+ogg;video/x-ogm+ogg;audio/x-shorten;audio/x-ape;audio/x-wavpack;audio/x-tta;audio/AMR;audio/ac3;video/mp2t;audio/flac;
X-KDE-Protocols=ftp,http,https,mms,rtmp,rtsp,sftp,smb

X-Ubuntu-Gettext-Domain=app-install-data

``` 
So i don't need this work-around.

---

### Post by TheFu on 2023-04-30
I haven't used any .desktop file in years.  The reason to use MPV without a GUI is to run it from a terminal, where no .desktop file would be used.
I can assure you that script above works TODAY with X11.  Nice to easily queue up 1 or 500 videos with a simple command:
```
$ mpv *kv *p4
```

If the OP posted a specific release and specific DE, then we'd know more and could customize the answer.  As usual, the man pages have the answer to this question.  The manpage for mpv:
```
       --stop-screensaver, --no-stop-screensaver
              Turns  off the screensaver (or screen blanker and similar mecha&#8208;
              nisms) at startup and turns it on again on exit (default:  yes).
              The screensaver is always re-enabled when the player is paused.

              This  is  not supported on all video outputs or platforms. Some&#8208;
              times it is implemented, but  does  not  work  (especially  with
              Linux "desktops").
```
If that option doesn't work, then something outside is necessary. What to use would depend on the release and DE and screen saver.

---

### Post by #&amp;thj^% on 2023-04-30
> **TheFu said:**
> 
I can assure you that script above works TODAY with X11.  Nice to easily queue up 1 or 500 videos with a simple command:
```
$ mpv *kv *p4
```


Most definitely still works on X11, and it used to work on wayland as well, but not so now.
> **TheFu said:**
> 
If the OP posted a specific release and specific DE, then we'd know more and could customize the answer. 
They did in round-about way:
> From what I have read on other forums, mpv backend does not inhibit screen dimming on wayland, _this problem does not happen on xorg._

Even after adding wayland in mpv.conf the behavior doesn't change:

---

### Post by kabirgandhiok on 2023-04-30
Thanks so much @fallen1 and @TheFu for your suggestions.

I added to the mpv.desktop file
```

Exec=gnome-session-inhibit

```

and in mpv.conf the stop screensaver option
```

save-position-on-quit
--geometry=1024x768+0+0
--gpu-backend=wayland
--stop-screensaver

```

but screen dimming still isn't prevented.

on checking the version of mpv i noticed a parsing option error
```

~ &#10140; mpv --version
Error parsing option gpu-backend (option not found)
/home/kabir/.config/mpv/mpv.conf:3: setting option gpu-backend='wayland' failed.
mpv 0.34.1 Copyright © 2000-2021 mpv/MPlayer/mplayer2 projects
 built on UNKNOWN
FFmpeg library versions:
   libavutil       56.70.100
   libavcodec      58.134.100
   libavformat     58.76.100
   libswscale      5.9.100
   libavfilter     7.110.100
   libswresample   3.9.100
FFmpeg version: 4.4.2-0ubuntu0.22.04.1+esm1

```

Trying after removing gpu-backend field from mpv.conf doesn't change the behavior. I'm using jammy jellyfish on wayland, and the main reason behind wanting to use mpv is i can make it resume videos from where I left off, and I can adjust window size on launch. I tried a GUI font end called celluloid, it does have the option to resume from where I left off but only if I close by pressing shift+q, as compared on mpv where it always remembers state after adding save-position-on-quit. I also cannot figure out how to make Celluloid use mpv.conf. Even after I save a copy of mpv.conf inside ~/.config/celluloid/ it doesn't pick it up. I tried uploading the file from the GUI directly but still it won't pick it up. So I find using mpv simpler except for screem dimming which is a problem.
```

~ &#10140; celluloid --version
Celluloid 0.20

```

Thanks!

---

### Post by kabirgandhiok on 2023-04-30
Edit: just read that Celluloid does not need a copy of mpv.conf inside ~/.config/celluloid/ but instead to upload the mpv.conf from ~/.config/mpv/mpv.conf, so I removed the .conf file from ~/.config/celluloid/ but it still doesn't read it

---

### Post by #&amp;thj^% on 2023-05-01
My line will work as:
```
Exec=mpv_inhibit_gnomeAUR /usr/bin/mpv --profile=pseudo-gui -- %U
``` 
The whole file reads:
```
[Desktop Entry]
X-AppInstall-Package=mpv
X-AppInstall-Popcon=126
X-AppInstall-Section=universe

Type=Application
Name=mpv Media Player
GenericName=Multimedia player
Comment=Play movies and songs
Icon=mpv
TryExec=/usr/bin/mpv
Exec=mpv_inhibit_gnomeAUR /usr/bin/mpv --profile=pseudo-gui -- %U
Terminal=false
Categories=AudioVideo;Audio;Video;Player;TV;
MimeType=application/ogg;application/x-ogg;application/sdp;application/smil;application/x-smil;application/streamingmedia;application/x-streamingmedia;application/vnd.rn-realmedia;application/vnd.rn-realmedia-vbr;audio/aac;audio/x-aac;audio/m4a;audio/x-m4a;audio/mp1;audio/x-mp1;audio/mp2;audio/x-mp2;audio/mp3;audio/x-mp3;audio/mpeg;audio/x-mpeg;audio/mpegurl;audio/x-mpegurl;audio/mpg;audio/x-mpg;audio/rn-mpeg;audio/ogg;audio/scpls;audio/x-scpls;audio/vnd.rn-realaudio;audio/wav;audio/x-pn-windows-pcm;audio/x-realaudio;audio/x-pn-realaudio;audio/x-ms-wma;audio/x-pls;audio/x-wav;video/mpeg;video/x-mpeg;video/x-mpeg2;video/mp4;video/msvideo;video/x-msvideo;video/ogg;video/quicktime;video/vnd.rn-realvideo;video/x-ms-afs;video/x-ms-asf;video/x-ms-wmv;video/x-ms-wmx;video/x-ms-wvxvideo;video/x-avi;video/x-fli;video/x-flv;video/x-theora;video/x-matroska;video/webm;audio/x-flac;audio/x-vorbis+ogg;video/x-ogm+ogg;audio/x-shorten;audio/x-ape;audio/x-wavpack;audio/x-tta;audio/AMR;audio/ac3;video/mp2t;audio/flac;
X-KDE-Protocols=ftp,http,https,mms,rtmp,rtsp,sftp,smb

X-Ubuntu-Gettext-Domain=app-install-data

```
The file I edit on xfce4 is:
```
sudoedit /usr/share/app-install/desktop/mpv:mpv.desktop
```

EDIT: This is the last suggestion I can come up with, and where I came up with the Idea.
Prevent the screen from blanking while a video is playing. [https://gist.github.com/crazygolem/a7d3a2d3c0cee5d072c0cbbbdee69286](https://gist.github.com/crazygolem/a7d3a2d3c0cee5d072c0cbbbdee69286)
This script is a workaround for the GNOME+Wayland issue documented in the
[Disabling Screensaver] section of the mpv manual, and depends on
gnome-session-inhibit (usually provided by the gnome-session package) to set up
the inhibitors.
[list]
# CAVEATS
[*]This is not (yet?) a foolproof solution.
[*]At this time GNOME's implementation of the Inhibit protocol does not support the
SimluateUserActivity method:[/list]

2nd Option My Idea came from:
```

curl -o ~/.config/mpv/scripts/mpv_inhibit_gnome.so -L https://github.com/Deminder/mpv_inhibit_gnome/releases/download/v1/mpv_inhibit_gnome.so
```

More info, this cplugin by Guldoman: mpv_inhibit_gnome?
My fork uses the mute and window-minimized again to inhibit idle,suspend for video and suspend for audio.
I prefer this approach since it doesn't require a gnome-session-inhibit process.
TIP:
OTOMH mpv will run mpv_inhibit_gnome.so if it is in the scripts dir:

---

### Post by kabirgandhiok on 2023-05-05
@1fallen I'm sorry for not being able to get back earlier, was caught up with other things. Will try out your suggestions and get back.

Thanks again!

---

### Post by kabirgandhiok on 2023-05-05
> **1fallen said:**
> 
```

2nd Option My idea came from
[code]
curl -o ~/.config/mpv/scripts/mpv_inhibit_gnome.so -L https://github.com/Deminder/mpv_inhibit_gnome/releases/download/v1/mpv_inhibit_gnome.so
```

More info, this cplugin by Guldoman: mpv_inhibit_gnome?
My fork uses the mute and window-minimized again to inhibit idle,suspend for video and suspend for audio.
I prefer this approach since it doesn't require a gnome-session-inhibit process.
TIP:
OTOMH mpv will run mpv_inhibit_gnome.so if it is in the scripts dir:

Running that code worked. The screen does not dim anymore while playing videos on mpv. Thanks so much for that. :) 

Just one question:
Before running that code, I tried build/install library manually but could not. Running make gave an error, it's probably because I've never used make manually before, but I'm curious to know what I did wrong. I downloaded mpv_inhibit_gnome.so from [https://github.com/Guldoman/mpv_inhibit_gnome/releases](https://github.com/Guldoman/mpv_inhibit_gnome/releases) and put it inside ~/.config/mpv/scripts/
Then I ran make -f mpv_inhibit_gnome.so from inside ~/.config/mpv/scripts but got the following errors:
```

kabir@kabirsubuntu:~/.config/mpv/scripts$ make -f mpv_inhibit_gnome.so
mpv_inhibit_gnome.so:1: warning: NUL character seen; rest of line ignored
mpv_inhibit_gnome.so:1: *** missing separator.  Stop.

```

---

