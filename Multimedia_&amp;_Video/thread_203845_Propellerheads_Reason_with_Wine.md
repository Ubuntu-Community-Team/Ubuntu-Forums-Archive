---
title: "Propellerheads Reason with Wine"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by EPOX123 on 2006-06-26
Will Reason work with Wine?:-k 
If it does, can some one make an easy tutorial?:-k

---

### Post by smartalecks on 2006-06-26
[http://appdb.winehq.org/appview.php?versionId=2940](http://appdb.winehq.org/appview.php?versionId=2940)

Says that everything but the audio output will work under WINE on Gentoo & SUSE. (So I don't know about Ubuntu).

As for an "easy tutorial," atm almost nothing with WINE is easy :???:

---

### Post by dolson on 2006-06-27
Everything but the most critical part works in Wine.

Sounds like every Windows application, ever, in Wine.

---

### Post by EPOX123 on 2006-06-27
Well i got it to install but crashes after i push ok after the serial .... sucks lol no good audio aplications for linux or graphic apps ether they all have stupid guis and not compatible with any thing.

:( i wish i knew how to program so i could help out these developers.

---

### Post by zettberlin on 2006-06-27
[QUOTE=EPOX123]sucks lol no good audio aplications for linux or graphic apps ether they all have stupid guis and not compatible with any thing.[/QUOTE]

Very cool much more of that - developers like such constructive criticisim :evil: :evil: 

[QUOTE=EPOX123]
:( i wish i knew how to program so i could help out these developers.[/QUOTE]

I wish you could be a littel more like ahmmmm -- specific about what you would like but cannot do with those "no - good aplications" of linux.

As for me: i hated reason the first time i saw it back in 2001 or so. I found it not much more than a stupid toy for people, that would like to make "music"  without investing too much interest in it...

So am i "stupid" also, because I use linux for audio - even though i could choose WnXP or Mac instead ?

---

### Post by Lord Illidan on 2006-06-27
Have you tried Audacity?

---

### Post by dolson on 2006-06-28
You know, you can learn how to program... It's really not that hard if you can follow basic logic and have time to dedicate to it.

I am a Perl programmer by trade, and there's not a lot I can do with Perl to help out...

I do know some C/C++ and GTK+ but not enough to do any good right now. Maybe when I have free time.

Until then, I'll suffer through the "horrible" GUIs.

---

### Post by Cybolic on 2006-07-21
Actually Reason runs fine with the latest Wine (0.9.17), though you have to switch window management to unmanaged.

It installs without a problem, runs without any graphical errors or anything else, and loads anything I throw at it, it's only the perfomance that has problems right now, probably due to some optimisation problems with the Wine audio drivers.

So all in all, I think it won't be long before Reason can run, and be used, just fine under Linux :D

EDIT:

It seems Reason just needs to be unmanaged while probing for the CDs (the startup screen covers the windows otherwise), it runs perfectly after that in managed.

The performance problems seems to be caused by the following repeated messages, and not the audio driver:
```
err:x11drv:X11DRV_CreateBitmap Trying to make bitmap with planes=1, bpp=32
fixme:msg:SendMessageCallbackW callback will not be called
```
...so if someone knows how to fix these two problems, it should run smoothly *hoping*.

Other than that, it seems to work fine with both the OSS and ALSA drivers, with driver emulation both on or off.

EDIT 2:

Yup, minimizing the window while Reason is playing makes it runs perfect (as long as you don't do much else than listen). So it's the x11drv that has some performance issues. Someone fix them :P (I would if I could)

EDIT 3:

I'm compiling CVS Cedega now, to see it they have a better graphics driver for running Reason. I'll post how it went when it's done :)

EDIT 4:

Just like last I tried, the CVS Cedega cvs is down... :/
Does anyone know of a package somewhere?

---

### Post by maku-d on 2006-07-21
This is probably a bit of a newbie question- but what alternatives to reason are there for linux?  

I mean- I've been using ardour through osx for just over a year, great protools replacement, fit nicely into my setup, but no midi so far. Otherwise maybe something like rosegarden? (haven't tried it yet) but then you have to find virtual instruments yeah?  ...and that's probably the only real problem for me...what sort of quality virtual instruments exist?- are they on the same level as reason's? Hydrogen already has the nnxt and redrum drum machines covered, and seeing as reason itself can't record analogue instruments, using something like ardour is a great addition (where you would've used rewire through something like cubase or digital performer previously) but yeah...virtual instrument quality? anyone know? does it compare to reason? Is there some better reason alternative out there?

Complaining about GUI's is crazy in my book, seeing as any gui is crappy when you really think about it...most of the commercial programs we use right now are all equally as crappy/don't make sense,  it's just we've learned to work with them. But yeah...functionality wise if there're equivalents I'd love to give them a run for their money. 

Cool.

---

### Post by Cybolic on 2006-07-26
Wired might be a good place to start.
It's a little tricky to get up and running, but it's quite Reason-ish.

[http://bloodshed.net/wired/?sid=2]("http://bloodshed.net/wired/?sid=2") (the site is currently down though :???:)

About the quality, I've worked with various professional audio equipment, and in my oppinion, the quality we can get in Linux by using several simple plugins together, is comparable to the best expensive software you can find - sure, you might have to tweak it a bit more, but you can achieve the same quality.

---

### Post by dolson on 2006-07-26
There is a fundamental difference between the way that Linux works (the Unixy, modular method) and the way that Windows works (the monolithic, one-app-to-rule-them-all way).

JACK is your friend, and there are lots of apps that work with it. DSSI will hopefully get many more good plugins as people take interest in it, but there are other standalone synths and such that work with it. Once LASH support is built into all of them, we're gonna be in great shape, but until then, it's a bit of a pain to load everything and draw the connections with JACK. Obviously Ardour is a good app to record all of this into, apply LADSPA effects, etc.

However, LMMS might be another app similar to Wired which seems to actually have some development work going on in a regular basis.

---

### Post by metasymbol on 2006-07-27
There is  a full featured commercial modular Midi/Audio sequencer/host announced for Linux -energyXT2 and it coasts 39€. eXT2 shall  featuring jack support, native Linux VST support and it is available yet as eXT 1.4 only for Windows.

-> [http://www.xt-hq.com/](http://www.xt-hq.com/) 
(eXT 1.4 vst version working with big limitations also with wine/dssi-vst)

Some diskussions about:

[LIST][*]FeatureRequests (JACK Support for eXT2/Linux)[/LIST]
[http://www.kvraudio.com/forum/viewtopic.php?t=136704](http://www.kvraudio.com/forum/viewtopic.php?t=136704) 

[LIST][*]Energy XT and Linux Distros Which one works?[/LIST]
[http://www.kvraudio.com/forum/viewtopic.php?t=141075](http://www.kvraudio.com/forum/viewtopic.php?t=141075) 

[LIST][*]Jack frustrations[/LIST]
[http://www.kvraudio.com/forum/viewtopic.php?t=141695](http://www.kvraudio.com/forum/viewtopic.php?t=141695) 

[LIST][*]energyXT on Linux[/LIST]
[http://www.kvraudio.com/forum/viewtopic.php?t=141802](http://www.kvraudio.com/forum/viewtopic.php?t=141802)

If someone really want to use Reason, Garageband, Logic or Cubase it`s the best to **use them on the native plattforms**. An (wine) runtime enviroment never give the same stability. Companys Like Apple or Steinberg will NEVER support Linux.
[B]
But some apps work[/B], like **Reaper** (with some limitations) as a jackclient with wine jack (card "audio" in winecfg, checkbox jack -> inside reaper setup "mme" (not ASIO!!!) giving 40ms latency - alsa midi dosn't work) but you can run every VST plugin inside Reaper!
->[http://www.cockos.com/reaper/](http://www.cockos.com/reaper/)

---

### Post by Cybolic on 2006-07-28
REAPER works perfectly here, I'm even considering using it for my projects :) ...no notacible latency here with the OSS driver.

The latest version of DSSI-VST is working with everything I throw at it too, so I've included it in an attachment - it's a just a simple checkinstall package - since the only other DEB I could find didn't work.

To start the Crystal VSTi with DSSI-VST:
```
vsthost /path/to/VSTi/Crystal.dll
```

Easy, no? :D

---

### Post by spacepluk on 2006-07-28
Hi everybody,

I'm new to the forum although I've been lurking for a long time. I've just seen this thread and just jumped and tried to install my Reason copy. But After installing when I launch the application it keeps asking for the cd's even after I put it in the drive.

Am I missing something??

Thank you very much :)

---

### Post by dolson on 2006-07-28
> **spacepluk said:**
> But After installing when I launch the application it keeps asking for the cd's even after I put it in the drive.

Am I missing something??

Windows?

---

### Post by spacepluk on 2006-07-29
Well,

I've managed to get it working even without "Windows"... I just forgot to configure the cdrom drive in winecfg...

It's working almost perfect except for the excesive cpu consumption and some minor cosmetic flaws. I think that some tweaking in x11drv should fix all the issues. Now heading to the cvs to see if I can help.

Saludossss

---

### Post by metasymbol on 2006-07-29
Reason with wine will NEVER work smooth like on a windows system, because there is no ASIO available for Linux and NEVER will be.

---

### Post by spacepluk on 2006-07-30
We have ALSA drivers and jack. Together they can get lower latencies than ASIO. Audio on linux works pretty well, but it's very hard to configure an audio system properly at the moment.

So it's just a matter of time and collaboration... and not being so negative.

Saludosss

---

### Post by dolson on 2006-07-30
You're right, but that isn't what metasymbol said. He was speaking of Wine and Reason, he didn't say anything about JACK. And he is right about what he said too.

---

### Post by Cybolic on 2006-07-31
He might not be right if a ASIO->Jack->ASIO interface/driver is created ;) Other than that, the latency isn't that bad - sure, it's not fitting for live performance, but for composing, it's fine.

---

### Post by philipacamaniac on 2006-07-31
Regarding comments about alternatives to Reason: if you suggest apps like Audicity, Ardour or Rosegarden, then you simply have no idea what Reason is.

Reason isn't an audio recorder. Heck, it doesn't even really import audio. It is a MIDI sequencer, combined with the most amazing rack of virtually unlimited synths/samplers available in software form. The killer feature of Reason is all the samples that have been included and built for their rack samplers, as well as all the REX loops that have been included. Plus the fact that you can rewire the back of the rack and plug any synth/sampler into anything else, like say, control the attack of your stab techno synth with the snare drum beat coming from the drum machine.

So, the only equiv in Linux would be a sequencer (Seq24?) combined with some crazy synths/samplers/loopers/drum computers. Please point me in the right direction if you can, because I hate booting into Windows.

---

### Post by metasymbol on 2006-08-01
> **philipacamaniac said:**
> Regarding comments about alternatives to Reason: if you suggest apps like Audicity, Ardour or Rosegarden, then you simply have no idea what Reason is.

Thats true. but there is no commercial biz behind audiolinux at the moment, so a very expensive and complete app like "reason" is very far for linux
> **philipacamaniac said:**
> I hate booting into Windows.
Why? Because Bill Gates has more money then Marc Shuttleworth? ;)
If you want play with Reason, Cubase, Ableton Live etc (also evil capitalist biz and propritary software dictators) you must boot windows / mac os x

 Or a play bit with zynadd and seq24 on linux and be satisfied.

---

### Post by drycellbattery on 2006-08-01
Evil proprietary dictators? hehe... I think you have a weird view of things, or just really enjoy the "us" versus "them" thing. Some people want to make a living from developing software which is something they may love. A lot of these companies started small, and got big through success (nice) or just by mergers and takeovers (not so nice). I guess the bigger they get the more beaurucratic and greedy they get. Avid is a good example which owns Digidesign, Maudio, etc.. Microsoft is a brand monster too, not evil per say, it's just that it's the nature of large brand oriented multinationals. A consumer's nature is to consume, not "evil" just not always the best way.

Anyways, back to Reason: I owned it for a while and started out some songs in Reason, but I found myself fiddling with the rack more than composing. Reason is neat and pretty but I was never able to fully work with it. It also crashed alot on my machine (probably more my keyboards usb-midi driver's fault). I've also had stability problems with Reason on a iMac with Pro Tools. The real advantage to Reason is in it's Refills and included sound banks and samples.

If you want a good sampler in linux try linuxsampler and the qsampler gui. It uses the giga format so you'll have to find some free gigas (google Worra's Place) or buy some cd collections.

Hydrogen is a great sample based drum machine, there's a analogue drum machine called Smack which use Om synth to make TR-808 like drum sounds.

Another sample based synth is Fluidsynth which uses soundfonts, it's available as command line, a dssi, or a standalone (qsynth).
There's a DX7 emulator plugin called Hexter you can try out. The DX7 used FM synthesis which the Subtractor also uses.

The best Dssi plugin may be whysynth but you'll have to compile that yourself (it's not hard). It uses a mix of synth techniques and I think it layers them. I think dssi plugins can reckognize midi messages but am not sure.

Zynaddsubfx can make some wonderful sounds and effects, superior to Reason in my opinion. However, it's interface is difficult to understand at first and the controls can't be mapped to a controller. Great for pad sounds though.

Alsamodularsynth and Om synth are modular synths and can make some nice analog sounds.

Amsynth is another good analog sounding synth with simple controls, the interface is choppy but the newer version coming out looks better. I hope he makes a dssi of it in the future.

I'm going to look into getting some VSTi s working. Check out the Greenoak Crystal synth, try looking in google or the KVR forum for it. It's free and can compete with plugins like Absynth. I beleive someone got it working in linux with FST.

So far there's nothing like the REX player, however there is freecycle for beatmapping. Ardour will be able to beat map in the future, perhaps as soon as this fall.

I really liked the patching a Reason synth filter to a sequencer CV, I hope that can be done in Linux now or in the future.

Give LMMS or Wired a try but they are both early in developement. LMMS looks great but has no effects yet :( .

---

### Post by philipacamaniac on 2006-08-04
I say I hate booting into Windows because I don't like Windows. I hate Windows. It has nothing to do with Mr. Gates. I was a Windows Network Administrator for 4 years; I have every right to hate using Windows. I feel more comfortable in Linux.

Anyway, see attached screenshot for a Ghetto Reason. It's just seq24, zynaddsubfx, specimen, and hydrogen open and ready to go. I didn't even test to see if seq24 could control zynaddsubfx (I'm sure it can) or hydrogen (I'm not sure about that). But even then, I run into the same problem as to why I'm running Photoshop in Wine, rather than using GIMP for every project. Interface, usability, and features.

Not trying to start a war. I wish I was a strong developer, so I could just create this killer app myself. All the dirty work has been done already (analog synths, wavetable synths, samplers, sequencers, drum computers). It's now a matter of creating a new frontend gui that can use all those engines together and make it look good and work well.

---

### Post by kellogs on 2006-08-04
> I didn't even test to see if seq24 could control zynaddsubfx (I'm sure it can) or hydrogen (I'm not sure about that).

yes, just openup jack, go to seq24 and on the last section in the preferences  enable jack master, and press connect. now in seq24 create one square pattern (right click-new) and then right click to assign a port/connection (you can select available jack connections).

I just put zynnadsubfx or amsynth connected to seq24. then in hydrogen put same BMP as seq24, and they do synchro... the loop mode of hydrogen is very useful kind of reminds me Fl studio patern-loop mode. you can keep jamming at the rythm of hydrogen... for ever:D (while jack does not drop of course :) :) :))

---

### Post by philipacamaniac on 2006-08-05
I've just had an epiphany with ardour, qjackctl (and it's lovely connections window), and my other jack apps (hydrogen, etc.). I didn't quite get the jack concept till tonight. Yay! It is basically the back panel of Reason, just without (so far) any CV or trigger inputs.

Now that I'm getting the hang if this whole jack thing, I'm wondering - can Ardour be used as a timing master to control hydrogen and seq24? I've already hooked up their MIDI inputs to the Ardour seq output, and I've tried enabling several options in Ardour, but I must be missing something, because the Ardour play button still isn't triggering any other programs.

EDIT: Okay, qjackctl transport controls can control hydrogen (and possibly seq24), but they won't don't seem to affect ardour. Any suggestions?

---

### Post by cutterjohn on 2006-08-05
@EPOX123
You SHOULD be able to use the GUI design tools, with no programming experience to generate what you think the GUI should look like and then forward it to someone who can do something with and cares.  (ASK first, just don't do it and random send.)

You may even be able to generate a GUI on your own that you could overlay an existing app with, but I'm no expert on how GNOME/KDE apps handle their GUIs(i.e. whether or not they get compiled into the executable(or libs) or rely on external files...) again, it never hurts to find someone to ask about an app that you like(or think had potential), but hate the GUI for...

Alternatively you could also just use a generic graphic design tool to mock up a GUI, but that would be a pain...

---

### Post by philipacamaniac on 2006-08-05
> **cutterjohn said:**
> You may even be able to generate a GUI on your own that you could overlay an existing app with, but I'm no expert on how GNOME/KDE apps handle their GUIs(i.e. whether or not they get compiled into the executable(or libs) or rely on external files...) again, it never hurts to find someone to ask about an app that you like(or think had potential), but hate the GUI for...

When you create a GUI in Glade (for GTK), it creates an XML file, which I believe becomes the GUI for the application. I'm not sure how KDevelop works, though. 

Whoever starts designing audio apps, please take a look at hydrogen. It has the best widgets in any Linux audio app I've seen yet (IMHO). At least, its widgets look most like Reason's. And the best thing about hydrogen's widgets and design is that it pulls them from PNG files in /usr/share/hydrogen/data/img, which means you can modify them and/or theoretically have theme support.

BTW, I figured out the whole Jack Transport issue, so last night I had ardour, hydrogen, and seq24 (playing a zynaddsubfx synth) all in perfect sync and controllable from qjackctl, or even from the apps' transport controls themselves.

I'm going to go make a Reason-like mockup with rack versions of hydrogen, zynaddsubfx, qsynth, amsynth, specimen, some specific ladspa frontends, and a generic ladspa plugin. Then of course I'll top it all off with a JACK mixer and a built-in sequencer.

---

### Post by nihilocrat on 2006-08-07
> **philipacamaniac said:**
> 
Not trying to start a war. I wish I was a strong developer, so I could just create this killer app myself. All the dirty work has been done already (analog synths, wavetable synths, samplers, sequencers, drum computers). It's now a matter of creating a new frontend gui that can use all those engines together and make it look good and work well.

Hydrogen or any other instrument that has a built-in sequencer would need to be stripped down, but otherwise you're probably right that it wouldn't be too difficult. It would be best to have a "full package" distribution which includes several of these instruments and effects which work together really well, or have been modified to work with the sequencer. Include an interface to JACK which metaphorically makes sense so you have the "backside of the rack" functionality that Reason does. Include a CD's worth of public domain / GPL / CC samples (which are hopefully pretty good) and you've got the power that Reason has by including really good instruments, samples, patches, and a really slick sequencer all in one package.

I would also try working on this if I didn't really know where to  start with the GUI... I only have experience making 'traditional' GUIs in asynchronous programs. The overall design would be easy because there's already a very good idea of what it should look like and how it should work... but the problem (in my world) lies with the difficulty of implementation.

---

### Post by coder_ on 2006-08-27
Is there any way I can have 32bit and 64bit JACK installed at the same time?  (32 bit for REAPER+WINE and 64 bit for regular JACK+seq24, ect.)

---

### Post by floogy on 2006-08-28
Hmm, I thought I have jack 64bit installed, and can connect it with  the jacklaunch (64 bit) started Last.FM (I guess its a 32bit elf, I'm not sure though).

---

### Post by majutsu on 2006-09-08
this is a great thread.  i would love to put something like this together.  i mostly play with sc3, pd and chuck in ubuntu, but i think i will try the hydrogen, etc as discussed here.  very interesting.  could be fREESON or something.

---

### Post by Cybolic on 2006-11-12
Just thought I'd mention that Reason runs pretty close to perfectly in the new CrossOver 6.0.0beta2, the only problem is the black icons that we know from Wine, playback and control of the program is perfect.

So for the added cost of CrossOver, Reason on Linux is now possible :D

---

### Post by coder_ on 2006-11-12
Reason works well, but I'd LOVE to get Renoise working under it :'(
I love Renoise, but the GUI is messed up in WINE and it doesn't respond to clicks in WINE :(

---

### Post by noxxle on 2006-11-14
have you tried any other audio production apps with that crossover beta?

---

### Post by cwolf on 2006-11-19
This new Linux software looks promising, somewhat like Reason:

[http://wired.epitech.net/](http://wired.epitech.net/)

However, at the time of this posting the website is down.  And forgive me if it is totally unlike Reason: I have only been able to glance at some screenshots.  Right now, I am running FreeBSD, which has very minimal MIDI support.

Cheers,
cwolf

---

### Post by CadetD on 2006-11-20
> **Cybolic said:**
> Just thought I'd mention that Reason runs pretty close to perfectly in the new CrossOver 6.0.0beta2, the only problem is the black icons that we know from Wine, playback and control of the program is perfect.

So for the added cost of CrossOver, Reason on Linux is now possible :D

You are so right!

Being the lazy bum that I am. I didn't want to fuss with installing Wine on my AMD64 so I too went with CrossOver. 
The new Beta is years ahead of the current release. 

I even tried my Cubase SX (which I no longer use in favor of Rosegarden) and it worked flawlessly. All VSTs loaded fine Audio tracks played fine and in sync. Something totally impossible with the previous version.

---

### Post by noxxle on 2006-12-01
NO F$#$#ing way cubase works?!?!?!? I know a lot of people who keep their windows partition solely for recording software. If cubase and reason now work under CrossOver, i suspect many other audio production programs will work too. Tried any of Native Instruments stuff?

---

### Post by majutsu on 2006-12-09
i actually have gone to using rosegarden, with specimen, hydrogen, zynaddsubfx, ams, and dssi's hexter and xsynth, as well as ladspa effects.  truthfully a lot of the stuff (especially effects) sound better than fl studio or reason (both of which i own and used for years).  i think cubase or protools is still ahead, but not really necessary for what stuff i make for fun.  i really think i like staying with open source stuff completely.  it makes little sense to run windows apps in wine or crossover at this point.  if you need them that badly ( like a pro audio station or gaming station) maybe that computer should be windows for you, and then another ubuntu station for other things.

---

### Post by jord1242 on 2007-04-24
> **maku-d said:**
> This is probably a bit of a newbie question- but what alternatives to reason are there for linux?  

I mean- I've been using ardour through osx for just over a year, great protools replacement, fit nicely into my setup, but no midi so far. Otherwise maybe something like rosegarden? (haven't tried it yet) but then you have to find virtual instruments yeah?  ...and that's probably the only real problem for me...what sort of quality virtual instruments exist?- are they on the same level as reason's? Hydrogen already has the nnxt and redrum drum machines covered, and seeing as reason itself can't record analogue instruments, using something like ardour is a great addition (where you would've used rewire through something like cubase or digital performer previously) but yeah...virtual instrument quality? anyone know? does it compare to reason? Is there some better reason alternative out there?

Complaining about GUI's is crazy in my book, seeing as any gui is crappy when you really think about it...most of the commercial programs we use right now are all equally as crappy/don't make sense,  it's just we've learned to work with them. But yeah...functionality wise if there're equivalents I'd love to give them a run for their money. 

Cool.

There is NO alternative to using Reason!

JJ

---

### Post by Bram77 on 2007-06-09
I'm trying to reduce latency in Reason. I've managed to let Reason (wine actualy) detect the Jack server. But when I choose a "MME Jack Waveout" output I see a red** [COLOR="Red"]X[/COLOR]** in the Reason setup where, if I choose the "MME mixer" option, a green** [COLOR="SeaGreen"]V[/COLOR]** shoud be.
So audio is not working when using the Jack server. What am I doing wrong?

When I use the "MME mixer" output I get noise when scrolling in reason. Even with the latency to it's max. My Computer is fast enough!

---

### Post by dz0004455 on 2007-07-19
:guitar:
it runs fine under Ubuntu Studio 7.04
The sound lags a bit though

---

### Post by jord1242 on 2007-07-19
Is the lag due to your hardware/computer or is there a definite lag? I have yet to try out Ubuntu Studio, but if Reason works, my windows days are done. Are you using the CrossOver thing?

I use Ableton Live as my sequencer, but I am sure that there is a GOOD sequencer in the Studio that supports VSTs.

JJ

---

### Post by Bram77 on 2007-07-19
Reason runs under Wine, but the performance is so terrible that I've decided to do a dualboot again after 3/4 year of dedicated Kubuntu usage.

---

### Post by jord1242 on 2007-07-20
@ Bram,

What kind of hardware are you running on? Just curious if my machine is quick enough to run with or if I too have to stick with my dual boot? I am starting the test this weekend and will let you all know.

JJ

---

### Post by jord1242 on 2007-08-10
Finally got wine installed with reason using Ubuntu Studio, and when I load up reason the splash screen just hangs. I end up having to kill the process each time, it never fully loads.

Anyone that has had any success getting reason running under Ubuntu Studio and wine can they post what they have done to get it working?

Thanks,
JJ

---

### Post by jord1242 on 2007-08-12
Got it working!

First off, the splash thing happens because it is covering over the options you need to set (like license number, etc.). If you go into winecfg and go under the graphics tab, you can turn on wine's virtual desktop. Then the option comes up when you run the install.

Second thing is, you need to run Reason as sudo wine Reason.exe - This way you have access rights to saving the preferences, otherwise it will not be able to save anything.

That is my two cents. I am still testing but EVERYTHING looks great so far.

JJ

---

### Post by latecomer on 2007-08-13
> **jord1242 said:**
> Got it working!
I am still testing but EVERYTHING looks great so far.

JJ
Cool.
Please keep us posted.

Also, what are the advantages of UbuntuStudio, apart from the pre-installed music packages? 
If I'm just going to run Reason in WINE, I wouldn't really need them, no?

---

### Post by Batuhan on 2007-08-24
Check out wineasio to have ultralow latencies under wine and to connect your wine apps to jack.

---

### Post by conner_bw on 2008-01-19
> **coder_ said:**
> Reason works well, but I'd LOVE to get Renoise working under it :'(
I love Renoise, but the GUI is messed up in WINE and it doesn't respond to clicks in WINE :(

Renoise for Linux (beta) was released to registered users yesterday. A public demo should be available in a few weeks.

More info:
[http://www.renoise.com/indepth/renoise-news/renoise-191-beta-with-linux-port/](http://www.renoise.com/indepth/renoise-news/renoise-191-beta-with-linux-port/)

Screenshots:
[http://www.renoise.com/board/index.php?showtopic=15243](http://www.renoise.com/board/index.php?showtopic=15243)

Good times!

---

### Post by StanObuX on 2008-02-05
Kinda funny how different people view different things.  I finally decided to give Linux audio recording a serious look in the past week and a half (in plave of Cubase, Nuendo, Reason, etc).  I'm a convert. . .  Normally using Ubuntu (Gutsy now) but running the Planet CCRMA (Karma) low-latency kernel from Stanford for Redhat-based systems.  Windows simply does not compare.  Other than the wonderful programs it has (that crash all the time) linux stands best. The softs for linux are just as powerful AND THEY DO WHAT YOU TELL THEM TOO!  This morning dived into using jack to "ReWire" stuff.   More powerful better..  More control fro a musician like is ultimate.  Stop being spoonfed the crap from MicroSoft.  Go MacroHard, lol.  Just LEARN what linux has to offer and I assure you will not be disappointed.

Stancliff of Buxley
[www.myspace.com/stancliffbuxley](www.myspace.com/stancliffbuxley)
[www.myspace.com/buxleys](www.myspace.com/buxleys)

Hotep


"As is above, so is below."

---

### Post by jord1242 on 2008-02-05
> **Batuhan said:**
> Check out wineasio to have ultralow latencies under wine and to connect your wine apps to jack.

The only reason I still have a windows box is to run Reason and Ableton Live. I got Reason running on a fast machine, but the latency was just not good enough, so I ended up going back to Windows (and feeling DIRTY again). If you could give some details about wineasio I would be interested in testing it out.

Thanks,
JJ

---

### Post by HaelSturm on 2008-02-11
Im going home and putting Ubuntu Studio on my computer. i wanna see this!!!

---

### Post by jord1242 on 2008-02-11
> **StanObuX said:**
> Kinda funny how different people view different things.  I finally decided to give Linux audio recording a serious look in the past week and a half (in plave of Cubase, Nuendo, Reason, etc).  I'm a convert. . .  Normally using Ubuntu (Gutsy now) but running the Planet CCRMA (Karma) low-latency kernel from Stanford for Redhat-based systems.  Windows simply does not compare.  Other than the wonderful programs it has (that crash all the time) linux stands best. The softs for linux are just as powerful AND THEY DO WHAT YOU TELL THEM TOO!  This morning dived into using jack to "ReWire" stuff.   More powerful better..  More control fro a musician like is ultimate.  Stop being spoonfed the crap from MicroSoft.  Go MacroHard, lol.  Just LEARN what linux has to offer and I assure you will not be disappointed.

Stancliff of Buxley
[www.myspace.com/stancliffbuxley]("http://www.myspace.com/stancliffbuxley")
[www.myspace.com/buxleys]("http://www.myspace.com/buxleys")

Hotep


"As is above, so is below."

Maybe I just haven't spent enough time with Ubuntu Studio but I do not see any comparable Linux version app like Propellerheads Reason, and it is what I use to compose my music. Then I go over to Ableton Live, which is incredible, and I have not found a sequencer like it on the Linux side, I also make some DJ mixes in Ableton Live and it is just incredibly easy and intuitive to use.

If you can point me at some progs that you use that are comparable, I would be glad to give them a spin because trust me, I would LOVE to be rid of the last bastion of Micro$oft rule in my house, my music PC. Everything else is Linux.

JJ

---

### Post by geo909 on 2008-02-11
Man, be sincere with yourself. If you want applications like reason, just dual-boot, it's not sin.

When it comes to music production and linux, in my opinion there are only two roads:
1)Dual Boot
2)Ubuntu Studio

 (I do the first one and I don't feel dirty at all. I just want to do my job well, that's all)

---

### Post by jord1242 on 2008-02-11
> **geo909 said:**
> Man, be sincere with yourself. If you want applications like reason, just dual-boot, it's not sin.

When it comes to music production and linux, in my opinion there are only two roads:
1)Dual Boot
2)Ubuntu Studio

 (I do the first one and I don't feel dirty at all. I just want to do my job well, that's all)

Oh I hear you man, it is just a bit frustrating because I got all the other six computers over to Linux completely (other than my wife's computer) and that is the last one kinda hanging on for dear life.

I heard that Ableton Live may port over to Linux next version, we'll see. If so, I can always try running Reason in a VM session in Linux I guess. That would be about as close as I can come. 

JJ

---

### Post by Bram77 on 2008-02-12
Wow! A port of Ableton Live to Linux would shake my world. Ableton is fantastic.

---

### Post by jord1242 on 2008-02-12
> **Bram77 said:**
> Wow! A port of Ableton Live to Linux would shake my world. Ableton is fantastic.

Ableton and Reason are worth every penny I paid for them. And Reason has really stepped up its sequencer in version 4. ALthough I still love how Ableton allows you to scroll left and right to go through time and scroll up down to zoom in and out, one continuous motion. Perfectly intuitive.

But if I could just get them working in Wine with no latency, I would be golden. Maybe I will try Ubuntu Studio again just to give it a try once 8.04 comes out.

---

### Post by wieman01 on 2008-02-12
> **jord1242 said:**
> Ableton and Reason are worth every penny I paid for them. And Reason has really stepped up its sequencer in version 4. ALthough I still love how Ableton allows you to scroll left and right to go through time and scroll up down to zoom in and out, one continuous motion. Perfectly intuitive.

But if I could just get them working in Wine with no latency, I would be golden. Maybe I will try Ubuntu Studio again just to give it a try once 8.04 comes out.
Keep us posted, I'd be interested as well. I tried Reason with CXOffice the other day but it failed. A newer version of Wine could make the difference.

---

### Post by jord1242 on 2008-02-12
> **wieman01 said:**
> Keep us posted, I'd be interested as well. I tried Reason with CXOffice the other day but it failed. A newer version of Wine could make the difference.

I got it working in Ubuntu Studio with Wine, but the latency wasn't good enough. I think the box had enough memory in it, and the processor was a good one. But I have been meaning to try it with 8.04 so when I do I'll post back.

peace,
JJ

---

### Post by wieman01 on 2008-02-12
> **jord1242 said:**
> I got it working in Ubuntu Studio with Wine, but the latency wasn't good enough. I think the box had enough memory in it, and the processor was a good one. But I have been meaning to try it with 8.04 so when I do I'll post back.

peace,
JJ
Sure. Look forward to it. 

Did you use the free version of Reason or the latest commercial one?

---

### Post by Nunu on 2008-03-26
Hi Guys

I have been running Reason 3 on a virtual machine in ubuntu for a while now it it works perfectly as long as you stay on the VM as soon as you do somthing outside the VM (On Linux) the sounds tends to crack but it works good enough for me. 

But i need to figure out how to get my Midi Controller to work in the VM still:guitar:

---

