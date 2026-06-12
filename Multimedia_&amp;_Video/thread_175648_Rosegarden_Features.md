---
title: "Rosegarden Features"
date: 2006-05-13
forum: Multimedia &amp; Video
---

### Post by jamesshuang on 2006-05-13
Hello everyone, sorry to post this here, but considering that rosegarden doesn't have real forums, I can only ask here...

Anyways, I've just got jack, qsynth, and all that good stuff working properly and in conjunction with rosegarden. However, rosegarden is missing a few critical features (at least for me)... I was wondering if I just overlooked them, or if they really don't exist?


1) Tempo scaling. The tempo window gives me all the midi tempo change events, but that's not quite what I want. I need to be able to scale the ENTIRE tempo, for example, half speed, full speed, double speed, etc.

2) Some recording options. For MIDI-based recording and such, I've always used Finale and windows. Finale had some nifty features, such as "SpeedyEntry", where you hold down the chord, then select the note duration on the computer keyboard, and it inserts the note. Works great for transcribing a peice of music already in front of you...

3) Some more recording options. In Finale, it was possible to denote the beat by tapping on the pedal. Is something similar possible in rosegarden?


I'm not even sure if rosegarden is completely the right program for what I need. If anything, it would be awesome if I could get something like Finale running, but right now rosegarden looks more like a pared-down cakewalk missing some important features Anyone have any suggestions of alternatives?

---

### Post by jamesshuang on 2006-05-15
Hmm... not to be replying to my own post, but I think I've found a workaround for this, although it's not optimal. Seems that wine has actually gotten to a stage where running Finale 2003 is fully possible. Not only that, if alsa is selected in winecfg as the audio output, it's possible to also get the midi to properly to come through qsynth... Very impressive, overall. Anyways, here's what you do:

1) Open qjackctl and qsynth, and connect Midi Through to qsynth using qjackctl
2) Install some version of Finale that's NOT 2006 using wine.
3) If you have a keyboard, connect the Keyboard to Midi Through as well.
4) Open Finale, Midi->Midi Setup, and configure both MIDI in and out as Midi Through. Everything should work fine!

The only issues I've encountered is that Finale is pretty slow in wine. If you click play, then stop, it will take a second or two to respond again. Finale 2006 WILL work (I tried it), but it's REALLY buggy, and it's horrendously slow. Trying to write notes with simple entry is torture. Not only that, all sorts of weird error messages pop up when you try to open, close, or save any file. I'm using Finale 2003, the last (legal) version that I have :D, and it's working marvelously. Finale 2002 also works, as does 2001. 

As impressed as I am with wine, I'm still fairly disappointed that the opensource world hasn't come up with something similar yet... Here's to hoping that Rosegarden will eventually make it to a level where I CAN use it! Perhaps if I have the time and energy, I'll even pick through the source code as well...

---

### Post by dolson on 2006-05-16
Not all programmers are musicians.

Not all musicians are programmers.

If you are one, maybe you are interested in becoming the other, so as to help out the scene?

---

### Post by jamesshuang on 2006-05-16
haha, I'll try my best! Being in college as neither a musician nor programmer is quite a challenge, but they are my two favorite hobbies. Time is never in excess...

---

### Post by dolson on 2006-05-17
I agree. I am not in college anymore, but I'm actually working as a Perl developer now.

When I have time, I might work on a music app. My ultimate software would be a GTK2 version of the Yamaha RM1x or Roland MC-505 devices. I don't know that I have the ability to do it, but maybe some day I will try.

---

### Post by ronlybonly on 2006-05-27
Linux still lacks a GOOD sequencer. Rosegarden is pretty darned slim as far as features go.

-Andy

IF there any programmers/musicians out there who want to work on Rosegarden, I would love to see an arpeggiator built in.

---

### Post by dolson on 2006-05-27
I'm surprised at how featureful Rosegarden actually is given that it got that way with very little financial support - just like almost every other open-source application.

To compare any open-source software to commercial apps and complain about things that are lacking is silly. Thousands of people pay millions of dollars to commercial companies for commerical music apps, it is not a wonder that their developers can produce more features than people who code on an application in their spare time.

The alternatives? BUY a copy of Windows and a commercial sequencer; donate a lot of money to sponsor development on free applications; learn to code yourself and submit patches; or be happy with what you get for free.

Since I refuse to buy Windows, and I don't have money to donate, and I am not that good at programming, I settle for the last option.

---

### Post by viciouslime on 2006-06-03
[QUOTE=dolson]
The alternatives? BUY a copy of Windows and a commercial sequencer; donate a lot of money to sponsor development on free applications; learn to code yourself and submit patches; or be happy with what you get for free.

Since I refuse to buy Windows, and I don't have money to donate, and I am not that good at programming, I settle for the last option.[/QUOTE]


Lol very well put! :)

---

### Post by DatBugler on 2006-09-01
jameshuang - Thank's a ton for that workaround!  I can finally be productive on my Linux system!

ronlybonly - Ardour GTK is a pretty nice sequencer, and you can use the LADSPA effects rack for all your bells and whistles.  There's even an open source arpeggiator program that you can find on the Ubuntu Studio website.  Rosegarden just isn't a sequencer, it's a GUI notation program.

---

### Post by kellogs on 2006-09-07
as an added note, if you find rosegarden a little resources-heavy, you could try seq24, its on dapper repository and its very minimal and light.

You can connect everything to it, for example jack-dssi-host works with it, all dssi plugins and all jack compatible plugins.

I think seq24 is a fine example of a good sequencer that is very friendly and you can run it without overloading the system.

last, I get better timing response with seq than rosegarden.

---

### Post by dolson on 2006-09-07
I love seq24. :D

---

