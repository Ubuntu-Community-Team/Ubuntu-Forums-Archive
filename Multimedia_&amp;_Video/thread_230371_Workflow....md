---
title: "Workflow..."
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-08-05
OK, so, have any of you actually sat down to record anything under Linux?

I was going to today, but I don't even know where to begin, really.

I am hoping there is someone here who knows a good workflow to help everyone who doesn't know what to do, to start..

I mean, seq24 is the sequencer I want to use, but it has some pretty annoying bugs, like the first note doesn't sound for some reason. I'm thinking of trying Tutka to see if it is more my style, and more complete...

I like the sounds in ZynAddSubFX, but the problem is that it outputs all sounds in only one stereo output. This means I can't record each synth into ardour in their own stereo channels, and apply further effects and mixing from there. So to resolve this, what do people do? Run a bunch of copies of Zyn? Seems rather silly.

Is there any synth engine that has separate JACK outs for each synth part?

How do you use the JACK transport stuff, so that all software lines up and plays in sync?

I don't know, this kind of stuff really isn't intuitive and needs work, but there isn't much I can do to help out...

---

### Post by philipacamaniac on 2006-08-06
> **dolson said:**
> OK, so, have any of you actually sat down to record anything under Linux?

Nothing major yet, no.

> **dolson said:**
> 
I mean, seq24 is the sequencer I want to use, but it has some pretty annoying bugs, like the first note doesn't sound for some reason. I'm thinking of trying Tutka to see if it is more my style, and more complete...

Agreed, seq24 seems pretty spartan. I just compiled the most recent version, so now at least I have seq24 connections in qjackctl. However, it is seemingly impossible to record live (using a real keyboard or the vkeybd) into Seq24. Programming it by hand is the only thing I can get to work well.

> **dolson said:**
> I like the sounds in ZynAddSubFX, but the problem is that it outputs all sounds in only one stereo output. This means I can't record each synth into ardour in their own stereo channels, and apply further effects and mixing from there. So to resolve this, what do people do? Run a bunch of copies of Zyn? Seems rather silly.

You can run the single copy of Zyn and set mix volumes within Zyn. Just save your work as the same name of the song/project your working on. I've had to do similar things like that when using Reason with Cubase (volume control in Reason for each synth track, and a combined output bus in Cubase).

> **dolson said:**
>  Is there any synth engine that has separate JACK outs for each synth part?

Qsynth does let you run multiple engines, each with a separate stereo output that appears in qjackctl. But qsynth is for soundfonts.

> **dolson said:**
> 
How do you use the JACK transport stuff, so that all software lines up and plays in sync?

I've managed to configure seq24, hydrogen, and ardour so that they all allow JACK to be the transport master. I can play, pause and rewind from any of the apps, or from qjackctl, and they all play nicely. I haven't really worked on a project yet, though.

I've basically figured out how to make it all play nicely (except for seq24 who doesn't like to record properly from the MIDI bus - suggestions, anyone?). What is lacking is something like one of my two suggestions in previous threads:

1) A project session manager (like LASH) that will open and save all the appropriate apps and settings for any particular project.

2. A Reason-like application (Treason, anyone?) that puts the hydrogen computer, zynaddsubfx, ams, amsynth, qsynth, qsampler and specimen (and possibly mx44) into a rack with a JACK mixer and the ability to adjust JACK connections graphically from within the program. I guess that would also require an ardour transport rack unit to make things really easy, and LADPSA effects rack units as well.

In terms of workflow, on my Windows machine, I typically create a drum track first in Reason, and then a bass line, and then start adding other cool stuff. If it is a techno/electronica song, I do all the work in Reason. If it is pop/rock, I finish up all the drums/bass/synth/samples and then do the guitars and vocals in Cubase or Sonar. To translate this to Linux, first map out your song in Hydrogen, then sequence a bass line into Seq24 (or something better) and pipe it through Zyn, then start adding on the cool stuff as you go along. Here's where Seq24 gets confusing in the workflow, and its why I'm also looking for new sequencer. At any point, you can start an Ardour session, and patch Hydrogen and each synth/sampler to separate busses (at this point disconnecting them from a direct connection to your soundcard outs). In theory, you should be able to start recording stuff in realtime in Ardour, with your backing tracks playing along in sync. I haven't tried this step yet, so I'll report back.

