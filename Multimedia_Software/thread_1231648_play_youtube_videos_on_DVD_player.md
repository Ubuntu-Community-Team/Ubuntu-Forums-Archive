---
title: "play youtube videos on DVD player"
date: 2009-08-04
forum: Multimedia Software
---

### Post by maximuss77 on 2009-08-04
hello, ill start by trying to explain basically what i am trying to do, and what i need help on

i own my own video game retail store and am trying to get a video of new and upcoming game trailers playing on one of the TV's i have in the store

there is a company that does it but they are crazy expensive so i want to try to do it myself first

i have the add on for fire fox to download youtube videos, so what i am looking for is a program to either convert one of the following MP4, FLV or 3GP(preferably mp4 as that is the file i can download in HD)

i really dont even need to edit these although it would be nice as long as it is fairly simple


thanks for the help in advance, and i hope i explained what i need clear enough if you need more information please let me know

thanks in advance

---

### Post by mc4man on 2009-08-05
What you may wish to explain is what your dvd player is and what format you need to playback in.
If it's from dvd media then it shouldn't be that hard (dvd format, VIDEO_TS, ect.

For that you need to convert to .mpeg (mpeg2) with ac3 audio which ffmpeg will do quite easily.
Then just author to dvd video format and burn to blank media.

The optons would be to make each video a new titleset, or use 1 titleset with each video a title, or 1 titleset, 1 title with chapters 

additionally you could edit the last title/chapter's post command to 'return' to first title/chapter, in other words just loop continuously.

Only had a little while to try, created a dvd with 3 hd .mp4's, let a java app (varsha) author and  create an image. (you could probably fit up to 150 min  on a dvd5 from ut hd sources

I didn't let it burn, actually didn't even use the .iso. Took the VIDEO_TS in the tmp folder, used ImgBurn to create an .iso and burn.(trust Imgburn over any linux burner

Plays great on standalone dvd player, and looks excellent, sound is pretty good for a aac to ac3 conversion

Probably other authoring apps, but varsha worked well for this purpase.
((  for a loop I'd probably do one titleset with 1 title and multiple chapters (to do so the edit should be in file format (the VIDEO_TS,) not an .iso

Didn't spend to much time in varsha, seems simple to use (if this is what you had in mind ...?

Just used a basic ffmpeg command (maybe could be improved...?
ffmpeg -i 8.mp4 -target ntsc-dvd 8.mpeg

Will try the dvd tommorrow on my son's hd tv, looked great though on my 36" sd  tv.


Edit:
specs on orig video (ut hd) (in case better suggests for ffmpeg command


> 
Video
ID                               : 2

Format                           : AVC

Format/Info                      : Advanced Video Codec

Format profile                   : High@L3.1

Format settings, CABAC           : Yes

Format settings, ReFrames        : 3 frames

Codec ID                         : avc1

Codec ID/Info                    : Advanced Video Coding

Duration                         : 5mn 43s

Bit rate mode                    : Variable

Bit rate                         : 2 011 Kbps

Width                            : 1 280 pixels

Height                           : 720 pixels

Display aspect ratio             : 16/9

Frame rate mode                  : Variable

Frame rate                       : 29.970 fps

Minimum frame rate               : 29.441 fps

Maximum frame rate               : 30.333 fps

Resolution                       : 24 bits

Colorimetry                      : 4:2:0

Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.073

specs on ffmpeg convert
> Video

ID                               : 224 (0xE0)

Format                           : MPEG Video

Format version                   : Version 2

Format profile                   : Main@Main

Format settings, Matrix          : Default

Duration                         : 5mn 43s

Bit rate mode                    : Variable

Bit rate                         : 4 522 Kbps

Nominal bit rate                 : 9 000 Kbps

Width                            : 720 pixels

Height                           : 480 pixels

Display aspect ratio             : 16/9

Frame rate                       : 29.970 fps

Standard                         : NTSC

Colorimetry                      : 4:2:0

Scan type                        : Progressive

Bits/(Pixel*Frame)               : 0.437


[http://varsha.sourceforge.net/](http://varsha.sourceforge.net/)

screen 4 shows easiest setup for looping (1 titleset,1 title, each video is a chapter.
the dvd spec allow up to 99 chapters which should be more than enough,  (have the VIDEO_TS looping on vlc right now.

---

### Post by soapBAR2 on 2009-08-05
Is it possible to attach your computer directly to the TV? Assuming you have a halfway modern video card with AVIVO/equivalent, the relevant adapters will cost as much as a stack of DVDs. It will also save your processor some effort (although since you've converting *TO* MPEG-2, it might not be so bad). 

Then, once you've got your computer hooked up to the TV, it's as easy as anything to just set up a playlist of your videos using your video player of choice (Mplayer might be your best bet, as it has options and modes specifically for outputting on attached TVs, although be warned - it's bloody difficult to work out if you're using the CLI version).

The other advantage of this is once it's up and running, you can change your content with a few clicks.

---

### Post by maximuss77 on 2009-08-05
no i cant set my computer up to that tv as it is at my business, thats what i do at home and it works great

@ mc4man i need to get it into a standard format that will play on most dvd players... i cant find the exact model as its one of those built in dvd tv player combo things

ill try that program and test the burn tom to see if it works 

thanks for the help as always the ubuntu forum never lets me down :)

---

### Post by mc4man on 2009-08-06
> i need to get it into a standard format that will play on most dvd players... i cant find the exact model as its one of those built in dvd tv player combo things

If you use ffmpeg then there are only 2 things for any standalone dvd player

Are you ntsc or pal, N america is ntsc, europe is pal, anywhere else check. (command posted is for ntsc

Does your built-in dvd player accept burned dvd video media. Most will, some may balk. If your's does then try using dvd-r instead of dvd+r.

The other workaround is some burners can be set to booktype dvd+r media as DVD-ROM (same as a commercial disk (if that's an issue post your burner model

For your use I'd do - 1 titleset, 1 title, each video a chapter
(though either with Varsha or other dvd authoring apps you could make a menu(s), chapter lists, multiple titles, ect.

Took me a few to figure the loading method, so in case I'll post a few screens

For ffmpeg I'd do a same name batch convert. 2 simple commands will take care of your videos for loading into Varsha (doesn't matter if names have spaces or not, on the dvd they will be chapter 1, chapter 2, ect.

So I'd put all the video's in a folder, cd to that folder and run (for mp4's

```
for f in *.mp4; do ffmpeg -i "$f" -target ntsc-dvd "${f%.mp4}.mpeg"; done

```
and then when ffmpeg is finished (if .flv replace the 2 .mp4's with .flv, if both are present run the command once for each
 ```
mkdir dvd && mv *.mpeg ./dvd
```

Then just run Varsha (I put the jar in a folder and then cd'ed to it, or loose in home folder from normal terminal prompt

```
java -jar varsha.jar
```

For simple 1 titleset, 1 title - 

When opened browse to your 'dvd' folder and click on it, all the files will show up in right box.

To add you need to highlight where in the left box, so to begin you'd highlight 'disc' !screen1

If you drag the 'dvd' folder over all the video's will be added in 1 title but randomly (name or number doesnt seem to matter

If you wish to add in specific order than with disc highlighted drag the 1st file over. Then expand the tree and highlight 'Title 1'

Now drag the rest over in order desired, they'll all be added to title 1 as chapters
(screen 2

Then click on DVD in task bar and choose (I'd have it make an image and then burn with either built-in burner or your burner of choice  

If you find this workable and want to make a looping dvd let me know (need the VIDEO_TS folder in varsha_temp, easy to do with 1 titleset, 1 title, a bit more with multiple

---

