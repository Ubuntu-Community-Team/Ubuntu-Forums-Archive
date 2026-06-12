---
title: "AVCONV error (...non monotonically increasing dts...) converting to xvid with winff"
date: 2014-04-27
forum: Multimedia Software
---

### Post by Saul.Lima on 2014-04-27
I am trying to convert a .rmvb video to .avi  with xvid codec using winff app. The terminal window open in conversion process shows me this error message:

[B][avi @ 0x12510c0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 22 >= 22
av_interleaved_write_frame(): Invalid argument[/B]

The setting used by winff to convert file is are:

**/usr/bin/avconv -y -i "file.rmvb" -f avi -r 29.97 -vcodec libxvid -vtag XVID -filter:v scale=640:480 -aspect 4:3 -maxrate 1800k -b:v 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -trellis 1 -flags +aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -b:a 128k -ac 2 "file.a**vi"

I am using Ubuntu 14.04 Trusty and default avconf instalation from repositories. This is the avconv -version:
 built on Mar 24 2014 06:12:33 with gcc 4.8 (Ubuntu 4.8.2-17ubuntu1)
[B]avconv 9.11-6:9.11-2ubuntu2
libavutil     52.  3. 0 / 52. 18.100
libavcodec    54. 35. 0 / 54. 35. 0
libavformat   54. 20. 3 / 54. 20. 3
libavdevice   53.  2. 0 / 53.  2. 0
libavfilter    3.  3. 0 /  3.  3. 0
libavresample  1.  0. 1 /  1.  0. 1
libswscale     2.  1. 1 /  2.  1. 1[/B]


Are there some solution? How correct this error?

---

### Post by Saul.Lima on 2014-04-29
AVCONV gives the error "Segmentation fault (core dumped)" when I try to convert some media to mp3, ogg or any other audio format. Are threre some way to get an updated version of avconv or ffmpeg with this bugs solved?

---

### Post by ron998 on 2014-04-29
> **Saul.Lima said:**
> ... Are threre some way to get an updated version of avconv or **ffmpeg** with this bugs solved?
Hi
Compile it yourself ---> [https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
or
Use a static build ---> [http://ffmpeg.gusari.org/static/](http://ffmpeg.gusari.org/static/)
or
Use a PPA.

---

### Post by Saul.Lima on 2014-04-29
Are there some safe ppa that provide an updated version of ffmpeg?

---

### Post by wmstrome on 2014-05-17
I also get this error with avconv in Ubuntu 14.04. It always worked up to about 13.04 when I had to go back to ffmpeg but that was not easy to install. I did not get much help when trying to report this to the avconv developpers.

Does anyone know when this might be fixed (or even acknowledged as a bug) or get ffmpeg put back into the Ubuntu repositories?

---

### Post by FakeOutdoorsman on 2014-05-17
> **wmstrome said:**
> I also get this error with avconv in Ubuntu 14.04.
Do you know the actual command WinFF is using that results in an error?

> **wmstrome said:**
> It always worked up to about 13.04 when I had to go back to ffmpeg but that was not easy to install.
Did you follow the[FFmpeg compile guide](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu)? It may take some time to compile. Generally you just need to copy and paste the instructions and it should work.

An easier alternative is the static builds. Just [download](https://ffmpeg.org/download.html#LinuxBuilds), extract, and execute. Throw it in /usr/local/bin or elsewhere in your PATH if you want it to work with WinFF. You may also have to update the WinFF presets to use ffmpeg instead of avconv. Of skip WinFF and use ffmpeg directly. See the [FFmpeg Wiki](http://trac.ffmpeg.org/wiki) for a bunch of encoding guides.

> **wmstrome said:**
> I did not get much help when trying to report this to the avconv developpers.
I'm not surprised.

> **wmstrome said:**
> Does anyone know when this might be fixed (or even acknowledged as a bug)
I'd like to see your command and the complete console output to see if I can duplicate the issue with a recent ffmpeg. Your input file may also be required to duplicate the issue. If it works with ffmpeg then use that and forget avconv.

> **wmstrome said:**
> or get ffmpeg put back into the Ubuntu repositories?
See bug [#729203](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=729203) and leave a comment for the maintainers that you want ffmpeg to be put back into Debian (and therefore Ubuntu probably).

---

### Post by michael.heuberger on 2014-05-20
Grrr, I have this issue too :(

---

### Post by monkeybrain20122 on 2014-05-20
If you install ffmpeg and use winff you have to replace its default presets with /usr/share/winff/presets-orig.xml (just by importing it in winff and click yes to all will replace the  default)

Apart from compiling you can install up to date ffmpeg from [https://launchpad.net/~samrog131/+archive/ppa](https://launchpad.net/~samrog131/+archive/ppa)

---

### Post by mdalacu on 2014-05-21
You could try my app: [dmMediaConverter]("http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html") :popcorn:

---

