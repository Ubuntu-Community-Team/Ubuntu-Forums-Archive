---
title: "[Ubuntu 18.04] Headphone not working"
date: 2019-07-19
forum: Multimedia Software
---

### Post by frosty.the.snowman on 2019-07-19
Hello forum,



Unfortunately, while my speakers work, when I plug in my headphones all I hear is a pulsating sound.

I've checked both Ubuntu settings and alsamixer and nothing is muted.

If I hit alsa retore all I get is this:

alsactl: state_lock:125: file /var/lib/alsa/asound.state lock error: File exists
alsactl: load_state:1683: Cannot open /var/lib/alsa/asound.state for reading: File exists
Found hardware: "HDA-Intel" "Realtek ALC295" "HDA:10ec0295,10431011,00100002" "0x1043" "0x1011"
Hardware is initialized using a generic method



My alsa info link is this:

[http://alsa-project.org/db/?f=7b87283b218cab3071b4ce6a02641192ac4ae870](http://alsa-project.org/db/?f=7b87283b218cab3071b4ce6a02641192ac4ae870)



Please help, and many thanks!

---

### Post by Autodave on 2019-07-19
Old trick that may help:

Try powering up (or rebooting) the PC with the headphones connected.

---

### Post by frosty.the.snowman on 2019-07-22
Doesn't work. Anything else?

---

