---
title: "VLC Streaming Desktop + Audio"
date: 2011-05-25
forum: Multimedia Software
---

### Post by batrick on 2011-05-25
I'm trying to stream my desktop + audio using VLC but am having difficulties getting the audio to stream at all. [Basically, I want to be able to stream my playing a game for friends.]

I've tried this on Ubuntu 10.10 and 11.04:

I'm using this command:

```
vlc screen:// --screen-left 0 --screen-top 0 --screen-width 1920 --screen-height 1200 --screen-fps=45 --sout '#transcode{venc=x264{keyint=60,idrint=2},vcodec=h264,vb=1500,acodec=mp4a,ab=32,channels=2,samplerate=22050,audio-sync}:file{dst="/home/batrick/game.mov"}'
```

This is the version of vlc on 11.04:

```
batrick@neverwinter:~$ vlc --version
VLC media player 1.1.9 The Luggage (revision exported)
VLC version 1.1.9 The Luggage (exported)
Compiled by buildd on allspice.buildd (Apr 14 2011 17:06:57)
Compiler: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.
```

(I can't access the machine I tried 10.10 on but I know it's either 1.1.4 or 1.1.3 version of VLC. I'll check when I get home.)


I've spent hours googling around and haven't found anything helpful for solving this issue. It seems the VLC guys just generally recommend removing pulse which isn't something I want to do. Those threads are usually about 2 years old anyway so I imagine someone has fixed this...

I've tried using ```
:input-slave=alsa://hw:0.0
``` and variants including ```
:input-slave=alsa://pulse
```. (The last one actually results in a uncontrolled memory leak with vlc rapidly using all the system memory.)

---

### Post by mpmf on 2011-09-23
I've managed to stream my desktop + audio using a combination of ffmpeg and vlc. Here is the command line I use to start sharing:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 1440x900 -i :0.0 -acodec libmp3lame -ar 44100 -b 128k -vcodec libx264 -vpre lossless_ultrafast -threads 0 -f flv - | vlc -I dummy - --sout '#transcode{vcodec=h264,vb=3500,acodec=mp3,ab=128,channels=2,samplerate=44100}:http{mux=ffmpeg{mux=flv},dst=192.168.1.4:8080/desktop}'
```

It's a long command line, but it works. It requires a ffmpeg compiled with libx264. 
While it works, it is kinda of slow (I get around 20 fps) and I believe that it may have to do with the double encoding (in ffmpeg and then in vlc to stream). If any of you have any suggestion on how to remove this double encoding, I'm all ears :).

By the way, I was trying to stream the Linux desktop to an Asus O!Play (with moServices) and this worked for me :)

---

### Post by snusmusa on 2012-05-24
> **mpmf said:**
> I've managed to stream my desktop + audio using a combination of ffmpeg and vlc. Here is the command line I use to start sharing:

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 1440x900 -i :0.0 -acodec libmp3lame -ar 44100 -b 128k -vcodec libx264 -vpre lossless_ultrafast -threads 0 -f flv - | vlc -I dummy - --sout '#transcode{vcodec=h264,vb=3500,acodec=mp3,ab=128,channels=2,samplerate=44100}:http{mux=ffmpeg{mux=flv},dst=192.168.1.4:8080/desktop}'
```

It's a long command line, but it works. It requires a ffmpeg compiled with libx264. 
While it works, it is kinda of slow (I get around 20 fps) and I believe that it may have to do with the double encoding (in ffmpeg and then in vlc to stream). If any of you have any suggestion on how to remove this double encoding, I'm all ears :).

By the way, I was trying to stream the Linux desktop to an Asus O!Play (with moServices) and this worked for me :)

I was able to do this without the double encoding.

```

ffmpeg -f x11grab -s 1680x1050 -r 30 -i :0.0+0,0  -f alsa -ac 2 -i pulse -vcodec libx264 -preset ultrafast -s 1280x768 -acodec libfaac -threads 0 -f mpegts - | vlc -I dummy - --sout '#std{access=http,mux=ts,dst=:3030}'

```

I have one more thing i want to do though, and that is adding my webcam as an overlay in the bottom corner. I'm gonna try this tomorrow

```

ffmpeg -f x11grab -s 1680x1050 -r 30 -i :0.0+0,0 -vf "movie=/dev/video0:f=video4linux2, scale=180:-1, setpts=PTS-STARTPTS [movie]; [in] setpts=PTS-STARTPTS, [movie] overlay=main_w-overlay_w-10:main_h-overlay_h-10 [out]" -f alsa -ac 2 -i pulse -vcodec libx264 -preset ultrafast -s 1280x768 -acodec libfaac -threads 0 -f mpegts - | vlc -I dummy - --sout '#std{access=http,mux=ts,dst=:3030}'

```

---

### Post by snusmusa on 2012-05-25
> **snusmusa said:**
> I have one more thing i want to do though, and that is adding my webcam as an overlay in the bottom corner. I'm gonna try this tomorrow

```

ffmpeg -f x11grab -s 1680x1050 -r 30 -i :0.0+0,0 -vf "movie=/dev/video0:f=video4linux2, scale=180:-1, setpts=PTS-STARTPTS [movie]; [in] setpts=PTS-STARTPTS, [movie] overlay=main_w-overlay_w-10:main_h-overlay_h-10 [out]" -f alsa -ac 2 -i pulse -vcodec libx264 -preset ultrafast -s 1280x768 -acodec libfaac -threads 0 -f mpegts - | vlc -I dummy - --sout '#std{access=http,mux=ts,dst=:3030}'

```


I got this working now, there were some minor things in the above command that was not working as intended. 

This is how i do it:

```

ffmpeg -f alsa -ac 2 -i pulse -itsoffset -0.2 -f x11grab -s 1680x1050 -r 30 -i :0.0+0,0 -vf "movie=/dev/video0:f=video4linux2, scale=180:-1, setpts=PTS-STARTPTS [movie]; [in][movie] overlay=main_w-overlay_w-2:main_h-overlay_h-2 [out]" -vcodec libx264 -preset ultrafast -s 704x480 -acodec libfaac -threads 0 -f mpegts - | tee myrecording.mpeg | vlc -I dummy - --sout '#std{access=http,mux=ts,dst=:8080}

```It's running steady at about 390 kbit/s bitrate. The -itoffset might vary on the system, Just be aware that the audio might not be in sync and tune it accordingly.

I also added the "| tee myrecording.mpeg" so that it would also save the recording to a file.

---

