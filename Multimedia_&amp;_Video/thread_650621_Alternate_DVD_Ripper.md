---
title: "Alternate DVD Ripper"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by Syndacate on 2007-12-26
I'm sure this has been asked 1000 times but I got some extrenuating circumstances here.

I need to rip DVD files to .iso format.

DVD::Rip would be nice, but it creates VOB files in chapters, I need ONE **.iso** out of these.

Right clicking on the cd-rom drive >> copy >> save as .iso (I'm not sure which program this is) - does it PERFECTLY...but there's no sound...

K9Rip would also be perfect but it crashes...every time except one (the first one).  Well it doesn't really crash, gets started a bit, then just freezes (hangs), if I close it it requires a force quit b/c it's not responding...or it just hangs there at wherever it gets stuck for eternity...it worked fine for the first one, just not the next(s).

So what alternative ripper can I use - **DVD to .iso** ?

Thanks for your time.

PS:
The right click >> copy would be EXCELLENT if it wasn't for the fact that there's no sound.

Which it does in a very weird way - the DVD entrance (title) has sound, but the movie itself doesn't...

---

### Post by markharding557 on 2007-12-26
> **Syndacate said:**
> I'm sure this has been asked 1000 times but I got some extrenuating circumstances here.

I need to rip DVD files to .iso format.

DVD::Rip would be nice, but it creates VOB files in chapters, I need ONE **.iso** out of these.

Right clicking on the cd-rom drive >> copy >> save as .iso (I'm not sure which program this is) - does it PERFECTLY...but there's no sound...

K9Rip would also be perfect but it crashes...every time except one (the first one).  Well it doesn't really crash, gets started a bit, then just freezes (hangs), if I close it it requires a force quit b/c it's not responding...or it just hangs there at wherever it gets stuck for eternity...it worked fine for the first one, just not the next(s).

So what alternative ripper can I use - **DVD to .iso** ?

Thanks for your time.

PS:
The right click >> copy would be EXCELLENT if it wasn't for the fact that there's no sound.

Which it does in a very weird way - the DVD entrance (title) has sound, but the movie itself doesn't...
dvdfab decypter works perfectly well on wine
this will rip dvd files to your hard drive,you can then use dvdshrink also on wine to encode them to an iso

---

### Post by RudolfMDLT on 2007-12-26
K9Copy is the best option that I have found to far. But it does crash some times with the new version of Ubuntu. Have you installed libdvdcss2? It's from this HowTo [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624).

DVD::Rip works well? You could always use K3B to burn an ISO of the decoded and ripped VOB files?

If the GUI rippers keep crashing you might want to try some text base rippers such as dvdbackup. I haven't used it but it's worth a try. once you have installed it, in the terminal type: man dvdbackup for a quick help file. It's not perfect but I if you can't fix K9copy then I think a commandline based tool is your only option.

---

### Post by Syndacate on 2007-12-26
> **RudolfMDLT said:**
> K9Copy is the best option that I have found to far. But it does crash some times with the new version of Ubuntu. Have you installed libdvdcss2? It's from this HowTo [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624).

DVD::Rip works well? You could always use K3B to burn an ISO of the decoded and ripped VOB files?

If the GUI rippers keep crashing you might want to try some text base rippers such as dvdbackup. I haven't used it but it's worth a try. once you have installed it, in the terminal type: man dvdbackup for a quick help file. It's not perfect but I if you can't fix K9copy then I think a commandline based tool is your only option.

The problem wasn't as much that they were VOB format, more along the liens of it split up every chapter.

That how-to is for feisty.  I'm using Gutsy.

The reason why .isos are good is because they retain their sound quality (where an .avi file will only be 2 speakers, if you record something as an .iso that's 5.1 - if you burn that .iso onto a blank DVD, it keeps the 5.1 - if you convert an .avi to DVD format then burn it to a blank DVD, you have crappy 2 speaker sound (RL audio).  Also, they can stay on the computer, VLC can play .iso images so I can view them here too...  Nothing really else can play .iso's.   

I just used ubuntu's ripper (right click >> copy >> as image) and it seemed to work fine, the problem before was that one and the other one I tried had no sound in the actual movie part..probably corrupted sound files or a bad burner - weird ****, but they wouldn't play sound when I just opened them up as DVD's.

It'd be nice if I could get kaffeine to play the .iso's, but you'd need them to be mounted.

Know any programs that can mount .iso's?  Like Daemon Toolz for Windows?

---

### Post by RudolfMDLT on 2007-12-26
yeah, its called gmount-iso. you can find it under Applications->Add/Remove. Back to DVD::Rip, don't you get the option of ripping to disc before encouding? can't you then use the raw ripped data? When creating you project, note where the vob folder is, under the rip tab, rip the entire DVD and then look for the vob files under the vob folder. Though I agree that ISO's are unbeatable. The HowTo works for Gusty Gibbon *** well - give it a shot.

---

### Post by Syndacate on 2007-12-27
> **RudolfMDLT said:**
> yeah, its called gmount-iso. you can find it under Applications->Add/Remove. Back to DVD::Rip, don't you get the option of ripping to disc before encouding? can't you then use the raw ripped data? When creating you project, note where the vob folder is, under the rip tab, rip the entire DVD and then look for the vob files under the vob folder. Though I agree that ISO's are unbeatable. The HowTo works for Gusty Gibbon *** well - give it a shot.

I got DVD::Rip to work, but it took a hell of a long time to rip. 

Sorry about that, was getting confused between programs :-P

---

### Post by RudolfMDLT on 2007-12-27
No problem, LOL, there are a LOT of app's to chose from! glad you got it to work.

---

