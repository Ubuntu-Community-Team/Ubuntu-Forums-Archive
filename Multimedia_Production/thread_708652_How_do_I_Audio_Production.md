---
title: "How do I: Audio Production?"
date: 2008-02-26
forum: Multimedia Production
---

### Post by Zeotronic on 2008-02-26
I am making a game, and despite my best efforts I have not been able to learn how to, or find someone who can, make sound effects and music for my game. I have messed with MANY programs to make music and sound and almost always they don't work, or I cant get them to work, or I don't understand them at all, or etc and so-forth. What programs can you advise? What is involved to make them work properly? and finally where are tutorials to learn them? Perhaps if you have some sort of profound insight, you can benifit from the knowledge that I am a C++ programmer/graphic artest, when paring me up with an audio program.

---

### Post by Stochastic on 2008-02-26
well first designation I'd make is between sound effects and music for your game

Sound effects, I assume, would be things like windows smashing and bombs exploding.  For this, I'd recommend either recording these yourself via foley (a labour intensive process that doesn't always get great results unless you know what you're doing & have the audio gear to do it) or taking them from online sources (try [www.findsounds.com](www.findsounds.com) for instance) though that may have issues with liscences.
For both of these tasks you'll need an editor; lots of people use Audacity, I prefer Rezound, but there are many others around.

Music will need some form of synth such as QSynth (need to download a soundfont before it'll do anything), ZynAddSubFX, or others, and a means of recording said synth (Audacity, Rezound, or Ardour will work).  Hydrogen is your best bet for drums.  Or you could use an all-in-one type app such as Jokosher or LMMS (maybe even Rosegarden, but that's a bit complicated to learn).

If you're looking to program audio to respond to events in your C++ program, I'd suggest learning a bit about a music programming language such as PD, ChucK, CSound, or SuperCollider.  Though that may be overkill if you know how to program audio in C++.

This may have confused you more than helped, but feel free to ask further details.

---

### Post by robeast on 2008-02-27
I'd like to write music for your game. If you're going to make money from it I'd appreciate some bones, but I'll do it for free if it's independently developed just for the fun of it!  \\:D/

Learning an audio editing program takes some time, getting good at it takes way more, having enough musical and ambient ideas on top of doing all the programming is nuts! I've got a solid work flow down in my home studio and I'm ready to rip out some tunes! What's your game like?

---

### Post by gorgon on 2008-02-27
I'm told that SuperCollider ([http://en.wikipedia.org/wiki/SuperCollider](http://en.wikipedia.org/wiki/SuperCollider)) has a similar structure to C++, but if you got any programming skills I'd recommend it anyways if you want synthesized sound. There are even some patches that emulate amiga, SID6581f, Astrocade, etc ([http://www.fredrikolofsson.com/pages/code-sc.html](http://www.fredrikolofsson.com/pages/code-sc.html)), and various other game machine sound chips if that's your fetish :)

Resources:

download:
[http://supercollider.sourceforge.net/](http://supercollider.sourceforge.net/)

the swiki has tutorials and such:
[http://swiki.hfbk-hamburg.de:8888/MusicTechnology/6](http://swiki.hfbk-hamburg.de:8888/MusicTechnology/6)

..but you might know this allready. ;)

---

### Post by chipants on 2008-02-27
everybody's suggesting midi/synth environments. don't forget, if you have any skills with musical instruments, you can always record semi-traditionally with a multi-track recording application such as ardour. there is a bit of a learning curve; but, it is a great application.

no matter which way you go, you'll need a few things before you start making music:

1) a sound card supported by ALSA (i'm assuming this is already the case)

2) jack (the jack audio connection kit) - an app that allows you to route audio between applications ([http://jackaudio.org/](http://jackaudio.org/))

3) qjackctl - a graphical frontend to jack, including an easy way to 'connect' audio applications

4) a sound source. this could be actual instruments recorded with a microphone, or synthesizer apps. stochastic mentioned qsynth and zynaddsubfx. these are two awesome applications that would be great. especially zyn for electronicy videogame music. also, hydrogen is a very easy, yet amazingly powerful drum machine.

5) an application to record it all! audacity is easy and simple. but, if you need multitrack recording, consider ardour. some people like LMMS and jokosher, but those apps are still relatively new to the scene. basically, there's less of a community to help you along if you need it.

all that being said, sound effects are a little tougher than music if you want to create your own.

it is all a bit much to swallow. you may be better off using other people's music. what kind of game are you writing? platformer, fps, etc? what is the general mood of the game? do you want something bleepy? you know, reminiscent of old 8-bit stuff? that can be tons of fun to record.

i'd also be interested in doing some music for your game. as long as it is going to be open source, i'd be willing to donate a song or two completely free. not really interested in commercial projects, though.

---

### Post by Zeotronic on 2008-02-27
> Sound effects, I assume, would be things like windows smashing and bombs exploding. For this, I'd recommend either recording these yourself via foley...
Yea, thats what I intended to do... I don't want to have to bother with licensing on audio repositiories, and I don't want to use something that has been used by a million other games (except for some of those classic sounds... but I wouldn't want to use them for fear of the licensing). To that end, can anyone reccomend equipment for someone on a limited (though not unrealistically so) budget?
> If you're looking to program audio to respond to events in your C++ program
Thanks for the suggestions, but I already know how I'm going to go about doing it.

> I'd like to write music for your game. & > i'd also be interested in doing some music for your game. as long as it is going to be open source
My game will be open source... I do not yet have any cohorts (despite my effors with the locals) so its not even possible for the decision to be changed by group vote. While it seems to me that it would be difficult to illustrate what I will need music wise, I will keep you in mind for when I have a demo ready (I have a specific game in mind, but if I point it out I could very possibly pollute creativity.)

> what kind of game are you writing?
2D platformer, with Box2D physics. Think Mario, yet think Castlevania, Metroid, and Kirby... now, while your confused I'll pick your wallet. ;) While it may or may not be done to death, the game is going to be a ninja game... I'm going for a slighly freasher than 16 bit look and feel.


I will explore the programs suggested here later, when time is more allowing and when I feel like messing with something other than code and graphics for a bit.

---

### Post by Stochastic on 2008-02-28
If the game is open source you may want to reconsider using online sources.  There are a growing number of samples and full songs available in creative commons license or (a little less so) in full GPL

---

