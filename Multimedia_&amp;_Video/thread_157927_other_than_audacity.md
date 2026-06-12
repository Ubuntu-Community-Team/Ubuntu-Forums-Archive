---
title: "other than audacity??"
date: 2006-04-10
forum: Multimedia &amp; Video
---

### Post by hezral on 2006-04-10
hi.is there any other app other than audacity to edit audio files? audacity is good but its not pleasing to the eyes :) 

thanks

---

### Post by damu on 2006-04-10
Audacity is for me probably the best audio editor in the open source world.
You can also use [Rezound]("http://rezound.sourceforge.net/") ...it might fit more with youreye Candy criteria

If you want to go further in sound editing, the professionnal solution is Ardour (multitrack recorder , and full automation of the mix). To get it working, you will need Jack, a low latency kernel, etc...Ubuntu is not yet the bets platform for that. You could have a look at the live-cd [Musix]("http://www.musix.org.ar/en/index.html") (free) or the state to the art solution [Studio-to-go]("http://www.studio-to-go.com/")

---

### Post by hezral on 2006-04-10
thanks for the info.
i do use audacity but was just wondering if there is any other alternatives in the open source world.
i'll check the ones you mentioned. thanks again.

---

### Post by stairwayoflight on 2006-04-27
[QUOTE=damu]If you want to go further in sound editing, the professionnal solution is Ardour (multitrack recorder , and full automation of the mix). To get it working, you will need Jack, a low latency kernel, etc...Ubuntu is not yet the bets platform for that. You could have a look at the live-cd [Musix]("http://www.musix.org.ar/en/index.html") (free) or the state to the art solution [Studio-to-go]("http://www.studio-to-go.com/")[/QUOTE]

umm.. sorry i don't understand.. ubuntu is not the best platform for *what?*
jack, the low-latency kernel, or both?

i'm trying out the demudi kernel, to see how it goes. just tryin to figure out my best options.

---

### Post by dolson on 2006-04-27
What damu means is that out of the box, Ubuntu is not set up for realtime-access (well, Dapper is), nor with a low-latency/realtime/completely pre-emptible kernel.

That will change in time, though. And if you get your hands dirty, you should be able to get it all up to par.

---

### Post by Iandefor on 2006-05-11
[quote=hezral]hi.is there any other app other than audacity to edit audio files? audacity is good but its not pleasing to the eyes :) 