---

### Post by philipacamaniac on 2006-08-06
[http://dino.nongnu.org/](http://dino.nongnu.org/)

This looks like a promising replacement for seq24. I looked at Tutka, but that's a tracker (definitely not my style).

EDIT: Dino apparently requires JACK SVN, so this should be interesting. It also requires LASH, so I guess it has LASH support.

---

### Post by dolson on 2006-08-06
Thanks for your reply.

Yeah, I added Dino to the list of apps not yet in Debian or Ubuntu a couple days ago. It looks really great, but it's very unlikely to hit Edgy in time... Who knows when JACK will make a new release with MIDI support out, which is basically what it needs.

I compiled Tutka, but haven't tried it yet. I like trackers, and this one seems to support JACK and only does the job of tracking and sequencing, fully using JACK and ALSA for MIDI routing. It might be what I need.

So, you lay out drums in Hydrogen first? Why not in Seq24? Are you using the live mode or song mode of Seq24? I can record in on Seq24 no problem, just set it in the options, and then enable the input in the Edit window for one of the patterns. But it's still flakey for me.. Why it cuts off the first note and the last note is beyond me.

I may end up sequencing everything externally, because nothing I've found works as well as my RM1x does.

I don't like the idea of having all of my instruments on a single track into ardour... I want to be able to remix them and pan them as I see fit, as well as apply compression and such to them, all in ardour. This is also the reason I wanted to move away from my hardware in the first place, because mixing once on the way into the digital recorder is just not a good idea.

Sometimes it's great how Linux and Unixy apps work, and JACK being the glue that it is, but I'm seeing now that it's actually pretty annoying when you try to use it for something productive...

---

### Post by philipacamaniac on 2006-08-06
Okay, so Dino looks cool, but it's a hopeless cause. Compiling the newer jack pretty much requires that you recompile everything that requires jack. Unless, maybe someone can tell me how to compile jackd and libjack separately? Because the SVN source compiles it all together. Which of course causes major debian package breakage.

I like the Hydrogen sequencer a lot. I wish it had a piano roll so I could do all my sequencing in Hydrogen. EDIT: I think I'm using live mode in Seq24. I'll keep fiddling.

All your instruments can have separate tracks/busses in ardour. Just like in Reason, you pretty much have to create new instances of any synth for multiple instruments with separate outputs. Qsynth and ams have menu options for this, and for Zyn, I think you just have to open a new instance manually for any different instrument output you want.

---

### Post by kellogs on 2006-08-06
> So, you lay out drums in Hydrogen first? Why not in Seq24? Are you using the live mode or song mode of Seq24? I can record in on Seq24 no problem, just set it in the options, and then enable the input in the Edit window for one of the patterns.

I don't need even to put a hydrogen pattern in seq24. the good thing of the independence jack gives is that you can create the drum line in hydrogen, and it will go at its own peace. I usually just have the first bars empty in hydrogen, so I put in the same BMP in both programs, and when I want rythm to start seq24 and hydrogen are already connected by jack, no matter where rythm starts/loops, this way I can even record the drum line as an audio sample. 

I use song mode, BTW, live mode havent got much use yet for me,(i've got yet to buy a midi cable for powerpc, its an spdif input, so pc ones are not valid here.)

---

### Post by metasymbol on 2006-08-06
> **dolson said:**
> OK, so, have any of you actually sat down to record anything under Linux?

I do so....
> **dolson said:**
> 
I was going to today, but I don't even know where to begin, really.


Surprising me, thought you know how to work with that stuff...

> **dolson said:**
> 
I am hoping there is someone here who knows a good workflow to help everyone who doesn't know what to do, to start..

I mean, seq24 is the sequencer I want to use, but it has some pretty annoying bugs, like the first note doesn't sound for some reason. I'm thinking of trying Tutka to see if it is more my style, and more complete...

seq24 is a nice and stable and bugfree minisequencer, the ideal "missing midi part" for Ardour (in my experience). There is a nice (GERMAN!!!) tutorial for seq24 - [http://www.audio4linux.de/wiki/index.php/Seq24](http://www.audio4linux.de/wiki/index.php/Seq24)
> **dolson said:**
> 
I like the sounds in ZynAddSubFX, but the problem is that it outputs all sounds in only one stereo output. This means I can't record each synth into ardour in their own stereo channels, and apply further effects and mixing from there. So to resolve this, what do people do? Run a bunch of copies of Zyn? Seems rather silly.

Yeah, only a stereo output for a multitimbral synth is not a professionel solution... The best you can do is to make your setup with any midisequencer you like and if you want so record your voices, so mute the majority of voices in zynadd - and record (bounce) one voice after the other. 


> **dolson said:**
> 
Is there any synth engine that has separate JACK outs for each synth part?


You can patch stuff like that with OM-gtk (dssi synths) or AlsaModular. But surly  this will be no substitute for the sound of zynadd.

> **dolson said:**
> 
How do you use the JACK transport stuff, so that all software lines up and plays in sync?


Just make in the setup dialog of the apps one as a jack master (ec seq24) and the others as clients - it is very easy, don't worry.

> **dolson said:**
> 
I don't know, this kind of stuff really isn't intuitive and needs work, but there isn't much I can do to help out...
 Yeah produce music with audiolinux is only for very experienced users with endless patience. It is helpfull to come from the windows plattform with a modular enviroment like Plogue Bidule or eXT, because on audiolinux are a lots of traps and missing documentation.

I know how to work with all this stuff but I decided only to use ardour for some (live)recordings and postproduction and make virtual composition again with windows/eXT. Linux works for me in a way but it eats a lots of creative energy (patching, routing, crashes, no total recall) so that I was not able to make one piece of music in one year.

Play around with audioLinux is ok that means open zynadd or h2 and make a little music without worry about the production of music. But Im a professionel producer I need much more the what linux giving me now. But this will hopefully change  - maybe in 2016 we can produce with ardour a whole song ;) (sounds like from a sience fiction).

---

### Post by philipacamaniac on 2006-08-06
You know, if Ardour had MIDI sequencing built in, then that would simplify things a ton. Your synths/samplers would just act essentially as plugins, which is no different to the workflow in Cubase or Sonar. Take a gander at this: [http://code.google.com/soc/ardour/appinfo.html?csaid=C321119C45B9B453](http://code.google.com/soc/ardour/appinfo.html?csaid=C321119C45B9B453)

Hmm... I feel the need to produce a full song just as a proof of concept that all this can be done.

---

### Post by damu on 2006-08-06
Yep, workflow, efficiency are essential in audio prod, and I think can be achieved on a GNU/linux system.
[Studio-to-go]("http://www.ferventsoftware.com") seems to me the only linux system so far with which one can intend do to "professional audio production" out of the box(well, I have been doing it). Why?

Because, if you are not a programmer and that you want to produce music, it is the only one I can think of that just works, with VST support, including in Rosegarden. This distro has been put together by the creators of Rosegarden...
Within less than an hour you have an audio system working + a live cd that can be used in any external environnement (workshops, recording sessions, etc)..

The support is just great, and the guys behind STG would do anything to help you if needed - that's another major point when you intend to do professionnal work. I once had an issue with Ardour, and within few hours, they delivered an update and saved my day...I could deliver the audio track in time for a video soundtrack! I tested the support of some other  companies well known in the Mac/Win environnement for audio, and none of them has answered so quickly and efficiently.

Rosegarden, and Ardour synced through jack is the winning team for me. I open all the synths, samplers and VST in Rosegarden (except these marvellous amp simulators for guitar that I jack directly in Ardour). I use Hydrogen at the initial mockup stage. As soon as I can , I import the hydrogen session in Rosegarden ,and record the rest of percs, breaks and so on in Rosegarden.
All tracks are then imported as audio tracks in Ardour before the final mix. Jamin is just an amazing tool for mastering, which result is exported in Audacity in 32 bit.

 
STG also has its bad points :
 - for anything else than audio prod, the knoopix based system is out of date .It is an issue for me...nightmare to connect on the net, and so on.I would much prefer STG to be based on an up to date Dapper, and not to have the need of 3 systems on my machine (Ubuntu for everything else, STG for audio prod, WinXP for the adobe authoring tools)! 

 - even though, it is mostly open source (except some parts which allow the vst support), it is far from obvious to me to find the ways to update an application, and because it has been compiled so that it would be "audio efficient", you might break something when you try to update an app. There   is no way you can update the sytem without breaking it (real time kernel...) and there is nothing like "add/remove programs" or an easy to use synaptic. Therefore, you can't tweak and update anything  you want, which is fine, as it's not the purpose of STG.
For audio apps, the STG team offers regular updates though, and if you ask them for an app that has not been included or which could benefit of an update, they usually try to provide a .deb. 

You can download a live demo cd for free (you won't be able to save, etc) and buy the download version for 40 £ (60 euros)...a price which I think doesn't reflect the quality of their product ...
These guys have put so much effort for years to developp audio tools on GNU Linux! I whish they could all(with the guys of 64Studio and Musix ...think twice...why not?) work on a system  to developp "the" audio system on linux (the dream team to developp Ubuntu Studio ;) )....that would hopefully create a big buzz which would allow them to create an eco-system: They could sell add-ons (VST support, commercial apps, remote control, etc) , professionnal support...

---

### Post by izle on 2006-08-06
I just tried Studio-to-go!'s demo, it looks awesome, well I mean it looks just like my system! Except for the support team, I don't see the point of buying a distro that you can build by yourself for free (ok I admit you need a bit of patience). 
I am used to gnome environment, and recently to fluxbox to optimize RAM, It seems however that the kde panel is well designed to manage all the software you have to run, and the alsa settings docked on the panel is just really useful, does this applet exist for gnome panel?

---

### Post by christhemonkey on 2006-08-06
The whole aim of [www.ubuntustudio.com](www.ubuntustudio.com) is to try and help make ubuntu easier for music production.
You should check it out!
Lots of very helpful things.

</plug> :D

---

### Post by huwshimi on 2006-08-07
So far I have recorded an album, an EP and a whole pile of singles under linux for various artists. But they have been done under Demudi.
I have mostly used Ardour, but have dabbled with a few other pieces of software, I'm learning to use Jamin at the moment.

So far linux has been more than fine for recording and production (mastering will be good too when I learn Jamin). My recordings have been played in pubs and clubs and I haven't heard any complaints yet.

I guess a thankyou goes out to those who have made all this possible.

Cheers.

---

### Post by zettberlin on 2006-08-07
My workflow has changed to the one i have in Linux now since i abandoned the all-in-one Steinbergstuff (NUENDO) in 2001 or so and switched to Orion and Samplitude and then to Linux.

Today i do like this:

1.) check, what musical idea i/my collegues, clients etc.  have - what sounds will we want to have, from what will our recording grow (sequencer/synth stuff, looped samples, or indeed instruments played by people...)

2.) record/construct a basis/demo/pilot - drop a simple drumloop into ardour, record guitars/voc OR clicketyclick a sequence in seq24 to be orchestrated with Zynadd and/or specimen, ams you name it!, record this with qarecord, OR compose more complex synthstuff with MUSE - cut loops with mhw or rezound and arrange the snipplets in ardour

3.)(everything in ardour) listen to the demo, destroy everything unneeded, add ideas, rerecord good stuff, add/manipulate samples/loops.

