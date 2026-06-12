---
title: "Script to convert .SRT files to vobsub (.sub/.idx)"
date: 2012-06-14
forum: Multimedia Software
---

### Post by sv1etk on 2012-06-14
For anyone interested, I wrote a small script to convert .srt subtitles to vobsub (.sub/.idx).

I wrote it because my media player (hardware) couldn't handle correctly the subtitles, so vobsub was the only way to make it work.

You can find it at: [http://code.google.com/p/srt2vob](http://code.google.com/p/srt2vob)

---

### Post by webe on 2012-07-12
hello **sv1etk**
thanks for your script.
I want to convert my srt-files for use in Handbrake.

But i get the following errors:

> DVDAuthor::spumux, version 0.6.14.
    [LEFT]Build options: gnugetopt magick iconv freetype[/LEFT]
    [LEFT]Send bugs to <dvdauthor-users@lists.sourceforge.net>[/LEFT]
    [LEFT]INFO: Locale=en_US.utf8[/LEFT]
    [LEFT]INFO: Converting filenames to UTF-8[/LEFT]
    [LEFT]INFO: Detected subtitle file format: subviewer[/LEFT]
    [LEFT]INFO: Opened iconv descriptor. *UTF-8* **[/LEFT]
    [LEFT]INFO: Read 608 subtitles[/LEFT]
    [LEFT]ERR: New_Face failed. Maybe the font path is wrong.[/LEFT]
    [LEFT]Please supply the text font file (Verdana).[/LEFT]
    [LEFT]WARN: subtitle font: load_sub_face failed.[/LEFT]
    [LEFT]srt2vob.sh: line 99: 17250 Segmentation fault      spumux -s0 "$xml" < tmp.vob > tmp.mpg[/LEFT]
    [LEFT]MEncoder 1.0rc4-4.4.3 (C) 2000-2010 MPlayer Team[/LEFT]
    [LEFT]success: format: 0  data: 0x0 - 0x0[/LEFT]
    [LEFT]Seek failed[/LEFT]
    [LEFT]Sorry, this file format is not recognized/supported[/LEFT]
    [LEFT]If this file is an AVI, ASF or MPEG stream, please contact the author!
Cannot open demuxer.[/LEFT]
    [LEFT]Exiting...[/LEFT]


Could you explain what i'm doing wrong?
btw. i changed de vformat to PAL

---

### Post by sv1etk on 2012-07-15
> **webe said:**
> hello **sv1etk**
thanks for your script.
I want to convert my srt-files for use in Handbrake.

But i get the following errors:



Could you explain what i'm doing wrong?
btw. i changed de vformat to PAL

Hi webe,

Well, the first thing you have to consider is :
[LEFT]"
ERR: New_Face failed. Maybe the font path is wrong.[/LEFT]
    [LEFT]Please supply the text font file (Verdana).[/LEFT]
    [LEFT]WARN: subtitle font: load_sub_face failed.[/LEFT]
    "

What i get from it is that you don't have the Verdana font in your system.
You can use other fonts like that:
$ font="Arial" srt2vob.sh ....
But my best guess is that you don't have Arial too (if you don't have verdana).
There are two options here. 1) Install these fonts 2) supply an already installed font to this option above. Example for the 2nd option:
$ font="DejaVuSans" srt2vob.sh myvideo.mklv mysub

I really can't remember where you can find a deb package for the usual microsoft fonts, but my money goes on the medibuntu repository :D .

A quick note here, I chose Verdana because as far as I know this font is made for Displays and not for witting texts. It's kind of optimal for subtitles.

On the other hand I saw that you provided the subtitles in the format:
INFO: Detected subtitle file format: subviewer

Can you please try to supply it in srt format? (subrip)
If this is the problem and you wish to include support for subviewer in the script I will gladly do it (on Monday, cause right now I am lying and a beach:D)

I would really like to hear from you again.

PS OK I just reviewed the script and I explicitly write at line 75:
<textsub filename="$2**.srt**" ....
So, try to supply srt format subtitle. Btw, you can convert your subtitle to srt using subtitleeditor (sudo apt-get install subtitleeditor)
A last thing, you do know that you have to OMIT the subtitle extension when you will use it:
I have myvideo.avi and mysub.srt
$ srt2vob.sh myvideo.avi mysub

