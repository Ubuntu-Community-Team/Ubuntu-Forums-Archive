---
title: "no sound from sb audigy"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by IanRH on 2007-10-26
I am running Gutsy Gibbon and very impressed however I have sound problems similar to those reported in earlier threads

~$ cat /proc/asound/cards produces

 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at 0xa000, irq 23
 1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0xc400, irq 23

so I tried $ sudo asoundconf list

Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
SI7012
Audigy

Which seems to confirm the first piece of information

I then tried as recommended

 sudo asoundconf set-default-card Audigy
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

and I was able to hear a radio station for about ten seconds and then no sound at all.

Alsamixer showed the Audigy card so that was successfull! BUT nothing showed about the "Audigy Analog/Digital Output Jack" on the GUI.

I tried the Gnome Alsa mixer GUI but that shows the card as a Realtek ALC655 rev 0

I have now, I think, tried all the solutions on the thread so am pleading for some help.

IanRH

---

