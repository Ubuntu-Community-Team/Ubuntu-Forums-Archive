---
title: "Ardour 2.3 w/ VST's"
date: 2008-03-29
forum: Multimedia Production
---

### Post by unknown03 on 2008-03-29
Hey ppl,
Coming from Windows and being an off and on user of Linux (SuSE 8 and Mandrake 10) I am proud to say that I am looking forward to using Ubuntu for the majority of my tasks.

I've been a Cakewalk Sonar user for quite some time now, using VST's and recording instruments/vocals. Sonar is a MONSTER when it comes to useful features, and the learning curve was pretty big when using Sony ACID before it..

I've searched google and these forums, and they all lead to posts asking for help, when it comes to Ardour and VST's


My question is:
are there any GOOD user manuals/tutorials for Ardour 2.3? After installing it I just stare at the screen, baffled by way its set up. 

How the hell do you use/enable VSTs? (rant)I understand steinberg wants complete control over the music market. But how can, in this year of 2008, no one create a universal installer, be it by reverse engineering or undermining? (yeah i know what ur gonna say, but i need to go back to school for programming knowledge)(/rant)

And how the hell is jack suppose to work? that thing has me spinning around in circles that I just gave up TRYING to understand.. I have midi instruments that I want to use, and JACK is supposed to supply the link, right?

and What other alternatives/good native programs under linux for DAW and/or MIDI instruments/synths? I would love to know what you musicians are able to create with them. Anything professional?

Music creation is only one of two areas that keep me chained to my installation of Windoze

---

### Post by Stochastic on 2008-03-29
One piece of advice with open source software: go straight to the source for your manuals.  [http://www.ardour.org/files/manual/index.html](http://www.ardour.org/files/manual/index.html) is one of the main links on Ardour's website.

And to get VST support in Ardour, they have this nifty howto on their webstie too [http://www.ardour.org/building_vst_support](http://www.ardour.org/building_vst_support)

As for JACK, it's an audio server designed for pro-audio.  What this means is that it allows apps to send audio and MIDI signals to and from each other and the soundcard.  Most people run it through a program called qjackctl (or simply Jack Control) but it can be done through the command line too and Patchage is quite often used as a graphical router to replace the one qjackctl gives you.

---

### Post by unknown03 on 2008-03-30
Hey thanks for the link, I couldnt find anything other than "We cant provide vst ready packages" on their site...but this will help

now, ardour doesnt actually support midi instruments, right? so would i need to load them up in a program for jack to send to ardour?

---

### Post by funkster on 2008-03-30
Of course you could always compile Ardour yourself with integrated VST support. But it seems that this is no minor task. You can find extensive help & explanations/HowTo's on the Ardour forum.
As for MIDI, there are a few options for you, like Rosegarden, MuSE, SEQ24 (which I like a lot, it's a MIDI looper of sort) and then some. 
[COLOR="Red"]_**[http://linux-sound.org/](http://linux-sound.org/)**_[/COLOR]

You could also go another route alltogether if you don't want to miss your VST(i)'s:

Search for wineasio, learn how to install that (not very difficult) and use [**_[COLOR="Red"]REAPER[/COLOR]_**](http://www.reaper.fm)
which runs quite nicely under wine if your PC is recent enough. This will give you access to most needed MIDI functionality, all your existing VST(i)'s and the awesome internal JS effects suite. Plus a very nice, helpful and knowledgeable community if you have any questions or problems.

Regards
Raphael ;)

---

### Post by Stochastic on 2008-03-30
Honestly I'm not much of a midi instrument guy (I prefer to twist samples into unrecognizable shapes), so I'm not really sure what you mean by a midi instrument (I'm assuming a soft synth triggered by midi? or do you mean a hardware keyboard/controller sending midi signals?).

From what I do know, MIDI in ardour is still in the development stages.  It will be coming but just not yet.  So anything going in or out of Ardour right now is purely audio or audio files.

If you want to get a soft synth recorded into ardour, open it up, through JACK connect the midi triggering signal in (either from your hardware keyboard or from your soft sequencer) to your soft synth, connect the audio out of your soft synth to ardour's input, hit record and play away.  One excellent feature of JACK is the Jack Transport - it gives you the ability to hit play on the Jack Transport and for all the apps connected (that support the feature) to start in sync.

Now as for your questions regarding other apps in Linux, Rosegarden is currently one of the preferred apps for MIDI heads as it bears more resemblance to say Cuebase (maybe Logic too).  You may also want to check out: 
- Renoise [http://www.renoise.com](http://www.renoise.com) - A closed-source sequencer that's recently been ported to linux
- Rezound [http://rezound.sourceforge.net/](http://rezound.sourceforge.net/) - An open-source wave editor that is the editor I prefer.
- LMMS [http://lmms.sourceforge.net/](http://lmms.sourceforge.net/) - An open-source MIDI heavy sequencer/synth app (claims to be similar to Logic on it's homepage)
- Jamin - a suite of audio mastering tools
- LADSPA plugin set - the reason why most users here don't worry about getting VSTs to run
- ZynAddSubFX - a powerful native soft synth
- QSynth - a syth that utilizes soundfonts for it's sounds

There are also a few other DAWs out there
- Energy XT [http://www.energy-xt.com/](http://www.energy-xt.com/) - A closed-source DAW
- Traverso [http://traverso-daw.org/](http://traverso-daw.org/) - Open Source
- XOWave [http://www.xowave.com/](http://www.xowave.com/) - Open Source
- Audacity [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/) - Open Source
- Wired [http://wired.sourceforge.net/](http://wired.sourceforge.net/) - Open Source

But there's a good reason why the majority of people recording pro-audio on Linux use Ardour.  It's stable, feature-rich, elegant in design, flexible, and in heavy development (when the MIDI finally arrives it'll be huge).

---

### Post by unknown03 on 2008-03-30
Thanks guys, your replies are very helpful!
and yes, by midi instrument I mean a hardware controller sending midi data to a soft synth/sampler

I have a Casio keyboard and a Korg padKontrol (which is AWESOME)
I just cant seem to get them setup correctly

Linux DAWs are new for me, but it seems like if you know what your doing then it can be more flexible than anything closed-source

---