---

### Post by webe on 2012-07-15
hi **sv1etk**,

> I would really like to hear from you again.

That's very kind of you, thanks.

> &#65279;... you don't have the Verdana font in your system

I certainly have, i use it daily (gedit, abiword).
I tried 'Arial',
I tried the absolute font-path, with and without escaping the slashes,
I tried: ```
font="Verdana" srt2vob.sh laputacd1.avi laputacd1
```,
all with the same result: ERR: New_Face failed. Maybe the font path is wrong.

> On the other hand I saw that you provided the subtitles in the format: INFO: Detected subtitle file format: subviewer

My sub-file is certainly a srt-file.

Some background info:

Ubuntu Lucid 10.04.2 LTS
video-file = laputacd1.avi (XVID+mp3)
sub-file = laputacd1.srt (encoding UTF-8, Unix/Linux)
my command: srt2vob.sh laputacd1.avi laputacd1

webe

ps. i hope you had a nice day at the beach!

---

### Post by sv1etk on 2012-07-16
Ok I confirmed it: I used an srt, and it spumux said "subviewer" and worked like a charm.
No problem there.

I bet it's the font. For some weird reason it doens't find your font. Could you please try to copy or link your font to the directory of your file?

I just did it and it used the font I provided.

$ cp /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf  .
$ font="./DejaVuSans.ttf" srt2vob.sh myvid.avi mysub

Can you do it and post the output. I guess it will work. Where are the ttf fonts in your system (I mean which is the path?)
Could you do a "locate verdana.ttf" and tell me the output?

