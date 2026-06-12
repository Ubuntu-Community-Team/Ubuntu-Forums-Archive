---
title: "dsp dsp1 and dsp2 got swapped?!"
date: 2006-02-12
forum: Multimedia &amp; Video
---

### Post by ivago on 2006-02-12
Hi, 

something strange happened, after running my breezy setup for months without probs I got this strange behaviour.

I have 
- 1 creative pci128 (ens1370) wich i use for audio playback (dsp)
- 1 hauppauge tv/radio card (for FM radio) wich uses v4l (dsp1)
- 1 voip cyberphone for skye (dsp2)


All of a sudden my dsp2 usb phone became dsp so all the music from bmpx, mplayer comes out my usb phone instead of my speakers.

Radio is still ok (plays back from /dev/radio) connected with a cable to my es1370 (creative labs pci128 audio card) so both pci cards are still working perfectly OK.

How can I switch my usb phone back to dsp2 and my creative labs pci128 sondcard back to the default playback device for  mp3 and system sounds /dev/dsp  :?:

thx in advance:!:

ivago

---

### Post by ivago on 2006-02-12
k, got it by choosing 'system' -> 'preferences' - 'sounds' but it's still strange behaviour...

---

### Post by ivago on 2006-02-13
booted up my box and this problem is back :( But now even choosing
System -> Preferences -> Sound and choosing my Ensonq AudioPCIas the default soundcard doesn't solve my problem.

so how do  I  swap the dsp and dsp2 devices on the command line??

---

