---
title: "can't change default sound card"
date: 2013-09-08
forum: Multimedia Software
---

### Post by scentsamillia on 2013-09-08
Ok I've tried just about every guide I could find... sudo alsamixer doesn't work and neither does sudo alsactl store.
I have 2 sound cards and both are recognized by alsa and the system and activated.... I don't really know much about ubuntu I've had it for a few weeks and I've had no sound at all, the default atm is HD-audio generic which apparently does nothing....
Can someone please help me?

---

### Post by scentsamillia on 2013-09-10
Anyone?

---

### Post by Yellow Pasque on 2013-09-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by scentsamillia on 2013-09-11
[http://www.alsa-project.org/db/?f=620ef8d6a5b80faae6f68c34f973725f9295d272](http://www.alsa-project.org/db/?f=620ef8d6a5b80faae6f68c34f973725f9295d272)

---

### Post by Yellow Pasque on 2013-09-11
So, are you trying to use the HDMI audio or the regular onboard audio?
For the HDMI audio, follow workaround 1 here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

---

### Post by scentsamillia on 2013-09-15
HDMI I'm guessing since I'm using an lcd monitor with an hdmi cord but when I got to alsamixer it shows that my default card has no audio capabilities, and when I switch to to other card it does, but I can't actually change the card that I'm using =/

---

### Post by Yellow Pasque on 2013-09-15
> HDMI I'm guessing since I'm using an lcd monitor with an hdmi cord
That doesn't mean that your monitor has speakers or that you want to use the hdmi sound..
How are the speakers that you want to use connected?

---

### Post by scentsamillia on 2013-09-16
It's the speakers in the monitor(it's actually an LCD TV but whatever).

---

### Post by Yellow Pasque on 2013-09-16
Okay, so did you do as I suggested in post #5?

---

### Post by scentsamillia on 2013-09-17
Well I tried but I can't figure out how to edit it, I could only find it by typing in the address in the browser and it showed up but searching my computer didn't show up anything and I tried sudo gedit like one of the sites said but it didn't work (i'm not sure if that was meant for 12.04 or not thought)

---

### Post by Yellow Pasque on 2013-09-17
```
gksu gedit /etc/default/grub
```

---

### Post by scentsamillia on 2013-09-18
[COLOR=#333333][FONT=Ubuntu Mono]Edit /etc/default/grub and change this line:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]to this line[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Now run "sudo update-grub", then reboot your computer.

did all this and it still didn't change anything, but I noticed something I didn't before in alsamixer. For the HD-Audio Generic card(Which is my default and doesn't work) the chip says ATI R6xx HDMI and for the HDA ATI SB(which looks like it should work when I select it in alsamixer) it says Realtech ALC 662 rev1. I don't know if this really matters but I never noticed it before... Any more ideas?

For some reason when I play a game that I downloaded from the software center the sound works but it doesn't for browsers or anything else I've tried... So maybe it's not the sound card?[/FONT][/COLOR]

---

### Post by scentsamillia on 2013-09-18
Nevermind it's just chrome that the sound doesn't work on, so I guess I'll just have to use firefox till I can find out what's up with that, thanks for all the help!

---

