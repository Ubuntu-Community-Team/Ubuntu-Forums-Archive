---
title: "[SOLVED] ffmpeg and aac audio"
date: 2008-08-06
forum: Multimedia Software
---

### Post by stoppage on 2008-08-06
Hi, I'm trying to convert an mp4/h264 with audio aac to avi/xvid using WinFF. It appears that my version of  ffmpeg doesn't have aac audio codec (doesn't show on terminal....ffmpeg -version). Video plays fine on other players, only on WinFF....silent. How can I introduce ffmpeg to aac codec please? I've included some ramblings from the terminal......heeeelp!

---

### Post by mcduck on 2008-08-06
THe ffmpeg verion in Ubuntu's repositories has no AAC support.

Get the ffmpeg from Medibuntu repositories, that will solve the problem.

[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

### Post by stoppage on 2008-08-06
I installed from Medibuntu, still no audio although it now appears to have enabled faac and faad....

:~$ ffmpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

---

### Post by FakeOutdoorsman on 2008-08-06
Can you display the WinFF preset or command that it is giving to ffmpeg?  Option names can change between ffmpeg revisions.  I was unable to open your attached file.

---

### Post by stoppage on 2008-08-06
Attached file on original post is OpenOffice format. Attached output here is terminal output from conversion in WinFF...I hope that's what you mean

---

### Post by FakeOutdoorsman on 2008-08-06
> **stoppage said:**
> Attached file on original post is OpenOffice format. Attached output here is terminal output from conversion in WinFF...I hope that's what you mean
Your screenshot is almost what I need.  It's showing ffmpeg's response, but not the command from WinFF.  If you're using a preset from WinFF, go to Edit -> Presets.  Choose the preset you are using and then paste the information from "Preset Command Line".  This is the command WinFF is passing to ffmpeg.

I just installed ffmpeg from Medibuntu, but it appears we are using different versions.  Yours looks much older.  The command "aptitude show ffmpeg" gives my ffmpeg package version: 3:0.cvs20070307-5ubuntu7.1+medibuntu1.  Which version of Ubuntu are you running?

Lastly, just so I don't forget once we get this working, your source video is PAL (25 frames per second) and most WinFF presets will needlessly convert to NTSC  (29.97 frames per second) and will reduce the quality of your video.  You can either edit the preset and change "-r 29.97" to "-r 25" or "-r pal", or you can go to Options -> Additional Options and enter "25" or "pal" in the "Frame Rate" box.

---

### Post by stoppage on 2008-08-07
I'm running &#8222;Feisty&#8220; 7.04. Since I changed over to Medibuntu's Ffmpeg the update manager keeps coming up with &#8222;updated&#8220; version of same but it doesn't have aac support. On WinFF if I choose to convert to   MS comptable avi preset command line reads.....-f avi -acodec mp3 -vcodec msmpeg4 -ab 192........ ,Preset Name is divx
and last line of terminal reads .....&#8220;unsupported codec for output screen no.1&#8220;
If I choose to convert to &#8222;Xvid in avi&#8220; preset command line reads....-r 29.97 -vcodec xvid -vtag XVID -s 704x384 -aspect 16:9 -maxrate 1800k...,preset name is XviDAVIWS and last line of terminal reads ...&#8220;Unknown codec xvid&#8220;
Thank you for your patience

---

### Post by FakeOutdoorsman on 2008-08-07
This is hard for me to debug since I can't easily use the packages for Feisty.  We can ignore WinFF and run ffmpeg itself to get more detailed errors:
```
ffmpeg -i inputvideo.mp4 -f avi -acodec mp3 -vcodec msmpeg4 -ab 192 output.avi
```
Paste the full ffmpeg output.

---

### Post by stoppage on 2008-08-07
I've truncated some names to try make it easier, without changing locations....huh!
I don't believe this output but I don't feel confident with long texts in the terminal.
Output..


:~$ ffmpeg -i /home/tony/Desktop/Music and Video/VIDEO/NEW VIDEOS/PROB VIDS/Venus/Venus.mp4 -f avi -acodec mp3 -vcodec msmpeg4 -ab 192 /home/tony/VIDEO/Venus.avi

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard

  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 

  libavutil version: 0d.49.0.0

  libavcodec version: 0d.51.11.0

  libavformat version: 0d.50.5.0

  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

/home/tony/Desktop/Music: I/O error occured

Usually that means that input file is truncated and/or corrupted.

---

### Post by FakeOutdoorsman on 2008-08-08
I ran a virtualized install of Feisty and now I am getting the same error as you when trying to decode an aac audio stream using Medibuntu's ffmpeg.  Although it was configured to support libfaad and libfaac it seems as if it was configured incorrectly.  I recommend trying mencoder, otherwise you would have to [compile ffmpeg]("http://ubuntuforums.org/showthread.php?t=786095") yourself.  This worked for me:
```
mencoder -ovc xvid -oac mp3lame -xvidencopts bitrate=512 -o output.avi input.mp4
```
From [MEncoder Gentoo Wiki]("http://gentoo-wiki.com/MEncoder") (has other examples like 2-pass)

---

### Post by stoppage on 2008-08-08
In other words the Ubuntu version of FFmpeg doesn't support AAC audio and the Medibuntu version is incorrectly configured....at least Mencoder is now encoding, if slowly. Thank you for your time

---

### Post by stoppage on 2008-08-12
This issue was resolved by a (later) update of libavcodec etc., while retaining "Medibuntu" earlier version of Ffmpeg

---