4.) polish the mix review mixes, cut it, jaminize, oggify, upload.

All this works very well in linux, i do not shed a single tear for Cubase or Nuendo - i´d like to have something more compact for seqencerstuff sometimes and i agree with metasymbol about the need for total recall but in the End i would not trade linuxaudio for ANYTHING :-)

---

### Post by dolson on 2006-08-07
> **christhemonkey said:**
> The whole aim of [www.ubuntustudio.com](www.ubuntustudio.com) is to try and help make ubuntu easier for music production.
You should check it out!
Lots of very helpful things.

</plug> :D

Uhh... I am the owner of that site, and I am the one who put 95% of the content there. I think I would not ask for help if I already know the info... And the site has NO content about actually USING the system, aside from connecting a couple apps together.

--

The "workflow" I am seeking is how to create a full song with Linux. Just read my first post in here.

Most people seem to just use one app or two apps, and don't actually create music, they simply record it - and that is fine too, but in that regard, you really don't need JACK, you don't need a sequencer, you don't need anything but ardour, Audacity, or whatever you choose to use.

I HAVE recorded a ton of songs with Linux, but I have not created any music under Linux yet. I use all my own external hardware and gear. As I have already said, I want to move away from this.

And as it stands now, I don't see it being possible.

---

### Post by philipacamaniac on 2006-08-07
> **dolson said:**
> Uhh... I am the owner of that site, and I am the one who put 95% of the content there. I think I would not ask for help if I already know the info... And the site has NO content about actually USING the system, aside from connecting a couple apps together.

