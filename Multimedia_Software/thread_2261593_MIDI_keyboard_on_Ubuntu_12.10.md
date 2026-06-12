---
title: "MIDI keyboard on Ubuntu 12.10"
date: 2015-01-20
forum: Multimedia Software
---

### Post by selvaswami2 on 2015-01-20
I'm trying to get my new M-Audio Axiom MIDI keyboard to run on my Ubuntu 12.10 box. I have the latest versions of Jackd and Ardour running, and opening a new session, but get no sound through the headphones or speakers.

What am I missing? Could it be video drivers?

Thanks for any help or advice.

---

### Post by marseille2 on 2015-01-20
I'm no expert, but I just went through a similar issue this weekend and got some really good help. 

Supposedly, your keyboard should work out of the box (see [link]("http://linuxmusicians.com/viewtopic.php?f=6&t=10280")). But here's some very basic troubleshooting tips I received.

1.) Make sure that you have audio. Open up Yoshimi, then test for sound through the virtual keyboard ... to confirm that sound works.
2.) If sound works, then decide how to route signal from the keyboard to ardour (via soundfont loaded in synth, etc; if no sound exists, then check your audio card and/or Jackd connections).
3.) Open up the mixer in Ardour. Choose the track you'll record the keyboard to. Click on inputs for that track, and after the window pops up ... in one of the tabs you'll see where you activate the  connection (on Ardour3 it's a different tab from system output). Then arm the track, and start recording.

---

### Post by mörgæs on 2015-01-20
12.10 is out of support. Better to begin with a fresh install of 14.04.1 or 14.10.

---

### Post by selvaswami2 on 2015-01-20
Thank you for your responses. I'll give it another try today.

---

