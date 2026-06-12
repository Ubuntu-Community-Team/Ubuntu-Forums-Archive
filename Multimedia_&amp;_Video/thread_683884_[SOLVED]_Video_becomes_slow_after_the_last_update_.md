---
title: "[SOLVED] Video becomes slow after the last update for xsever-xorg-core on intel"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by angusvitamin on 2008-01-31
I am not using xgl, just the default xorg. Does anyone have a fix?

---

### Post by overdrank on 2008-01-31
> **angusvitamin said:**
> I am not using xgl, just the default xorg. Does anyone have a fix?

HI and what is the model of the intel graphics? You can find this with the lspci command in the terminal. And you may go to synaptic manager and search for intel and insure that the i810 driver and the 915 resolution is installed. good luck!

---

### Post by angusvitamin on 2008-01-31
it's a g965...all the drivers are installed. It has been working perfectly until the last update

---

### Post by angusvitamin on 2008-01-31
i just did a dpgk-reconfigure xserver-xorg and it fixed itself...thank you

---

