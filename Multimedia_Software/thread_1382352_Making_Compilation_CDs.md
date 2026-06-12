---
title: "Making Compilation CDs?"
date: 2010-01-15
forum: Multimedia Software
---

### Post by JSeymour on 2010-01-15
Hi All,

Okay, I searched this sub-forum for threads with "ripping" and "audio burn" in the subject, and I'm really no better-off than when I started an hour or more ago :-P.

What I'd like to do is be able to rip a track or two off of each of X number of original CDs and create a compilation CD from those tracks.  Mostly all I'm finding here is how to rip CDs to various formats such as ogg, wav, FLAC, and mp3.

So... How to do this?  Would be nice if the per-track meta-data could be retained, but it's not vitally necessary to me.  Not too worried about track-to-track gaps.  The originals have them, so my compilation can have them :).

All this point-n-drool stuff is making me lazy.  (I used to be a committed command-line kind of a guy.)  A graphical app, or a pair of them, that would allow me to easily rip the tracks I want, set the ripped tracks up in the order I want them, and burn them would be terrific--but if I have to go command-line to accomplish it, that's okay, too.

Thanks in advance for any pointers!

---

### Post by liveB on 2010-01-15
If you can open the CD (I could when I did this, but don't know if that's 'normal' otherwise refer to the 'ripping' process) then you can copy the .wav files to a new directory on your HD.  I then used brasero to create an audio disk and wrote the files from that new directory to the CD by dragging the file names to the new CD's directory within brasero.  The only two problems were that I ended up renaming the file names by prepending a letter of the alphabet (Nickleback's FigureYouOut became bFigureYouOut to make it the second song) and I lost the meta-data (you said that wouldn't be a problem for you).

---

### Post by JSeymour on 2010-01-15
> **liveB said:**
> The only two problems were that I ended up renaming the file names by prepending a letter of the alphabet (Nickleback's FigureYouOut became bFigureYouOut to make it the second song) and I lost the meta-data (you said that wouldn't be a problem for you).What I've been reading (since posting the thread starter) is that you can arrange the track order to your liking and that the meta-data comes along.  I guess I'll just have to try it.

We just picked up a spindle of 100 Sony CD-Rs at Costco, so I have plenty of CDs to "burn" in experiments :)

Thanks for the follow-up!

Jim

---

### Post by JSeymour on 2010-01-16
It looks like the Big 5 for ripping are RubyRipper, Grip, abcde, RipperX and Sound Juicer. Guess I have to do my research and decide which would best meet my needs.

For burning: It looks like Brasero will do the trick--and that's already installed.

Thanks,
Jim

---

### Post by HomoGleek on 2010-01-16
> **JSeymour said:**
> Hi All,

Okay, I searched this sub-forum for threads with "ripping" and "audio burn" in the subject, and I'm really no better-off than when I started an hour or more ago :-P.

What I'd like to do is be able to rip a track or two off of each of X number of original CDs and create a compilation CD from those tracks.  Mostly all I'm finding here is how to rip CDs to various formats such as ogg, wav, FLAC, and mp3.

So... How to do this?  Would be nice if the per-track meta-data could be retained, but it's not vitally necessary to me.  Not too worried about track-to-track gaps.  The originals have them, so my compilation can have them :).

All this point-n-drool stuff is making me lazy.  (I used to be a committed command-line kind of a guy.)  A graphical app, or a pair of them, that would allow me to easily rip the tracks I want, set the ripped tracks up in the order I want them, and burn them would be terrific--but if I have to go command-line to accomplish it, that's okay, too.

Thanks in advance for any pointers!
I use Audio CD extractor for burning/ripping, I **think** it will fit all your needs.

Plus its in the SC

---

### Post by JSeymour on 2010-01-16
> **DarrenTod said:**
> I use Audio CD extractor for burning/ripping, I **think** it will fit all your needs.

Plus its in the SC
Near as I can tell, from searching on it, "Audio CD Extractor" is Sound Juicer?

Putting either "audio cd extractor" or "Sound Juicer" into Synaptic's search produces
nothing.

Jim

---

### Post by mc4man on 2010-01-16
It's sound-juicer
Sometimes its better not to be to verbose in synatpic, sound  would produce the results

---

### Post by JSeymour on 2010-01-16
> **mc4man said:**
> It's sound-juicer
Sometimes its better not to be to verbose in synatpic, sound  would produce the resultsRight you are :).  Thanks!

The research continues...

Jim

---

### Post by ron999 on 2010-01-16
Hi
It's possible to do what you require.
If I were doing the job I would use **Ruby Ripper** to rip the required tracks as **flac** files into a folder on the hard drive.
Then I would use **EasyTag** to edit the file title and meta-data etc as required, then save the changes.
Then I would use **GnomeBaker** to create an audio cd from those files. You drag and drop the files in any order you like.
I'm not sure whether any Meta-Data would still be there when the cd is burned though.
:D

---

### Post by JSeymour on 2010-01-17
> **ron999 said:**
> Hi
It's possible to do what you require.
If I were doing the job I would use **Ruby Ripper** to rip the required tracks...No offense to those who like Ruby, and I know it may seem lame, but I'm disinclined to install Ruby to support just this one app.

> **ron999 said:**
> ...as **flac** files into a folder on the hard drive.Since I'm doing this just to create compilation CDs, wouldn't .wav be better?

> **ron999 said:**
> Then I would use **EasyTag** to edit the file title and meta-data etc as required, then save the changes.Thanks for the hint.  I'll look into *EasyTag*.

> **ron999 said:**
> Then I would use **GnomeBaker** to create an audio cd from those files. You drag and drop the files in any order you like.I think I'll stick with Brasero for burning.

Part of the reason, and this also applies to RubyRipper, is that I'm trying to stay with apps that are in the standard repos.  I know I don't *need* to.  And I'm perfectly comfortable going "outside the box," as it were.  I had to do that for nearly everything on my old system.  And often do a lot of hand-tweaks to the code or build process, to boot.  (It was Solaris 7 on an UltraSparc IIi mobo.)  But, with this new system, I'm trying to keep it "point, click, install and use" to the extent possible.

> **ron999 said:**
> I'm not sure whether any Meta-Data would still be there when the cd is burned though.
:DYeah, I need to look into that more.

Thanks for the recommendations!

Jim

---

### Post by ron999 on 2010-01-17
> **JSeymour said:**
> 
Since I'm doing this just to create compilation CDs, wouldn't .wav be better?


I don't think that .wav files have any meta-data at all, but flac files do.
And EasyTag will let you edit flac meta-data.
But this is academic if the meta-data isn't going to appear on CDs anyway.

I agree with your views, use the apps that you're familiar with.
:D

---

### Post by lyall on 2010-01-18
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
scroll down to 2.10 Multimedia Applications and you will see some others you might like

good luck and have fun learning

---

### Post by JSeymour on 2010-01-19
> **lyall said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
scroll down to 2.10 Multimedia Applications and you will see some others you might like

good luck and have fun learningHey, lyall, thanks for that pointer!  *Asunder* looks like just the thing I wanted for a ripper.  Clean.  Simple.  I think I'll give that one a go, for ripping, first.

(Edit) Tho it looks like what's in the repos is a bit out-of-date, so maybe not...

Jim

---

