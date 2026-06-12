---
title: "Surround Sound Problem"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by TheZorch on 2008-02-15
Ok, first of all my Surround Sound "is" working in Ubuntu 7.10.  I get actual surround sound in DVD on Xine and VLC.  The main problem I have is that the volume for the front and rear speakers don't synchronize.  I have to set them separately.  Now I've tried this in .asoundrc file ...

pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

But it either it doesn't do anything or sound stops working altogether until I remove this code.  I have an internal PCI Sound Blaster Live 5.1 card using the .EM28028 chip.  I don't have actual surround speakers but two sets of speakers; 2.1 speakers in the front and a set of 2.0 speakers in the back.

What I need to do is get the Master Volume and Wave Surround volume controls to synchronize.  Some people have recommended trying Alsamixergui but that doesn't help either.  Any suggestions?

--TheZorch
[email]thezorch@gmail.com[/email]

---

### Post by kyphi on 2008-02-18
Of course you have to adjust the front and rear channels separately.

Surround sound, in this instance, is synthethised - it does not mean quadraphonic sound.

As for setting your channels to 6 when you only want to use 4 - that was not what was suggested to you when you asked this question in Launchpad.

You could just wire the front and rear speakers together to avoid the extra effort of adjusting another slider (although that would alter the resistance value of your speakers).

---

