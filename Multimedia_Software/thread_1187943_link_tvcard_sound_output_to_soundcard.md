---
title: "link tvcard sound output to soundcard"
date: 2009-06-15
forum: Multimedia Software
---

### Post by Aijse on 2009-06-15
Hi there,

I about finnished my Mythbuntu project, I can play videos, listen to music, and now I've also got myself a tv Card. I finally got the channels arranged the way I wanted and got it matched with the EPG data, tuned in for a show and was surprised by high pitched tones and beeps.
I found out that the sound output of my Hauppauge GO2 wasnt the problem per se. When I wire the card directly to my soundsystem it has good sound. But I need to wire it to my soundcard, and then have the soundcards audio out to the stereo. Somehow the tv-card interferes with the sound output, even when there is no wire from the tv card to the soundcard!! 
Can some one tell me what the problem could be?

Im on mythbuntu 8.04 

[FONT="Courier New"]lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:03.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:03.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)[/FONT]

thanks in advance

---

### Post by Aijse on 2009-06-15
found the solution  here

[http://ubuntuforums.org/showthread.php?t=626282]("in this thread")

---

