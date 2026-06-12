---
title: "TV card sound problem"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by cos4 on 2007-02-03
I'm using a Cingery 400 TV card(*), ALSA and tvtime as gui to watch TV. I'm living in Germany so I use PAL-BG.
Everything seems to work fine but in the background there's a very high sound. Something like a "beep" or so but very high. It isn't really loud but over the time it's really annoying.
This sound only occurs when I use Linux(what I mostly do), using Windows it works fine. 

Do you have any idea how to solve that? I guess some configuration of the driver isn't correct.

*)The card is using the saa7134 chip and according to the German ubuntuwiki the tda9887 module is providing the sound(theres a cable tvcard.soundout to mainboard.lineIn at the back of my PC).

---

### Post by josesanders on 2007-02-05
Your card has an audio output that you connect to the sound card to get sound input.  It is also possible to get sound from the TV card directly, but that has been very problematic, which is why they provide the output.  Make sure the sound you are using is coming from your sound card and not your TV card.

Then, check if you have sound on the audio output of the TV card by plugging it into a stereo or something other than your computer.  If you do have sound, do you have the same interference?  If you don't have anything on that output at all, you can run this command to manually unmute the output:

$ v4lctl -c /dev/video0 volume mute off

In order to execute that command, you need to have xawtv installed, so if you don't, then do this first:

$ sudo apt-get install xawtv

If there is no problem there, but there is a problem when you plug into your sound card, then the problem is with the sound card, and not the TV card.  If you do have the problem there, then you know that the problem is with the TV card.

I hope this helps.  Those saa7134 cards are always trouble.

---

### Post by cos4 on 2007-02-18
The output of the soundcard also contains some kind of a noisy beep so it's really a TV-card problem I guess. Any ideas?

---

