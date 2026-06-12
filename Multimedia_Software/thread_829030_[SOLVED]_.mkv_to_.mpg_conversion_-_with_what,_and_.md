---
title: "[SOLVED] .mkv to .mpg conversion - with what, and how?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Thanh-BKK on 2008-06-14
Hello :)

I have a couple of huge (4+ GB) video files in .mkv format, i believe they are HD DVD rips. I want to convert these to .mpg to be able to edit them further (in fact i want to create a number of clips from that movie).

Which software, if possible with GUI and from the repos, can i use for this job? The initial conversion, that is - i know how to continue once i have .mpg files :)

Appreciate any advice...... many thanks in advance.

Thanh

---

### Post by foo on 2008-06-14
With avidemux you can easily make a DVD format mpeg2:

[http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD](http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD)

Avidemux can also open and edit matroska, anyway.

---

### Post by Thanh-BKK on 2008-06-14
Hello :)

Yeah, i tried with Avidemux - i found that i can make my clips right from the .mkv file, which is great, however it only generates .avi files - mpg, mp4 etc all don't work, they generate files that won't play (Totem complains that it "can't detect stream type" and VLC simply does nothing at all).

So i have found solution #2 (making clips) before #1 (convert to mpg). I still need THAT function, as Avidemux is a no-go (by the way it has to be VCD-compliant, not DVD).

With kind regards......

Thanh

---

### Post by IanW on 2008-06-15
With Avidemux, you click on the "Auto" tab & select VCD (the top item on the list)
Of course, it all depends on what codecs you have installed on your system.

---

### Post by Thanh-BKK on 2008-06-15
Hello :)

yeah, i've tried that too - it started doing something (converting?) which it estimated to take 420 minutes - sorry, to generate a 5 min clip out of a 3 hour movie i don't want to wait 7 hours, probably only to see a huge file that doesn't play at all. 

What i did is select the start frame and end frame of my clip ("A" and "B") and then selected "container" (well, avi, mpg, mp4 etc) and then clicked the "floppy" symbol to save, at first i was surprised that i had to enter the file ending (i.e. ".mpg") myself.... Avidemux is not exactly helpful. 

It the goes on to convert/create clip, which takes anywhere from a few seconds to a couple of minutes depending what "container" i chose - however the only ones that come out working are .avi. 

Anyway if i can't go the route A->B maybe i can get there B->A. Normally i convert *anything* to mpg, create my clips, merge/cut etc, and then convert to final format, usually mp4 or 3gp for phone use. 

However Avidemux allows me to create clips first - now how, or "with what", can i do the "merging"? I.e. i have several short .avi files now which i need to merge to become one larger .avi file, and that i need to convert to mp4 with 176x128 video resolution to be used on Sony-Ericsson phones. 

I used to have a bunch of programs under Windows to do that, and i'm sure they exist for Linux too.... i just need someone to point me in the right direction :)

Appreciate any help.....

your Thanh

---

### Post by hypocratus on 2008-06-16
If you have mencoder installed, you can do the following:
mencoder -ovc copy -oac copy -idx -o <name of the merged file> <files you want to be merged>
Here is an example:
mencoder -ovc copy -oac copy -idx -o football.avi quarter1.avi quarter2.avi quarter3.avi quarter4.avi
Fill in the name you want the file to be for the merged file and then the separate video files you want merged. The different video files have to be the same resolution and use the same codec. The merged file will default to an avi file. Here is a webpage with more:
[http://en.wikibooks.org/wiki/Mplayer](http://en.wikibooks.org/wiki/Mplayer)
I hope that helps.

---

### Post by Thanh-BKK on 2008-06-17
Hi :)

Thank you so much for that. Yeah, i have Mencoder in my system and will give this method a try as soon as i'm back home. The small files should all use the same resolution (as they are from the same, large, file) and codec (as they are produced by the same software, ie.e Avidemux).

Is there a GUI front end for Mencoder available? I don't mind the terminal but then i'm a mouse pusher :)

Best regards......

Thanh

---

