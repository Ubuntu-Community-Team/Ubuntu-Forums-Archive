---
title: "any audio people care to share their workflow?"
date: 2007-11-24
forum: Multimedia Production
---

### Post by kensuguro on 2007-11-24
've done a test install of ubuntu studio, contemplating the idea of making a linux daw and actually doing some serious work on it. (since there was a small project coming up) Unfortunately, I couldn't get the box set up in time, so I missed that chance this time, but at least now I have a basic setup with some working applications.

What I don't understand is, how do people set up their applications so that it's manageable? It seems like there's a lot of stand alone apps (synths, rosegarden, ardour, etc) and it seems like I need to run them and patch them each time.. Maybe I'm missing something, but I can't seem to find any documentation on how to set up the "big picture". So, it'll be nice if some more experience people could point me in the right direction. Or perhaps to the right forum.

Personally, my opinion about the soft synth selection on linux is that it's much more limited than I thought it was, and their quality is very diverse. (probably more free VSTi) So, I would tend to want to stick to VSTi, through WINE.. but then, rosegarden uses DSSI (no multiple output) while others use fst? Seems like every method is broken in one way or the other, or is there a "correct" combination of sequencers to use? I just need a sequencer that does VSTi, handles MIDI, and also does audio effects. (cubase, sonar, etc) I tried MuSE, but some parts of it seemed under development.

I've heard of people creating "studios" based on linux, so I'm guessing a serious setup can be built.. I'm just not sure how.
__________________

---

### Post by Geoff Leopard on 2007-11-28
My background is in hardware (desks, tape, outboard etc.), so the idea of syncing Ardour to Rosegarden is just like using SMPTE to sync tape with a sequencer. I personally don't have a problem in saving songs in two or three places and repatching when I start back up (a screenshot in Patchage is fine for this); if anything it gives me a minute to make sure the patching and workflow is what I want. However, enough people do want this to have started [LASH]("http://www.nongnu.org/lash/"), which looks like it'll do what you want when it's fully implemented.

I work with bands and don't deal with soft synths etc that often, but when teaching synthesis I get a lot of milage out of SuperCollider and LinuxSampler/gigedit.

G

---

### Post by Stochastic on 2007-11-28
My general workflow revolves primarily around sampling and recombination of audio bits.  Rezound and Ardour are my main tools though I also regularly use jamin, hydrogen, xwax, puredata, chuck, csound, freqtweak, and jack rack as I do play/improvise live with my laptop and some outboard gear.  The LADSPA set tends to do most of what I need for plugins (though it takes a while to learn which ones to like and which to hate), but when I run into a particular task that needs something a little different I jump into PD first, then either csound or chuck if those look like they'd be better for the job (I'm not a supercollider guy but maybe someday).  Synthesis plugins I've rarely ever touched as I find MIDI to be useful more for triggers than for actual nuanced music.  If I need a complicated synthesis patch I'll build it rather than using someone else's sound, if I want someone else's sound I'll sample it and tweak away.

As for your question of repatching, LASH is the answer though it's not fully implemented.  There is also the much lesser ubuntustudio application (not the distro) that is available in the backports repo.   This was an app that opened a selected set of programs for you at once but it doesn't patch things together.

---

