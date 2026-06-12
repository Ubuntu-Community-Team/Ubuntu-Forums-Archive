---
title: "MythTV audio issue under Maverick--possible fix"
date: 2011-01-02
forum: Multimedia Software
---

### Post by oldHat on 2011-01-02
Mythtv stopped playing audio after I upgraded to Maverick.

I found the following workaround on some other site(sorry, no link).  It worked for me.  Here's hoping it might work for some of you.

[LIST]
[*]aplay -l # to get a list of sound cards
[*]under utilities/setup->setup->general->Audio System, Audio output device:, enter the following:   ALSA:default:CARD=2
[/LIST]

The card number should be the value returned by aplay.

---

### Post by BicyclerBoy on 2011-01-02
What mythtv version is involved ?

The 0.24 release notes recommend that after update: Use the MythTV audio device scan to list all available devices..

---

### Post by oldHat on 2011-01-07
> **BicyclerBoy said:**
> What mythtv version is involved ?

The 0.24 release notes recommend that after update: Use the MythTV audio device scan to list all available devices..

Interesting.  I seem to be using the latest version from the repository:  0.23.1+fixes26437-0ubuntu1

---

### Post by BicyclerBoy on 2011-01-07
The 10.10 upgrade could have changed your kernel version (alsa) & changed your video driver version.

Some of your personal changes/setup could have been overwritten.

The MythTV 0.24 is latest release.
0.24+fixes is in 3rd party ppa.
These are not in *buntu repositories.

---

