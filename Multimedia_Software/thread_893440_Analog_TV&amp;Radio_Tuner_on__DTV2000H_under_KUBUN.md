---
title: "Analog TV&amp;Radio Tuner on  DTV2000H under KUBUNTU Hardy"
date: 2008-08-18
forum: Multimedia Software
---

### Post by xbesnard on 2008-08-18
Hello guys,

I need some help to operate properly my LEADTEK DTV2000H board on my PC (ATHLON 64/3000, KN8-ultra, ATI X800 GTO, Kubuntu Hardy/Kernel 2.6.24-19-generic). I post on this forum.

This board supports one DVB entry, one analog TV entry, one analog entry for video capture and one radio tuner. 
The v4l2 driver supports the DTV200H  (#define CX88_BOARD_WINFAST_DTV2000H  51).

All entries work under WXP properly. However, under Kubuntu, I only succeed on using properly the DTV entry with Kaffeine (Video reception and sound are good). 

But I found very little information on how to operate the others entries. For the radio entry, it doesn’t work at all with Kradio, Kaffeine.  I got only a /dev/video0 entry but no /dev/radio* device.

My first idea is to have a confirmation that those entries (analog TV, radio and video capture) are or are not supported by the driver 

If yes, I would be very grateful for any help on this topics.

Thank you for your feedbacks. 

Xavier.

---

### Post by bouncingmolar on 2008-08-31
i cant get the radio working either. i've searched the forums and i think noone has figured that part out.

definately the tv part works though.

---

### Post by xbesnard on 2008-09-15
Hello, 

I found this [page ]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Leadtek")on the subject
However it only said "FM tuner is not found, no radio function". But, is it a restriction in the driver or something else. I dont know.

 [http://ubuntuforums.org/images/smilies/confused.gifContinue](http://ubuntuforums.org/images/smilies/confused.gifContinue) Continuing searching information on this subject...

Bye. Xavier

---

