---
title: "Switching graphic card"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by hans796 on 2007-03-01
Hi there..

I'm happily running Ubuntu Dapper. I'm very pleased with it.

Now I want to change my graphic card to a better one. Now I use an old NVIDIA MX400 with 64MB and have the legacy driver installed (had problem with official).

My new card isn't exceptional good, but it's better than my old one, a budget FX5200 128MB card.

First a bit more abouth my PC;
A Sempron 2600+
768 DDR RAM
Soundblaster Live
40GB HD

I'm running latest linux-K7.

This is how I intend to try it: (This is where you guys come in! Need guidance, and will not try before I get some verification that I'm on the right track)

1. Change driver in xorg.conf nvidia->nv

2. Turn of machine. Change cards.

3. Uninstall legacy driver.

4. Install official driver.

5. Change back driver in xorg.conf nv->nvidia.

6. Reboot and say a little prayer..

Is this enough? One of those things that mess me up, sometimes, is this magic word, linux restricted modules, puh! How abouth it? Well you guys (girls) maybe can help me in my mess.

Loooking forward with thankfullness of some Ubuntu Forum wisdom.

Greetz from the kingdom of Sweden..

---

### Post by Stemp on 2007-03-01
7. If the prayer is not enough, ctrl+alt+F1 to switch to text mode, log in and run **dpkg-reconfigure xserver-xorg** ;)

---

