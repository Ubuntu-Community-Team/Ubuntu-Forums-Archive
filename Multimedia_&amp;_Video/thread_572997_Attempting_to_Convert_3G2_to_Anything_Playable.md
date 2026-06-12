---
title: "Attempting to Convert 3G2 to Anything Playable"
date: 2007-10-11
forum: Multimedia &amp; Video
---

### Post by Ngiri on 2007-10-11
I'm running Ubuntu 7.04.  I have a 3G2 video from a friend's cell phone.  Ideally I want to convert it to a Flash video with ffmpeg.  The problem I'm having is that I can't figure out how to process the audio that's embedded in the file.  I can convert the video without any trouble.

Both mencoder and ffmpeg will convert the file giving me a new file with no sound.  Depending on the command line options used, I can also get ffmpeg to produce the following error: Unsupported codec (id=86043) for input stream #0.x.  Googling that error produces a link to an ffmpeg FAQ saying the audio is most likely QCELP which is unsupported at this time.

I've changed tactics from trying to convert the file to just trying find something that can allow me to hear the audio.  The closest I've come to that is the documentation for the Helix Player which says it supports 3G2/QCELP.  I've tried the version that is available with apt-get install and also the latest nightly build but both produce an error saying "The following components are required: 3g2"  I'm wondering  how to find this "component."  I couldn't find any further details on the Helix site.

Just for reference, here are some of the other apps I've tried to play the file with:  Mplayer, ffplay and Media Player.

mencoder was installed from the repositories (apt-get).  ffmpeg was compiled from cvs and reports as version "SVN-r10700."  I think I pulled that ffmpeg from cvs yesterday, but I'll admit that I've compiled and tried a lot of different things lately and it could be a bit older.

There's a qualcomm sdk available that can encode/decode QCELP, but the format in movie files is apparently different.  I built the tools from the sdk and tried the decode one on a copy of the audio stream made with ffmpeg and it didn't seem to even try to process the file.

Is playback and/or conversion of QCELP audio possible on Linux?  Is there some way to figure out if the audio is really QCELP?  I have played and converted this file on *another* operating system so I don't suspect the file of being corrupt.

Any feedback is appreciated.

Thank you.

---

### Post by DaleEMoore on 2007-11-12
I've uploaded mine to [http://YouTube.Com](http://YouTube.Com) which imports video and audio just fine. Then VideoDownload [http://javimoya.com/blog/youtube_en.php](http://javimoya.com/blog/youtube_en.php) or [http://www.download.com/VideoDownloader/3000-11745_4-10596547.html](http://www.download.com/VideoDownloader/3000-11745_4-10596547.html) it afterwards if I want.

---

