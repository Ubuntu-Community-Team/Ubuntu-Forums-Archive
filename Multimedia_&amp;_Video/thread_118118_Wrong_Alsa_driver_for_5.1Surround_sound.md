---
title: "Wrong Alsa driver for 5.1Surround sound?"
date: 2006-01-16
forum: Multimedia &amp; Video
---

### Post by Geo123 on 2006-01-16
Hi.

I have recently installed ubuntu "Breezy Badger" on my AMD64 Sempron, which has a Gigabyte "GA-K8VM800M" motherboard. This motherboard has integrated 6 channel sound, using the "VIA VT8237R" chip. The Audio codec is "Realtek ALC655". 5.1Surround sound can be obtained by inserting stereo plugs into the "Line-in, Line-out and Mic".

I can get ordinary sound through "Line-out", but not 5.1Surround sound.
Alsamixer does not give me the options "Mic As Center/LFE" & "Line-In As Surround".

Also: "speaker-test -c6 -D plug:surround51" only plays sound out of front-left and -right speakers.

I think that I may not have the exactly correct alsa driver installed. On the Alsa website ([http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VIA](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VIA)) they say that the "hda-intel" driver should be used. My ubuntu currently uses "via82xx". Furthermore, when i go "System->preferences->Multimedia system selector" the Alsa audiosink gives me "Unable to construct test pipeline".

If the problem is indeed the wrong driver, how can I remove it and install the proper one (My linux skills are quite basic). Is there something like "dkpg -reconfigure alsa"?

Regards
George

---

