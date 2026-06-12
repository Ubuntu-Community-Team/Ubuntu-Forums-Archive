---
title: "Abobe Flash player"
date: 2010-05-28
forum: Multimedia Software
---

### Post by Amol Parithosh on 2010-05-28
Hi!!!

Which version of Adobe Flash player plugin should I download for Ubuntu 10.4 LTS???

Please help.

Regards,
Amol,
Bangalore, India

---

### Post by WinterRain on 2010-05-28
There is only one version of adobe flash for 32bit ubuntu, just different ways to install it. Do:

```
sudo apt-get install flashplugin-installer
```

Or, if you want that, *and* all codecs, do:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
then
```
sudo apt-get install non-free-codecs
```

---

### Post by Amol Parithosh on 2010-05-29
It worked!!
Thank you :)

---

