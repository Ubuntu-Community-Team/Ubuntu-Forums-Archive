---
title: "Streaming Audio capture Test Results?"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by discmaster on 2007-10-27
I am unable to capture any audio stream; From radio station websites, or what I am playing through the speakers, etc. I can hear everything just fine, but can't record anything, using a program such as audacity, etc.I have an ASUS A8V-VM SE mainboard w/ onboard sound.

When I do a  test for sound capture in sound preferences, this is what I get; No matter which device I choose under capture, I still get the same error. Does this make sense to anyone? 

[[IMG]http://img135.imageshack.us/img135/9074/soundtestxs0.jpg[/IMG]](http://imageshack.us)

---

### Post by pieisgood4589 on 2007-10-27
> **discmaster said:**
> I am unable to capture any audio stream; From radio station websites, or what I am playing through the speakers, etc. I can hear everything just fine, but can't record anything, using a program such as audacity, etc.I have an ASUS A8V-VM SE mainboard w/ onboard sound.

When I do a  test for sound capture in sound preferences, this is what I get; No matter which device I choose under capture, I still get the same error. Does this make sense to anyone? 

[[IMG]http://img135.imageshack.us/img135/9074/soundtestxs0.jpg[/IMG]](http://imageshack.us)


K, if you are using Ubuntu 7.10, it's a major bug that basically EVERYONE'S having, including me. They have not found a solution yet... Post back if you are using 7.10! :popcorn::guitar::lolflag::guitar::lolflag::guitar::lolflag::popcorn:

---

### Post by discmaster on 2007-10-27
I am using 7.10; Ubuntu Studio at this point. BUT, I had the same issue 7.04. I know the sound issue is a big one, but some folks seem to be able to get it working.

I don't know weather to fault the sound card, etc.? It would be nice if there was some command line tool to run that would pinpoint the problem.

---

### Post by ron999 on 2007-11-14
Hi discmaster
I'm able to capture using 'arecord'.
I followed this tutorial here:-[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

When it's set up right, the command
**arecord -f cd  output.wav**
will capture whatever's coming through your sound card.

---

