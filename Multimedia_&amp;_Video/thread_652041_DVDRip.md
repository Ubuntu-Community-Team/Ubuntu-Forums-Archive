---
title: "DVD::Rip"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2007-12-28
Alright, I'm trying to use this program, and I have no idea how to use the stupid thing..

A)  In the Transcoding process, what codec should I use - as in what's the most common that the most players (including kaffeine, Windows Media Player, and Mac's DivX Player (I think that's obvious)) can play?  I was thinking DivX - anybody know any others that would be more versatile?

B)  In the DVD rip mode, how do you make it rip to **ONE** VOB image, it seems to split them up, even if it's only one chapter, it splits 'em up after a certain length.

C)  Anybody have any recommendations on programs for converting a VOB image to an .iso?

There's like 90,000 options in the transcoding menu, and I don't know what 95% of them mean.  Out of the transcoding I'm trying to pull the best quality vid possible, with the best sound possible, into an .avi file.

Thanks for your help :-\

---

### Post by Syndacate on 2007-12-28
Never mind, I came to the conclusion that DVD::Rip sucks ***.

It's easier just to right click >> copy disc >> save as image onto the desktop (ubuntu does it, I"m not sure which program it uses, it doesn't state), that can give me an .iso.

Then I can just use ConvertIT to convert it into an .AVI, takes 3 damn hours to encode in AVI format, but it's worth it I suppose...

---

### Post by arman.haghi on 2008-02-12
Hey mate,

I find DVD::rip to be very good and have excellent results, perhaps we have different needs, but if you're willing to give it another go I'd be happy to help.

):P

---

### Post by Syndacate on 2008-02-14
> **arman.haghi said:**
> Hey mate,

I find DVD::rip to be very good and have excellent results, perhaps we have different needs, but if you're willing to give it another go I'd be happy to help.

):P

It depends on the use - I usually only need to rip DVD files to .isos - which Ubuntu itself has a program that can do.

As far as DVD::Rip goes, not sure what it has that can't be done without "extra" programs.

---

### Post by arman.haghi on 2008-02-15
Hi Syndacate,

True, very true, it always depends on your use, and that's the beauty of being in Linux land isn't it, that the user counts!

Anyway, my use is to find a step by step method of teaching my mum to backup her DVDs to AVIs on the fly, as I've setup a mediabox for her.

I find the progression of tabs (from left to right) on the DVD::rip interface to be helpful in teaching this, in combination with a print out of the manual from:

[http://exit1.org/dvdrip/doc/gui.cipp](http://exit1.org/dvdrip/doc/gui.cipp)

Section 2.3 onwards.

Cheers, :)

Arman.

---

### Post by Syndacate on 2008-02-16
> **arman.haghi said:**
> Hi Syndacate,

True, very true, it always depends on your use, and that's the beauty of being in Linux land isn't it, that the user counts!

Anyway, my use is to find a step by step method of teaching my mum to backup her DVDs to AVIs on the fly, as I've setup a mediabox for her.

I find the progression of tabs (from left to right) on the DVD::rip interface to be helpful in teaching this, in combination with a print out of the manual from:

[http://exit1.org/dvdrip/doc/gui.cipp](http://exit1.org/dvdrip/doc/gui.cipp)

Section 2.3 onwards.

Cheers, :)

Arman.

Ha, yeah, ur right.

I don't know what u use DVD::Rip for - I just use it to rip things as .isos, then I can convert the .iso to an .avi using Fuoco Tools.

What else do you use it for?

Ubuntu has a program build into it (I believe it's called sound juicer although I am not sure) that you can just right click on a mounted DVD and "save" it as an .iso - works 100% well, and since DVD .isos are playable in VLC Media player it works out rather well.

I hear ya though about backing stuff up - at some point I have to look into how to automatically back up my hard drive image O.O.

---

### Post by arman.haghi on 2008-02-17
Hey,

yeah, pretty much for a DVD -> Avi process that requires no thinking (e.g. running out of the house, no time to mess around), I find DVD:rip to be best.

And I hadn't looked into "Fuoco Tools" yet, fact is I've been using Linux for about 3 years (despite only just joining Forums, finally) and am always surprised / pleased by finding out about some new package. I'll look into it!

Cheers.

---

### Post by Creative2 on 2008-02-17
i think you can use fuoco tools with this command line (NOT SURE OF THAT COMMAND LINE )

mencoder INPUT -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=1200 -vf scale -zoom -xy  720  -oac mp3lame -lameopts br=128 -o 'OUTDIR/MYNAME.AVI'

[B]ADD  an url and write this :
[/B]
 dvd://1

so INPUT will  ne replace with dvd://1

and it will not message you with an error :) and you don't care to use other software

