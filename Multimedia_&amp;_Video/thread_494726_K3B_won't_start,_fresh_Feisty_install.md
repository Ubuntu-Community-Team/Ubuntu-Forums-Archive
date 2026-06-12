---
title: "K3B won't start, fresh Feisty install"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-07-07
K3b fails to start up with the following message on a fresh Feisty installation:

```

kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
k3b: symbol lookup error: k3b: undefined symbol: _ZN11K3bVideoDVD8VideoDVDC1Ev

```

Qt: 3.3.7
KDE: 3.5.6
K3b: 1.0

Anyone else seen this before?

---

### Post by stijn1989 on 2007-07-07
What I should try is to remove k3b and install it again

```
sudo apt-get remove k3b
```
and when it's removed, install it again
```
sudo apt-get install k3b
```

---

### Post by pickarooney on 2007-07-08
I'd tried that, it doesn't help.

---

### Post by pickarooney on 2007-07-08
Seeing as I can't get this to run ATM, any suggestions for a decent replacement. I'm using gnome-baker for now; seems OK.

---

### Post by Gremlinzzz on 2007-07-08
this might be worth a try add  Medibuntu then uninstall and reinstall dont forget sudo apt-get update before reinstalling
[https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29)

---

### Post by pickarooney on 2007-07-14
After trying that K3B just stays stuck on the splashscreen a bit then dies

---

### Post by pickarooney on 2007-07-15
Upgrading to KDE 3.5.7 and rebooting (then reconfiguring GRUB, obviously) fixed this.

---

