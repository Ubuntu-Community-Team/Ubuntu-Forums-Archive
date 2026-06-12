---
title: "DVD Authoring question"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by reiki on 2007-12-17
My wife spent the better part of the day yesterday taking old family movies that were on VHS tapes and burning them to a DVD.  ( DVD-R media ) When she went to remove the disk from the burner it prompted her to finalize it, which she did. HOWEVER, she didn't put new text titles on each of the 24 chapters and there were some other things she could do in the menu that the burner creates for the DVD.

I am hoping to find a solution that will make it so she doesn't have to reburn the entire DVD again.

So here's my question. Is there DVD authoring software out there that will allow me to Copy the current DVD but create a new menu for it ... so when it's inserted into a standard DVD player (not a computer) it will bring up the menu from which you can choose a chapter to watch?

** edit : clarifying what I want **
I want to take an existing DVD that we made, and use a program that will allow me to take all of the individual "pieces" or chapters and burn them to a different DVD but I want to add a menu.

This is my first foray into DVD authoring at all so I don't know what to expect or what I'll even see on the DVD if/when I stick it into my computer. So if it's a standard DVD what kinds of files will I see? Does each chapter have it's own file (or files)? I've been stomping around this morning reading about DVD authoring software... in the US... I want to create NTSC video? I want this to play on standard DVD players like grandma might have in her living room. (no computer)

Thanks for any help and/or pointing me in the right direction.

---

### Post by yabbies on 2007-12-17
In order to do what you are asking you would have to first rip the dvd to your hard drive. You can use DVD::Rip, vobcopy or some other similar linux software. 

This will give you a directory of your dvd. 
for instance if you use vobcopy
open a terminal and use the code ```
vobcopy -m
```
which will copy the whole dvd_directory to your hard drive.

open the directory and there will be to folders an audio_ts and a video_ts
in the video_ts folder there will be .vob files that contain your home movies

the only way I know is to transcode those vob files to mpg-mpeg-2 for dvds that way you will be able to make a menu with all the bells and whistles.

to make a dvd with folders and a complete menu I would recommend using tovid and todisc.

tovid/todisc is not in the ubuntu repos so you can check this[ out]("http://ubuntuforums.org/showthread.php?t=617994") to help you along.
just switch the avi transcode to vob. need any help or have any questions don't hesitate to ask.
good luck

---

### Post by reiki on 2007-12-17
thanks... hmmmm...

on a "standard" DVD would I expect to see separate files for each title? (sorry... I'm at work and don't have the DVD here) and what would that file format be? .vob? 

Again I appreciate your patience as I'm totally inexperienced in this and trying to help my wife get these done as gifts for her siblings.

---

### Post by yabbies on 2007-12-17
an example of a dvd_directory inside the Video_TS folder you will see something like this:
VIDEO_TS.BUP
VIDEO_TS.IFO
VIDEO_TS.VOB
VTS_01_0.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_02_0.BUP
VTS_02_0.IFO
VTS_02_0.VOB
VTS_02_1.VOB
VTS_02_2.VOB
VTS_02_3.VOB
VTS_02_4.VOB
VTS_02_5.VOB
VTS_02_6.VOB

.bup is the backup of the .ifo files
.ifo contains the information to sync the audio and video and playback details
the.vob files are the actually movies, the vobs contain the mpg files, the audio files, any subtitles that have all been multiplexed together.

so in the example the VIDEO_ts.vob file usually contains the dvd menu. Then the VTS_01_0.vob would contain maybe a preview or content warning.
and then 2_0 through 2_6.vob would contain the actual movie.

in order to make a menu you would have to transcode those 2_0-2_6 vob files to mpg. That would give 7 separate titles of the movie. You could then use todisc to make a menu with 7 animated thumbnails(depending on the length of the home movie which you would have to split between discs) with an xml that would give you seek times or chapters, where you can skip through each title to seek to a place in the movie. 

Trying to explain this as best as I can with out being to complicated.
[URL="http://tovid.wikia.com/wiki/Screenshots"]
here[/URL] are some screenshots of menus being made by tovid/todisc

let me know if this helps you out

---

### Post by reiki on 2007-12-17
I'm *starting* to understand more.... but the light ain't going on yet.
I don't understand why I'd have to take the .vob and make them mpg.

Is that just so that todisc dvd authoring program can manipulate them? Or make titles from them?  

 
The DVD burner that made the DVD created the menu, but it isn't what we want.  
As a n00b, I look at this and say, "The DVD is done but we screwed up the menu." 

Can't I just import the entire DVD structure and create a menu that points to those .vob files?  
I'm asking because I feel like every transcode is going to subtract a bit of quality. These are already home movies transferred from 8mm onto VHS and now I'm gonna burn to DVD. I have the first generation VHS tape (from which many copies were made). The original 8mm were destroyed by fire. So this is all we have left.

---

### Post by yabbies on 2007-12-17
yeah every transcode will diminish the quality and coming from vhs your quality is already effected

the only reason you would have to make mpg is if you wanted to edit or make "one complete movie" file.
other wise if you wanted just install tovid
which todisc comes with it

rip your dvd so that it includes all vob files and then run the todiscgui 
add all your vob files and create the exact menu you would like to have
the good thing about todisc is that it shows you a preview of the menu before you create the new directory and burn the disc

I was misunderstanding you. Vob files are golden and you can create a menu thumbnail or text menu  however you want to do it. If you have three vob files you will have three different titles.

