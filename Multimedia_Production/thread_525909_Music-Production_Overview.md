---
title: "Music-Production Overview?"
date: 2007-08-14
forum: Multimedia Production
---

### Post by MusicProducer on 2007-08-14
I've been using Ubuntu for a month now, and it is awesome, and I thank everyone who's helped create it.

On Windows XP I was using Cakewalk Sonar (DAW software for music-production). I'm wondering what people are using for music production in Ubuntu? I'm aware of Ubuntu Studio, but haven't tried it yet -- I will soon.

My needs are:

- virtual instruments of all kinds, including drum machines
- virtual effects (chorus, delay, reverb, etc.)
- multi-track audio recording/mixing

My Cakewalk-Sonar setup, along with all the add-ons I bought for it, was expensive, so I don't expect all that power for free. But I'm curious how much I can do in Ubuntu, without having to boot Windows, which I hate.

If anyone has any software recommendations, please post them here.

---

### Post by eric71 on 2007-08-15
Using Ubuntustudio is a good idea, as their extra repository has a few extras. Ardour is really the best recording solution for Linux.  It is audio only at this time, but will do midi in the future. There are plenty of good softsynths available, the Qsynth soundfont player being a good example.  The beauty of Linux music production is that all of these programs can be tied together by the jack sound server.  Through the configuration program, QJackCtl, you can patch input and output from many Jack-ready programs any way you want. So you can use Qsynth with your MIDI keyboard, record audio from that with Ardour along with guitar and vocals, and master it all with Jamin.  Ardour can use LADSPA effects plugins.  They are good, although there are not nearly as many as for the VSTs you are used to in Windows. It is possible to compile Ardour yourself with VST support, but it can't be distributed that way.

If you do mostly MIDI with a little audio thrown in, then Rosegarden is best for you.  A wonderful midi sequencer with piano roll and music notation.  The audio is fairly limited, but the interface is clean.  It's also a KDE program, so will have a little extra overhead on a Gnome based system beacuse it's using KDE libraries.  It also can use LADSPA effects and can use VST as well with its DSSI plugin system and DSSI-VST. If you search these forums, you'll find out how.

Another option I'm trying out now is the use of the Windows program Reaper with Wine and the new wineasio. It seems to run pretty well and uses all the same VST and VSTi it does in Windows. I'm getting 10 ms latency and am generally quite happy with it.  Wish it were a native linux app, but I really like its features and workflow.  You'll find a howto here: [http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/)

The best drum program is Hydrogen.  You can get some great sounding kits for it. It exports as wav or MIDI.

---

### Post by MusicProducer on 2007-08-15
I really appreciate the reply. I'll start off with Rosegarden and Hydrogen. I have no MIDI keyboard, but I'm looking forward to using a sequencer to control softsynths / drums.

To record audio, I may have to go back to Windows, because I record my guitar through a Line6  Pod XT, and I don't know whether Line6 has made linux drivers (I'll check).

I'd rather have a handful of good, open-source audio-effects, than hundreds of dubious VST's; so I'm guessing that Ubuntu will be the superior platform for audio-effects, at least eventually.

Thanks again.

---

### Post by KoRnholio on 2007-08-15
If you haven't seen it yet, the Rosegarden Handbook - [http://rosegardenmusic.com/doc/en/](http://rosegardenmusic.com/doc/en/)
is a great source for information if you plan to use it.

As for the Line 6 POD, 
[http://www.squash-ligue.gf/podgui/podgui.php](http://www.squash-ligue.gf/podgui/podgui.php)
[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)

---

### Post by tgalati4 on 2007-08-16
Give Dynebolic a spin.  It's a live CD that will create a "nest" to store your music files on your Windows disk.  It's a low-latency kernel and has a lot of music production programs ready-to-use.

---

### Post by Tom Mann on 2007-10-13
I'm downloading UbuntuStudio right now, if I can get Wine/VST support in Ardour then I'm kissing SONAR goodbye! :-D

Ardour has support for the BC*2000 series, freebob, and with the above I have no excuse (the only thing that has been holding me back has been the DFH plugin - which I could never do without!)

Links:

[http://64Studio.com/howto_vst]("http://64Studio.com/howto_vst") (32 Bit Wine/VST support) - I will attempt my first HOWTO if I manage this!
[URL="http://http://ardour.org/files/manual/sn-bcf2000.html"]
http://ardour.org/files/manual/sn-bcf2000.html[/URL] - the BCR2000 (which I own) is nothing more than a BCF2000 with extras. (the bottom two rows are extra pots on top of the BCF, the third row up being the equivalent of the BCF2000's sliders)

And FreeBoB (for my Edirol FA-101) was just a case of selecting 'FreeBoB' as the driver in QJackCtl (or jackd -d freebob -r (sample rate)

---

### Post by orange2k on 2007-10-13
I like to work with Energy XT2.
Its very powerfull, but in the native Linux version I miss the VST plugs, so I installed XP in dual boot  to be able to work properly.
There is a way to setup a wineasio version of Energy XT in Linux, but it takes some time and effort to set it up right...
If you like, I can point you to a very straightforward tutorial for setting up wineasio in Ubuntu...

BTW Energy XT (1 & 2) is a very nice and cheap Cubase/Sonar alternative with some added bonuses - the demo version allows everything except saving projects (version 1 disables loading them), so there is nothing to prevent you from a test ride...:guitar:

---

### Post by Tom Mann on 2007-10-16
Hi Orange,

Last night I had VSTHost (windows app) host my drumkit from hell plugin correctly :-D

I'd love to read anything on getting windows VST plugins on Linux as the next thing I will attempt to do is get Ardour to pick up the drumkit from hell plugin, then I'll be rolling!

Thanks :)

---

### Post by jfulton on 2007-12-31
I got Drumkit From Hell somewhat working on Ubuntu Studio.  Here are my notes:
[http://infinitestateautomata.blogspot.com/2007/12/drumkit-from-hell-on-linux-part-i.html]("http://infinitestateautomata.blogspot.com/2007/12/drumkit-from-hell-on-linux-part-i.html")

---

