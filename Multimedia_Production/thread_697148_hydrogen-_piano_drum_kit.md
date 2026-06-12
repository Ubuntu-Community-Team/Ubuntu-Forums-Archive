---
title: "hydrogen- piano drum kit ?"
date: 2008-02-14
forum: Multimedia Production
---

### Post by secondstage on 2008-02-14
Is there a drum kit for Hydrogen that would have the sound of a piano?

OR maybe just a good piano emulator(for a lack of a better word)?

---

### Post by chipants on 2008-02-18
there probably isn't a piano 'drumkit' for hydrogen, as it is a drum machine. you can very easily create your own 'drumkit' with whatever sound samples you like, though.

however, you should probably just install qsynth and download a decent piano soundfont. on its own, qsynth doesn't have any 'sounds'. you will need to locate soundfonts (they'll have a file extension .SF2) to be loaded into the app.

---

### Post by Stochastic on 2008-02-18
May I suggest ZynAddSubFX as a piano synth.  Not the best in the world, but gets the job done.  And you could probably send midi out from Hydrogen and into Zyn through qjackctl if you wanted to use Hydrogen as your sequencer.

---

### Post by chipants on 2008-02-19
> **Stochastic said:**
> May I suggest ZynAddSubFX as a piano synth.  Not the best in the world, but gets the job done.  And you could probably send midi out from Hydrogen and into Zyn through qjackctl if you wanted to use Hydrogen as your sequencer.

i disagree completely. zynaddsubfx is a phenomenal synthesizer. i use it on almost every recording project. however, it is *very* much a synthesizer and does not (and is not intended to) produce realistic piano sounds. at all.

qsynth, on the other hand, is able to load up industry-standard soundfonts that are available abundantly, free and for-cost all over the web. soundfonts can be created from recorded samples of actual instruments. for a realistic piano sound, this is definitely the easiest way to go.

also, hydrogen would be very limited in what it could do as a sequencer for anything but creating beats. it is a superb application that i use on most of my recording projects, but a general-purpose midi sequencer it is definitely not.

if you require a comprehensive midi sequencing application, may i suggest rosegarden4? it is quite capable. using rosegarden4, you would not even need an external application, such as qsynth because rosegarden4 has built-in facilities to allow the use of DSSI soft-synths as well as SF2 soundfonts via fluidsynth. there is a slightly steep learning curve, i'll admit. however, if you're creating anything besides the simplest of melodies, hydrogen is not going to fit the bill.

---

### Post by Stochastic on 2008-02-19
chipants, you are right in your value judgements but the original poster was asking as to how to make hydrogen play a piano sound.  ZynAddSubFx does have a piano-like  preset and therefore could be considered as an option.  Qsynth is probably a more realistic sound (provided the sound bank is nice) though it'd be nice to see a link to a soundbank or some instructions as to how to install one.

I really don't mean to start an argument, I'm merely trying to add to your answer.  After all, you are right, Hydrogen makes for a pretty bad sequencer.  But that's what the thread was asking for.

out of curiosity what sequencer would you suggest to secondstage?

---

### Post by chipants on 2008-02-19
> **Stochastic said:**
> ...I really don't mean to start an argument, I'm merely trying to add to your answer.  After all, you are right, Hydrogen makes for a pretty bad sequencer.  But that's what the thread was asking for.

out of curiosity what sequencer would you suggest to secondstage?

actually, he asked about a piano drumkit *or* a piano 'emulator', which leads me to believe that he probably just wanted a nice piano sound. i truly don't mean to sound argumentative. i do fully realize that zyn has a patch (well, several) that are made to sound piano-ish. however, they don't sound very much like pianos. (i do love the various rhodes patches, though).

there is one free grand piano soundfont that i've used in the past. ([http://www.pianosounds.com/](http://www.pianosounds.com/)) it's not "free" as in "freedom", but it's quite nice to fiddle about with.

as i said in my previous post, rosegarden4 is a very capable midi sequencer. i'm not a really an expert on midi sequencing, but rosegarden is pretty much the undisputed king of linux midi sequencing. another option is LMMS, i suppose. but, i really haven't been able to play around with it much. also, there's muse. although, muse is a little more rough around the edges. at least visually, it seems rather dated. of course, if a person wants more of a 'tracker'-type of sequencer, there are countless options. lastly, i suppose i should mention seq24 ([http://www.filter24.org/seq24/](http://www.filter24.org/seq24/)). very handy for loop-based midi sequencing.

personally, i use a midi keyboard, zynaddsubfx, qsynth, and hydrogen for most of my music. however, i don't use a midi sequencer very often. instead, it seems more natural for my workflow to treat the output of hydrogen, zyn, and qsynth as audio instead of midi data, and dump straight into ardour.

one other place to look for linux audio apps, etc., is [http://linux-sound.org](http://linux-sound.org). the maintainer of that site does not update as often as he used to; but, it remains a very comprehensive site, listing a multitude of linux audio applications, and related things.

---