### Post by eye208 on 2008-06-17
> **Thanh-BKK said:**
> Yeah, i tried with Avidemux - i found that i can make my clips right from the .mkv file, which is great, however it only generates .avi files - mpg, mp4 etc all don't work, they generate files that won't play (Totem complains that it "can't detect stream type" and VLC simply does nothing at all).
MP4 is a container for MPEG streams. If the MKV contains streams in non-MPEG formats (e.g. Theora, Vorbis), you can't put them into MP4. Well, actually you can, but most players will be unable to play the resulting file.

---

### Post by rainwalker on 2008-06-17
Also, you can install ffmpeg and WinFF (a GUI for ffmpeg), it's the king of file conversion

---

### Post by Thanh-BKK on 2008-06-18
Hello again :)

The command line thingy worked PERFECTLY, and super-fast too! Too bad i need to remember it now....... i guess i'll just bookmark this page :)

I wish there was a front end with GUI for this command.... after all, i found that "DeVeDe" uses Mencoder too, it does in fact generate perfect .mpg files that really work. However it can't join files. 

I tried getting the WinFF (already got ffmpeg) but no luck - Synaptic doesn't find it. How do i obtain this one? 

Many thanks in advance for advice......

Thanh

---

### Post by rainwalker on 2008-06-19
[http://www.winff.org/](http://www.winff.org/)
It's not in the repos, unfortunately, and I haven't used it much so I'm not positive that it will do what you want

---

### Post by Thanh-BKK on 2008-06-19
Hi :)

Thank you very much for that - judging by the screen shots this is exactly what i need :) I have downloaded it but i am now at the office (Windows!) and can only try it when i am back at home in the evening or tomorrow morning.

I very much appreciate your link :)

Best regards.....

Thanh

---

### Post by Thanh-BKK on 2008-06-19
Hello once more.

I have installed that now, it opens and runs fine, however converting fails - regardless what i chose, i ALWAYS get something to the tune of "unsupported codec". 

What should i do? I believe the codecs are installed because i can watch ALL video formats.

Weird.

Best regards.....

Thanh

---

### Post by rainwalker on 2008-06-20
Have you installed ffmpeg?

---

### Post by Thanh-BKK on 2008-06-20
Hi :)

Yes, i've got that installed. 

Meantime i also found out that the .avi file, initially produced by Avidemux, plays in Totem - and that's it. Due to a "corrupted avi header" it does not play in ANYTHING else! Not even VLC, Linux or Windows. 

I managed to make a mpg file that does play, however it's a very low resolution (the original mkv is widescreen/HD)....

There must be a way to convert videos in Linux??

Or do i really need to install XP in a VM to get that job done??

Best regards.....

Thanh

---

### Post by sweethe on 2008-10-09
> **Thanh-BKK said:**
> Hi :)

Yes, i've got that installed. 

Meantime i also found out that the .avi file, initially produced by Avidemux, plays in Totem - and that's it. Due to a "corrupted avi header" it does not play in ANYTHING else! Not even VLC, Linux or Windows. 

I managed to make a mpg file that does play, however it's a very low resolution (the original mkv is widescreen/HD)....

There must be a way to convert videos in Linux??

Or do i really need to install XP in a VM to get that job done??

Best regards.....

Thanh

Let us know if it works!:guitar:

---

### Post by Thanh-BKK on 2008-10-09
Hi :)

Umm i kind of never followed up on this one.... mostly because within hours my topic is somewhere on page 17 or so, it goes just so fast :)

Meantime i do not remember what exactly i did, i believe what finally did the trick was installing some more codecs from some "restricted" kind of package.... those had to go into a different folder, it was an awful lot of codecs in fact (a whole package) and ever since i can pretty much convert anything into everything with just Avidemux (gtk) and WinFF. 

I installed XP in a VM regardless.... and never touched it since :) And recently even installed Win95 in another VM (my work colleague gave me a genuine CD plus a genuine MS Office 97, would be a shame NOT to use them.....) was fun to get that old system running. But my daily computing is done with PPP (Pure Penguin Power).

Best regards.....

Thanh

---

