---
title: "Dosemu Sound In Lucid"
date: 2010-06-05
forum: Multimedia Software
---

### Post by Kenneth D. Gladden on 2010-06-05
Dosemu sound worked fine in ver. 9.10.
Cannot get Dosemu sound to work under Lucid. Any help would be appreciated.

---

### Post by Kenneth D. Gladden on 2010-06-10
Doesn't Any One Have Any Ideas?

---

### Post by emendelson on 2010-07-18
> **Kenneth D. Gladden said:**
> Dosemu sound worked fine in ver. 9.10.
Cannot get Dosemu sound to work under Lucid. Any help would be appreciated.

In your .dosemurc file, try changing the default sound device to /dev/snd by adding this line below the commented default line (# sb_dsp = "/dev/dsp")

$_sb_dsp = "/dev/snd"

This worked for me, but I also installed quite a lot of additional sound software, so I don't know if it will work on a default installation.

---

### Post by Kenneth D. Gladden on 2010-07-18
Thanks for your reply.

I do not have a .dosemurc file, but the line you refer to is in 
the dosemu.conf file. Tried the change here.

Did not work.

thanks

---

### Post by emendelson on 2010-07-18
In the same file, try changing:

# $_sound = (on)

to

$_sound = (2)

(note comment removed)

and also try replacing /dev/snd with /dev/audio

---

### Post by Kenneth D. Gladden on 2010-07-19
Thanks Again.

It does not solve the problem. One weird thing,
I have several programs written and compiled in Power Basic.
These programs use notification sounds which work, although 
distorted, until a key is pressed on the keyboard. 
After a key is pressed no more sound in dosemu until the computer is restarted.

Thanks
kdg

---

### Post by emendelson on 2010-07-19
Did you upgrade 9.10 to 10.04, or did you make a fresh installation of 10.04? If it was an upgrade installation, you might try a fresh installation instead. If 10.04 was a fresh installation, of course ignore this.

---

### Post by Kenneth D. Gladden on 2010-07-20
Fresh installation on two machines. a desktop and a laptop.
Same problem on both machines.

---

### Post by crixtiano on 2011-01-16
I'm with the same problem.

Sound doesn't work in dosemu in Ubuntu Lucid.

I'm trying to run Simcity 1 and if I enable sound, the game freeze.

The "beep" DOS command doesn't work too.

Please, I need some help too.

Thank you!

Cristiano

---

### Post by theotheo on 2011-01-30
Hi all,
couldn't even activate PC speaker beep for simple DOS orgram (File Express 6.0, running o.k, by the way). I'm using Lucid with Pulseaudio without sound problems in normal ubuntu use. Tried all variations suggested in the etc/dosemu/dosemu.conf file. No success with midi, no success with PC speaker at all.
Any ideas (WITH Pulseaudio)...?

---

