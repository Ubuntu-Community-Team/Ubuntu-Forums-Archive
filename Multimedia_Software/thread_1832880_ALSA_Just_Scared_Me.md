---
title: "ALSA Just Scared Me"
date: 2011-08-25
forum: Multimedia Software
---

### Post by kid1000002000 on 2011-08-25
ALSA just scared the crap out of me. I listen to media using a pair of IEMs via a USB sound card, the Creative soundblaster SB1140. Naturally, I woke up this morning to begin work, put my headphones in after a resume from standby, and just about crapped my pants from something that resembled a fighter jet inside my head.

It's time to get this fixed. Here are the technical details.

My computer has two soundcards, one onboard (Realtek), and one from USB. In order to get the USB one to work, here are the steps I must follow everytime I plug my USB card into the laptop.

[LIST=1]
[*]Open terminal. Run "alsamixer."
[*]F6 to select soundcard
[*]Turn volume to soundcard all the way up, mic volume all the way down (reduces hiss).
[*]exit alsamixer
[*]Click on the sound icon in the appmenu, go to "sound preferences"
[*]Click "output" and select the correct "3od3" soundcard option.
[*]*Adjust* the volume using the volume icon. If I don't, it may blast full volume until a volume step adjustment.
[/LIST]
I'd like to reduce those 7 steps into something that just happens automatically. Also, I'd like to not get blasted by sound when I resume from standby. Here's the details:

[LIST=1]
[*]Run the 7 steps above and listen normally
[*]Shut the lid to the laptop, wait for it to standby
[*]Remove USB card.
[*]Travel/whatever
[*]Plug USB card back in
[*]Resume from standby
[*]Get maxed out volume of sound from USB card, volume adjustments showing on the screen but doing nothing to reduce volume.
[*]Navigate to the ubuntu sound menu again and reselect the correct sound output after it defaulted to the internal card.
[LIST]
[*]Note that this time, I was getting full volume output from my USB card, whereas in the previous 7-step program, I started out with *no *sound from the USB card.
[/LIST]
[/LIST]

Please help me (and my hearing).                                      ](*,)

---

### Post by kid1000002000 on 2012-01-15
Workarounds are good, but don't forget to subscribe to this bug.
[https://bugs.launchpad.net/ubuntu/+s...on/+bug/871133]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133")

---

