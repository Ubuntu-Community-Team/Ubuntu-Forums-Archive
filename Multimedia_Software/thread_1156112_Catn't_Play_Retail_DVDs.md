---
title: "Catn't Play Retail DVDs?"
date: 2009-05-11
forum: Multimedia Software
---

### Post by RoB RuLeZ on 2009-05-11
Sorry if this is a noob question, I can't play retail (css) DVDs. Not to sure why, I did some searching and I have all the necessary plugins (I think). If anyone can help me with this I would be grateful.

---

### Post by zero777zero on 2009-05-11
terminal:
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

then follow this: [https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

---

### Post by binbash on 2009-05-11
you need libdvdcss2 package from medibuntu repo

---

### Post by m_2009 on 2009-05-11
If you dont have the ubuntu-restricted-extras package installed, then install that first vis synaptic or in terminal using the following:

```
sudo apt-get install ubuntu-restricted-extras
```

Then from a terminal window run the following command depending on which version of ubuntu you are using.

Jaunty (9.04)
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Intrepid (8.10) and Hardy (8.04)
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

This will save having to add the medibunto repo, and will automatically install the libdvdcs2 package from the medibuntu repo without needing to manually add it.

---

### Post by serotta_rider on 2009-05-11
I installed smplayer from the package manager. This brought down some necessary add on that enabled it to work.

---

### Post by Maki9389 on 2009-05-12
> **zero777zero said:**
> terminal:
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

then follow this: [https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

This worked for me.  Thanks

---

### Post by RoB RuLeZ on 2009-05-13
Thanks everyone I got it working!

---

