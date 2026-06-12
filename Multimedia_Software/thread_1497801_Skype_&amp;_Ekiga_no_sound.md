---
title: "Skype &amp; Ekiga no sound"
date: 2010-05-31
forum: Multimedia Software
---

### Post by SomethingFishy on 2010-05-31
Hi

I'm struggling to set up sound so I can make calls via Skype or Ekiga.  I've tried various settings, installed latest versions of Ubuntu (64), Skype  (2.1 beta) and pulseaudio, but can't get a test call to work on either Skype (call fails immediately) or Ekiga (test call opens but no sound out, apparently none in either).

The headphones are working fine: I can record sounds and hear them played back, and in Skype I can hear the test sound.

Skype's sound options don't give me any choice other than pulseaudio but frankly I wouldn't know what else to choose anyway: I don't really understand what pulseaudio/alsamixer/OSS do.

Will I be able to get it working?  Is there some setting I can change from the terminal that will make all the difference?  Any hints much appreciated.

---

### Post by Amerinidiot1231 on 2010-05-31
Are you using a notebook or a desktop (and if a laptop what model)... laptops are tricky with integrated sound when it comes to pulse and skype(especially), some models like mine have been a real pain.

---

### Post by SomethingFishy on 2010-05-31
Hi Amerinidiot

Thanks for the reply.  It's a desktop.

---

### Post by SomethingFishy on 2010-06-01
I still have no idea what I can do.  Can anybody suggest anything?

---

### Post by Wobblybob on 2010-06-01
I've got the same problem mate on a desktop running 64 bit Lucid, not found a solution so far, the sound works ok on other apps and the mic is being picked up my the system but not Skype. Still playing with the setting but getting sick of having to listen to Skype's test call now.

---

### Post by SomethingFishy on 2010-06-01
> **Wobblybob said:**
> I've got the same problem mate on a desktop running 64 bit Lucid, not found a solution so far, the sound works ok on other apps and the mic is being picked up my the system but not Skype. Still playing with the setting but getting sick of having to listen to Skype's test call now.

Thanks Wobblybob, I'll let you know if anyone comes up with anything.  In the meantime I'm off to look for some yoghurt pots and string.

---

### Post by tobiz on 2010-06-23
Audio input and output works for me on Ubuntu 10.04 with Skype.  Audio is using Philips SPC 710NC webcam for audio input.  The processor is an Intel Atom D510 on an integrated M/B.  Audio in/out doesn't work with Ekiga.

---

### Post by Wobblybob on 2010-10-20
I got the mic to work with;

$ sudo gedit /etc/modprobe.d/alsa-base.conf

add this line at the end of the file;

options snd-hda-intel model = auto

and save and reboot

---

### Post by alexandari on 2010-10-20
[B]sudo apt-get remove pulseaudio

sudo apt-get install alsa-base

sudo apt-get install esound[/B]

---

