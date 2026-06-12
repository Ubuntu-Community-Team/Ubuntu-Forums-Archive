---
title: "ati 2900 hd"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by trufaldini on 2007-08-20
I spent last week by trying to install a fglrx driver for my ATI 2900 with latest driver from ati (fglrx 40.4) but without success. Can someone help me or give an advice if there's any alternative driver which support 3D rendering (composite window decorator as Compiz, Beryl or Compiz-fusion)?

Thank you very much.

---

### Post by w4ett on 2007-08-21
Dou you mean the ATI 9200 card?  If so , the correct driver to use is the open source xorg-driver-ati.  Fglrx is not compatible with that card in Ubuntu Feisty.  It only supports the 9500 series cards and above.

In the terminal (or command line) type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select 'ati' as your driver, select your desired resolutions, save, then type:

```
startx
```

This will get you back to a GUI Desktop.

---

### Post by rozhman on 2007-10-24
I have thesame problem with ati hd2600 pro.

---

