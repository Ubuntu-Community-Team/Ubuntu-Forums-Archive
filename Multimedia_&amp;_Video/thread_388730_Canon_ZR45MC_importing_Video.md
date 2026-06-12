---
title: "Canon ZR45MC importing Video"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by damvcoool on 2007-03-19
ok i just bought a Camera from my mom, and i bought a firewire card from a local store(chip is VT6306) now the Firewire card is recognized but the camera is not :( what should i do??

I open kino normally and it says dv1394 not loaded or /dev/dv1394/0 not read/write not possible or something like that. so i load the module and the same thing. When i open kino as sudo, i do not get that problem but i and i do capture and it says that i have to press play on the camera, and i do but nothing happens!!!

Also kino run as sudo says NO AV/C Compilant Cam conected or not  switch on?

but i check and the camera is av/c compilant and it is on :S :S

Please Help.

what modifications can i do to what file??

---

### Post by damvcoool on 2007-03-20
Never mind, it is supported out of the box, just have to restart a lot of times so that the card is recognized and the camera is recognized as well. just one little easy to resolve problem and is that the group on the device /dev/dv1394/0 is root and should be users so that we can normally access it by kino :D

---

