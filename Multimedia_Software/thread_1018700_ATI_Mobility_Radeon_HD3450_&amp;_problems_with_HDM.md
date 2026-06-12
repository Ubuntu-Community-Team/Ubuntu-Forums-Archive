---
title: "ATI Mobility Radeon HD3450 &amp; problems with HDMI video (and audio) output"
date: 2008-12-22
forum: Multimedia Software
---

### Post by uhappo on 2008-12-22
So, a short styry:

I'm not able to output video, or my laptop screen/desktop, correctly to a HDMI television. Mouse cursor is displayed correctly but everything else is sort of digital mess.

I can view my laptop screen in television, but then laptop screen is digital mess. So it's nothing to do with cable or something like that.

I have ATI 8.12 drivers installed.

So, what's wrong?

---

### Post by homeriq5 on 2009-01-07
I'm having this problem too, is ubuntu not able to handle HDMI?  Vista wins again, it seems like

---

### Post by uhappo on 2009-01-08
Aargh!

We need more input on this issue, c'mon people!

I won't let vista/xp/M$ win, I won't give up!

---

### Post by nickb834 on 2009-01-08
you may be relieved to know that on my machine, not only does 1080p work over HDMI, but so does Audio!

Literally all it took on my Intrepid 386 install was to install the Restricted Driver when prompted by the system after install for the ATI 3450 (From Asus) , and then in sound preferences set everything to  "HDA ATI HDMI ATI (ALSA)" and set the default mixer to "HDA ATI HDMI (alsa mixer)".

Then in volume control set the device to "HDA ATI HDMI (alsamixer)" and ensure that IEC 958 was ticked in the same preference screen. 

After that ensure the volume is turned up and voila!

On my system pulseaudio shows that there are no output devices, so I set everything I could to alsa (except for capture which I am not bothered about).

So ignoreing all the forum advice of tinkering with pulseaudio I had sound working on a 3450 HDMI to my LG475010 TV in about 5 mins after a fresh install.

---

### Post by PhatKat on 2009-01-11
Hehe ok got a mate planning to go with a 790GX HDMI mobo and dual booting Windoze and 8.10 64 bit - bookmarked for reference :popcorn:

---

