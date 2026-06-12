---
title: "No video in mplayer with gl3: [gl] Error: framebuffer completeness check failed!"
date: 2015-08-29
forum: Multimedia Software
---

### Post by Daniyal_Javani on 2015-08-29
Hello
Could you please tell me why I have no video with gl3 in mplayer?
```
$ mplayer -vo gl3 Data/Movie/Untitled\ Folder/The.Equalizer.2014.720p-/The.Equalizer.mkv 
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Cannot open file '/home/vahid/.mplayer/input.conf': No such file or directory
Failed to open /home/vahid/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.

Playing Data/Movie/Untitled Folder/The.Equalizer.2014.720p-/The.Equalizer.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang eng
[mkv] Will play video track 1.
Detected file format: Matroska
Load subtitles in Data/Movie/Untitled Folder/The.Equalizer.2014.720p-/
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Selected audio codec: AAC (Advanced Audio Coding) [libavcodec]
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
VIDEO:  1280x536  23.976 fps    0.0 kbps ( 0.0 kB/s)
VO: [gl3] 1280x536 => 1280x536 Planar YV12 
[gl] Error: framebuffer completeness check failed!
[gl] Error: framebuffer completeness check failed!
A:   5.1 V:   5.1 A-V:  0.001 ct:  0.000   0/  0  2%  0%  0.7% 0 0 


MPlayer interrupted by signal 2 in module: sleep_timer
A:   5.2 V:   5.2 A-V:  0.001 ct:  0.000   0/  0  2%  0%  0.7% 0 0 

Exiting... (Quit)


```

---

### Post by SeijiSensei on 2015-08-29
Let's take a step back first.  Does it play with "-vo xv", or with any other video output driver?

---

### Post by Daniyal_Javani on 2015-08-29
> **SeijiSensei said:**
> Let's take a step back first.  Does it play with "-vo xv", or with any other video output driver?

Yes play with xv and gl
```
$ mplayer -vo xv Data/Movie/Untitled\ Folder/robocop\ 2014/robocop\ 2014.mkv 
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Cannot open file '/home/vahid/.mplayer/input.conf': No such file or directory
Failed to open /home/vahid/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.

Playing Data/Movie/Untitled Folder/robocop 2014/robocop 2014.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Will play video track 1.
Detected file format: Matroska
Load subtitles in Data/Movie/Untitled Folder/robocop 2014/
[ass] auto-open
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Selected audio codec: AAC (Advanced Audio Coding) [libavcodec]
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
VIDEO:  1280x536  23.976 fps    0.0 kbps ( 0.0 kB/s)
VO: [xv] 1280x536 => 1280x536 Planar YV12 
Colorspace details not fully supported by selected vo.
A:   5.4 V:   5.4 A-V:  0.000 ct:  0.000   0/  0  0%  1%  0.7% 0 0 

Exiting... (Quit)
```

```
$ mplayer -vo gl3 Data/Movie/Untitled\ Folder/robocop\ 2014/robocop\ 2014.mkv 
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Cannot open file '/home/vahid/.mplayer/input.conf': No such file or directory
Failed to open /home/vahid/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.

Playing Data/Movie/Untitled Folder/robocop 2014/robocop 2014.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Will play video track 1.
Detected file format: Matroska
Load subtitles in Data/Movie/Untitled Folder/robocop 2014/
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Selected audio codec: AAC (Advanced Audio Coding) [libavcodec]
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
VIDEO:  1280x536  23.976 fps    0.0 kbps ( 0.0 kB/s)
VO: [gl3] 1280x536 => 1280x536 Planar YV12 
[gl] Error: framebuffer completeness check failed!
[gl] Error: framebuffer completeness check failed!
A:   5.5 V:   5.5 A-V:  0.000 ct:  0.000   0/  0  2%  0%  0.7% 0 0 

Exiting... (Quit)


```
Thanks for your attention

---

### Post by mc4man on 2015-08-29
If you want mplayer2 & -vo gl3 then I'd suggest you use 15.04 or 15.10 as it's broken in 14.04.x 
It may be that 14.04.1 with the oibaf or xorger ppa may work, don't know as don't use either of them nor mplayer2.

---

### Post by SeijiSensei on 2015-08-29
Have you tried other players, mpv in particular?  I recommend using the version in Doug McMahon's repositories.  If you're using 14.04 (Trusty Tahr), try this:
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install mpv

```
The excellent front-end for mplayer, smplayer, has been updated to support mpv as the player engine as well.

Is there some specific reason why you want to use gl3?  Frankly on most computers I've used xv works fine for ordinary video, unless you need support for VDPAU or VAAPI.  SMPlayer lets you switch easily among the various output options using the dialog at Options > Preferences > General > Video.

---

### Post by Daniyal_Javani on 2015-08-29
Thanks, seems I should migrate to 15.10.

Wow, mpv with opengl-hq was great!
```

sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install mpv

```
The excellent front-end for mplayer, smplayer, has been updated to support mpv as the player engine as well.

---

