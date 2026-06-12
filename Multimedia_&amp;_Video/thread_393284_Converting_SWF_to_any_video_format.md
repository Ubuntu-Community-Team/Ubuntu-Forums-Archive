---
title: "Converting SWF to any video format?"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-03-25
How can I convert a .swf/.flv video to a "regular" video format such as .mpg/.avi?

ffmpeg can't do the job. Output:> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
[swf @ 0xb7f09c30]Compressed SWF format not supported
/home/pdedecker/Desktop/BB_table.swf: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by muhkayoh on 2007-04-03
> **Mariana-1 said:**
> Take a look at [Flash To Video Encoder]("http://www.geovid.com/Flash_To_Video_Encoder/"). I've been using it for some years.

Great, but how would you do it in Ubuntu?  I tried your suggested program in CrossOver and couldn't get it running.  Still looking for a linux-based way to do this.  So far, neither mencoder nor ffmpeg can read swf files a far as I can tell.  I've also tried a host of Windows programs (since I have CrossOver) but can't get any of them to work.  Also, some linux video editors can apparently output swfs (like LiVES), but can't read swfs for converting to other formats.

I'm even willing to use a command line solution if there is one.  Just can't find anything that works.  And, I should add, unlike the original poster, I'm only interested in converting swf files, not flv files (which ffmpeg apparently can handle from what I've read elsewhere).

Thanks,

Matt

---

### Post by stokedfish on 2007-04-03
[www.vixy.net](www.vixy.net)  ;)

---

### Post by muhkayoh on 2007-04-03
> **stokedfish said:**
> [www.vixy.net](www.vixy.net)  ;)

Thanks but - again - unless I'm missing something, this is an flv convertor.  From the site:

