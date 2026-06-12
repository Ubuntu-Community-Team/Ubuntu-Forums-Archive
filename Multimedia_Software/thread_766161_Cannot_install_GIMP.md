---
title: "Cannot install GIMP"
date: 2008-04-25
forum: Multimedia Software
---

### Post by Rodmiester on 2008-04-25
Hi all...
I'm trying to install GIMP on Ubuntu Studio 7.1 Gusty Gibbon. I run sudo apt-get install gimp and get the following error:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.4.5) but 2.4.0~rc3-1ubuntu7 is to be installed
        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
E: Broken packages

I try to install libgimp2.0 but it says it needs gimp-data, but it is already installed, and libpango1.0-0 is already installed. I've also checked Synaptic and it says I have 0 broken packages but the console says otherwise...
Any help would be greatly appreciated :)

Cheers...

---

### Post by DaV|d on 2008-04-25
Have you tried ```
sudo apt-get -f install gimp
```

Also check whether you have the correct repositories enabled.

---

