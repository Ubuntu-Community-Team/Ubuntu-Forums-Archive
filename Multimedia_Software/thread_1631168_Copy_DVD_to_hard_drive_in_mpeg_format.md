---
title: "Copy DVD to hard drive in mpeg format?"
date: 2010-11-26
forum: Multimedia Software
---

### Post by PDA1 on 2010-11-26
I want to copy my home video DVD's to my hard drive and I want the format to be in an mpeg format (I suppose I should want mp4).  The DVD's are in some sort of VOB, IFO format....or whatever they're called.

There are many chapters on each of the DVD's and I want each of the individual chapters copied to the hard drive so I can rename the files something like, "fishing.mpeg" or "skiing.mpeg" and not some huge 3 gb file.

K9copy does a fair job but won't complete it.  That is- k9copy gets 86% encoding done (I think that's the word for it) but won't finish copying the remainder of the chapters.


Any ideas how to do it?

---

### Post by Naitsirhc Hsem on 2010-11-26
you can use thoggen to create .ogv videos.  Thoggen is one of the best programs out there.  if you need the file in another format, you can use pitivi video editor or something better to convert.

---

### Post by PDA1 on 2010-11-26
I don't want ogg files.

Thoggen and Pitiviti won't do what I want.

---

### Post by cptrohn on 2010-11-26
I use K9 copy quite a bit, have you tried cleaning the disc you are using?  Because it sounds like it is a problem with the disc if it gets that far before it happens.  You could also try VLC, as it has a record feature for you to use as you are watching a DVD.  DVD;;rip is also pretty good as well.

---

### Post by PDA1 on 2010-11-26
The disk is perfectly clean.

I tried VLC and can't figure out how to record.  Man, there's just gotta be an easier way to do this stuff.

---

### Post by ron999 on 2010-11-26
Hi
You can copy the files onto your hard drive using **vobcopy**.
Then afterwards use a converter such as **ffmpeg** to convert them to mp4 or whatever.

This is how I use vobcopy.

Insert the disc.
Enter:-
> vobcopy -I
This will show you all the 'Titles' on the disc.
To extract a title use a command like this (title 3 for example):-
```
vobcopy -n 3
```

---

### Post by PDA1 on 2010-11-26
That's pretty neat.

What would be the syntax for copying only a certain chapter from a DVD?

---

### Post by ron999 on 2010-11-26
> **PDA1 said:**
> That's pretty neat.

What would be the syntax for copying only a certain chapter from a DVD?

Maybe chapter = title

Try
vobcopy -n 1
vobcopy -n 2
etc.

See what happens.

---

### Post by PDA1 on 2010-11-26
All vobcopy -n 1 (etc) does is copy the entire dvd and not specific chapters.


I noticed that the -s option would copy chapters but that's not the case.  It doesn't work.

---

### Post by cascade9 on 2010-11-26
I'm always a little suprised that people even bother with command line encoders when its easier to use a GUI DVD ripper. I spose if it floats your boat then use it, but its always seemed like far to much of a sod-around to me. 

> **cptrohn said:**
>   DVD;;rip is also pretty good as well.

If K9copy isnt working, then DVD::rip is what I would use. Its got a 'chapter mode' and should do exactly what PDA1 wants.

---

### Post by andrew.46 on 2010-11-27
Hi cascade,

> **cascade9 said:**
> I'm always a little suprised that people even bother with command line encoders when its easier to use a GUI DVD ripper. I spose if it floats your boat then use it, but its always seemed like far to much of a sod-around to me.

Keep in mind that usually gui dvd rippers are simply glitzy frontends for these commandline programs. Using such guis has been compared to operating a light switch by using a broomstick :).

Andrew

---

### Post by shantiq on 2010-11-27
Ron999 thanx for vobcopy 



```
vobcopy -o ~/Desktop/ -v -t section_cinq  -n 5

```This copied Title 5 and i renamed it section_cinq and placed it on my Desktop

=========================================

There is  a great piece of software called [**Handbrake**]("http://handbrake.fr/")

=========================================

also ffmpeg has an easy to use gui called WinFF which will do the conversion once you have the vob


```
sudo apt-get install winff 
```     or the synaptic

============================================================
**BUT** what i suggest here is a very simple way of doing what PDA1 wants to do

1.   **go** places/where your dvd is and open it drag the vobs that you want or all of them place them in a folder cd to the folder then use this script


2.    ```
for f in *.VOB; do ffmpeg -i "$f"   -b 2000k  -s sxga "${f%.VOB}.mp4"; done
```make sure your file is VOB and not vob it is case sensitive so correct accordingly


of course you can change the bitrate to suit you also the size