LOL... LOL... ](*,):p:-k:confused:

Very true. But I think as time allows, there should be more content made available about actually using the system (tutorials, documentation, etc.), and that would be useful. Maybe I can help in that area, as I'm getting used to this whole disconnected Linux way of doing things.

---

### Post by huwshimi on 2006-08-07
> **dolson said:**
> OK, so, have any of you actually sat down to record anything under Linux?

Oh, sorry you said record... and I didn't realise what you were getting at.

---

### Post by zettberlin on 2006-08-07
> **dolson said:**
> 
And as it stands now, I don't see it being possible.

look twice ;-)

The workflow i use, if i do NOT record via microphone into Ardour is indeed heavily influenced by the extreme Modularity of Linuxaudio.

If i want to build a track from scratch i first build sounds either by cutting and manipulating samples with rezound and/or by fiddeling the knobs of Zynadd and ams.

As i do so i use seq24 to hear the sounds, i make - sometimes i find sequences, i really like and i record them with qarecord and cut loops from such recordings to be arranged in Ardour. 

More often i use Muse to play the synths and the sampler, because there is more control about longer compositions in Muse and you can easily add FX to synths.
Later on i can sync Muse and Ardour via jack to bring stuff together.

If i just need Rhythm i use Hydrogen also: i got an Alesis SR16 Drummachine with Pads but i never use it, as i prefer to work with H2...

