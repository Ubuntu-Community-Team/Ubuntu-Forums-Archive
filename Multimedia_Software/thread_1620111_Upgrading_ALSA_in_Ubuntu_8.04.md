---
title: "Upgrading ALSA in Ubuntu 8.04"
date: 2010-11-12
forum: Multimedia Software
---

### Post by dschaller on 2010-11-12
Hardy Heron includes ALSA 1.0.15 but I need at least 1.0.16 to make VMWare player happy with it. I couldn't find the packages in backports, but maybe I missed it. Does anyone know if I can upgrade this without causing big problems?

---

### Post by Yellow Pasque on 2010-11-12
Maybe: [https://launchpad.net/~alsa-backports/+archive/ppa](https://launchpad.net/~alsa-backports/+archive/ppa)

---

### Post by dschaller on 2010-11-13
Thanks Temüjin! For some reason I had not been able to find those particular backports. They did the trick. I was able to install 1.0.17 and now VMware can use ALSA and the sound quality is *much* improved.

---

