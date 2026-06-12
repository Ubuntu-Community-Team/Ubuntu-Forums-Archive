---
title: "Creative X-fi Surround 5.1 USB, not working properly?"
date: 2009-02-03
forum: Multimedia Software
---

### Post by kbutcher5 on 2009-02-03
I bought a Creative X-fi Surround 5.1 USB, some time ago, for my windows machine, so it never was and never has been inteded for linux.
But i tried it on my linux box, out of curiosity, and it seems to be extremely buggy if it just pnp.

For starters, the sound is the same level always, the volume knob can't change it, the ubuntu sound controls can't change it. Secondly, it only runs in 2.1 mode, and therefore doesn't utilise the speakers properly.
Thirdly, the remote control is even more useless for linux than it is for windows. :P

So my question is, has anyone gotten this to work, and if so, does the remote and volume knob work aswell?

---

### Post by izizzle on 2009-02-03
I read about this somewhere, but I forget where it was. However, it did say something about Removing ALSA and installing......what was it....

---

### Post by kbutcher5 on 2009-02-03
If you remeber do IM me :P
Been searching far and wide for a solution.

---

### Post by BinklesCloryl on 2009-02-04
I am thinking of getting one of those sometime, but if it won't work...then why should I...

> **izizzle said:**
> I read about this somewhere, but I forget where it was. However, it did say something about Removing ALSA and installing......what was it....

Might you be thinking of Pulse-Audio mixer? That is what I use/used to get my usb speakers/headphones working. At any rate, try PulseAudio, and tell me if it works >.>

---

### Post by nagyon ribanc on 2009-04-02
Found something that might help (though I can't get it to work at all, which maybe my lack in knowledge in Open Source stuff)

Check [http://opensource.creative.com/souncard.html](http://opensource.creative.com/souncard.html) which gives lots of info on different soundcards from Creative and how to get them to work in Linux distro's. 

For the Creative X-fi 5.1 surround (USB) you can get a beta driver, which is not supported and also not on their site. (you'd expect it to be as they created it, but yeah ...) The download can be found here [http://tweakers.net/meuktracker/17583/creative-sound-blaster-x-fi-118-beta.html](http://tweakers.net/meuktracker/17583/creative-sound-blaster-x-fi-118-beta.html)
Be aware that if you are using Ubuntu they tested it on 7.10 so that is some time ago.

---

### Post by vorgusa on 2009-12-11
I just got this device for Karmic and it worked great.  I just plugged it in and went to sound preferences.  Make sure under the hardware tab it has Analog Stereo Duplex (this works even for the Digital outs) and then slelect "SB_X-FI_Surround_5.1 Analog Streo" in the output tab.  Unfortunately the volume knob does not work. I have mainly just tested the optical output, but if that works I am sure every other output works.

---

### Post by ceminino on 2010-02-12
any luck with the volume button?

forget the volume button, I can't get surround to work on karmic! did anyone manage to do it?

---

### Post by tanchaz on 2010-03-08
Hello,


Just an "UP" message, with goal to don't create a new subject.

Did anybody get his creative remote control working properly ?


I've tried several tutorials, but, while the sound works perfectly, the remote control is not in love with ubuntu...


Has anyone a new solution to this problem ?

I have also the RM-900B in stock, wich is knewn from lirc (who doesn't seem beginners friendly..)



Thanks a lot,

Tanchaz

ps: sorry for bad english, my mother tongue is french ;)

---

