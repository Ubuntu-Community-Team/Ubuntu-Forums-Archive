---
title: "Help with Amarok and XVID"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by telovoyagarcar on 2007-08-08
I just installed the Wubi version of Ubuntu. Feisty.

Amarok does not play my XVID videos. I installed the Gstreamer ffmpeg package from synaptics. Here is the description of the package:

[B]FFmpeg plugin for GStreamer
This GStreamer plugin supports a large number of audio and video compression
formats through the use of the FFmpeg library.  The plugin contains GStreamer
elements for encoding 40+ formats (MPEG, DivX, MPEG4, AC3, DV, ...), decoding
90+ formats (AVI, MPEG, OGG, Matroska, ASF, ...), demuxing 30+ formats and
colorspace conversion.[/B]

I assume that now it should work, but Amarok can't find the codecs. 
What else can i try? I don't want to use automatix... i read it breaks some security stuff in the system.
Thanks

---

### Post by Steveway on 2007-08-08
Amarok is used to play music, not videos!
You should use VLC or Mplayer or another Videoplayer for your videos.

---

### Post by telovoyagarcar on 2007-08-08
What about this: It does not even play MP3. it crashes. "no mp3 support"

---

### Post by A-Sylum on 2007-08-08
get mplayer from add/remove software in applications --> system

and i used automatix to get my codecs and they work just fine :D and i don't see anything wrong with my system 

if you want to install it go to your terminal and type
> 
wget [http://beerorkid.com/arnieboy/automatix_6.1_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1_i386.deb)
sudo dpkg -i automatix_6.1_i386.deb


and if somethng goes horribly wrong type
> 
sudo apt-get remove automatix


oh god, never mind that code is like 2 years old!!
go here instead 
> 
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29)


---