I also found this thread:
[http://ubuntuforums.org/showthread.php?t=1440135&page=2](http://ubuntuforums.org/showthread.php?t=1440135&page=2)
It seems that other ppl had the same problem with spumux and solved it the way it's described in this thread.

A last thing. At the man page of spumux it states that it uses fontconfig package to lookup fonts. Do you have it installed?
To install it: sudo apt-get install fontconfig
(it's binaries aren't called fontconfig-something, they are called fc-.. like fc-scan or fc-query etc).

---

### Post by webe on 2012-07-16
hi **sv1etk**, thanks for your reply

> Can you do it and post the output.

Copied DejaVuSans.ttf to my working directory, and did

command: font="DejaVuSans.ttf" srt2vob.sh laputacd1.avi laputacd1

and got as output:

ERR: New_Face failed. Maybe the font path is wrong.
Please supply the text font file (DejaVuSans.ttf).
WARN: subtitle font: load_sub_face failed.

> I also found this thread:

YES! \\:D/

I copied Arial.ttf to a new folder .spumux, as advised, and did

command: font="Arial.ttf" srt2vob.sh laputacd1.avi laputacd1

and got

laputacd1.idx     26.7 KB
laputacd1.sub    1.8 MB

> that it uses fontconfig package to lookup fonts. Do you have it installed?

Yes. Btw. Arial and Verdana are, like in the other thread, in "/usr/share/fonts/truetype/msttcorefonts/"

thanks a lot,

webe

---

### Post by sv1etk on 2012-07-16
"Copied DejaVuSans.ttf to my working directory, and did

command: font="DejaVuSans.ttf" srt2vob.sh laputacd1.avi laputacd1"

Could you please copy again DejaVuSans.ttf and run your command again but changed like this:

font="./DejaVuSans.ttf" srt2vob.sh laputacd1.avi laputacd1

Just to check if spumux looks at the current dir.

The way with .spumux is the correct way because you don't have to copy around fonts. The purpose of the script was to have a all-in-one tool. Which means that you can do the process manually but it's kind of daunting process.

Btw, the guys at dvdauthor did something wrong, if the fonts are in your system and your system can find them then spumux SHOULD be able to find them. In ubuntu 12.04 (which I am running) it has no problem :D

Now that it worked you can change the script to use your prefered font so you don't have to right 12342315 things in the command line.

Anyway, I am glad that it worked for you.
My suggestion is to use Verdana font. It's made for display purposes not writting books. You can create two subtitles, one with verdana and one with, say, Arial, grab screenshot of the same subtitle and zoom in and check the differences. You will find out that Verdana is better :D
A second note: If you read the project page I suggest that you recompile spumux with a changed line. The difference with the patched spumux is CLEARLY visible. I do understand that ppl are reluctant to compile source code, but it's really nothing that hard. It takes 2-3 minutes and its worth it.
I MAY create a statically linked version of spumux with the patched code one day if ppl ask me for it...

Again, glad to help :D

---

### Post by webe on 2012-07-16
hi **sv1etk**

> Just to check if spumux looks at the current dir.

I moved Arial.tff from .spumux to my working directory, and did:

command: font="./Arial.ttf" srt2vob.sh laputacd1.avi laputacd1

NOPE!

> My suggestion is to use Verdana font.

I will try it.

thanks again,

webe

---

### Post by sv1etk on 2012-07-16
Ok so when I tried from the local dir it just ignored me and used the font it found on the proper dir. LOL!

Whatever you want to ask drop a message. (The private message did the work because I didn't check the forum page, and it sent a message to my email address)

Anyway, see you around.

---

### Post by webe on 2012-07-18
hi **sv1etk**,

I've a lot of old - in the double sense of the word - movies in avi-format with
external srt's, i want to view as mp4's with burned-in subs on my SONY-TV
from an external USB-device.

I found your projectpage searching for a solution of the problem that
Handbrake doesn't hard-burn external and internal srt's, nor external
VobSubs.

My workflow is:

1. convert the srt's to VobSubs with your script
2. create mkv-files with them (in MKV file creator)
3. convert the mkv's in Handbrake (my favorite conversion program)

Step 1 worked, as i let you know.
Step 2 and 3: idem dito with a small change in your script (see question 2).

My new questions are

1. Is it important to set vformat? Although i'm an ignorant in bash-scripting
compared to you, i couldn't find a use of $vformat in the rest of your script.
Some of my avi's are PAL, some NTSC. If it is important i could make two
versions of your script.

2. There are some weird things - colors, position - going on displaying
the output of the script in mplayer, GMplayer, MoviePlayer, SMplayer.
Idem dito with the display of the mkv-file, and last but not least with
it's conversion in HandBrake.
After a lot of googling i understand that this issue is not uncommon.
In your script you insert (DVD) palette data in the idx-file.

What about:
# Custom colors (transp idxs and the four colors )
custom colors: ON, tridx: 1000, colors: 000000, ffffff, 000000, 000000

Btw. i had to change the first color in your palette from 550000 to 000000
to get acceptable burned-in subs in my mp4's.

thanks in advance for your reply,

webe

---

### Post by sv1etk on 2012-07-20
Not only you are wellcome to send me private messages, but you are encouraged to do so. Mainly because it's the only way to reach me. I can't monitor 5234523 sites and our beloved ubuntu forums send you emails when you get private messages. Now, I check regularly my email so I know that someone sent me a question :D .

Anyway, to your questions now.

1) vformat is used by spumux. As you may have guessed you can run:
$ vformat="NTSC" srt2vob ...
Now, is it important? I don't think so. vformat (ntsc, pal) describes stuff about resolution and framerate but these are explicitly set by my script to the xml file that is created on-the-fly for use by spumux. You can check if you get different quality of subtitles by creating one with ntsc and one with pal. But my guess is that you will not get different subtitles. I wrote it once and converted my subtitles and never checked if my movie was in nstc or pal to be frank. 
I would be interested to hear if you experience different quality with different vformat, but my best guess is that you wont.

2) Now, this is really interesting. It seems to get different behaviour with different devices on the matter of colors. I had to change the palette because I got crappy colors with my original setting. Now, the purpose of 550000 was to create a gray outline (if I remember correctly). I guess it didn't work for you. Let me guess, it created a pink outline right? (I am thinking of (r,g,b) = (55, 00, 00) )
The line :
   custom colors: ON, tridx: 1000, colors: 000000, ffffff, 000000, 000000