> This service allows you convert a Flash Video / FLV file (YouTube's videos,etc) to MPEG4 (AVI/MOV/MP4/MP3/3GP) file online. It is using a compressed domain transcoder technology (outline in Japanese). It converts FLV to MPEG4 faster and less lossy than a typical transcoder.

To the extent that the original poster mentioned both swf and flv (though the subject of the post mentions only swf), consider the flv part answered.  Still looking for swf conversion capability in linux, though.

Thanks,

Matt

---

### Post by elreteipos on 2007-04-04
> **muhkayoh said:**
> Great, but how would you do it in Ubuntu?What? It's not free and it's not even Linux-based? I can find [free conversion software for Windows]("http://www.erightsoft.com/SUPER.html") easily...

---

### Post by muhkayoh on 2007-12-06
> **sunground said:**
> You can use [SWF to Video Converter]("http://www.swfkits.com/swf_to_video/") to converter swf to mpg, avi, etc, and you can also use [FLV to Video Converter]("http://www.flvsoft.com/flv_to_video") to convert flv to avi, mpg, or other formats, hope this can help you.

Thanks for the reply, but again I'm only interested in a linux-based solution.  The product you linked is a Windows product.  From the site:

>  System Requirements

    * Windows 2000, NT4.0 + SP6, XP, Vista, etc. 

For the purposes of this thread, there's really no need to post anymore Windows-based solutions.  There are plenty of them around.  My quest is for a Linux-based solution. 

And to reiterate, we have a way to convert flv files.  So I'm only interested in a linux-based swf-to-video converter.  

This is an old thread and I've been busy with other projects, so it's possible that there has been some new development along these lines.  I'll try to do a little new research and will report if I find anything promising.

Thanks,

Matt

---

### Post by eye208 on 2007-12-06
You can always start up RecordMyDesktop and record whatever is being shown on your screen. Then use MEncoder to transcode the resulting .ogg file to your format of choice.

I'm using this method to capture game engine graphics all the time (see my signature) and it works pretty well as you can see. Doing the same with SWF animations should not be difficult.

---

### Post by muhkayoh on 2007-12-06
I have tried that approach and found it unsatisfactory for my purposes.  The screen capture rate is really too slow when what you're wanting to do is basically convert flash to a format that could be used for broadcast video of an animated cartoon.

EDIT:  I also have had trouble with bounding box ghosts - i.e., the screen capture picks up the bounding box for many movie clips, rendering the resulting footage unwatchable.

But it does work well enough for other, less demanding purposes.

Matt

---

### Post by eye208 on 2007-12-07
I capture 3D graphics using the "full shots at every frame" option at 25 fps without problems. If you can't get a decent frame rate even with 2D Flash, this might be due to a misconfiguration of X.org.

Do you have direct rendering enabled?

---

### Post by elreteipos on 2007-12-07
@eye208: have you tried capturing a game? Does that cause any problems? You should also note that the speed probably depends on the speed of your video card. I tried xvidcap and Istanbul in the past and they couldn't capture 25 frames per second...

---

### Post by eye208 on 2007-12-10
> **elreteipos said:**
> @eye208: have you tried capturing a game?
Yes. Results can be seen [here](http://masami.blip.tv/posts?view=archive).

> I tried xvidcap and Istanbul in the past and they couldn't capture 25 frames per second...
Istanbul didn't work for me either. RecordMyDesktop is quite good for capturing game graphics if the game is running in windowed mode. There is another tool for full-screen capturing named "Yukon", but I haven't used that yet.

---

### Post by lsutiger on 2007-12-12
FFMPEG will do what you need. You need to install it from the mediabuntu repository. [Follow this guide.]("http://www.ubuntu1501.com/2007/11/how-to-convert-videos-for-your-ipod.html")

---

### Post by muhkayoh on 2007-12-13
> **lsutiger said:**
> FFMPEG will do what you need. You need to install it from the mediabuntu repository. [Follow this guide.]("http://www.ubuntu1501.com/2007/11/how-to-convert-videos-for-your-ipod.html")

It doesn't appear to work for converting swf to video.  (It works great for flv to other video format, but we've resolved that earlier in the thread.)

Here's a thread on this forum demonstrating the recurring problem with attempting swf-to-vid conversion with ffmpeg:

[http://ubuntuforums.org/showthread.php?t=411707](http://ubuntuforums.org/showthread.php?t=411707)

And here's an even more recent thread from the ffmpeg user-list archives still showing failure:

[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/011845.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/011845.html)

Given how often this comes up (I've found dozens of fruitless attempts all around the web), you'd make a lot of folks happy by explaining the method to get this to work (or linking to a how-to, since I can't find it).  But everything I've read online suggests that, while a lot of people seem to think it *should* work, nobody seems to be able to get it to work.  I also remember reading a definitive statement earlier this year that ffmpeg could not convert swf to video but a) I can't find that link anymore and b) things may have changed.

Matt

---

### Post by srmantis on 2007-12-13
-Install mencoder:
sudo apt-get install mencoder

-for example: video.flv to video.avi
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video.flv -o video.avi

---

### Post by muhkayoh on 2007-12-13
> **srmantis said:**
> -Install mencoder:
sudo apt-get install mencoder

-for example: video.flv to video.avi
mencoder -oac mp3lame -lameopts cbr=128 -ovc xvid -xvidencopts bitrate=1200 video.flv -o video.avi

Heh, I guess I'll just have to live with the fact that people will keep posting about the flv issue that's already been solved.  Here, have some popcorn...:popcorn:

Matt

---

### Post by srmantis on 2007-12-15
it's not easy. You need to download the next files:
from:
[http://davidf.sjsoft.com/files/pyvnc2swf/](http://davidf.sjsoft.com/files/pyvnc2swf/)
download:
pyvnc2swf-0.8.2.1.tar.gz
unrar on desktop
it's necessary because contains the file "edit.py"


from:
[http://sourceforge.net/project/showfiles.php?group_id=86491&package_id=89813&release_id=368116](http://sourceforge.net/project/showfiles.php?group_id=86491&package_id=89813&release_id=368116)
download:
pymedia_1.3.5_i686-py2.4.deb
double click and to install.
it's necessary because contains the codec: mpg

to install python-pygame from synaptic
it's necessary to run the file "edit.py"
if you understand spanish go:
[http://cgacimartin.wordpress.com/2007/09/11/convertir-swf-en-avi-y-salvar-videos-de-youtube/](http://cgacimartin.wordpress.com/2007/09/11/convertir-swf-en-avi-y-salvar-videos-de-youtube/)


I don't try to convert because i have ubuntu amd64 and the solution is for normal ubuntu (32 bit o x86)

To convert:
copy video_input.swf
cp video_input.swf /Desktop/pyvnc2swf-0.8.2.1/pyvnc2swf

now you go to the file cd /Desktop/pyvnc2swf-0.8.2.1/pyvnc2swf
and to run edit.py:

python edit.py -o video_output.mpg video_input.swf

finally video_output.mpg to avi, you use the mencoder

Good luck

---