```
`-s size'
Set frame size. The format is `wxh' (ffserver default = 160x128, ffmpeg default = same as source). The following abbreviations are recognized:
`sqcif'
128x96
`qcif'
176x144
`cif'
352x288
`4cif'
704x576
`16cif'
1408x1152
`qqvga'
160x120
`qvga'
320x240
`vga'
640x480
`svga'
800x600
`xga'
1024x768
`uxga'
1600x1200
`qxga'
2048x1536
`sxga'
1280x1024
`qsxga'
2560x2048
`hsxga'
5120x4096
`wvga'
852x480
`wxga'
1366x768
`wsxga'
1600x1024
`wuxga'
1920x1200
`woxga'
2560x1600
`wqsxga'
3200x2048
`wquxga'
3840x2400
`whsxga'
6400x4096
`whuxga'
7680x4800
`cga'
320x200
`ega'
640x350
`hd480'
852x480
`hd720'
1280x720
`hd1080'
1920x1080
```also in my experience mkv the matroska format is usually better quality than mp4

so i would suggest as an alternative ```
for f in *.VOB; do ffmpeg -i "$f"  -b 3000k  -s sxga "${f%.VOB}.mkv"; done
```======================================================

**ok **there can be an issue around audio tracks if the vob contains multiple languages.  The vob i used had 5 languages audio track.

if not specified the conversion will pick number one so one needs to use

[COLOR=#000000][FONT=Times New Roman][FONT=Bitstream Vera Sans]"-map" can also be used to create a new movie from this .vob file using, for example stream #0.0 for the video and #0.5 for the audio. If any streams in a video file are mapped with "-map" then they must all be specified explicitly.[COLOR=Red] [COLOR=DarkRed]In this case the first "-map" option specifies the stream to use for the video and the second one specifies which stream to use for the audio:[/COLOR]


[/COLOR] [/FONT][/FONT][/COLOR]```
for f in *.VOB; do ffmpeg -i "$f"  -map 0:0 -map 0:3   -b 3000k   -ab 192k  -s sxga "${f%.VOB}.mkv"; done
```
which copied the video 0:0   and copies audio stream 0:3 which is english    where 0:1 was german   and would be picked if no mapping was entered

This may help someone else:KS

---

### Post by amsterdamharu on 2010-11-27
You have your home video DVD, does it have subtitles and or several/seporate audio files?

This might not work for most DVD's because there might be multiple  audio, subtitles and such but you can give it a try by opening the vob  files in VLC (only the ones over 10MB or so).

If you want to re-encode it you can use winff and ffmpeg (winff is a gui for ffmpeg). Start winff -> add files (the vob files from the DVD VIDEO_TS directory) -> select what format you want to encode -> choose where to put the re-encoded files and you're done.

---

### Post by PDA1 on 2010-11-27
I agree 10,000%.

The only problem I'm having is NONE of the Gui rippers are doing what I want and all fail.

K9copy (a great program for ripping) won't copy selected chapters- instead it copies the entire disk.  When I try copying a disk to mpg it crashes at around 86% of completion.

Acidrip doesn't rip a DVD at all.

Remember- in my situation I'm taking home videos (family stuff) and trying to rip and encode them to mpeg.


I'll try DVD::rip and let you know what happens.

---

### Post by cascade9 on 2010-11-27
> **andrew.46 said:**
> Hi cascade,

Keep in mind that usually gui dvd rippers are simply glitzy frontends for these commandline programs. Using such guis has been compared to operating a light switch by using a broomstick :).

Andrew

Fair point. Though I will be a smart alec and say that any GUI is just a front-end for command line, even on windows. :lolflag:  

I cant image that there would be much more than a percent or 2 difference between using a command line ripper and a GUI ripper, and GUIs mean you dont have to remember commands. But I've never seen any performance comparison between ripping via command line and a GUI, so thats just a guess. 

If it works for you, use the command line versions, I just dont get it myself. Maybe if I didnt have dyslexia I'd remember the commands better and maybe even spell them right, but as it stands I just find GUIs a lot easier in most cases. ;)

---

### Post by PDA1 on 2010-11-27
DVD::rip worked perfectly!!!!!  I selected out the chapters I wanted and it copied them perfectly....into vob format.  


Unreal!  I can't believe it!  At much as I love Ubuntu it's very frustrating to have programs that simply don't work or won't work properly.  You probably have to find which ones work in certain situations and use them.

Oh, concerning command line stuff- FFMPEG is really a great one.  I keep the commands simple and don't get involved in the complex stuff with it.  


Thanks for the help.

---

### Post by shantiq on 2010-11-27
PDA is vob is what you want you can simply open the dvd and copy and paste the vob to hard disc    no need for software for that:KS:KS

---

### Post by 0N3 on 2010-11-27
Handbrake by far the best DVD ripper for gnome

---

### Post by 12apennachi on 2010-11-27
Yeah Handbrake is great. Probably the easiest way, though I haven't tried many of them.

---

### Post by PDA1 on 2010-11-27
> **shantiq said:**
> PDA is vob is what you want you can simply open the dvd and copy and paste the vob to hard disc    no need for software for that:KS:KS

No, I really only want the ability to copy individual chapters from a DVD to my hard drive.

Copy the vob's from a DVD gives me nothing but the entire DVD with no chapters.


I want it all converted to mp4 which I can do with ffmpeg quite easily.

---

### Post by PDA1 on 2010-11-27
> **0N3 said:**
> Handbrake by far the best DVD ripper for gnome


Glad it works for you.  It won't do what I want.

---

### Post by shantiq on 2010-11-27
> **0N3 said:**
> Handbrake by far the best DVD ripper for gnome



i certainly second that

see image attached  ripping a chapter to mkv from dvd



but dvd's are so complex it probably works with some and not others   way beyond my understanding

====================================================================


Another handy tool i have come across is** dvdbackup**

this tells you what your dvd contains
```
dvdbackup -I

```


this will copy the entire disc```
dvdbackup -M  -v -o  ~/Desktop/

```

---

