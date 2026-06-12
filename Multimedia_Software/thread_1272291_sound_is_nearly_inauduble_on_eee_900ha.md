---
title: "sound is nearly inauduble on eee 900ha"
date: 2009-09-22
forum: Multimedia Software
---

### Post by spartanghost on 2009-09-22
I just recently nuked xp in favour of UNR, but my sound is ridiculously quiet, even with the volume turned way up.  this is tru of both the speakers and the headphone jack, leading me to believe it's a software issue.  Is there some kind of internal volume control apart from the main one on the bar at the top? (that one is linked to the hardware volume controls; they're just function keys)

As said before i have an Asus eee 900ha.

---

### Post by raboofje on 2009-09-22
What kind of card is that?

Iirc this is a common problem with Intel HDA cards when it fails to correctly autodetect the 'model', see [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by spartanghost on 2009-09-22
I started going through the steps in that link but 
```

cat /proc/asound/card0/codec#* | grep codec
```

produces no output at all.

is there any other way to find out what my sound card is?

---

### Post by raboofje on 2009-09-22
'lspci', 'cat /proc/asound/cards'

---

