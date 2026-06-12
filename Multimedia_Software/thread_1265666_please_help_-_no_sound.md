---
title: "please help - no sound"
date: 2009-09-13
forum: Multimedia Software
---

### Post by gstamets4 on 2009-09-13
my sound quality using an audigy 2 zs card on jaunty 9.04 was pretty crappy (bass, for instance, sounded awful), so i tried to run some updates and didn't really know what i was doing.

i completely killed my sound.

as it stands right now, i can't run alsamixer under the terminal or i get this error:

[INDENT]'function snd_ctl_open failed for default: No such device'
[/INDENT]
the only way i get any sound is if i CHECK the analog/digital output jack option under switches in volume control - in which case my music sounds just as bad as before this whole mess.  but, unlike before, none of my keyboard controls for sound volume work.

anyone have any clue what i'm supposed to do?  do i not have the driver, or alsa installed right?  i've gone through the forum and other sites for HOURS, pretty much exhausting everything i've seen, to no avail.

---

### Post by gstamets4 on 2009-09-14
anyone?

---

### Post by gstamets4 on 2009-09-14
bump

---

### Post by HappyFeet on 2009-09-14
You could try reinstalling alsa. Go to synaptic and completely remove alsa. Then do:
```
sudo apt-get install module-assistant
```
then:
```
sudo m-a a-i alsa
```
then
```
sudo modprobe alsa
```
reboot.

---