---

### Post by Syndacate on 2008-02-20
Why use the command line when you can just use the GUI front end?

---

### Post by arman.haghi on 2008-02-20
Thanks Creative2,

I'll definately give that a spin!

Syndacate, I think one reason for a command line is if you have a set way you like to do the conversions, or have a series of similar INPUTs that you want to convert the same way, well all you have to do is drop to console and run a command, no thinking required. You could even take advantage of a none-gui environment (e.g. no KDE, console only) for better performance.

But again, its about your needs and scenario.

Having said that, you know what would rock? A single screen gui program, like a form, with the following features:

Imaginary Software:
Target Audience: less computer savy, wants a simple series of steps
Main Function: Convert DVD to Xvid Avi

Supposed GUI Features:

1) Name of output Avi

2) target folder (options below)
2.1 Desktop\folder_named_after_avi or
2.2 Browse

3) 'quality' adjustment bar, from 0-100, like saving a jpg in GIMP, it could tell you how big the resulting VI is in mb.

4) Some sort of Preview mechanism, perhaps linked to feature 3. Also, a selection of a few different, typical clippings type. + review mechanism

5) Convert!.

OK, th'ats it from me, not sure what I just wrote, but its 1am here and I'm about to fall asleep at my pc.

---

### Post by Creative2 on 2008-02-20
@sindacate you rip a dvd and convert the iso ?

instead  i will convert and stop xD 1 step and with mutithreads(if you have dual core ) i can go faster xvid about 15% and with 264 multithreads you can go faster about 90% LOL (respect to normal cpu...)

---

### Post by Syndacate on 2008-02-21
> **Creative2 said:**
> @sindacate you rip a dvd and convert the iso ?

instead  i will convert and stop xD 1 step and with mutithreads(if you have dual core ) i can go faster xvid about 15% and with 264 multithreads you can go faster about 90% LOL (respect to normal cpu...)

Errr..what?

---

### Post by Creative2 on 2008-02-21
if you look at mencoder documentation  :

14.7.7. Encoding example
 You are now ready to encode the video. Since you care about quality, of course you will be doing a two-pass encode. To shave off some encoding time, you can specify the turbo option on the first pass; this reduces subq and frameref to 1. To save some disk space, you can use the ss option to strip off the first few seconds of the video. (I found that this particular movie has 32 seconds of credits and logos.) bframes can be 0 or 1. The other options are documented in Encoding with the x264 codec and the man page. 

```
mencoder dvd://1 -o /dev/null -ss 32 -ovc x264  -x264encopts pass=1:turbo:bitrate=900:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:direct_pred=auto:keyint=300 -vf crop=720:352:0:62,scale=-10:-1,harddup  -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000  -ofps 24000/1001
```

 If you have a multi-processor machine, don't miss the opportunity to dramatically speed-up encoding by enabling  x264's multi-threading (the option i think is this for dual core threads=2  or threads=auto )mode by adding threads=auto to your x264encopts command-line. 
 The second pass is the same, except that you specify the output file and set pass=2. 

```
mencoder dvd://1 -o narnia.avi -ss 32 -ovc x264 -x264encopts pass=2:turbo:bitrate=900:frameref=5:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:direct_pred=auto:keyint=300 -vf crop=720:352:0:62,scale=-10:-1,harddup -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000 -ofps 24000/1001
```

 The resulting AVI should play perfectly in MPlayer, but of course QuickTime can not play it because it does not support H.264 muxed in AVI. So the next step is to remux the video into an MP4 container.

NB CODEC X264 is not supported by normal divx player but it produces small file with nice quality

---

### Post by Syndacate on 2008-02-22
Okay, you might not think that mess is confusing, but I do.  Very confusing.

What's wrong with just right clicking on the DVD >> save as (rips to .iso) then using fuoco tools to convert the DVD to an .avi and if necessary (for title screen and such) trim it up with avidemux and resave?

---

### Post by Creative2 on 2008-02-22
well you can do with one step ... less time :) less button i will press  this is the issue , in that command line you can see filter vf crop this is a cropping of couse ... and you can automatically detect how to crop with mplayer 
mplayer INPUT  -vf cropdetect  
so you have not to re-encode another time

If you read mencoder documentation you can easly do what you want only with a string and with a encoding , re-encoding = lost of quality

---

