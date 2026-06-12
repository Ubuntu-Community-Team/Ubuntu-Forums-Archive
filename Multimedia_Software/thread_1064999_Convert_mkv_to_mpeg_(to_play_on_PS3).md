---
title: "Convert mkv to mpeg (to play on PS3)"
date: 2009-02-09
forum: Multimedia Software
---

### Post by sombrancelha on 2009-02-09
Hi,

I have downloaded a .mkv file and I want to play it on my PS3, but I heard it only plays .mpeg files.

This is a 720p video, so my question is: how can I convert it without losing quality (or with minimal loss) to mpeg?

Or if anyone knows, if there's another solution.

Thanks

---

### Post by loboc on 2009-02-09
google ffmpeg and ps3 i use it to convert for tivo bu

for my tivo it looks like

ffmpeg -i input.avi -target ntsc-dvd -b 2000k outfile.mpg

Im sure the PS3 has different acceptable formats

---

### Post by loboc on 2009-02-09
google ffmpeg and ps3 i use it to convert for tivo bu

for my tivo it looks like

ffmpeg -i input.avi -target ntsc-dvd -b 2000k outfile.mpg

Im sure the PS3 has different acceptable formats

---

### Post by sombrancelha on 2009-02-10
I tried using the command you suggested, but I got that error:

```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[matroska @ 0xb7f29110]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb7f29110]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb7f29110]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7f29110]Unknown entry 0x73a4 in info header
[matroska @ 0xb7f29110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7f29110]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from 'heroes3x14.mkv':
  Duration: 00:42:30.3, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 1280x720, 23.98 fps(r)
  Stream #0.1: Audio: 0x0000, 48000 Hz, 5:1
Output #0, dvd, to 'outfile.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 2000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1

```

---

### Post by madhi19 on 2009-09-08
The command line that I use is simple and you can drag and drop inside the terminal the file you want to convert to get the right path.


ffmpeg -i "drag and drop here" -sameq "copy the drag and drop line here except that you change the extension to mp4"

-sameq is the best way to keep quality while converting but it make for larger file I like to finish the job and reduce the size with Avidemux.
I choose this profile Video MPEG-4 (x264) Audio AAC (FAAC) Format MP4.
See bellow.
[IMG]http://ubuntuforums.org/picture.php?albumid=1351&pictureid=4714[/IMG]

---

### Post by xaliqen on 2009-09-11
You can use yamb through wine to strip tracks and reassemble in an mp4 container. You can also use mkvinfo, mkvextract, mencoder and MP4Box through the terminal.

Of course, if you want, you can use avidemux for pretty much everything too. I prefer using a variety of interfaces and you should experiment to see what works best for your needs.

Keep in mind that PS3 doesn't support most subtitles unless contained in an avi (and only srt or idx/sub).  So, you'll have to burn in any subtitles for mp4 (and re-encode) using avidemux or similar.  Here's hoping Sony adds support for soft subs in mp4 at some point!

---
Example: To convert a file named needles.mkv from mkv to mp4 without re-encoding, from the command line enter:

$ sudo apt-get update && sudo apt-get install gpac mkvtoolnix

{This installs the tools you will use for the conversion.}

$ mkvinfo needles.mkv

{This gives you information about each track in the file so that you can perform the extraction properly (for example: track number 1 is video encoded with AVC/mpeg4 at 23.976 fps; track 2 is AAC audio; track 3 is subtitles in SRT format) Be sure to note the fps for the video track, because you will use this later with MP4Box.}

$ mkvextract tracks needles.mkv 1:needles_video.h264 2:needles_audio.aac 3:needles_subtitles.srt

{This extracts the tracks and names them according to what you specify.  Be sure to specify names for the tracks that match the information from mkvinfo}

$ MP4Box -fps 23.976 -add needles_video.h264 -add needles_audio.aac -add needles_subtitles.srt needles_final.mp4

{this tells MP4Box the source material is running at 23.976 fps (change according to fps information from mkvinfo you noted earlier) and to combine your extracted video, audio and subtitles tracks into an mp4 container named "needles_final.mp4"}
---

So, there's your straight conversion to an mp4 file without re-encoding.

But remember, the subtitles in my example will not display on PS3, because they are not burned into the video (i.e. part of the picture and non-removable).

If you want your PS3 to display subtitles in an mp4, I suggest using avidemux to re-encode the video with the subtitles filter:

