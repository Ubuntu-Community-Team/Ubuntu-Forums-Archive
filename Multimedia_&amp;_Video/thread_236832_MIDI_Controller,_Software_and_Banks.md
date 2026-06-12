---
title: "MIDI Controller, Software and Banks"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by jasonkostempski on 2006-08-15
I want to buy a USB MIDI Controller. Does anyone know of one that will definitely work under Ubuntu? Also, I'd like to know what sequencer software might be available and if there are any nice MIDI banks that can be used.

---

### Post by Xanderfoxx on 2008-01-05
I don't know if this helps, but

Investigate the merits of:

[Rosegarden]("http://www.rosegardenmusic.com/")

This is a sequencer that looks really great, and I'm just now trying to get it to work, and I am making progress.

Here's what I recommend you do:

NOTE: Before you follow these commands, please be advised that I haven't yet got it to work perfectly, but I'm close. Just take it carefully.

Ok! Here goes!

First we need to install everything we need.

I got it working by installing the whole audio-development desktop, but this wrecked Compiz Fusion, and by installing a real-time kernel, my nVidia proprietary driver did not work. However, it was only eye-candy, so I wasn't overly ticked at that.

```

sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins flac

```


This will take a long time, so pour yourself a glass of something, and wait.

After it all settles in, you'll need to reboot after such a grueling install, so go ahead and do that.

Now after in reboots, open these applications in order from this menu:

Top-right of screen:

Applications -> Sound & Video -> Audio Production ->
[LIST=1]
[*]JACK Control[LIST=1]
[*]Click "Start" (If it doesn't start, follow the directions given at the bottom.)
[*]Wait, and look for the yellow text that says "started"[/LIST]
[*]ZynAddSubFX Software Synthesizer[LIST=1]
[*]Click "Beginner"[/LIST]
[*]Patchage (Ignore for now)
[*]Rosegarden[/LIST]That should get you up and going. (Yeah, I know, it *is* complex!)

Ok. in ZynAddSubFX, turn up the Master Volume until you can hear it, and click the Keyb.Oct.'s left arrow until it says 3 or 4, try clicking the keys. If you don't hear any sound, then I don't know what to tell you.

If it works, and you have the hardware all setup pretty, then you'll hear a nice reverbed piano or something.

In Patchage, scroll a little down and to the right. Connect, by click-and-dragging a link between Rosegarden's "out 1 - General MIDI Device" output to ZynAddSubFX's "ZynAddSubFX" input.

No you can trigger notes in ZynAddSubFX from Rosegarden.

For from perfect, or maybe I just have to get used to it? :)

Anyway, after you setup all of your instruments by setting Part 1 how you like ti, then clicking the right arrow the the right of "Part" and enable it, you can start making music with Rosegarden.

I'm going to have so much fun, these guys have great synths!

And the reverb is fun, too! :lolflag:

Well, good luck! Don't be afraid to email me: maurin dot alex at gmail dot com about this, okay?

---

