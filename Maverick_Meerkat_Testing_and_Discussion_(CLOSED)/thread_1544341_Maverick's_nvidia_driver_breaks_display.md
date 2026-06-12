---
title: "Maverick's nvidia driver breaks display"
date: 2010-08-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2010-08-02
I use 64-bit laptop with geforce 9500m, and I upgraded lately to maverick.

The system became very sluggish and unresponsive, even after removing all ubuntu-one related horrors. Compiz animations stutter and window contents are being drawn slowly. Moreover, there are elements the system fails to paint correctly with the nvdia driver (probably gradient-related):

1. Selected menu items and progress bars are brighter then they should be.

2. The lovely glowing dots below docky icons, which mark which app is being ran, became ugly grey blobs. 

I love compiz and love my games, so I cannot stick to nouveau (which draws these 2d elements fine).I wish I could just downgrade to nvidia 195 driver. Unfortunately, maverick only allows me to go back to 173, which does not work well with my card.

Bug reported: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/612614](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/612614)

Any idea how I can solve this?

---

### Post by jontxo on 2010-08-02
there is another problem with nvidia drivers. When you start vuze, gdm crashes and you return to the login page.

---

### Post by dino99 on 2010-08-02
add this ppa to your synaptic repo tab, it might be better graphic experience

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Wise Ferret on 2010-08-02
> **dino99 said:**
> add this ppa to your synaptic repo tab, it might be better graphic experience

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Thank you, but unfortunately the packages from this PPA did not resolve any of the issues.

EDIT: This seems to be an nvidia issue triggered by libcairo2 from the 1.9 branch. see also discussion in the nvidia forums: [http://www.nvnews.net/vbulletin/showthread.php?t=153683](http://www.nvnews.net/vbulletin/showthread.php?t=153683)

---