### Post by Syndacate on 2008-02-22
> **Creative2 said:**
> well you can do with one step ... less time :) less button i will press  this is the issue , in that command line you can see filter vf crop this is a cropping of couse ... and you can automatically detect how to crop with mplayer 
mplayer INPUT  -vf cropdetect  
so you have not to re-encode another time

If you read mencoder documentation you can easly do what you want only with a string and with a encoding , re-encoding = lost of quality

Right, so you're saying use mencoder to rip it from a DVD directly to .avi?

Would DVD::Rip be able to do that - that uses the mencoder, right?  Or does it have to be a command line use of Mencoder like you posted.

Also, how does the size turn-out?  Sometimes loss of quality is worth it if you consider a ripped DVD .iso is like 8 gigs.

---

### Post by Ramptu on 2008-02-23
I used vlc to play iso's also. On my XP machine I would use vlc360 to stream iso's to the 360. They had to be without menus for vlc360 to do it. I use DVDshrink on XP. Here is a thread that explains how to stream dvd's to 360 by ripping the movie as one big VOB file. Can DVDrip do that? It is lossless and carries the 5.1 sound. Also good if you need to burn it to DVD.

---

### Post by Creative2 on 2008-02-23
i mean, if you know some things on mencoder you don't need to press too much buttons, my point of view,  is this you use too much software xD  i don't know dvd::riip but i think is of couse based on mencoder..

cutting..... 

-vf crop=720:352:0:62 this is the part of mencoder to cut the video 

open a terminal before encoding and run 

mplayer INPUT -vf cropdetect  , in that terminal will appear  something like that 

[CROP] Crop area: X: 0..319  Y: 0..239  (-vf crop=320:240:0:0).6 0

as you can see here is a -vf crop=320:240:0:0
this mean is a normal 320:240 and you don't need to cut nothing becuase x=0 e y=0

---

### Post by Syndacate on 2008-02-23
> **Creative2 said:**
> i mean, if you know some things on mencoder you don't need to press too much buttons, my point of view,  is this you use too much software xD  i don't know dvd::riip but i think is of couse based on mencoder..

cutting..... 

-vf crop=720:352:0:62 this is the part of mencoder to cut the video 

open a terminal before encoding and run 

mplayer INPUT -vf cropdetect  , in that terminal will appear  something like that 

[CROP] Crop area: X: 0..319  Y: 0..239  (-vf crop=320:240:0:0).6 0

as you can see here is a -vf crop=320:240:0:0
this mean is a normal 320:240 and you don't need to cut nothing becuase x=0 e y=0

That just seems like a lot of extra stuff that I simply don't know.

avidemux is a GUI - works well to crop things - I like it, b/c often I don't know the times, that's why avidemux makes quick work of cropping files.  Fuoco tools is like, the greatest software ever.  With those combined it makes it easy to make an efficiently sized file, regardless of format, regardless of origin.

You can convert an .iso to an .avi then clip out the whole entry thing and it becomes a movie.  That way is jut confusing.

IMO GUI front ends will always make things faster and easier.

---

### Post by arman.haghi on 2008-02-23
:lolflag:

This whole thread brings me back to my original point; I was trying to find a method that I could teach to someone who is capable of learning, but is a movie a hobbyist not a linux guru and not likely to want to drop to Konsole or go between programs (eg my mum).

DVD::rip is visual, and has a step-by-step tab progression. It isn't perfect, but it is the most intuitive one I've seen so far, while a more intuitive program would be like the imagined one I described earlier in this post (Any comments?)

---

### Post by Syndacate on 2008-02-24
> **arman.haghi said:**
> :lolflag:

This whole thread brings me back to my original point; I was trying to find a method that I could teach to someone who is capable of learning, but is a movie a hobbyist not a linux guru and not likely to want to drop to Konsole or go between programs (eg my mum).

DVD::rip is visual, and has a step-by-step tab progression. It isn't perfect, but it is the most intuitive one I've seen so far, while a more intuitive program would be like the imagined one I described earlier in this post (Any comments?)

Well the programs I use are ridiculously simple - one of them is command line based (avimerge) but the syntaxing is very very easy.  Not like the cropping commands that Creative2 tried explaining to me.  Cropping things visually and going frame by frame in avidemux is a very good feature IMO, and it doesn't have to re-encode like Kino so it doesn't own ur file size or take a long time to load.

i think with a "how-to" written in open office she can do the stuff she wants to do quite easily.

I don't think there's one "end all" - "god" program that you seem to be looking for which is very stable, very versatile, easy GUI, and can do everything.

---

### Post by Creative2 on 2008-02-25
nevermind

---

