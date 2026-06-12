---
title: "midi not working on serial port in ubuntu 7.04"
date: 2007-09-07
forum: Multimedia Production
---

### Post by linuxmann on 2007-09-07
I am trying to get my piano keyboard to work with ardour and MIDI. The connection is through a midi adapter converted to attach to the serial port in the back of my computer. Ardour just does not seem to recognize that i have something connected. Is there any way i can make this work. Is there anything i might be missing?

---

### Post by Em-Buntu on 2007-09-08
> **linuxmann said:**
> I am trying to get my piano keyboard to work with ardour and MIDI. The connection is through a midi adapter converted to attach to the serial port in the back of my computer. Ardour just does not seem to recognize that i have something connected. Is there any way i can make this work. Is there anything i might be missing?

You will need a serial to MIDI/MID to Serial driver running under ubuntu to receive and convert the serial signal. I don't believe Ardour or any MIDI program looks to the serial port by default.

---

