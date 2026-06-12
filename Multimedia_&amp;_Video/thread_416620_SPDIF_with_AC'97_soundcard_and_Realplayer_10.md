---
title: "SPDIF with AC'97 soundcard and Realplayer 10"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by ThomasNovin on 2007-04-21
Hi all

I had problems getting the sound to work OK in Feisty, there was only output on my headphones and not on my receiver which is connected on the SPDIF-output on my soundcard.

I eventually found somewhere that I should create a ~/.asoundrc containing this:

pcm.!default {
     type plug
     slave {
          pcm "spdif"
          rate 48000
          format S16_LE
     }
}

That worked! 

However, when I try to play stuff in Realplayer (10.0.8-0ubuntu3) there is no sound output on the SPDIF but only to my headphones!

Anyone got a clue?

---

### Post by ThomasNovin on 2007-04-23
Found a solution:

Install the alsa-oss package via Synaptic.

Edit the Firefox rc script:

gksudo gedit /etc/firefox/firefoxrc

Change the line FIREFOX_DSP=”none” to FIREFOX_DSP=”aoss"

This solves the problem when you are using realplayer in Firefox.

If you want to run the stand-alone application, start it with:

aoss /usr/bin/realplay

---

