---
title: "Sound doesn't work in 8.04 on my Dell laptop"
date: 2008-05-16
forum: Multimedia Software
---

### Post by - 000 - on 2008-05-16
I installed Ubuntu 8.04, and the sound is very quiet.  The volume meter is at max.  If I plug in speakers, I can turn up the volume, but it then makes popping and cracking sounds.  Is there any way to fix this?  I don't know what sound card I have, but I'm using a Dell Inspiron 1525 laptop

---

### Post by BandD on 2008-05-16
Post the output of the below run in a terminal:

```
lspci | grep Audio
aplay -l
```

Those are two different commands.  The first one looks at what devices are connected via PCI with the word Audio as an identifier and the second shows you some more specific info regarding your sound card.

---

### Post by dicecca112 on 2008-05-16
right click Audio Icon top Right -> Open Volume Control, make sure PCM and Front are all the way up

---

### Post by - 000 - on 2008-05-16
Yeah, it looks like Ubuntu recognizes it.  I took dicecca's suggestion, and it works now.  I think the sound quality is reduced, but I'm not sure.

---

### Post by Ichido on 2008-06-24
> **- 000 - said:**
> I installed Ubuntu 8.04, and the sound is very quiet.  The volume meter is at max.  If I plug in speakers, I can turn up the volume, but it then makes popping and cracking sounds.  Is there any way to fix this?  I don't know what sound card I have, but I'm using a Dell Inspiron 1525 laptop

Try this:
Select System>Preferences>Sound>
Choose the TAB "Devices" and test the options.
My set up is:
**Sound Events**-autodetect
**Music & Movies** -autodetect
**Default Mixer Tracks -Device- -HDA Intel (ALSA Advanced Linux Sound Architecture)**

It's working on my 1525n.
good Luck.

---