Sure it all ends up with arranging snipplets in ardour but those snipplets are made in Linux also and i did a lot of tracks that do not contain any conventionally recorded stuff.

So again: if you look for a workflow to create music completely within a Linuxcomputer you need to accept the modularity: there is no all-in-one-App ready for primetime for Linux that i know of - use small specialized tools and you can get easily beyond 90% of the stuff that can be clicked together in cubase ;-)

best regards
Z

---

### Post by dolson on 2006-08-09
zettberlin,

Can you explain how exactly you arrange samples in Ardour? I mean, won't you run into issues just cutting and pasting random clips? Timing is critical, I would think, and it is going to sound weird if your timing is not right.

I wasn't aware that it would be easy to use small samples in Ardour.. How do you get them lined up and repeating nicely and stuff?

Is there a good tutorial for Ardour somewhere? The documentation was pretty... eh, sparse the last time I looked at it (which wasn't long ago).

You know what I would really love to see is downloadable video tutorials... We could even host them on Google Video (or YouTube, but YouTube doesn't allow downloads). I guess what we need is a screen capture tool that works well and will not interfere with JACK apps... Anyhow, that's for the future.

---

### Post by zettberlin on 2006-08-09
> **dolson said:**
> zettberlin,

Can you explain how exactly you arrange samples in Ardour? .

> **dolson said:**
> 
How do you get them lined up and repeating nicely and stuff?
.

1.) I try to keep the timings of the samples into control, that is: if I record loops from hydrogen, seq24 or Muse I have the bpm into the filename such as: rumpelbeat_112bpm.wav, basssong_86bpm.wav and so on. I f i cut stuff, that is not from a sequencer, I try to find out the timing using a metronome.

2.) The samples I import into ardourprojects are normally longer than needed (diskspace is not really an issue) so i can use longer chunks, that are comfortably looped with a sequencerprog.

