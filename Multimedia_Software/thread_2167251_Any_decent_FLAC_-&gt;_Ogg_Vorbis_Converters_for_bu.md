---
title: "Any decent FLAC -&gt; Ogg Vorbis Converters for *buntu?"
date: 2013-08-13
forum: Multimedia Software
---

### Post by Gilad_Pellaeon on 2013-08-13
I had a look this evening in Lubuntu software center and I wasn't really too impressed. Tried both sound converters available and uninstalled both. So far the only decent converters I have to convert FLAC to Ogg Vorbis with finer quality control is the following under a WinXP virtualbox VM. Foobar2000 for loading the FLAC files and using Oggenc2 to convert them, and MP3TAG software being used to strip all extended tags, convert filename to title tag, and finally again Foobar2000 to use it's Replaygain scanner on a per track (file) basis.  

I'd love to be able to find *buntu replacements for converting flac to ogg vorbis, tagging ogg files with embedded artwork and a good replaygain scanner that applies the replaygain tags so that Audacious can use it, but so far i've not seen much for converting unless someone knows of other alternatives that don't require Windows XP in a VM. :)

Foobar2000 - [http://www.foobar2000.org/](http://www.foobar2000.org/)

MP3TAG - [http://www.mp3tag.de/en/](http://www.mp3tag.de/en/)

Oggenc2 - [http://www.rarewares.org/ogg-oggenc.php#oggenc-libvorbis](http://www.rarewares.org/ogg-oggenc.php#oggenc-libvorbis)

---

### Post by shantiq on 2013-08-13
Command line can do the conversion very neatly


cd to folder your album is in

then run:


```
for f in *.flac ; do ffmpeg -i "$f"  -c:a libvorbis   -b:a 320k  "${f%.*}.ogg"; done 
```


all tags will be kept but not artwork  [maybe someone knows how to add this functionality to the line of code if available]


if you want to do folders in bulk   use


```
for i in */
do
cd "$i"
for f in *.flac ; do ffmpeg -i "$f"  -c:a libvorbis   -b:a 320k  "${f%.*}.ogg"; done 
cd ..
done
```

---

### Post by Gilad_Pellaeon on 2013-08-13
Good to know about being able to use the command line if need be to mass convert flac files like that, thanks! :) Although for some reason I only see libvorbis 1.32 instead of 1.33 which I thought was kind of odd.

---

### Post by shantiq on 2013-08-13
hi Gilad may i suggest installing the very latest [ffmpeg]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide")   instead of the one you will have got if you just went to the repository

might provide you with l[COLOR=#000000]ibvorbis 1.33     [but i have not updated for 3 months or so and therefore do not know]    as it is up to date




[/COLOR]   &#9679;  [COLOR=#000000][B]using oggenc and oggenc2
[/B][/COLOR][COLOR=#000000]

use [1.33 ]("https://launchpad.net/vorbis/trunk/1.3.3/+download/libvorbis-1.3.3.tar.gz")  from [here ]("https://launchpad.net/vorbis/trunk/1.3.3")     install with   > ./configure && make   then run  > sudo make install


[more]("http://www.xiph.org/downloads/") versions ?


[/COLOR]> **for f in *.flac ; do  oggenc  "$f" -b 320k  "${f%.*}.ogg"; done **


but sadly  oggenc is part of vorbis-tools and seems stuck on 1.32 for Ubuntu


> it gives you  [COLOR=#444444][FONT=arial]Xiph.Org [/FONT][/COLOR][COLOR=#444444][FONT=arial]**libVorbis I 20101101**[/FONT][/COLOR][COLOR=#444444][FONT=arial] (Schaufenugget)[/FONT][/COLOR]
    which is 1.32  
[COLOR=#000000]

[/COLOR][COLOR=#444444][FONT=arial]Schaufenugget  =1.32   Omnipresent  = 1.33    if you read in mediainfo or ogginfo or winamp or foobar[/FONT][/COLOR][COLOR=#000000]



=====================  i leave all previous info up  but the answer to your question is this  ====>

**SO USE** the oggenc2 [/COLOR][COLOR=#000000]you [linked]("http://www.rarewares.org/ogg-oggenc.php") under wine and run     [/COLOR][COLOR=#000000][place it in the folder you want converted make it executable (right click/properties/permissions/tick execute)and cd there] 


Now this works and gives you   [/COLOR]

[COLOR=#000000]

[/COLOR]>  [B]for f in *.flac ; do wine oggenc2  "$f" -b 320k  "${f%.*}.ogg"; done
 [/B]

fixme:service:scmdatabase_autostart_services Auto-start service L"UMWdf" failed to start: 2
fixme:heap:HeapSetInformation 0x230000 0 0x22fc90 4
Z:\home\shan\Desktop\oggenc2\oggenc2.exe: invalid option -- i
WARNING: Unknown option specified, ignoring->
Opening with flac module: FLAC file reader
    [ 99.7%] [ 0m00s remaining] -


Done encoding file "01 - Içime Sinmiyor.ogg"


    File length:  3m 48.0s
    Elapsed time: 0m 17.0s
    Rate:         13.4306

    Average bitrate: 332.4 kb/s


which is  1.33   >  Writing library : libVorbis (Omnipresent) (20120203 (Omnipresent))

[COLOR=#000000]



and then maybe to play command line too with>  ogg123 *
   [/COLOR]ogg123 --help

---

