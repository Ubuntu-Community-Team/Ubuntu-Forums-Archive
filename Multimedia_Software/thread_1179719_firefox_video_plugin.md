---
title: "firefox video plugin"
date: 2009-06-05
forum: Multimedia Software
---

### Post by nafihsus on 2009-06-05
I am running Ubuntu 8.04 and can't see certain videos / pictures in Firefox. I only see a "play" button, clicking on it makes the button disappear and the field turns black (eg [http://www.rolandgarros.com/en_FR/index.html]("http://www.rolandgarros.com/en_FR/index.html")).

Can someone tell me whether a plugin is missing (see snapshot). Firefox does not automatically load them.

---

### Post by hansdown on 2009-06-05
Hi nafihsus.

Have you installed flashplugin, flashplugin-nonfree, and ubuntu-restricted-extras?

Search for them in synaptic package manager.

---

### Post by lovinglinux on 2009-06-06
I believe that is gnash flash plugin. You can replace it with the one from Adobe.

Open "Applications >> Accessories >> Terminal", then paste the code below and hit enter:

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree ubuntu-restricted-extras
```

This command will remove the gnash and swfdec flash players if installed and install the one from Adobe and ubuntu-restricted-extras.

---

### Post by nafihsus on 2009-06-06
:p Thank's a lot. The gnash replacement helped.

---

