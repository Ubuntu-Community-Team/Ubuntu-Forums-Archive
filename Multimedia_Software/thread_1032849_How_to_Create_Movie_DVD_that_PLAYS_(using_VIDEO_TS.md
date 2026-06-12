---
title: "How to Create Movie DVD that PLAYS (using VIDEO_TS folder)? Data DVD isn't working..."
date: 2009-01-06
forum: Multimedia Software
---

### Post by OzzyFrank on 2009-01-06
OK, this is something that has plagued me since first trying Ubuntu in Oct 2006: How the hell can I get a Data DVD with the VIDEO_TS folder to just play like in Windows? If your answer is I should be creating a movie DVD, then let me clarify: in Windows, nearly every app I've used lets you create a playable DVD via making a Data DVD with a VIDEO_TS folder (there is usually not even a Movie DVD option). It's as simple as that: burn the VIDEO_TS folder to a disc and it will play in any DVD playing software and in the DVD player in the lounge.

However, do this in Ubuntu with apps like Gnomebaker and Brasero and Ubuntu will look at it as just a data disc (for that matter, Windows and my lounge player won't recognise them as playable DVDs either). The only parallel I can think of is using Nero in Windows. That godawful app will give you an unplayable disc if you do it via Data DVD (it at least warns you) and you have to do this via a movie DVD project (which adds some extra files... quite weird and unneeded, since apps like RecordNow can make a playable disc with just the VIDEO_TS folder on the DVD).

The apps in Ubuntu basically seem to be like my preferred Windows apps like RecordNow, in that there actually ins't a Movie DVD option. The difference of course is that these Ubuntu apps seem to give me unplayable data discs (of course, if I get players like Kaffeine to open the folders, then they will play, but this isn't the same... especially if trying to play it in the lounge, which results in the message that the disc isn't playable).

Just so you know, I am quite familiar with concepts like finalising the disc, etc. While default options should be sane useful ones, I do check those. Only thing I am not sure about is default filesystems - for example, in Gnomebaker's preferences, or should I say the dialogue box that comes up when going to burn a data DVD, in the Filesystem tab, it has Joliet and Rock Ridge checked. I am used to default settings working in my Windows apps, but is it one or both of these interfering with what I am trying to accomplish? Like I know Joliet is a default system for data CDs and DVDs (not familiar with Rock Ridge at all) but am not sure if having this checked is the right thing (ie that a movie discs need no filesystem specified, and that having it enabled actually forces it to be seen as a data disc).

Like I said, this is an ongoing issue I've never resolved in 2 years, and really wouldn't mind not having to boot into Windows to burn movie discs... or ending up with more coasters when I try in Ubuntu. All I can think of it that in Windows programs like RecordNow automatically set the correct filesystem based on the contents... ie it sees a VIDEO_TS folder so knows how to burn it correctly, and that in Ubuntu programs like Gnomebaker need more input to see the difference between a data disc and movie DVD.

Any help on this would be appreciated, as I gather there must be people who are successfully burning movie DVDs. The only movies I've successfully burned in Ubuntu are via ISO images created by DVD Shrink. Thanks in advance.

---

### Post by mc4man on 2009-01-06
Well if your using wine then why not just install Imgburn and you can burn pretty much anything 100% correctly, everytime (including dual layer movies

As far as video_ts there's 2 basic ways
Use Imgburn in build mode -> output to image (.iso), then burn in write mode.

Or use in build mode -> output to device ( builds and burns on the fly.

While there are a ton of setting the defaults are good, though Id change the IO to below (takes drive detection out of wine's control


[http://www.imgburn.com/](http://www.imgburn.com/)

[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

---

### Post by wolfen69 on 2009-01-06
i believe with Devede you can burn with the video_ts folder. there are a bunch of dvd apps out there. try a few.

---

### Post by OzzyFrank on 2009-01-06
> **wolfen69 said:**
> i believe with Devede you can burn with the video_ts folder. there are a bunch of dvd apps out there. try a few.

Problem is I HAVE tried a few... more than a few... so am reluctant to create more coasters, when in Windows this isn't an issue. When you've tried about 10 apps... including the main players in Ubuntu and Kubuntu... the next logical thing to do is come here and ask for info from those who can successfully do this. I welcome any input on this... but call me fussy, I'd prefer "I know" rather than "I believe"... "I believe" sounds like a new coaster in the making, hehe!

---

### Post by OzzyFrank on 2009-01-06
Hehe... DeVeDe... well, good news is it won't create coasters... but that's because you can't even add a VIDEO_ts folder, hehehe! This is the error, which you get trying to add it via a few different ways:

"Some files weren't video files. None added."

Like I said, I'd welcome any info, but would much prefer you'd actually tried the program yourself and have already achieved what I want to achieve. When I opened DeVeDe it did look promising, as there was a Video DVD option, though when I saw you could choose between PAL and NTSC it had me worried (since it should automatically detect this, or just not even worry about it, since the job is to burn it, not do any encoding.re-encoding).

I might yet look at Imgburn, especially since it seems to run in Wine OK, but I would prefer native apps, given the choice. I just figured that in the last 2 years there would HAVE to be either a new app to handle this simple task I take for granted in Windows, or at least a way to do it successfully in apps like Gnomebaker. I have to admit I find this staggering!

---

### Post by GrandpaLeaman on 2009-01-06
I installed tovid from the repositories and use "makedvd" in the terminal to create DVD's. It's very easy, but no gui. Once you install tovid, go to the terminal and type in the following:
> man makedvdThere you will be able to select the options you need.

Example: makedvd -burn -speed 2 -label your_video_folder "/location/of/your_video_folder"

Replace the "your_video_folder" with the name of your folder which contains the "VIDEO_TS" folder.

I hope this helps!

---

### Post by killabee44 on 2009-01-14
Guys,

I had this same problem. Had .Vob files in a video_ts folder that I needed to burn. 

K3b can do it. You have to click on the bar below the gui with the options. Click on "Further Options" ---> then select: "New Video DVD Project". 

You will see a Video_ts folder on the bottom. Open it and drop your .vob files inside. That's it.

This it the thread where I found the info. I hope this helped someone find the answer faster than I did.

[http://ubuntuforums.org/showthread.php?t=823219&highlight=mandvd+video_ts&page=2](http://ubuntuforums.org/showthread.php?t=823219&highlight=mandvd+video_ts&page=2)

Killabee44

---

### Post by OzzyFrank on 2009-01-15
Thanks killabee44 - that was the info I was looking for!

You don't actually need to select the .vob files and drag them into the VIDEO_TS folder either... just drag the source VIDEO_TS folder to the project for the same result.

I was afraid it would not give me the option to add extra files (I generate an md5sum.txt file for the disc so I can check it for defects) but it does. I suspect when specifying the title label in Filesystem you could probably add more characters, as I'm used to Windows apps being limited in that respect (with discs I create in Ubuntu it's not uncommon to be only be able to see half the label in Windows).

So now that's another task I will prefer to do in Ubuntu. I already preferred to make data DVDs here, as I could generate a checksum, burn the disc, and verify it in one sitting. Now I can do that with movie DVDs.

To learn how to do this, check out my tutorial:

[http://ubuntuforums.org/showthread.php?p=6556564](http://ubuntuforums.org/showthread.php?p=6556564)

---

### Post by crjackson on 2009-01-15
I actually use that program you love to hate (Nero Linux)and it has NEVER made a coaster for me.

I've had plenty of problems with Brasero, Gnomebaker AND K3B.

For reliability (FOR ME) nothing beets Nero Linux.

---

### Post by OzzyFrank on 2009-02-02
Unfortunately, Nero for Linux costs money, unless you download an illegal copy. Most of us here want to avoid both those options. As for Nero in Windows, I used to use it, but eventually found others worked better for me, and as I mentioned, I didn't like its approach to video DVDs (and using RecordNow meant less mouse clicks, so I just went with what was quicker). At least in Ubuntu I can now do as I do with RecordNow with K3B.

I'd be interested in hearing about more apps that can successfully do this, but will mark this as solved.

---

### Post by hissyfut on 2009-02-02
just wondering.. in some apps the type of disc getting created states it as UDF. Is there a default mode or official spec which says what DVDs should to be burned in, UDF for example?

---

### Post by OzzyFrank on 2009-02-03
> **hissyfut said:**
> just wondering.. in some apps the type of disc getting created states it as UDF. Is there a default mode or official spec which says what DVDs should to be burned in, UDF for example?

That's sort of what I was wondering. I figured that may have been the main factor for not being able to play DVDs where I had just burned the VIDEO_TS folder to disc. Not sure what K3b (and apps like RecordNow! in Windows) are doing right.

---

### Post by mc4man on 2009-02-03
Dvd Video should be in *ISO9660, UDF (1.02)* for compatibility with all Os's and standalones.


> The standard requires an UDF Bridge format: UDF version 1.02 plus ISO 9660 Level 1.


---

### Post by OzzyFrank on 2009-02-04
Thanks for that informative answer, mc4man.

Hey, I've tried to mark this as solved, but seems I am missing the option under Thread Tools! If this has been changed, can someone please let me know the new way of marking threads as solved? Thanks

---

### Post by mc4man on 2009-02-04
Solved and thanks have been disabled.
You can always edit your thread title and add a [Solved] to the end of the title.

---