in the place of palette, works ?
If this works I will gladly modify the script and re-release it. It seems to be optimal to define only the four colors needed (background, outline, text-color, anti-alias color) but if this is the case then I see that there is no antialias gradient there. Please enlighten me about how this palette setting work.

Ty for you time,
Nick.

---

### Post by webe on 2012-07-20
hi **sv1etk**

Next time when i post questions in the thread i will notify you via a pm.

> vformat is used by spumux
I had to read the manpage to understand what you let spumux do in your script.
The version of dvdauthor i use is 0.6.14-3. There is a newer version (0.7) with more attributes in the xml-file. One of them is 'fill-color'. That would give me the possibility to choose my own font-color. Another interesting attribute is 'transparent': should be already present in 0.6.
I tried it, without any change in the output of srt2vob.sh

How your script makes the xml-file i've still to find out.

Btw. what did you mean that spumux uses the variable vformat? It's a minor point, but i'm just curious.

> The line :
custom colors: ON, tridx: 1000, colors: 000000, ffffff, 000000, 000000
in the place of palette, works ?

I tried several commutations of transparency and of colors - but none made any difference.

What interest me most at the moment is the question of the color palette. I understand that  in extracting the subs from a dvd that the palette information is taken from the ifo-file.
In my case there is no ifo-file. I've tried to found out if there is an alternative, e.g. a standard dvd palette. Well, no way. Have you any ideas?

Yes indeed, anti-aliasing would be great because my subs are still rather, well crappy.

greetings, webe

---

### Post by sv1etk on 2012-07-21
> **webe said:**
> hi **sv1etk**

Next time when i post questions in the thread i will notify you via a pm.


Thank you. I believe this way is faster :D

> 
One of them is 'fill-color'. That would give me the possibility to choose my own font-color. Another interesting attribute is 'transparent': should be already present in 0.6.
I tried it, without any change in the output of srt2vob.sh


Hm, that's interesting. But this makes me wonder, why they included such option (fillcolor) since they can't manage it?
I mean, the file spumux creates is a mpeg-pes stream (actually the spu part). This means that they save into an mpeg stream  2bits-wide information. These bits are 00,01,10,11 (and they run a runlength encoder to compress them). These become usefull only after we provide with a mapping:
00 -> 0x550000
01 -> 0x000000
...
So the player knows which color is represented by each 2-bit.
I will examine their source code to find out why they include such info. If they decided to create idx files I will be more than happy :D

> 
How your script makes the xml-file i've still to find out.

You mean what information I include in the xml? Or how I create it?

If you want to keep the .xml file to examine it you can remove "$xml" from line 100:
```
rm tmp.vob "$xml"
```

