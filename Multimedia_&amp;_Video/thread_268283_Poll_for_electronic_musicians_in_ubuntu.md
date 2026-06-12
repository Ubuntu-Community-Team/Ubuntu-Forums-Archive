---
title: "Poll for electronic musicians in ubuntu"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by majutsu on 2006-09-29
hi i am doing electronica in ubuntu.

i am curious if others who are similar could give some idea as to their favorite tools for music composition on ubuntu.  

i have all the usual suspects, pd, rosegarden, supercollider, hydrogen, BUT

my favorite tools of the moments are the Whysynth ( [http://home.jps.net/~musound/whysynth.html](http://home.jps.net/~musound/whysynth.html) ) and Soundtracker( [http://www.soundtracker.org/](http://www.soundtracker.org/) ) .  I still love trackers :mrgreen: 

Om synth ( [http://www.nongnu.org/om-synth/](http://www.nongnu.org/om-synth/) ) is very close in third.  i am very curious as to the ingen version.

anyway, please, if you make music in ubuntu, let me know your favorite tools.  i hope to learn some and feel a little sense of community.

thx

---

### Post by mushroom on 2006-09-30
trackers rule. Unfortunately, I haven't really come across anything that beats Renoise yet, which unfortunately does not have a Linux version. Skale comes close.

---

### Post by gorilla on 2006-09-30
I really dig Milky Tracker
No Jack, no synths or effects, but pure FT2-ness :)
Set to 800x600 and fullscreen, instant retro trip!

---

### Post by chameleon_789 on 2006-09-30
I don't usually make electronia, but I love messing with live sound so freqtweak and jackrack are among my favourites.. also got guitar rig 2 and reaktor 5 working as vst's.. trouble is they are all pretty unstable when jack'd together, really frustrating when jamming :( 

I used to use FT2 all the time so I'm gonna go check out skale and milkytracker :D

---

### Post by zettberlin on 2006-10-02
> **majutsu said:**
> 
i am curious if others who are similar could give some idea as to their favorite tools for music composition on ubuntu.  


Electronic stuff I do mostly with seq24, zynaddsubfx, ams - if I record from the midi-keyboard I use muse. Samplerstuff is made with specimen and of course I use hydrogen.

> **majutsu said:**
> 
i have all the usual suspects, pd, rosegarden, supercollider, hydrogen, BUT


I rarely use pd and never supercollider - I simply have not got the time to learn a programminglanguage just to make sounds. Can you recommend some tutorials and most important: good templates for those?

> **majutsu said:**
> 
my favorite tools of the moments are the Whysynth ( [http://home.jps.net/~musound/whysynth.html](http://home.jps.net/~musound/whysynth.html) )

this one crashed a bit too often on my box.

> **majutsu said:**
> 
Om synth ( [http://www.nongnu.org/om-synth/](http://www.nongnu.org/om-synth/) ) is very close in third.  i am very curious as to the ingen version.

This I absolutely confirm - as ams is unfortuantely not developped anymore, we need a new modularsynth. OM is quite good, so I have highest hopes regarding ingen!

> **majutsu said:**
> 
anyway, please, if you make music in ubuntu, let me know your favorite tools.  i hope to learn some and feel a little sense of community.


My basic set of must-haves is:

- ardour
- rezound and mhwaveedit
- muse and rosegarden
- hydrogen
- seq24
- Zynaddsubfx, ams and om
- jamin
- specimen

---

### Post by kellogs on 2006-10-02
doing electronic music in ubuntu is very cool, im starting to make some quality sounding loops at the same level I did them in windows.

This is my general program usage list:

-Drum sequencing:Hydrogen(try to compile 0.9.3, the Qt gui is way more improved and has less bugs).

-music/melody sequencing: Seq24. its piano roll and pattern editor works quite well(for example MIDI events in seq24 are working pretty well in comparison with other commercial sequencers). The more you work on it, the faster you become and you will start to see what the autor wanted to achieve in a "minimal" environment.

-sampling/soundfonts: I use for SF2 loading the fluidsynth wrapper:Qsynth. Although Im still learning to use it, it is quite comfortable and fast to set. as a side note: does anyone know how to set its memory cache limit?

There is another unknown here, Linuxsampler... it can load .GIG Files, and it does support Keyswitching and a lot of Gigastudio format capabilities (articulations, filters, etc). I compiled it and it does work well for simple giga files.(big GIG sample libraries are expensive but you can try and see if you have one of these).

For overall effect processing I use the Ladspa plugins, and for recording Ardour. sTill learning though.

cheers.

---

### Post by wavesound on 2006-10-02
HI
Does Ardour and jack run ok on Ubuntu?
I used studio64 but I cant get it to reload since loading Ubuntu on my third HD.
I would need alsaconf as I have a RME card in the box.

Got a spare HD waiting for a 64bit studio setup!

Cheers
Bob
Wavesound :)

---

### Post by majutsu on 2006-10-02
great to hear from people!

i love seq24 as well.  it's one of those tools that's basic and complete.

i need to look into qsynth, as i used to love soundfonts on windows.

p.s. when i say electronic music, i mean music made with ubuntu.  Electronic does NOT imply techno or the like.  techno is just a subgenre of electronic music, which is music made with electronics in any way, as opposed to just acoustic instruments.  there is a lot of indie rock, classical, jazz etc made electronically now.  i personally like modern classical (schoenberg etc), jazz (bop) and IDM as genres myself.  

i like om synth a lot.  the ladspa plugins are good.  

whysynth hasn't been used much lately by me.  

i love pd, chuck and supercollider.  the "programming languages".  although calling them programming languages is a little misleading to the musician.  in pd or max/msp, instead an oscillator box, you draw a box and type osc~ into it.  not much difference in my point of view.  it's not like c++ or anything.  also, supercollider if you want an oscillator in a chain you type SinOsc.ar .  Big deal.  it's just modular with text boxes or plain text.  these "programming languages" are just Reaktor with no GUI budget.  :p   Dave Cottle's tutorial on Supercollider is very good.  And max puckettes books (as free pdfs on his site and the pd swiki) are truly awesome.  i never understood fft or detailed sampling issues before, e.g.

these programs are hard to use musically, which is why every supercollider or pd patch you've heard sounds like a twisted fart/drone.  the only one who used these artistically like autechre (max) and cylob (superc) really used the control data (midi etc) functions to trigger analogue/hardware keyboards algorithmically, whatever.  i've never heard anything but experimental tweaky shit from those who stay totally within the programming paradigm.  i think their true value (like with BT and csound) is to educate yourself deeply in electronic music.  i recommend pd highly, as max puckette is a geniotic god, it's free, and almost militantly open-source.

---

### Post by CadetD on 2006-10-12
> **wavesound said:**
> HI
Does Ardour and jack run ok on Ubuntu?
I used studio64 but I cant get it to reload since loading Ubuntu on my third HD.
I would need alsaconf as I have a RME card in the box.

Got a spare HD waiting for a 64bit studio setup!

Cheers
Bob
Wavesound :)

I've had pretty good success using both on my AMD64 Kubuntu box.

---

### Post by coder_ on 2006-10-14
I too am finally getting some good quality sounding stuf now with JACK and friends relative to what I had going in Windows.  And it's all free or open source stuff! Yay! :D

My favorite apps to use:
Milky Tracker or Soundtracker (Beginning to like MT a lot more than ST now)
Seq24
qsynth (For my soundfonts, especially the very nice, free Titanic200 sf)

I want to try Rosegarden but it doesn't work with any of the ones in APT with my 64 bit system, so I guess I have to compile it like I had to do with MUSE to get it to work. :'(

---

### Post by hendrikwout on 2006-10-25
yes, it works very well on ubuntu, allthough it needs some tweaking (realtime-lsm-module and preemptive kernel option). But works very well as 7 track recorder/fxprocessor on my old pentium III 550Mhz, 512kb cache. It needed some tweaking also to get the best performance. I get latency of 8ms 3x128 samples) while recording 7 tracks (16 bit, 44100Hz) and mixing it all together with ardour to two stereo tracks with reverb effect.

---

### Post by okcomputer0101 on 2006-10-28
Wow silly me I just found out here that you can do music with Ubuntu or GNU supported software. I am really spoiled thoug. I do electronica! Mostly vocal deep house and downtempo. I use alot of live audio.. So I am not sure how well that would go over on an older computer using a linux based system. I push my MAC iBook G3 to the limit everytime I record. I use Ableton Live 5 and external hardware Akai samplers. To think artist back in the day did all those classic tracks on Mac G2  and Pentium 2's wow!!! Thanks for the info I have to investigate! I could save alot of money on upgrades!

---

