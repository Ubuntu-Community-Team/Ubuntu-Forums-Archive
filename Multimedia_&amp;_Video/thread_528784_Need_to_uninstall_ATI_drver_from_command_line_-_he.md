---
title: "Need to uninstall ATI drver from command line - help"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by JGT on 2007-08-18
Hi

I need to uninstall my ATI driver. I inserted a new VisionTek  X1550 PCI (sic) card, and the driver was installed via "restricted drivers".

X windows didn't work on reboot. I need to recover my intergrated graphics but, since I'm locked out of Gnome, I can't do it the easy way. Any ideas?

John

---

### Post by tseliot on 2007-08-18
type:
```
sudo apt-get --purge remove xorg-driver-fglrx fglrx-control
```

then type:
```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then restore mesa:
```
sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri
```

and finally type:
```
sudo /etc/init.d/gdm restart
```

---

### Post by JGT on 2007-08-18
Many thanks. The command line didn't like "-g", and later couldn't find "lib-gll-mesa", but I proceeded anyway and now I'm back in X. It's a huge relief!

I don't think that I've restored the Intel accelerated graphics because GLdesktop doesn't work yet, but I'm sure I'll get it up and running.

Thanks again

John

---

