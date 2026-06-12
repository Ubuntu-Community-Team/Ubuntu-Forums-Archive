---
title: "Trouble getting sound card to work..."
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by dmber on 2006-11-28
I followed the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=205449"), finding what i think is my sound card [here.]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VIA#matrix")

I don't know off the top of my head the actual model of my soundcard so i tried to figure it out from the instructions from the first thread i linked. 

after typing ```
~$ lspci -v 
``` into the terminal i found this: 

```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
        Subsystem: ABIT Computer Corp.: Unknown device 140b
        Flags: medium devsel, IRQ 193
        I/O ports at c800 [size=256]
        Capabilities: <available only to root>
```
am i correct to have deciphered that my soundcard is a VIA model 8233/A/8235/8237?  if so, what does that mean in conjunction with my [second link]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VIA#matrix")?  

that's where i'm stuck.  can anyone help me please?

thank you

---

### Post by lhtown on 2006-11-29
Basically, it means that you have a really cheap sound card/modem. Getting a new sound card that supports multiple channels is not a bad idea at this point. Software audio mixing is a bit spotty in Linux currently, although it can work if you are willing to fiddle with it at times.

Since you don't need the modem, you can focus on the sound card.

You can check Sytem > Preferences > Sound to see if it was detected by your computer. (I'm betting it was.)

Assuming it was detected properly, you can search the forums for more information on how to configure it or just play with it until you find something that works.

---

### Post by dmber on 2006-11-30
hmm...it must not be recognizing my sound card, then, because i do have a multi-channel soundcard.  i have a 5.1 card that works fine with XP.  i think the one that its recognizing is on my motherboard.  does that make sense?

---

### Post by lhtown on 2006-11-30
Are you saying that you have more than one soundcard installed on your computer?

---

### Post by dmber on 2006-11-30
well there's one on my motherboard...right?  sorry to be confusing, my old roomate built my computer for me.  the way i understand it, there's a "sound card" built in on my motherboard, and then there's the one we actually installed.  the one we installed is 5.1 (i know that because i'm listening to 5.1 right now.  now that i think about it, i'm pretty sure it's philips.

EDIT: ok.  i figured it out what model my sound card is:

philips PSC706

---

### Post by dmber on 2006-12-02
i don't know if i'm not supposed to bump (sorry if i'm not) but i figured out that my sound card is a philips psc 706 but i don't know what to do from there.

the sound card works fine in windows...i'd really like to get it working in ubuntu.

thanks!

---

