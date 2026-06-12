---
title: "Smplayer Xv problem (Mplayer exit code: 1)"
date: 2009-03-04
forum: Multimedia Software
---

### Post by Giga777 on 2009-03-04
I am using Intrepid and I've installed the svn version of the mplayer . I just get exit code: 1 when I switch to xv instead of x11(slow).

I think it's something about my ati mobility x700 radeon graphic card. because i had a similar problem when i was using a previous version (Gutsy or Hardy) of ubuntu. I was able to solve it with the instructions given [here]("http://ubuntuforums.org/showthread.php?t=220757") just entering the code: "sudo aticonfig --overlay-type=Xv" I tried the same trick, it didn't work.

Anywhere here is the log and i appreciate your help:
> /usr/bin/mplayer -noquiet -nofs -sub-fuzziness 2 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -nostop-xscreensaver -wid 31457292 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/cihan/.config/smplayer/styles.*** -fontconfig -font Verdana -subcp ISO-8859-9 -vid 0 -aid 1 -subpos 100 -volume 40 -cache 2000 -ss 14 -osdlevel 0 -nocorrect-pts -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 /media/d/Downloads/Dizi/Lost/lost.s05e02.the.lie.hdtv.xvid-2hd.avi

MPlayer SVN-r28403-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /media/d/Downloads/Dizi/Lost/lost.s05e02.the.lie.hdtv.xvid-2hd.avi.

AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  12bpp  23.976 fps  1069.1 kbps (130.5 kbyte/s)
Clip info:
 Software: MEncoder dev-SVN-r26059-4.1.2
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=MEncoder dev-SVN-r26059-4.1.2
ID_CLIP_INFO_N=1
SUB: Detected subtitle file format: subviewer
SUB: Read 622 subtitles.
SUB: Adjusted 104 subtitle(s).
ID_FILE_SUB_ID=0
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/Lost - 5x01 - Because You Left.HDTV.PusherCrew.en.srt
SUB: Added subtitle file (1): /media/d/Downloads/Dizi/Lost/Lost - 5x01 - Because You Left.HDTV.PusherCrew.en.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 550 subtitles.
ID_FILE_SUB_ID=1
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/Lost 5x4 The Little Prince.hdtv.xvid-xor.srt
SUB: Added subtitle file (2): /media/d/Downloads/Dizi/Lost/Lost 5x4 The Little Prince.hdtv.xvid-xor.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 599 subtitles.
SUB: Adjusted 86 subtitle(s).
ID_FILE_SUB_ID=2
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/Lost.S05E02.HDTV.XviD-2HD.srt
SUB: Added subtitle file (3): /media/d/Downloads/Dizi/Lost/Lost.S05E02.HDTV.XviD-2HD.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 569 subtitles.
SUB: Adjusted 32 subtitle(s).
ID_FILE_SUB_ID=3
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/Lost.S05E03.HDTV.XviD-XOR.srt
SUB: Added subtitle file (4): /media/d/Downloads/Dizi/Lost/Lost.S05E03.HDTV.XviD-XOR.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 487 subtitles.
SUB: Adjusted 2 subtitle(s).
ID_FILE_SUB_ID=4
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/Lost.S05E06.HDTV.XviD-XOR.srt
SUB: Added subtitle file (5): /media/d/Downloads/Dizi/Lost/Lost.S05E06.HDTV.XviD-XOR.srt
SUB: Detected subtitle file format: subviewer
SUB: Read 445 subtitles.
SUB: Adjusted 12 subtitle(s).
ID_FILE_SUB_ID=5
ID_FILE_SUB_FILENAME=/media/d/Downloads/Dizi/Lost/lost.s05e05.hdtv.xvid-fqm.srt
SUB: Added subtitle file (6): /media/d/Downloads/Dizi/Lost/lost.s05e05.hdtv.xvid-fqm.srt
ID_FILENAME=/media/d/Downloads/Dizi/Lost/lost.s05e02.the.lie.hdtv.xvid-2hd.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1069080
ID_VIDEO_WIDTH=624
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=120824
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=2441.81
ID_SEEKABLE=1
ID_CHAPTERS=0
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=mp3
[AO_ALSA] Unable to find simple control 'PCM',0.
[Mixer] No hardware mixing, inserting volume filter.
Video: no video
Starting playback...


MPlayer interrupted by signal 11 in module: seek
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


---

### Post by hatalar205 on 2009-03-13
I think you should look here.
[http://ubuntuforums.org/showthread.php?t=1042348&highlight=hatalar205](http://ubuntuforums.org/showthread.php?t=1042348&highlight=hatalar205)

---

