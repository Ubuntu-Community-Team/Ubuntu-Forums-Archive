---
title: "Reason/Live/logic Alternative for ubuntu"
date: 2008-04-12
forum: Multimedia Production
---

### Post by creeco on 2008-04-12
I've long been wanting to use ubuntu full time, but the reason i keep my winxp is because i produce songs with a program called "Reason 4" (from propellerhead). I havent been able to find a good alternative for linux yet, so i am asking if one of you guys out there know one..

Im looking for an app similar to reason or ableton live it doesn't matter if its loop based but i would prefer if it wasnt.. Support for vst's and vsti's is also needed.. Oh and it should also include a good drum sampler that can load .wav's

I hope some of you can help me!

---

### Post by thorgal on 2008-04-12
yeah, I have something for you, it's called WinXP :lol:

---

### Post by SynthesizersFTW on 2008-04-13
creeco,

First off, there are lots of music-related projects that are free and open source, a lot of them created by the professors at places like Stanford who taught the people writing commercial products!

You might want to check out Ardour, a complete DAW for linux.  If I remember correctly it might support VST - but I know it supports LADSPA (tons of free FX plugins out there for that).  If you work with loops you can audition and import .WAVs to the timeline very easily.  The learning curve is much better than Logic IMHO, just skim the online manual when you get stuck and you'll be producing tracks in no time.

:guitar:

Also, Rosegarden is quite nice for working with MIDI and virtual instruments like Hexter (a nice DX-7 emulator).  There are soft-synths and drum machines out there, you name it, just be persistent in looking (try searching descriptions in Synaptic) and you'll find what you need to do the job! 

Good luck

---

### Post by kayosiii on 2008-04-19
you won't find a direct replacement for those running natively under linux... Well you won't find a single program anyways...

Firstly Drum Sampler - Hydrogen is your best bet supports multi-layered samples I think the format is FLAC but this is not lossy compression, is well supported under linux and will save you space.
You could quite easily do a batch conversion of your wave files.

Ableton live - there are two programs that do things that ableton does... Freewheeling is an excellent live looping environment (that is all it does though) and Ardour is an excellent multitrack recorder (more like protools than live )... Typically I use Freewheeling to ad-lib a song then bring the samples into Ardour to build it into a more conventional song.

Reason - Basically Jack Audio on which most pro audio programs on linux are based does the same job as rewire. It is just happening at a system level rather than inside an app. This allows you to mix and match most linux pro audio apps in the way you would mix and match components in Reason. So I guess the question now comes down to virtual instruments.  [http://www.jackaudio.org/applications](http://www.jackaudio.org/applications) will give you a list of jack compliant audio applications to look at. to do the actual routing between audio apps I recommend patchage. also look at dssi there are a few reasonable softsynths in that lot.

VSTs -- vst are currently a pain on Linux... you can get vst on linux but for legal reasons you have to build it for yourself (no redistribution of binaries). 

The problem is that the Licence for the VST SDK specifically prohibits redistribution of the SDK by anybody other than Steinberg. Most Linux audio programs are licensed GPL and as such all sources must be available from the creators of the program. It is sometimes possible to grant a specific exception but all the authors of the code both past and present would have to agree with this as would authors of gpl libraries used. (or those libraries would have to be removed)...

The most common approach with VSTs is to use parts of wine to run the windows binary of the VST. There is now another approach that will run the VST natively but this requires that the VST be specifically compiled for linux. The wine based approach has its own problems and can be a bit hit and miss.

Linux has its own native plug in formats, ladspa,  dssi and now lv2 and since you can wire apps together most applications eventually behave like plugins too.

Hope that helps
    Danni

---

### Post by eric71 on 2008-04-24
The best way to get all you are looking for is to run Reaper via Wine with Wineasio. There's a great tutorial at the Reaper forums:

[http://www.cockos.com/forum/showthread.php?t=16786](http://www.cockos.com/forum/showthread.php?t=16786)

I like both Rosegarden and Ardour, but Reaper is just so well designed and runs so well under Wine. And you can use all of your VST effects and VSTi's.

---