3.) I often use a simple drumtrack as a pilot to align other samples - normally this pilot is muted/erased, if the track has its intended structure.

Practically I arrange the samples by using the 2 cursorbars to align stuff (if two loops have harmonizing bpm-speed such as 120bpm and 60bpm or if both have the same speed, they can easily be aligned by simply having an emphasized beat synchonized). I also use the looprange-function of ardour to align stuff and to find loopable chunks of regions by letting the loop play and dragging regions on the timeline whithin the looprange.
To achive the needed flexibility the sample should not bee too short. If you want to use a single bassdrumsample the sample should run at about 20bpm if it is uncut. You can than raise the speed by simply shortening the region to the looprange that loops at the timing you need. Than rightclick -> duplicate to have the loop repeated. This method is not as comfortable as in a real sequencer but it works very well and it is much more flexible then a beatassistent or stuff like that.
One can also work with "chunks", that are something like meta-regions but i never felt that comfortable with this method / was allways too lazy to learn how to work with it ;-).

I will try to build an illustrated tutorial for this method within the next few days. Thank you for pointing me to the need of such a tutorial - i tend to work better/faster if someone ask me to do a certain thing ;-) :-)

---

### Post by philipacamaniac on 2006-08-10
> **dolson said:**
> You know what I would really love to see is downloadable video tutorials... We could even host them on Google Video (or YouTube, but YouTube doesn't allow downloads). I guess what we need is a screen capture tool that works well and will not interfere with JACK apps... Anyhow, that's for the future.

ScreenKast / captorials.com is for that very purpose. I've never done it, but that is what it is for, and they have Dapper packages available.

Oh, and YouTube vids can be download with the VideoDownloader Firefox extension, and then converted from flv to mpg/avi with ffmpeg.

---

### Post by dolson on 2006-09-11
I wrote a tutorial for seq24, Hydrogen, and ZynAddSubFX (and Virtual Keyboard). I posted a thread here announcing such, but wanted to reply to this thread I started for some closure.

It is indeed possible to make music in Linux. And it's fun, and will be even more fun once I install Edgy.

---

### Post by zettberlin on 2006-09-11
> **dolson said:**
> 
It is indeed possible to make music in Linux. And it's fun, and will be even more fun once I install Edgy.

Do you know details about improvements in edgy right now? 

I tried the recent beta as a live CD and the first impressions are  hmmmm mixed:

quite recent versions of muse, jack, rosegarden and specimen but ardour is still only 0.9.2. The betaCD comes with a SMP-Kernel, i did not find someone/some website right now that could give detailed info regarding PREEMPT in edgys stock-kernel.

---

### Post by dolson on 2006-09-12
I use Edgy at work, and I also used it to write my seq24 tutorial. It worked great, and I had no Xruns, although I wasn't doing much intense work. I will try and check the kernel config tomorrow. I didn't have time to install it on my main studio PC yet.

Ubuntu generally only follows Debian for packages, which is why we have Ardour 0.99.2 and seq24 0.8.6. We're only X.X.1 releases behind for each app, which isn't that bad, really. But the more people who package software for Ubuntu or Debian, then the quicker these apps can get updated.

---

