---
title: "What are you using since Mythtv .24 doesn't rip DVD's?"
date: 2010-12-22
forum: Mythbuntu
---

### Post by williammanda on 2010-12-22
I have been using Makemkv to rip DVD's since Mythtv .24 doesn't have this function. My question is... what is everyone else using and why? I like Makemkv since it doesn't use alot of cpu and the ease of use. I tried Handbrake but I didn't like that it used almost 100% of the cpu. With Makemkv I can rip a DVD and watch a HD recording in Mythtv. Also depending on the format, the rip time was very long. It could be just over an hour while Makemkv was around 15 minutes. I have a C2D 6400 with a 9600GT video card. Has anyone integrated a rip program in the mythtv menu structure?

---

### Post by klc5555 on 2010-12-23
> **williammanda said:**
> I have been using Makemkv to rip DVD's since Mythtv .24 doesn't have this function. My question is... what is everyone else using and why? I like Makemkv since it doesn't use alot of cpu and the ease of use. I tried Handbrake but I didn't like that it used almost 100% of the cpu. With Makemkv I can rip a DVD and watch a HD recording in Mythtv. Also depending on the format, the rip time was very long. It could be just over an hour while Makemkv was around 15 minutes. I have a C2D 6400 with a 9600GT video card. Has anyone integrated a rip program in the mythtv menu structure?

Well, since the Myth Police haven't shown up at my door yet to make me upgrade, I rely on the simplest step of not running 0.24, and so retain use of the myth ripper. Since I never do "iso rips" but only "perfect rips" the whole "iso vs. storage group" kerfluffle never affected me. The myth ripper, when it works, is by far the most convenient solution, particularly with subtitled or multiple soundtrack DVDs, even though the myth ripper frequently produces unusable frame indexes that have to be rebuilt from the command line using mythtranscode. 

However, for the 30% or so of DVDs that the myth ripper can't handle, I tend to rely on Handbrake (or HandbrakeCLI), VLC, and Thoggen, in that order. Handbrake produces the best, most usable output under the widest range of circumstances, and the CLI version is a bit less CPU hoggish, since the GUI is stripped away. (It might also seem to be fairly readily integratable to the mythtv menu structure, if anyone cared to do so.)

VLC is mostly useful to identify the correct track on Disney/Sony disks, which are then ripped on some other program. VLC can do its own rips, of course, but I've never been able, in turn, to successfully encode VLC output (regardless of wrapper or encoding) onto a DVD backup.  

Thoggen is OK sometimes when other things fail, but the quality of its output is a bit inferior to the other three rippers (even at its maxim quality settings), while (at least in my experience) it makes Handbrake look lightning-fast by comparison. A couple of runs I made with Thoggen took over 20 hours to complete, though in fairness I ended up with pretty good rips.

For what it's worth, the Mythtv wiki recommends Handbrake or VOBcopy in the absence of the myth ripper. I've never tried the second option.

---