a couple of screenshots to show what you can expect from the vob files.
read up on todisc cause it can make some pretty sweet menus and gui is very easy to use

let me know if this helps

---

### Post by reiki on 2007-12-17
Ahhhh.... ok . 

Can't just copy the file structure, have to rip it... right? 
I don't even know if I can SEE the file structure at this point 'cause I don't have the disc in my hand.

But after ripping I'm going to see the file structure on my computer wherever I ripped it to. That gets done using tovid (right?) 

And then using todisc, I would take all that stuff and create the menu and rewrite the DVD with the menu we want. 

Am I getting close?

It's a shame I can't just copy the VOB files (and the other ones) right from the DVD onto a hard drive location. 

Thanks again for the help. This is much appreciated.

---

### Post by yabbies on 2007-12-17
you will want to rip the disc structure to hard drive

tovid is essentially a transcoder, dvd authoring tool and burning tool

todisc is a menu maker

I would suggest vobcopy to copy your vob files(clever name) vobcopy I believe is in synaptic
pop in your dvd and open a terminal and use the code:

```
vobcopy -m
```

-m is just telling vobcopy to mirror the dvd, which copies all directories to your hard drive.
when it's done you will have a dvd folder with the name of the disc in your home folder.
That will contain the VIDEO_TS directory with all your vob files.

you can then take those vob files and start todiscgui add them in give them a name and make a menu to your liking. Sometimes dealing with vob files I have run into scr moving backwards(the timecode on the movie starts over) and everything needs to be re-transcoded and remuxed. It's very rare and since you were able to already make a disc this shouldn't be a problem.

I'll be around tonight and will pop in periodically in case you need any more help
good luck
sounds like a pretty cool christmas present for everyone.

---

### Post by reiki on 2007-12-18
Ok this is a little weird...

After finalizing the DVD, I can't read the VIDEO_TS folder. Can't open it. And there is no audio_ts folder. The DVD plays. I can view the movie segments on it. I inserted a different DVD that I burned as a copy from something else (legal) and on that one I can see the video_ts folder and also an audio_ts folder. They show up as folder icons when I "view as icons". The video_ts on the NEW dvd doesn't even show as a folder. 

vobcopy gives me an error about not finding the information file and I can't seem to get vobcopy to write the verbose log. My wife redid the entire dvd and made the menu changes she wanted. 

Makes me wonder if there's something odd in the way the dvd recorder is finalizing. However it can apparently be played in other dvd players. 

Am I missing something?

---

### Post by reiki on 2007-12-18
Replying to myself.... actually just adding a bit more info.

I was reading the manual for the dvd recorder and it mentions that after finalizing, the disk will be "play only" and can not be copied. This is a Panasonic ES15S dvd recorder. 

I am fairly certain I can still copy it by making an image (haven't tried yet) and then burning that to additional dvd media, but man this would suck if my wife went through all this and we discover we can't mass produce it :)

We used DVD-R media for this. Should we be using different media for stuff we know we're going to want to make copies of?

---

### Post by yabbies on 2007-12-18
never heard of such a thing, will look into though.


no, dvd-r is fine. Some cheaper brand names of media don't burn properly at high speeds but that has nothing to do with not having a VIDEO_TS folder.

let me know what happens when you rip and try to burn the iso

---

### Post by reiki on 2007-12-18
When I open the DVD .... not play it... open it as a "removable device" there is only one item and it does indeed say, "VIDEO_TS"

However it is not recognized as a directory or file and if I double click it I get a dialog telling me it can't be read (or opened). 

If I stick any other DVD in my computer (not created on this same recorder), it PLAYS ... I see the movie or menu. When I put this one in it comes up as normal removable device with files. It does not auto run the menu. 

This is the first time we've actually tried to do anything with a DVD recorded on that dvd recorder. I've never had a need to look into the structure or anything.

I thought "finalizing" was doing something to it so I tried to read it on my computer before it was finalized and the computer thinks I've inserted a blank DVD. So I don't think THAT's the problem. 

When I get home I'm going to try using vobcopy again, but as sudo and see if I can at least get it to write a verbose log.

I'm kinda at a loss here. unless this is just a quirk of the Panasonic DMR-ES15 recorder.

*shrug*

The disc I'm slaving over has 34 titles. Most of those have only 1 chapter. Chapters inserted automatically every 5 minutes. These are short home movie clips. There are only a few that have 2 or 3 chapters. I should have more time tonight to mess with this. But I think when I tried to rip it, it only picked up the first chapter of the first movie clip.

---

### Post by reiki on 2007-12-18
y'know I HATE having to admit my "duh" moments.....

So today I install libdvdcss2 (that's the "duh") ... and things started working a bit better, but still a few issues.

So I ran "sudo dvdrip" and that worked. Got a listing of everything on the DVD and ripped one title to hard drive. It worked!

So then I ran "sudo vobcopy -m" and away it went and dutifully created 36 sets of vob/ifo/bup files.

Now all those files are owned by root and while I know I can change THAT part easy enough, is there a way to not have to run these as root? I don't like running stuff as root if it's at all avoidable.

I would love to get that taken care of before I mark this as [SOLVED]  :)

Thanks for the help.

---

### Post by yabbies on 2007-12-19
by running vobcopy with sudo you are making the files root only
just run
```
vobcopy -m
```

sorry about the null been extremely busy with work

---