If you are asking how is the file created with this weird command inside the script I can point you to the right place: [http://en.wikipedia.org/wiki/Here_document](http://en.wikipedia.org/wiki/Here_document)
Read it and you will understand everything :D

> 
Btw. what did you mean that spumux uses the variable vformat? It's a minor point, but i'm just curious.


Well, the vformat information is solely used by spumux. It get's it's way inside the .xml file that spumux uses. Why spumux want that info?
I read the source and it appears that it want to know if the video file is in NSTC or PAL in order to compute the vertical resolution of the font (it uses this in the FT_Set_Char_Size and then in the FT_Set_Pixel_Sizes ...). As I read the code, the difference is minor.
The most interesting part is that spumux appears to just ignore my setting of video format. If you carefully read the output of spumux you will find out that it says that I have to explicitly set the format. Something that I do!! I thought that I was writing the xml the wrong way, so I tried to change the option name to video_format (not randomly, I saw some reference inside their source code) only to find out that spumux exits with error!!! This means that I do write the xml correctly and that spumux was meant to ignore me hehehe:D
Bottom line, don't bother with the vformat. It's not important as I see it.

> 
What interest me most at the moment is the question of the color palette. I understand that  in extracting the subs from a dvd that the palette information is taken from the ifo-file.
In my case there is no ifo-file. I've tried to found out if there is an alternative, e.g. a standard dvd palette. Well, no way. Have you any ideas?

...

Yes indeed, anti-aliasing would be great because my subs are still rather, well crappy.


As far as I know, there is a standard dvd palette. I once used a program that converts srt to vobsub in windows and I checked the option that it had for stadard dvd palette only to find out that my subs were displayed pink!! (in my media player, not dvd).

As I said above, the vobsub stream (mpeg-pes) only have 4 2-bit long colors inside it. So, one represents the background (colored, or transparent) one represents the font fill color, one the outline of the font and there is one extra for the use of antialias. Just to be correct you can't have antialiasing with only 3 colors available (font color, outline color and one spare to generate the intermediate color level. these are just not enough!). There is a use of the intermediate color just to make the subtitle not look extremely ugly, but there is one more thing that helps a great deal. This is called hinting.
If you recompile the spumux source code (it's the file subfont.c from dvdauthor source tree) with the patched line that I suggest you WILL see a big difference.
So, to sum it up, correct color usage, hinting and correct font (used for display purposes and not books) make the subtitle look good!

And a last thing about the uglyness. The largest the frame-size of your video, the best the subtitles. This means that if you have a movie in 640x480 the subitles WILL look awfull (no matter what). If you have the same video at 1920x1080 they will be cool.

I hope I helped you.

By the way could you give me more info about the COLORING problem that you have? I mean, is the color different on pc and different on dvd? You changed the palette and you got the same or different results? where? on dvd or pc?


Nick

---

### Post by webe on 2012-07-22
hi **sv1etk**, thanks for your reply

Your last post has set me thinking about the goal i've set myself:
getting good-looking subs in my mp4's for playing on my SONY-TV.

My start assets are mostly old divx's (DX50, Xvid, and the like) with different
video sizes. Am i right that your start-assets are from dvd's,
in full-size mpeg2 format? I think that your script and your remarks points
in that direction. Correct me if i'm wrong.
One of the problems i encounter in displaying the results of your script is
the position of the subs:
mplayer puts them at the top. The keyboard a doesn't work.
I read somewhere that that it has to do with smaller video-sizes.
Color is another problem: mplayer can't display color subs.
Well, that isn't a real problem for me, for i prefer white subs, with a black
border.
The crappy look: i wanted to see how the subs look like as images.
With spuunmux i could extract them out of the vob-file that your script
makes.
Jaggies, jaggies. Why? I don't know. A question of

> The largest the frame-size of your video, the best the subtitles

> This means that if you have a movie in 640x480 the subitles WILL look awfull (no matter what)

Well maybe, but in the meantime has my re-thinking my goal made me
change my workflow with good results, even in movies
smaller than 640x480 (what about 720x288 or 640x464?)

> ... is the color different on pc and different on dvd?

Dvd's aren't part of my workflow, so i can't answer that.
MKV- and MP4-files are. With the palet your script inserts: dark-red borders.
The trials with the 'custom colors' had none or completely unpredictable
results. Some subs are completely green on my monitor.

Thanks for the link to the special bash construct you use in your script.
I saw the article and decided to study it some time in the near future.

And now my discovery of SSA v4+ aka Advanced SubStation Alpha.

As you know, the problem i wanted to tackle was the impossiblity
to burn-in srt-subs in Handbrake.
But.., Handbrake can burn-in vobsubs AND ssa subs.
So i explored that. And the first results are good.
No jaggies! Smooth all over the place.

New workflow
1. convert srt to ssa with Subtitle Editor
2. change some parameters in ssa-file
3. mux with Mkvmerge
4. convert mkv-file with Handbrake to mp4 with burned-in subs

As you see sv1etk, i take another route from here.
I liked the journey along your script path, but ...
Maybe our paths may cross again.

Thanks for all your help.

webe

---

### Post by sv1etk on 2012-07-22
Hi webe,
I am happy that you found a way that works for you.
The truth is that with a lot of videos comming from various sources (forum, youtube, your camcoder, you name it...) the sizes vary a lot. The problem is that vobsub underperforms with low resolutions.

Anyway, see you around.
Hope we meet again :D

---

### Post by sv1etk on 2012-07-27
For anyone interested, I also added a nautilus script that uses srt2vob to convert the subtitles to vobsub. Check it at the download section at [http://code.google.com/p/srt2vob](http://code.google.com/p/srt2vob)
(it is called nautysrt.py)

---

