---
title: "How to install ati driver for an old card"
date: 2006-08-02
forum: Multimedia &amp; Video
---

### Post by Frafra on 2006-08-02
I've an old latop, with xubuntu installed. It works perfectly! I've only a problem. I've installed xorg-driver-fglrx and edited xorg.conf, but it says "No screen found". I would know how to install ati drivers for my card.
lspci says:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

Thanks!

---

### Post by whatever on 2006-08-02
fglrx does only support radeon cards from the 2nd generation or newer (8500+).
why don't you want to use the open source drivers which are installed by default?

---

### Post by Frafra on 2006-08-03
Yes, I'm using the open source driver. But I haven't direct rendering :) Could I have a "base" accelleration with open source drivers?

---

