---
title: "convert .webm and .webp to something else"
date: 2019-09-05
forum: Multimedia Software
---

### Post by Skaperen on 2019-09-05
i have some .webm and .webp files that all my usual (command line) tools do not recognize.  for example, the "[COLOR=#0000cd][FONT=courier new]convert[/FONT][/COLOR]" command is not recognizing them.  one tool does ... the "[COLOR=#0000cd][FONT=courier new]file[/FONT][/COLOR]" command.  but confirming the file format is not helping.  so i'm looking for a working tool that is on the ubuntu 18.04 repository that can convert these files, preferably to a lossless format.

---

### Post by CatKiller on 2019-09-05
ffmpeg should be able to do it, I think. [This article](https://opensource.com/article/17/6/ffmpeg-convert-media-file-formats) suggests it can read and write webm files, and it will happily convert a stream it understands into another stream it understands. I can't test it myself since I'm on my phone rather than my computer.

---

### Post by Skaperen on 2019-09-05
ffmpeg fails unless i am doing it wrong:
```

lt2a/forums /home/forums 5> ffmpeg foo.webm foo.mp4
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Output #0, webm, to 'foo.webm':
Output file #0 does not contain any stream
lt2a/forums /home/forums 6> 

```

---

### Post by mc4man on 2019-09-05
wrong command,  ffmpeg is used - 
ffmpeg -i input file any options output file.

webm is just a container, typically using vp8/9 for video, opus for audio. On rare occasions it has h.264 or more recently av1
So to change containers you need to know what are the codecs  the webm used and what codecs the format you wish to use supports

just going ffmpeg -i /path/to/whatever.webm  will tell what codecs were used in your file

Ex.  to convert webm to .mp4 do a web search:  convert webm to mp4 ffmpeg

---

### Post by CatKiller on 2019-09-05
I think that with ffmpeg you do need to specify the input file with - i, since there could be multiple output files. Still can't check personally, but I did find the [man page](https://ffmpeg.org/ffmpeg.html).

---

### Post by TheFu on 2019-09-05
webm is a subset of MKV.    If you want lossless conversion to an MKV container, then 
```
mkvmerge -o newname.mkv oldname.webm
```
The video and audio and any other tracks like subtitles or captions are included.  It probably won't play any better unless the player simply doesn't recognize the webm extension.  mpv / mplayer handle it fine.

I know ZERO about webp.  Never heard of it.

If you want to change the videocodec then using ffmpeg to transcode is probably what you want:
```
nice ffmpeg -i "$IN" -c:v libx264    -crf 19    -c:a copy      "$IN.mkv"
```
That forces an h.264 video at a fairly high "quality" - the file will probably become larger.  The audio will be copied.  I usually copy the original audio and transcode another audio track into vorbis. Both audio tracks are included.  There are presets depending on what is more important, file size or speed of compression. The default is "medium", which seems like a good enough trade off to me.  YMMV.

BTW, manpages are on your box for all commands and usually the top page has a clear example for someone of your skill.

---

### Post by mc4man on 2019-09-06
webp is an image format, again very easy to search out how to convert to another image format in linux, either with webp of ffmpeg ( webp is available in Ubuntu
Ex.
sudo apt install webp
Installs several binaries, you want to use dwebp
[https://developers.google.com/speed/webp/docs/dwebp](https://developers.google.com/speed/webp/docs/dwebp)

---

### Post by Skaperen on 2019-09-06
ok, i tried it again with -i.  got a little further this time.  at least it now tells me it failed.
```

lt2a/forums /home/forums 7> ffmpeg -i foo.webm foo.mp4
ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
[webp @ 0x55ac2bebce60] skipping unsupported chunk: ANIM
[webp @ 0x55ac2bebce60] skipping unsupported chunk: ANMF
    Last message repeated 1 times
[webp_pipe @ 0x55ac2bebb8c0] decoding for stream 0 failed
[webp_pipe @ 0x55ac2bebb8c0] Could not find codec parameters for stream 0 (Video: webp, none): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, webp_pipe, from 'foo.webm':
  Duration: N/A, bitrate: N/A
    Stream #0:0: Video: webp, none, 25 tbr, 25 tbn, 25 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (webp (native) -> h264 (libx264))
Press [q] to stop, [?] for help
[webp @ 0x55ac2bed4520] skipping unsupported chunk: ANIM
[webp @ 0x55ac2bed4520] skipping unsupported chunk: ANMF
    Last message repeated 1 times
Error while decoding stream #0:0: Invalid data found when processing input
Finishing stream 0:0 without any data written to it.
Nothing was written into output file 0 (foo.mp4), because at least one of its streams received no packets.
frame=    0 fps=0.0 q=0.0 Lsize=       0kB time=-577014:32:22.77 bitrate=  -0.0kbits/s speed=N/A    
video:0kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
Output file is empty, nothing was encoded (check -ss / -t / -frames parameters if used)
Conversion failed!
lt2a/forums /home/forums 8>

```

---

### Post by SeijiSensei on 2019-09-06
```
Could not find codec parameters for stream 0 (Video: webp, none): 
```

ffmpeg doesn't seem to find a video stream in that file. Did you install webp as mc4man suggested?

---

### Post by Skaperen on 2019-09-06
yes.
```

lt2a/forums /home/forums 15> dpkg -l|fgrep webp
ii  libwebp6:amd64                        0.6.1-2                 amd64                   Lossy compression of digital photographic images.
ii  libwebpdemux2:amd64                   0.6.1-2                 amd64                   Lossy compression of digital photographic images.
ii  libwebpmux3:amd64                     0.6.1-2                 amd64                   Lossy compression of digital photographic images.
ii  webp                                  0.6.1-2                 amd64                   Lossy compression of digital photographic images.
lt2a/forums /home/forums 16> 

```
so these are really .webp images?
```

lt2a/forums /home/forums 15> xd32 foo.webm|head -n3
000000000  52494646 aa250000 57454250 56503858  0a000000 12000000 ef00004f 0000414e |RIFF.%..WEBPVP8X...........O..AN|
000000020  494d0600 0000ffff ffff0000 414e4d46  ee180000 00000000 0000ef00 004d0000 |IM..........ANMF.............M..|
000000040  84030002 5650384c d6180000 2fef4013  00ef0539 b26dd5ca 3ef25cbe bb31b248 |....VP8L..../.@....9.m..>.\..1.H|
lt2a/forums /home/forums 16> 

```
i guess so.  but firefox doesn't even know how to display any of the first 20 i tried.  i have 253 of these files.

---

### Post by SeijiSensei on 2019-09-06
Apparently GIMP can open webp images with a plugin: [https://www.bettertechtips.com/how-to/open-webp-gimp/](https://www.bettertechtips.com/how-to/open-webp-gimp/)

---

### Post by Skaperen on 2019-09-06
i renamed them with the extension [COLOR=#0000cd][FONT=courier new].webp[/FONT][/COLOR] and this lets imagemagick's [COLOR=#0000cd][FONT=courier new]convert[/FONT][/COLOR] command to convert it to png.  i can now view them in [COLOR=#0000cd][FONT=courier new]eog[/FONT][/COLOR] (which won't display webp directly).  firefox is still not recognizing them, either.

---

