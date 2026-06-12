---
title: "Help with ALSA and SiS 7012??"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by rondamato on 2007-11-18
Hello all,

I am a kinda-Ubuntu newbie running Gutsy.  I am running it on a crappy garbage-picked HP Sempron 3100 with 2GB.  My God though, it out-races my brother's dual-core Pentium at some tasks.  All hail Ubuntu!  

I have been playing around with it for a few years now (I work mostly on Solaris and HP/UX due to my job and have to "find time" to run Ubuntu at home because running anything but XP/Hummingbird on our desktops at work is verboten).

This HP has an SiS 7012 soundcard with a Realtek ALC658D chipset--and like most consumer-level HPs (no offense to anyone) it isn't that good and has integrated everything on the MoBo (which drives me nuts).

Here's my problem: Recently, the right channel of my soundcard just up and quit.  I removed all mixer apps using "Add/Remove Apps" and verified that the L&R channels are both cranked up with alsamixer run at the shell thru KConsole.  You can slightly hear the right channel if it is turned up all the way in the mixer.  The left comes thru loud and clear like "it's suppossed to."

To test cables,  I plugged headphones directly into the "speaker out" of the card--same story.  No right channel.  If I turn the left all the way down and CRANK the right I can hear it very softly...and I AM hearing the right channel--I'm playing a test CD I made that alternately puts tones out the left channel and then the right channel.  Just telling you this so you know that I'm not hearing "crosstalk."  

What's strange is that a few days ago this card worked fine I'm pretty sure.  Now, like any newbie I installed/tried many sound packages since then, but have removed all of them since in search of a solution to this problem.  Same problem.  I verified that no channels are muted or turned down, as I said.

Of course, buying a cheap PCI soundcard would probably help, but (get this) this $#%$ HP will NOT go into BIOS no matter what so I can disable the onboard sound.  I can press F1 all day at POST--it ignores it.  I have tried to work around this MANY different ways (I've been a PC tech for 25 years now-God, I'm old...)--the machine will NOT go into BIOS.  I even had a 20-year HP PC tech try it and he gave up after an hour saying "Wow, never seen something like that..."

But I digress.  I just want my right channel back.  Can anyone think of something I might be doing wrong??  I know, the soundcard's right-channel amp may have just fried but this hardly ever happens--and I never touch the box anyways once I have it set up ruling out (probably) static-shocking the right-channel amp.  Can I just drop in a PCI soundcard w/o disabling the o/b sound?  Will Ubuntu "see" it?  I am VERY hazy on how Ubuntu "detects" new hardware and assigns resources to them/it so I want to ask an expert this question if at all possible.  I have a NVidia 5500 I just "dropped in" despite the on-board video and, after a driver load to correct resolution, Ubuntu had no trouble using it instead of the OBV.  Is this the case with the OB sound as well, maybe?  Oh, I hope so....

Any help would be greatly appreciated.  Toss me your ideas!  The Ubuntu community has helped me so much!  I just wish that I could give back more.  Perhaps a few more years with this wonderful OS and _I_ can help people like me!  We run the best OS in the Universe at least!

Thank y'all for reading this, and have a great day.  ANY help is welcome.

DoctorRon
Chicago, IL
<rondamato@gmail.com>
------------
v7.10 Gutsy Gibbon 32-bit/Gnome
HP Pavillion (something)
AMD Sempron 3100 w/2GB DDR 533

---

### Post by rondamato on 2007-11-19
Hey,

Just thought I'd update you folks on this....

After a number of great suggestions in previous posts, I tried running amixer (duh).  It reports that my output is MONO!  I then ran alsamixer--all was good there.  Checked everywhere--no channels muted.  Uninstalled all "other" volume/mixer controls so that alsamixer was the only one left.  All looks good there.  Still only left channel though.

So....I d/led the Realtek drivers and compiled.  Result?  Still sound only on left channel, but for some reason it sounds WAY better.  Go figure.

Oh Ubuntu, I'll crack your secrets someday!

(The Good) DoctorRon
Chicago, IL
<rondamato@gmail.com>
v7.10 Gutsy Gibbon 32-bit/Gnome

---

