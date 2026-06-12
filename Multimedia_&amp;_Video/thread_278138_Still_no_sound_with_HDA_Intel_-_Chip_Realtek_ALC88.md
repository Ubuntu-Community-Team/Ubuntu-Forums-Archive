---
title: "Still no sound with HDA Intel - Chip Realtek ALC882"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by didobuntu on 2006-10-15
Hello,

I still never succeeded to get sound on my Asus laptop. My card is an HDA Intel with a Chip of Realtek ALC882.

When I do the command "cat /proc/asound/cards", I get the following result:

0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xfebfc000 irq 66
1 [SAA7134        ]: SAA7134 - SAA7134
                     saa7133[0] at 0xfeaff800 irq 169


That is, the sound card 0 is detected (and the tv card 1 I guess, the saa7134, does not run too).

When I do tha command "aplay -L", the "spdif" device is present.

And when I launch "alsamixer", the card is well identified as an HDA Intel card with the Chip Realtek ALC882.  But when I scroll to the right to see the item "IEC958", I cannot move that setting to get it to 100%. It not responds and it is always at 0%.](*,) 

Is that normal? .. Any help of what can I do to get sound at least via the headphones?

Thank you in advance for you answers

---

### Post by Cannaregio on 2006-12-02
Have exactly the same problem

```
cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff8000 irq 169
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfddfe000 irq 225

```

The Intel card sounds nice enough, but why is the Realtek ALC882 not usable?

---

### Post by didobuntu on 2006-12-04
Well because I think that alsa project are busy enough to concentrate on this problem.

Many integrated hda-intel sound cards exist.. and there are many different realtek chipsets ... all those stuff have the denomination hda-intel .. but in reality for each Realtek chipset there is it's own specification.

I think the problem comes from the constructor Realtek who develops driver only for windoze forgetting all about Linux. Fortunately there is alsa project which develops free drivers .. but they are to much busy.

I tried other Linux distros ... and the problem is the same ... I stay with muy favorite ubuntu distribution and hope that the drivers will come soon.

---

### Post by didobuntu on 2006-12-04
I saw in some chat rooms that hda-intel with Realtek alc882 chipset  can run, partly, in Desktop configurations. Not well, but at least there is sound.

I think that for the asus w2jc laptop, there is also another problem of conflict between the hda-intel and the saa-7134 card (which I think is a tv card).

---

### Post by ema on 2008-01-13
On my notebook, I have HDA Intel with ALC882.

Output works great, is the integrated microphone that doesn't work.
I posted in hardware section about it...is anyone able to make microphone work?

Thanks,
Ema! :-)

---

### Post by MicShadow on 2008-05-15
Try unmuting the surround channels and making sure Nvidia HDA is selected in sound properties. under Hardy Heron. Worked for me

---

