---
title: "HDA Intel Digital Output on Karmic - just a stupid tip"
date: 2009-12-05
forum: Multimedia Software
---

### Post by vanRaewa on 2009-12-05
I'm not sure if this is gonna help anyone at all, but in my case
I have two sound cards - Creative X-Fi and the integrated HDA Intel (I don't remember the name of the circuit). My default card is X-Fi, but when watching movies on my TV I use the Digital Output if the HDA Intel card/circuit. 

This worked almost perfectly in Jaunty, and when I recently did a clean install of Karmic both cards was detected and installed properly. 
However, whichever way I tried to redirect sound to the digital output in using Digital Stereo ( IEC958 ) i couldn't get it to work (even though the sound stream showed that <something> was playing on the card). All volume sliders were set at 100%, so that couldn't be the problem. 

I then tested ```
alsamixer -c 1
``` where 1 is the card id of the HDA Intel card as reported by ```
aplay -l
``` I went all the way to the IEC958 channel and guess what - the volume was 0. I turned it up and now the sound could finally be heard.

Seemed kinda stupid when I found it, but the volume did appear to be set in gnome-volume-control. Wasn't to obvious then...

---