In avidemux, open the original file you want to convert to mp4 (e.g. needles.mkv). Add the subtitle track (e.g. needles_subtitles.srt) extracted using mkvextract to the subtitles filter in avidemux (located under "Filters").  Use the subtitle filter appropriate for the type of subtitles you are using (e.g. subtitler for srt), and be sure to select a ttf font if it asks for one. Remember, you have to re-encode the video for this to work (e.g. select MPEG-4 AVC under video), otherwise the subtitles won't be burned into the video.  Finally, select mp4 under "Format", save the video (ctrl+s) and wait for the encode to finish.

Since you are re-encoding the video when you use avidemux to burn in the subtitles, you may notice a loss in visual quality.

There are some steps you can take to minimize the quality lost in an avidemux re-encode.  One way is to click on "Configure" and change the encoding mode to "Video Size (two pass)" and make sure the target video size is the same size as the video information in the original file (e.g. same size as needles_video.h264).  This works reasonably well when I've tried it.

As a final note on subtitles, MP4Box is not compatible with SSA and various other subtitle formats at the moment.  Therefore, if you are trying to add soft-subs in this format, you must first convert them to a format MP4Box understands.  Just open the subtitles extracted with mkvextract (e.g. needles_subtitles.ssa) using a subtitle-editing program such as Gnome Subtitles.  Then save a copy as subrip (srt) or other compatible format, and you're ready to put things together with MP4Box.

---

### Post by sadohert on 2009-11-13
I originally started to solve my same problem following this thread:

[http://ubuntuforums.org/showthread.php?t=548547](http://ubuntuforums.org/showthread.php?t=548547)

And the script they refer to in it.  When I went to reply to update on the thigns I had to do differently (its a thread from 2008) I couldn't because it was closed, so I search for a related thread and ended up here... SOO... I'll put my updates here.

I used the last version of the mkv2ps3.pl script mentioned in that thread.  I had 2 problems after I installed all the tools (install gpac for MP4Box, and mkvtoolnix for the mkv tools).
- I couldn't find the nero software then link to.  But after a quick google I guess I found the latest:
[http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php](http://www.nero.com/eng/downloads-nerodigital-nero-aac-codec.php)
-The script expects mp4box, but gpac installs MP4Box... I Just made a symlink to mp4box:
cd /usr/bin/
sudo ln -s MP4Box mp4box

I'm doing my first test right now, but won't be able to test t6he PS3 until I get home.  I'll try to remember to follow up with results.... actually... scratch that... I just checked on things and MP4Box gave me a buffer overflow.  Everythign else up to that point *SEEMED* to work.

I'll have to keep looking into it.

---

### Post by SSamiK on 2009-11-15
I have found wine+mkv2vob to be the simplest way to do this. It works very well, and takes next to no time. 

It's quite easy; 
Install wine
```
sudo aptitide install wine
```
Then get winetricks
```
 wget http://www.kegel.com/wine/winetricks
```
Use winetricks to install some dependencies
```
./winetricks vb6run wsh56
```
Download mkv2vob
```
wget http://www.3r1c.eu/mkv2vob/mkv2vob.exe
```
And install it like this: 
```
wine mkv2vob.exe INSTALLDIR=&#8221;C:\\mkv2vob&#8221;
```

And you should be good to go...

---

### Post by pellgarlic on 2010-01-13
just to add to SSamiK's instructions in the previous post:

after:

```
wget http://www.kegel.com/wine/winetricks
```

you need to make the file executable:

```
chmod a+x winetricks
```

before you execute it:

```
./winetricks vb6run wsh56
```


also, anyone else getting "that folder is invalid" when trying to install visual basic 6.0 this way? it doesn't even ask for a folder... =(

---

### Post by Etern1ty on 2010-01-24
I'm getting the invalid folder thing too, anybody got a solution?

---

### Post by omanni on 2010-02-12
worked perfectly for me. thanks!

---

### Post by The_Boss on 2010-03-20
> **Etern1ty said:**
> I'm getting the invalid folder thing too, anybody got a solution?

I ran across the 'invalid folder' issue just now, and was able to resolve it.  The issue was that I must have originally tried running winetricks as the root user "sudo winetricks", so it creates it's temporary folder with "root" as the owner.  You just need to modify the owner of the winetricks temporary folder:

sudo chown ~/.winetrickscache <your username>

Then you should be able to install properly.

---

### Post by pSYcl0Ne on 2011-09-25
I know this is an old thread, but I was wondering if there is a way to ski all this and use mediatomb to stream the mkv similar to tversity or windows media player does when the right codecs are installed?

---

### Post by nothingspecial on 2011-09-25
> **pSYcl0Ne said:**
> I know this is an old thread

You are right. Please make a new one. This one is moldy.

Closed.

---

