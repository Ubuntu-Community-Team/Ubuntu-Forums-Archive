---
title: "Can't Change to 1280x1024 Res on ATIX600"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by MikeConley on 2007-05-02
I just did a fresh Feisty Install and I did little more than run Automatix and install the restricted ATI drivers.

For some reason, I absolutely cannot make my screen resolution higher than 1280x1024 @ 60Hz. I've tried changing the refresh rate, but I can't change that, nor can I do anything other than lower my resolution.

Other than this minor (yet very annoying) setback, my install is working fine (WoW runs better through Wine than it did when I was on XP :P)

If anyone can help me fix this, that'd be lovely.

Thanks in advance :)

- MC

---

### Post by tyboon on 2007-05-02
Type in terminal...  sudo dpkg-reconfigure -phigh xserver-xorg ... use cursors up-down to find Ati...
Select resolution with the SPACE button...
I hope it works

---