thanks[/quote] Yeah, audacity is still compiled against the gtk+ 1 libraries. Looks horrible :(. 

I believe there are plans to change this in future releases, but I I wouldn't count on it being soon.

---

### Post by samoht on 2006-05-12
I'm using "sweep" at the moment. It's gtk2 and uses alsa. pretty cool.
[http://www.metadecks.org/software/sweep/](http://www.metadecks.org/software/sweep/)
Sweep is available in the universe-repo.

---

### Post by BobSongs on 2006-06-18
It's funny. Audacity is one of the software packages I used in order to prepare for my eventual plunge into Linux. So was Firefox, OpenOffice, Inkscape, and Apache2. So the move to Linux wasn't that difficult.

Oddly enough the interface in Windows is almost identical. So I'm very comfortable with the look. My problem is with multi-tracking. It works fine in Windows but it's not quite functioning yet in Ubuntu. Perhaps other Linux kernels allow for playback while recording. But so far Ubuntu doesn't.

However, I did find a small trick to be able to record a second track (say, from a microphone) in Ubuntu. This is just a "work-around", but it's better than nothing. And since I record narration I like to be able to say a phrase in a new track and then paste the correction into the original track. This is how to do it.

In Audacity:[INDENT]**Edit -> Preferences**[/INDENT] Make sure "Play other tracks while recording new ones" and "Software Playthrough" are **unchecked**. You want those features **off**.

Now, from the main menu (I'm speaking of the Ubuntu Gnome menu) click:[INDENT]**System -> Preferences -> Sound**[/INDENT] Make sure "Enable software sound mixing" is **unchecked**. You want this feature off as well.
[INDENT]**Note:** this is the feature that allows several applications to use the system sound at the same time, like XMMS and Audacity, for example. In this state Audacity can use the sound resources without sharing. Other applications will complain about the lack of sound when fired up. So you use this setting only temporarily.[/INDENT] To restore your system open the Sound applet again and check "Enable software sound mixing" and you're back to normal sound again.

Oh yeah, if you open another application that uses sound while Audacity is running Audacity stops recording and playing sound. So it's a bit of a system trade-off.

---

### Post by dolson on 2006-06-19
That all depends on your sound card. I use Creative Audigy2 ZS and SB Live! 5.1 cards, and they both work fine without doing any of those steps. All of the music I recorded on my site (except for the track called Originem) was done in Audacity under Linux (Debian or Ubuntu, and one track was done in Mandrake years ago).

---

### Post by BobSongs on 2006-06-19
Cool. Well, I'll be upgrading to a new machine soon. The current one I have appears, by that description, to not be powerful enough. That and I'm running a Celeron. But with the upgrade to an AMD 64 with the latest/greatest SoundBlaster card things would appear to be hopeful! Thanks, dolson. I'd pretty much given up hope on Ubuntu for sound. :)

---

### Post by zettberlin on 2006-06-19
If you run jackd by default, mhwavedit may be a fine  editor as well, i do not know any other destructive editor that interacts that perfectly whith jackd:

[https://gna.org/projects/mhwaveedit/](https://gna.org/projects/mhwaveedit/)

rezound is great too if it comes to cut samples really comfortable and exact. And, if one does not fear to ride a big beast: Ardour can serve quite good as an editor also, yet it needs lots of diskspace and is not that comfortable if you want to save intermediate results often.

---

### Post by BobSongs on 2006-06-19
Thanks for the tip on **mhWaveEdit.** Just thought I'd note that the following applications are located in the Dapper Drake repositories:[LIST]
[*]mhWaveEdit
[*]Sweep (not bad at all!)
[*]Rezound
[*]Ardour[/LIST]

---

### Post by BobSongs on 2006-06-19
Dolson;

Are you saying that in Ubuntu when Audacity's preferences are set to play other tracks while recording a new one you've experienced no garbled second track?

I've had this difficulty with the SoundBlaster Live! card on my Pentium III machine. I was wondering if this was no longer a problem with ESD enabled.

Thanks.

---

### Post by dolson on 2006-06-19
Bob,

I tested this not too long ago, and I do have that same issue now. For some reason, this was introduced into Ubuntu only, as on Debian I don't get that issue... Not sure why, but I have recorded stuff on Hoary and Breezy I think without issues.

Note that the garbled track turns out OK for me if I bear with it and record it anyhow. Playing back both tracks turns out OK. Weird... Should maybe open a bug to get this fixed in Edgy and backported or put into updates.

---

### Post by manfo on 2006-06-20
[QUOTE=dolson]I tested this not too long ago, and I do have that same issue now. For some reason, this was introduced into Ubuntu only, as on Debian I don't get that issue... Not sure why, but I have recorded stuff on Hoary and Breezy I think without issues.

Note that the garbled track turns out OK for me if I bear with it and record it anyhow. Playing back both tracks turns out OK. Weird... [/QUOTE]

Same problem to me. I have this issue with Audacity since I'm on Dapper: AMD64 Breezy worked fine...

Bye
.m

---

### Post by BobSongs on 2006-06-21
**Cool!!** I'm pricing a new system. I broke my last one.

I'm opting for the AMD Athlon64 x2 4400+ Dual-Core 2.20GHz 64-bit Processor. So that should deal with the ability to record multiple tracks in Audacity.

Anyone have a suggestion as far as soundcard? Or what soundcard **not** to buy. ;)

---

### Post by dolson on 2006-06-23
Well, if you need a cheap sound card, go with an Audigy2 ZS or a SB Live! 5.1. If you have cash to spend, go with an RME Hammerfall... Check the hardware section on the wiki for the model used by Rufus for a good one.

Just my recommendations, I have little experience with anything else.

---

### Post by GuitarHero on 2006-06-27
Linux isnt the most ideal reconrding OS simply because the most widely used software isnt supported by it.

---

### Post by dolson on 2006-06-28
[QUOTE=GuitarHero]Linux isnt the most ideal reconrding OS simply because the most widely used software isnt supported by it.[/QUOTE]
I think that is pretty irrelevant. How do you ever expect the situation to get any better if nobody uses the OS?

---

