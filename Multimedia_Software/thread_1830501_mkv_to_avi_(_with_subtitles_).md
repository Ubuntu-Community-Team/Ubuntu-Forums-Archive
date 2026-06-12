---
title: "mkv to avi ( with subtitles )"
date: 2011-08-21
forum: Multimedia Software
---

### Post by Skopuningurin on 2011-08-21
Hi

I'm struggling to convert mkv to avi, where the subtitles that were on the mkv also appear in the converted avi. I've successfully converted the mkv file into avi with Winff, which worked out perfectly, but I don't get any subtitles. I've tried some other convertes, but none of them showed any subtitles in the finished result...

Does anyone know a solution to this?

---

### Post by drawkcab on 2011-08-22
> **Skopuningurin said:**
> Hi

I'm struggling to convert mkv to avi, where the subtitles that were on the mkv also appear in the converted avi. I've successfully converted the mkv file into avi with Winff, which worked out perfectly, but I don't get any subtitles. I've tried some other convertes, but none of them showed any subtitles in the finished result...

Does anyone know a solution to this?

Pull the subtitles from a website and drag them into vlc.

---

### Post by BicyclerBoy on 2011-08-22
avi is an obsolete container format. A big step backwards from mkv or mpeg4.

I think only hard subtitles work in avi for stand-alone players.
You can leave subs external as SRT for PC media player.

---

### Post by Skopuningurin on 2011-08-22
Well, the fact is that I need the videofile to be playable on a external harddrive, so that I can view the video from my tv, via the external harddrive. My tv does not play mkv. 

I've downloaded an srt file to the converted avi, but it's not aligned at all, and yes. I know that I can adjust it in VLC so that the subtitles and the video are alinged. But I do not want to adjust it every single time. 

If I could somehow transfer the subtitles from the original mkv track over to the avi or what ever format it could be.

---

### Post by BicyclerBoy on 2011-08-23
If your TV is digital tuner dvb-t model it could very likely play mpeg-ts containing mpeg4/10 AVC H264.

Hardsubs in avi ?

DLNA server from PC (Samsung seems the best).

---

### Post by aeiah on 2011-08-23
avi isnt an encoding format, its a container. if your tv supports mp4, it will be better to demux the mkv and remux the video and audio into an mp4 container. you might even be able to put the subs in there, im not sure. if not, rip them out the mkv and put them into an .srt.

---

### Post by handy on 2011-08-23
I wonder whether the windows version alltoavi will run in Wine:

