---
title: "libcec support in mythbuntu 14.04?"
date: 2015-10-04
forum: Mythbuntu
---

### Post by daveg3 on 2015-10-04
Hi,

I've just built a new mythbuntu 14.04 box recently and I noticed that the frontend doesn't get built with libcec support anymore (it used to get built with it back in mythbuntu 12.04). libcec2 is in the 14.04 repos, does anyone know why its not getting built or where the right place to raise a bug report this is?

Cheers,
dave.

---

### Post by philip7 on 2015-11-08
Not really going to be much help with this but very interested as I'd like to control Mythtv using HDMI-CEC and would like to know how you get on.

I did find these instructions, not sure if they will be much help: [http://themanfrey.blogspot.co.uk/2012/09/enabling-libcec-on-mythbuntu-1204-with.html](http://themanfrey.blogspot.co.uk/2012/09/enabling-libcec-on-mythbuntu-1204-with.html) 

If you get it working could you provide any feedback how successful HDMI-CEC is with Mythtv.

---

### Post by blm-ubunet on 2015-11-11
libcec2 support only made it into master.
[https://code.mythtv.org/trac/ticket/11338](https://code.mythtv.org/trac/ticket/11338)

master (0.28) builds with libcec2 if it is installed.
This build option is meant to be enabled by default.

---

