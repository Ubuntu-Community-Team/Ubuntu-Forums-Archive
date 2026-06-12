---
title: "Sound config with a CMI9880 soundcard on an Asus P5AD-2 Deluxe"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by ternary_bit on 2007-03-19
Greetings all!

     My rather euphoric entrance to the world of 100% open-source computing with the advent of installing Kubuntu Edgy Eft has been a largely successful endeavor, save for a few hiccups here and there.

     One such hiccup has to do with my soundcard, which is a C-Media 9880 7.1 channel card integrated into my Asus P5AD-2 Deluxe motherboard. A bit of an audiophile, I chose a speaker setup that made use of my card's digital fiber optic S/PDIF output for crystal clear Dolby surround. Kubuntu recognized my card's standard 1/4" stereo mini jacks (i.e. the green output) and audio works well when I switch the fiber cable to the standard stereo mini, but S/PDIF optical out does not work. I get no sound when I use my fiber optic setup.

     I know this sounds a bit touchy, but when I use the stereo mini outputs, I get a lot of feedback and general static/nose from my equipment which annoys the hell out of me. Not to mention the fact that I lose my surround sound setup, and yes, I *can* tell the quality difference between FLACs played with an analog setup versus a digital setup. In any case, I really appreciate any help you all can provide and thank you in advance for your time and willingness to help us Linux n00bs!

ternary_bit

---

### Post by ternary_bit on 2007-03-20
Well, after much hair-pulling I seem to have answered my own question. I checked the sticky'd post about audio issues, and following those instructions I reinstalled my ALSA drivers. From there I fired up alsamixer (just type that into a console) and saw that several output channels were muted.

alsamixer listed PCM, Surround, Center, LFE, Side and IEC958 as output channels. I unmuted the "IEC958" output and voila! Crystal clear, 5.1 channel S/PDIF audio. I have read several unanswered posts from people with my same soundcard so I hope this helps. Cheers!

ternary_bit

---

### Post by Ghiepo on 2007-10-25
Hi, I have your exact problem but I'm not able to solve it. In alsamixer I have the IEC958 but It seems off. I can mute or unmute but I can not increase the volume and from my digital optical output I can hear only a PCM signal L+R (My motherboard is a P5AD2 Deluxe too).
Any suggestion? could you explain exactly (with command description) the procedure you used to make it works?
Thank you.
Geppo

---

### Post by Ghiepo on 2007-11-23
Anyone has suggestions??? Thank you.

---

