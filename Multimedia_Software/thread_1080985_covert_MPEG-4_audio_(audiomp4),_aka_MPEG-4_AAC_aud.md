---
title: "covert: MPEG-4 audio (audio/mp4), aka MPEG-4 AAC audio to .mp3"
date: 2009-02-26
forum: Multimedia Software
---

### Post by WaNaBePi on 2009-02-26
i have some music files that are on a external hard drive but they are all in .aac and i cant play them on my ipod. they add fine even show up on the list but wont play. so i guess i need to convert them to .mp3 so i can listen to them

ive looked around the forums and i cant seem to post where i want to post or im not getting answered....so

how do i convert .aac to .mp3

i already have faad and lame installed...when i attempt to convert using this script:

faad -w inputfile.aac | lame - outputfile.mp3

i get:

projectmayhem@projectmayhem-lapbottom:~$ faad -w blue moon.aac | lame - blue moon.mp3
lame: excess arg moon.mp3
 *********** Ahead Software MPEG-4 AAC Decoder V2.6 ******************

 Build: Oct  8 2008
 Copyright 2002-2004: Ahead Software AG
 [http://www.audiocoding.com](http://www.audiocoding.com)
 Floating point version

 This program is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License.

 **************************************************************************

Only raw PCM data (2) may be sent to the standard out.
projectmayhem@projectmayhem-lapbottom:~$ faad -w bluemoon.aac | lame - bluemoon.mp3
 *********** Ahead Software MPEG-4 AAC Decoder V2.6 ******************

 Build: Oct  8 2008
 Copyright 2002-2004: Ahead Software AG
 [http://www.audiocoding.com](http://www.audiocoding.com)
 Floating point version

 This program is free software; you can redistribute it and/or modify
 it under the terms of the GNU General Public License.

 **************************************************************************

Only raw PCM data (2) may be sent to the standard out.
Warning: unsupported audio format
projectmayhem@projectmayhem-lapbottom:~$ 


those were two attempts I just tried, special just for who ever answers this. what am I doing wrong?

---

### Post by dLeon on 2009-02-26
That's mean you must produce WAV output; not mp3.
PS:
Except Mplayer/Mencoder, I notice there are some AAC converters in main repo's.

---

### Post by dzark on 2009-02-26
easy answer is use vlc (apt/aptitude/synaptic install vlc)

If it's only one or two files just use the wizard from the Media -> Convert/Save.. option in the GUI

If it's a whole lot, or a few big ones, reply back and i'll help you build a command for it.. or use ```
man vlc
```

---

### Post by WaNaBePi on 2009-02-26
I think if its possible, there are 2 different codecs on these songs

the properties window reads:

type: MPEG-4 video (video/mp4)

codec: MPEG-4 AAC audio

so its seems to be both a video and audio file? a likely cause as to why I'm having so much trouble?

i tried converting them using vlc the "media>covert/save" method but in actuality the songs wont play in vlc...they only play in totem...no scratch that, they play fine, I renamed them .mp4....when I have the list showing, in list view, the type reads "MPEG-4 video" regardless whether i name the the individual song .aac or .mp4....so i guess they are more .mp4? so i need to convert .mp4 to .mp3....sorry guys, if i could give better information I would.

i have 250mb of data @ about 150 songs. so it may be worth the trouble to write a command, once we figure out a conversion process.

Thank You SO Much for replying to me. I've been in the dark about this for some time.

---

### Post by dzark on 2009-02-26
try the 'convert/save' in vlc. 

1st dialog box, select the file you wish to open
2nd dialog box, output filename and select "Profile: MP3" and hit save


There wont be any music playing while it does its thing, but once the seek bar has gone all the way to the end you'll have an MP3

---

### Post by WaNaBePi on 2009-02-27
when i do the convert save there is no "seek bar". let me go through what i am doing. i tried to put up screen shots but i need to toy with the sizes. so describing what im doing with words will take just as much time....

so i: 

open vlc media player

navigte to media> covnvert/save

i click on covert/save

a window called "open" comes up

using the "look in:" pull down menu i navigate to the file i want to covert.

i double click the file i want

a windo comes up titled "stream output"

in the "outputs" section of that window i check the box "file"

then with the browse button in the same area, i again navigate to the appropriate file

in the generated output string text line i have:

:sout=#duplicate{dst=std{access=file,dst=/home/projectmayhem/Desktop/Pandora music/Akron& Family/Crickets.mp3}}

i then hit save the stream output window disappears, and im left with just the vlc media plaer main window.

i search for, in this case "Crickets.mp3" using the "search for files" under "places" and there is no "Crickets.mp3" to be found in the entire "file system"...........

at this point it may be easier for me to just copy and paste a code or script... but I don't know what that entails, I certainly haven't the fist clue how to write a script to convert these blasted files.

thanks again.

---

### Post by WaNaBePi on 2009-03-01
still no solution to covert.....

"Type: MPEG-4 video (video/mp4)"

"audio
   Codec: MPEG-4 AAC audio"


....to .mp3, anyone have a solution?

---

### Post by dzark on 2009-03-01
VLC **will** do it. RTFM. :)

[http://wiki.videolan.org/Documentation:Documentation](http://wiki.videolan.org/Documentation:Documentation)

---

### Post by mc4man on 2009-03-01
Why don't you first find out if you have really have video or not.
if your on 8.10 then just install mediainfo - .deb available here
[http://www.getdeb.net/search.php?keywords=mediainfo](http://www.getdeb.net/search.php?keywords=mediainfo)
Then open mediainfo and just drop one of your files on it. (the view > html will provide full info

Or install ffmpeg and go 
ffmpeg -i path to file

If you have just audio there's a good possibility the reason the ipod won't play is they're encoded to the 'main' profile, an ipod wants 'LC' profile. (mediainfo will tell you that.

---

### Post by WaNaBePi on 2009-03-02
well i just read tfm. vlc still just stops playing the song as soon as i click save in the stream output window, and i search for .mp3 on my entire file system and it doesn't come up. it also doesn't even mention the stream out put window, which is the one that actually says convert/save not just convert...in addition I had to add the.mp4 part at the end of the file because originally they don't have a ".anything"
~~~~~~~~~~~~~~~~~~~~~~~~~~~
mc4man I appreciate the suggestion but I have no clue how to install that software its in 3 different parts...this is what ffmpeg got me...is there a script to chagne from main to lc???????

projectmayhem@projectmayhem-lapbottom:~$ ffmpeg -i /home/projectmayhem/Desktop/Pandora music/Akron& Family/crickets.mp4
[1] 9388
bash: Family/crickets.mp4: No such file or directory
projectmayhem@projectmayhem-lapbottom:~$ FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
/home/projectmayhem/Desktop/Pandora: no such file or directory
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
there seriously isn't a script out there that I can insert a given .mp4 and get a .mp3...it amazes me.

im ready to call it quits...almost

---

### Post by mc4man on 2009-03-02
> I have no clue how to install that software its in 3 different parts.

I'm sorry, forgot that it had 2 dependencies. Easiest way is to d. click and install the .deb's from right to left (in other words mediainfo is last.

When it comes to dealing with music files and folders life is much easier if you install and use nautilus-open-terminal. (allows you to right click on a folder and open that folder at a terminal prompt, then you just run a command or script
```

sudo apt-get install nautilus-open-terminal
```

After installing go Ctrl+backspace to enable

This way you could just right click on the 'Akron& Family' folder and when the terminal pops up go
```
ffmpeg -i crickets.mp4
```

the reason ffmpeg couldn't find it is you have spaces in the path and even if you didn't one mistyped letter and the path is wrong

This probably would work but install nautilus.... anyway, will make converting easy

```
ffmpeg -i /home/projectmayhem/Desktop'/Pandora music/Akron& Family/crickets.mp4'
```

If you want I'll give you a command to convert to either mp3 or m4a (LC), it would be better to know what you have first (mediainfo would be best

See what properties shows if you change the ext. to m4a

---

### Post by WaNaBePi on 2009-03-03
ok! thank you so much, im in the middle of my math home work so im gonna try that in a bit, but i have a good felling about this one.

---

### Post by WaNaBePi on 2009-03-04
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i crickets.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
crickets.mp4: no such file or directory
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i crickets
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
crickets: no such file or directory
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ 


^^^^^when i use the "ffmpg, natulis open terminal route" i get the above^^^^

the "media info":

General

Complete name                    : /home/projectmayhem/Desktop/Pandoramusic/Akron&Family/Crickets.mp4

Format                           : MPEG-4

Format profile                   : Base Media / Version 2

Codec ID                         : mp42

File size                        : 1.85 MiB

Duration                         : 3mn 59s

Overall bit rate                 : 64.8 Kbps

Encoded date                     : UTC 2008-02-29 22:59:10

Tagged date                      : UTC 2008-02-29 22:59:10



Audio

ID                               : 1

Format                           : AAC

Format/Info                      : Advanced Audio Codec

Format version                   : Version 4

Format profile                   : LC

Format settings, SBR             : Yes

Format settings, PS              : No

Codec ID                         : 40

Duration                         : 3mn 59s

Bit rate mode                    : Constant

Bit rate                         : 64.0 Kbps

Channel(s)                       : 2 channels

Channel positions                : L R

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits

Stream size                      : 1.83 MiB (99%)

Encoded date                     : UTC 2008-02-29 22:59:10

Tagged date                      : UTC 2008-02-29 22:59:10





GETTING WARMER!!!!!

---

### Post by WaNaBePi on 2009-03-04
I tried it again, with no file extension, and i got this!!!!! how do i designate the output file type??????? in the code:"ffmpeg -i crickets" 


projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i Crickets
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Crickets':
  Duration: 00:03:59.2, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0(und): Audio: mpeg4aac, 44100 Hz, stereo
Must supply at least one output file
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$

---

### Post by andrew.46 on 2009-03-04
Hi WaNaBePi,

> **WaNaBePi said:**
> I tried it again, with no file extension, and i got this!!!!! how do i designate the output file type??????? in the code:"ffmpeg -i crickets" 

The command that mc4man gave you is simply to identify the file that you want to convert. You can make life easy for yourself by typing:

```
ffmpeg -i crick
```

and then pressing the tab key, which will complete the filename for you. But the file has been identified for you now:

```
$ ffmpeg -i Crickets
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 
Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab 
--prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis 
--enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin 
--enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te 
--disable-armv6 --disable-altivec --disable-vis --enable-shared 
--disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Crickets':
[B][COLOR="Red"]  Duration: 00:03:59.2, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0(und): Audio: mpeg4aac, 44100 Hz, stereo[/COLOR][/B]
Must supply at least one output file
```

Does not look as if your copy of FFmpeg comes ready for mp3 conversion, might be worthwhile looking into that if you want to continue with FFmpeg? The version of FFmpeg looks like Intrepid which usually means you need to install [libavcodec-unstripped-51]("http://packages.ubuntu.com/intrepid/libavcodec-unstripped-51"):

```
sudo apt-get install libavcodec-unstripped-51
```

to be able to have a useful FFmpeg and in particular the ability to encode to mp3.

Andrew

---

### Post by WaNaBePi on 2009-03-04
so now that i have finaly identified the file how do i convet it to .mp3 i installed that "libavcodec-unstripped-51" didn't change anything far as i can tell...
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i Crickets
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Crickets':
  Duration: 00:03:59.2, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0(und): Audio: mpeg4aac, 44100 Hz, stereo
Must supply at least one output file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by FakeOutdoorsman on 2009-03-04
You need to specify an output file:
```
ffmpeg -i Crickets -acodec libmp3lame output.mp3
```

---

### Post by mc4man on 2009-03-04
Not really up on these new formats but what stands out in your mediainfo is 
> Overall bit rate : 64.8 Kbps
Format settings, SBR : Yes

Maybe that's why your ipod doesn't accept...? (HE-AAC, ACC+ ?)

You could use ffmpeg or try soundkonverter, soundconverter for a gui
You may want to add some basic tags before adding to ipod (easytag, others

If you have multiple tracks here's a basic command (or you could make a simple script 

At the directory (folder) prompt

```
for f in *.mp4; do ffmpeg -i "$f" -acodec libmp3lame  "${f%.mp4}.mp3"; done && mkdir temp && mv *.mp3 ./temp

```

(you can change the mkdir, mv to anywhere you wish or set a destination directly in front of this ${f%.mp4}.mp3"

Ex. to existing folder, mp3, in Music folder
> for f in *.mp4; do ffmpeg -i "$f" -acodec libmp3lame ~/Music/mp3/"${f%.mp4}.mp3"; done

---

### Post by WaNaBePi on 2009-03-05
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i Crickets -acodec libmp3lame output.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Crickets':
  Duration: 00:03:59.2, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0(und): Audio: mpeg4aac, 44100 Hz, stereo
Output #0, mp2, to 'output.mp3':
    Stream #0.0(und): Audio: libmp3lame, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1869kB time=239.3 bitrate=  64.0kbits/s    
video:0kB audio:1869kB global headers:0kB muxing overhead 0.000000%
projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ 

so as you can see i acctualy got some thing!!!!!!!!! ("output.mp3" in the folder the original file came from) using the code that FakeOutdoorsman provided...the file does open in totem, however the sound never comes out nor does the time ever progress.

in vlc the time progresses, but there is still no sound GAR, but its SO CLOSE!!!! THANK YOU ALL OF YOU THANK YOU THANK YOU THANK YOU!!!!!

so it did its job but there was an error of some sort.
here is the media info:
General

Complete name                    : /home/projectmayhem/Desktop/Pandoramusic/Akron&Family/output.mp3

Format                           : MPEG Audio

File size                        : 1.83 MiB

Duration                         : 3mn 59s

Overall bit rate                 : 64.0 Kbps



Audio

Format                           : MPEG Audio

Format version                   : Version 1

Format profile                   : Layer 3

Duration                         : 3mn 59s

Bit rate mode                    : Constant

Bit rate                         : 64.0 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits



so um before i try these other more complicated scripts to see if they work...

for f in *.mp4; do ffmpeg -i "$f" -acodec libmp3lame  "${f%.mp4}.mp3"; done && mkdir temp && mv *.mp3 ./temp

"f" means the file i want?
do i leave the $ and % signs?
the * is what I modify?
does done mean a new part of the script is starting?

...where can i go to learn to read/write script.

so what im thinking to use would be, from the folder:

crickets.mp4; do ffmpeg -i "$crickets.mp4" -acodec libmp3lame  "${crickets.mp4}.mp3"; done && mkdir temp && mv crickets.mp3 ./temp

---

### Post by mc4man on 2009-03-05
The commands are just for 'batch encoding' (doing multiple files at once, though you can do just one, will give you the same track name automatically
For instance if there were 10 .mp4's in the folder it would encode them all using the same file name to mp3

*You don't change anything* except if you wanted to save elsewhere (example - 2nd command I showed previously

Ex. I have 3 .mp4's in a folder, I cd to that folder and run the command verbatium (actually I'll use the right click 'open in terminal' (clipped irrelevant info

> doug@doug-desktop:~/Desktop/untitled folder$ for f in *.mp4; do ffmpeg -i "$f" -acodec libmp3lame  "${f%.mp4}.mp3"; done && mkdir temp && mv *.mp3 ./temp

....clipped
[COLOR="Red"]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '01 - (Love Is Like A) Heat Wave - Joan Osborne.mp4'[/COLOR]:
  Duration: 00:03:01.52, start: 0.000000, bitrate: 294 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
[COLOR="Blue"]Output #0, mp3, to '01 - (Love Is Like A) Heat Wave - Joan Osborne.mp3'[/COLOR]:
    Stream #0.0(und): Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1418kB time=181.55 bitrate=  64.0kbits/s    
video:0kB audio:1418kB global headers:0kB muxing overhead 0.002203%
....clipped
[COLOR="Red"]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '02 - You've Really Got A Hold On Me - Meshell Ndegeocello.mp4'[/COLOR]:
  Duration: 00:03:28.79, start: 0.000000, bitrate: 297 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
[COLOR="Blue"]Output #0, mp3, to '02 - You've Really Got A Hold On Me - Meshell Ndegeocello.mp3':[/COLOR]
    Stream #0.0(und): Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1631kB time=208.82 bitrate=  64.0kbits/s    
video:0kB audio:1631kB global headers:0kB muxing overhead 0.001916%
....clipped
[COLOR="Red"]Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '03 Keep On Growing.mp4'[/COLOR]:
  Duration: 00:06:22.75, start: 0.000000, bitrate: 131 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
[COLOR="Blue"]Output #0, mp3, to '03 Keep On Growing.mp3[/COLOR]':
    Stream #0.0(und): Audio: libmp3lame, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    2990kB time=382.77 bitrate=  64.0kbits/s    
video:0kB audio:2990kB global headers:0kB muxing overhead 0.001045%

Notice how it aotomatically finds the input for each file(red) and then outputs with the same name to mp3(blue

Then, in this case, a temp folder is created in the current folder and all the mp3's are moved in.

If you wanted a bit more bitrate (not sure what's good here) then put -ab xxxk after libmp3lame (with a space

Ex. same command as above

```
for f in *.mp4; do ffmpeg -i "$f" -acodec libmp3lame -ab 96k  "${f%.mp4}.mp3"; done && mkdir temp && mv *.mp3 ./temp
```

---

### Post by WaNaBePi on 2009-03-05
IT WORKED ALL THE WAY THANK YOU SO MUCH, mc4man, and all of you.

its solved, finally finally solved

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!!!!!!!!!!!!!!

UBUNTU ROCKS, LINUX ROCKS, OH THANK YOU SO MUCH!!!!!!!!!!!!

May the gods grant you luck and prosperity.

---

### Post by drz4007 on 2009-03-10
why don't you use sound converter? i do and works fine with aac files

---

### Post by aadityabhatia on 2009-03-28
> **WaNaBePi said:**
> 

projectmayhem@projectmayhem-lapbottom:~/Desktop/Pandoramusic/Akron&Family$ ffmpeg -i crickets.mp4
...
crickets.mp4: no such file or directory

...

Complete name                    : /home/projectmayhem/Desktop/Pandoramusic/Akron&Family/Crickets.mp4


Did you realize that in Linux **file names** are **case-sensitive**?

---

