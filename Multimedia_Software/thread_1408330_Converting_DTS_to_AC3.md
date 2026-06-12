---
title: "Converting DTS to AC3"
date: 2010-02-16
forum: Multimedia Software
---

### Post by phoenix81000 on 2010-02-16
Hey everyone,

I have spend the entire weekend trying to convert a mkv file with a DTS audio track to an AC3 audio track. I wrote a small article on it on my website with plenty of links and suggestions. I used applications like TVersity, PS3 Media Server, mkvdts2ac3 script, and avidemux. I just hope i can save someone's weekend with this. Anyway here is the link:

<link snipped for spam>

---

### Post by sukeltje on 2010-02-16
Thank you so much for this!

i just couldnt get my movies to convert right and already gave up untill i came across this :)

---

### Post by ridetheteapot on 2010-09-22
It's a little old of a thread, but still thought i should add this.

Avidemux (and also ffmpeg it seems) have a nice bug when converting from aac to ac3.
The center channel audio is sent to the front left speaker! this sucks and pretty much makes using avidemux a No-Go for the usage described in the link. (Maybe there is some way to map channels in avidemux to manually correct this, I do not know)

I don't really know how anyone followed the link didn't notice it - but avidemux still has a bug to be squashed in this regard.

---

### Post by MarceloCulotta on 2011-09-01
For converting MKV DTS to MKV ac3, I use two applications: 
WinFF and MKVmerge (it shows as MKV files creator in the Applications menu)


[LIST=1]
[*]WinFF:For creating the AC3  audio track, I open WinFF, then I Add the MKV file that contains the DTS  track. In Output details,  I select
[/LIST]
           
           Convet to           **Audio**
            Device Preset      **Ac3 - 384kbps Stereo **
           Output Folder      **Any folder you like** (I use the one containing the MKV file)
           
           This will create an audio file with the same name as the MKV file, but with the   ac3 extension

            2. MKV files creator (mkvmerge)
    
    Input Files: **add the MKV** file for which you created the ac3 audio track.
    In the Tracks, chapters and tags, **UNSELECT the DTS audio file**
    Input files again: **add the ac3** file that you created with WinFF
    **Start muxing**

This creates a file with the same name as the MKV file, except it has a  (1) added to it that will have the ac3 audio track for playing as 2  channel stereo.
   
I hope this helps!

---

### Post by Zulu (Be) on 2011-09-25
WinFF only supports AC3 - STEREO, no dolby surround ! If you want more read on ...

FFmpeg can convert to dolby but has one very annoying problem: center speaker sound is not correctly mapped.

best solution is to use the **[mkvdts2ac3]("https://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664")** script**. **

[https://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664](https://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664)

Very user friendly, even for a ubuntu dummy like me ;).

However, if you have to convert larger dts files it becomes tricky: 

since dcadec is used, you need to install package [libdca]("http://videolan.org/developers/libdca.html%5D"). I recommend following site (step 1)
[http://juliensimon.blogspot.com/2009/01/howto-processing-multichannel-audio-dts.html](http://juliensimon.blogspot.com/2009/01/howto-processing-multichannel-audio-dts.html)

However Package libdca-0.0.5  has a bug when converting large files. You need to adapt 
in previous link following step: 

ubuntu% ./configure --prefix=/usr/local[B]

[/B]should become 

ubuntu% ./configure --prefix=/usr/local **CFLAGS="-D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE"**

(see also [http://forums.gentoo.org/viewtopic-t-836439-start-0.html](http://forums.gentoo.org/viewtopic-t-836439-start-0.html) )

I hope this will save you a lot of time I had to spent finding a real solution to convert DTS to AC3 - dolby surround :D

---