[http://alltoavi.sourceforge.net/](http://alltoavi.sourceforge.net/)

There is also a Linux version though it has stopped being developed:

[http://alltoavi.sourceforge.net/download.php](http://alltoavi.sourceforge.net/download.php)

It is worth a try, perhaps someone will pick it up & run with it code wise if it gets some attention here?

---

### Post by SeijiSensei on 2011-08-24
I've done this with **mencoder**, and just to be certain, I tested it again with an MKV with *SS subtitles.  Use the methods detailed [here](http://en.gentoo-wiki.com/wiki/Mencoder#XviD).  

You'll need to add an "-sid #" parameter replacing "#" with the ID of the subtitle track you want to embed.  If there's only one, it has ID 0.  Just to make sure, you can play the file with mplayer from the command line and see what it reports.  Use Ctrl-C to quit playback.  I'll assume we're using subtitle track zero.

Quick and dirty one-pass method:
```
mencoder -o output.avi -oac mp3lame -ovc xvid -xvidencopts pass=1 -sid 0 input.mkv
```

The [two-pass method]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD_Two-Pass_Encoding") described in that link will produce better quality and enable you to control the filesize.  Notice the trick of using a number like -175000 for the bitrate.  That tells mencoder to choose a bitrate that will create a file of 175MB in size.

In my test this worked well for the show itself, but created a mess during the opening and closing songs which had "karaoke" subtitles.  During encoding, mencoder complained that some of the "subtitle words" were "too long."  It might be that my mencoder is using an out-of-date libass library.  I haven't built one from source in a while now.  It could also be a problem with differing character sets, or maybe the font I'm using for the embedded subtitles is too big.  (You can't preserve *SS stylings, I don't believe.)

---

### Post by handy on 2011-08-25
Great reply SeijiSensei.

Have you thought about adding it to the wiki? It would be really nice to be able to point people to your info' on the wiki, which shows how to do it. The OP's question is bound to be an oft asked question for a long time to come.

---

### Post by SeijiSensei on 2011-08-25
> **handy said:**
> Great reply SeijiSensei.
Have you thought about adding it to the wiki?

Thanks!
What wiki is that?

---

### Post by perspectoff on 2011-08-25
> **BicyclerBoy said:**
> avi is an obsolete container format. A big step backwards from mkv or mpeg4.

I think only hard subtitles work in avi for stand-alone players.
You can leave subs external as SRT for PC media player.

My DVD players recognize neither MP4 nor MKV. Only AVI with XVID (or DivX) or MPG for video and AC3 or MP3 for audio (not AAC).

I end up converting all my MP4s and MKVs to AVI with one of those formats, "obsolete" or not.

From:

[http://www.kubuntuguide.info/index.php/Video_Conversion](http://www.kubuntuguide.info/index.php/Video_Conversion)

or

[http://ubuntuguide.org/wiki/Video_conversion](http://ubuntuguide.org/wiki/Video_conversion)

    The AVI container only allows a constant bitrate, so the MP3 audio must be encoded at CBR. If the AAC is 5.1, it will be downcoded to stereo for MP3. 

    This example is a two-pass technique that allows the file size to be specified and quality optimized for that filesize (using the information generated in the first pass). In this example, a 700 Mb file is desired (and is specified by the negative value). 

This information is from the Gentoo Wiki for Xvid and mencoder at [http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide#XviD](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide#XviD) .

mencoder <input.mp4> -ovc xvid -oac mp3lame -oac mp3lame -lameopts cbr:br=192 -xvidencopts pass=1 -o /dev/null
mencoder <input.mp4> -ovc xvid -oac mp3lame -oac mp3lame -lameopts abr:br=192 -xvidencopts pass=2:bitrate=-700000 -o <output.avi>

I like the tip about the setting for addition about the subtitle. I assume the .srt subtitle file is in the video directory and the mencoder program chooses it automatically (I've never tried it).

---

### Post by handy on 2011-08-26
> **SeijiSensei said:**
> Thanks!
What wiki is that?

Ubuntu.

---

### Post by Skopuningurin on 2011-08-26
Thanks. I'll try what you wrote!

---

### Post by BicyclerBoy on 2011-08-26
@ #11 Very detailed & practical soln.
 
The OP is not using a stand-alone DVD player but an external HDD connected to TV (USB probably).

If you wanted to support all DVD players you would be better to make compliant DVDs.
mpeg2 container with mpeg2 video mpg2 or AC3 audio.
AAC & mp3 are not DVD compliant.

For the OP, it would make more sense to determine the TV file playback capabilities & then maximize the use of them.
Some modern TVs with digital tuners have no problem playing mpeg2-ts with mpeg4/10-AVC(H264) AAC or AC3.

---

### Post by SeijiSensei on 2011-08-28
> **perspectoff said:**
> I like the tip about the setting for addition about the subtitle. I assume the .srt subtitle file is in the video directory and the mencoder program chooses it automatically (I've never tried it).

Matroska supports subtitle "streams" the same way it supports video and audio streams.  The method I described assumed the subtitles were included in the container.  With subtitles in an .srt file, I'd imagine the -sub option would work instead.  (I"ve never transcoded a file with .srt subtitles.)

---

### Post by tux-gamer on 2012-11-09
I found this Thread from Google....

I Want to share some information....

You can convert Mkv to Avi with Avidemux2, and this support SSA/AS* Subtitle with Subtitle Efect and colour.

You need to Extract the subtitle first with mkvextract.
For Font Style , you must make sure you have all the font, you can check it with Aegisub, just open the subtitle, and go to File -> Font Collector -> Check Font Availability -> then click Start

The missing font sometimes included in the Mkv, you just need to extract it, and put in /usr/share/fonts/ 
Or you can search in the web in put in /usr/share/fonts/
You can re check it with Aegisub

To add Subtitle in Avidemux2, you click in Video to Xvid, and then Click Filters , and then Subtitles , and then Double Click AS*, then Browse to Subtitle you want to Add.

ps: 
- I Use Avidemux2 2.5.5 and this not support Hi10p ( it's just my Avidemux2 or i need to compile with the newest x264 library )
For this, i will convert it with mencoder then with avidemux2

- AS* is Advanced SubStation Alpha

- I like Avi because converting to Xvid and hardsubing subtitle  is much faster

- I Put all my converted Avi file to my MiniDLNA Server (ver 1.0.25) in TPLink MR3220 with OpenWRT Backfire 10.03.1 , then Play it in my Samsung TV

---

### Post by nothingspecial on 2012-11-09
Old thread.

Closed.

---

