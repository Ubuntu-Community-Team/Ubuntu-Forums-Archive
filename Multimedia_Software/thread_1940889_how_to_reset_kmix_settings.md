---
title: "how to reset kmix settings?"
date: 2012-03-14
forum: Multimedia Software
---

### Post by princeofnam on 2012-03-14
I completely bonked my KMIX settings for Kubuntu apparently because now sound doens't work for either my headphones or laptop speakers.  Does anyone know how to completely reset everything?

---

### Post by Zorael on 2012-03-17
I'm not sure it will help, but try deleting its settings.
```
$ rm ~/.kde/share/config/kmix*
$ rm -rf ~/.kde/share/apps/kmix
```
Then log out and back in.

You may also want to install the [PulseAudio Volume Control tool](apt://pavucontrol); it's ugly as sin in KDE, but it's a good tool to fall back upon if kmix fails you.

---

### Post by princeofnam on 2012-03-17
oh. that would have been smarter. i just completely removed .kde l.

---

### Post by SeijiSensei on 2012-03-18
Also check "System Settings > Multimedia > Phonon" to make sure you have the right defaults for inputs and outputs.

---

