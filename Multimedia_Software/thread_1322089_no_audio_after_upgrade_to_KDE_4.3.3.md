---
title: "no audio after upgrade to KDE 4.3.3"
date: 2009-11-10
forum: Multimedia Software
---

### Post by barlowrm on 2009-11-10
Hi all,

I just upgraded my (perfectly working) kubuntu 9.10 to use KDE 4.3.3 with the Kubuntu Updates PPA.

The result is: no sound at all.

Some tests I have done: from System Settings->Multimedia I get a list of output devices for "Music". "Pulse" does not play anything when clicking on "Test" button. "HDA Intel" plays ok. "HDA ATI HDMI" plays through the HDMI cable, as expected.

Any hints are welcome...

Andrea.

---

### Post by barlowrm on 2009-11-11
Hi,

for the record, I solved this by un-muting the headphones channel...

---

### Post by lanzen on 2009-11-11
> **barlowrm said:**
> Hi,

for the record, I solved this by un-muting the headphones channel...

You were quite lucky. I had to "sudo alsa force-reload". Sound came back but Plasma crashed and didn't restart. I had to hard reset.

---

