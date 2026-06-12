---
title: "Lame and Audacity"
date: 2007-06-02
forum: Multimedia Production
---

### Post by Pumalite on 2007-06-02
Audacity complained that it couldn't find libmp3.lame.so, while trying to convert FLAC to Mp3. I looked for the file myself and it was nowhere to be found in the whole system ( 6.10 ). Lame is installed but apparently does not make a 'libmp3lame.so' during its installation. How can I make Audacity work anyway? What file do I offer it?. Thank you in advance for your help.

---

### Post by Pumalite on 2007-06-02
> **Pumalite said:**
> Audacity complained that it couldn't find libmp3.lame.so, while trying to convert FLAC to Mp3. I looked for the file myself and it was nowhere to be found in the whole system ( 6.10 ). Lame is installed but apparently does not make a 'libmp3lame.so' during its installation. How can I make Audacity work anyway? What file do I offer it?. Thank you in advance for your help.

I solved my problem by copying from my Suse 10.2 /usr/lib/libmp3lame.so to Ubuntu's /usr/lib. Now Audacity works fine.

---

