---
title: "Looking for a program ----"
date: 2009-02-02
forum: Multimedia Software
---

### Post by hatewindows on 2009-02-02
That will record what is playing on your pc speakers then save that to say a wav file or mp3 file.. I see there is a program like that for windows--But i dont deal with windows!  The site for the windows recorder is----
[http://www.mp3mymp3.com/mp3_my_mp3_recorder.html](http://www.mp3mymp3.com/mp3_my_mp3_recorder.html)

I need something like this for ubuntu 8.10   Thanks for any help!!

Mark   LI NY]

---

### Post by Crafty Kisses on 2009-02-02
Maybe Audacious? Try it.

---

### Post by hatewindows on 2009-02-02
Yeah i saw that one--It does just about everything but record.. I'm looking for a program that will record to hard drive what you hear coming out your speakers... Thanks for your help!!

---

### Post by skullmunky on 2009-02-02
I've seen this question a bunch before but never seen a clear answer, so I thought I'd give it a shot.

It turned out to be really easy.  Disturbingly so.  I don't understand why it was so easy.  

Answer: use Audacity, just click the Record button.

Now here's what I did.  This may only work for this specific combination of programs, and there may be mixer settings I've accidentally set up in the right manner without knowing it.


1. Open Amarok.
2. Play a radio stream
3. Open Audacity.
4. Click the Record button.
5. Done

Specifics in this test:

Kubuntu 8.04
Audacity 1.3.5-rc3
 Recording set to "ALSA: default" (default)
 using Portaudio v19

Amarok 1.4.9.1
 Sound system: xine (default)
 Output plugin: Auto (default)

Sound card: Nvidia CK804, standard onboard chip

Mixer Settings:

In "Input", "Capture" is enabled.  There is a volume slider but it doesn't matter.

This may or may not work, depending on the program you're trying to record from.  I just tried this with the game "GJeweled", for kicks, and that worked fine too, which is great b/c I love the music (it's like William Orbit on a classic NES cart).  If you're using an app that can use the Jack sound system, you can just route the output from it into Audacity or Ardour to record it.  If the app is really old and only uses OSS this method may not work; if not you can try the 'aoss' ALSA->OSS wrapper to run the target app, too.

---

### Post by Crafty Kisses on 2009-02-03
Yeah that's how I would usually do it. ;) Nice post skullmonkey!

---

### Post by hatewindows on 2009-02-03
Thanks so much!!!!!! Great help!!             Mark

---

