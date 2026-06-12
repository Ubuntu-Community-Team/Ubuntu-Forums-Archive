---
title: "Ubuntu 10.10 Dpkg Problem ( All Debs )"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PixelPirate on 2010-08-29
[http://imgur.com/TAYj3.png](http://imgur.com/TAYj3.png)

I get that error message with all debs, literally. Is there a fix or workaround for this?

---

### Post by Iowan on 2010-08-29
Moved to Maverick Meerkat Testing and Discussion

---

### Post by ranch hand on 2010-08-29
I have been running 10.10 since the toolchain went up and have had no problem with this at all.

Instead of a screen shot, how about some real information on what you are doing, how how you are doing it and why you are doing it.

This is a dev (testing) OS.  Some packages may not be compatible with it yet.

---

### Post by Starks on 2010-08-29
> **PixelPirate said:**
> [http://imgur.com/TAYj3.png](http://imgur.com/TAYj3.png)

I get that error message with all debs, literally. Is there a fix or workaround for this?
Confirm. I get this with all debs when using gdebi.

Need to manaully dpkg everything now.

---

### Post by dino99 on 2010-08-29
bug 620297 : add your vote " yes, it affects me" on top page

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/620297](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/620297)

---

### Post by jpeddicord on 2010-08-29
Does this occur when opening & installing the package in software-center, vs gdebi? software-center can load and install .deb packages now, so I recommend trying that.

---

### Post by cariboo on 2010-08-29
As far as I know, it's just a bug in gdebi, I don't use the Software Center, but synaptic and the command line work with zero problems. I've used dpkg to install a few packages that gdebi crashed on.

---

### Post by mc4man on 2010-08-29
The current bug is in gdebi-gtk
Previously gdebi had a bug where it could not install additional dependent packages from available repos.
That was apparently fixed, but in the meantime gdebi-gtk broke altogether.

I think a fix will require some other package re-builds first (python-apt, vte ?

If there is a rare occasion where gdebi is preferred over other means (installing a non repo package that needs add. packages installed from avail. repos) then gdebi itself is fine as in
sudo gdebi /path/to/<whatever.deb>

---

### Post by ranch hand on 2010-08-29
> **mc4man said:**
> The current bug is in gdebi-gtk
Previously gdebi had a bug where it could not install additional dependent packages from available repos.
That was apparently fixed, but in the meantime gdebi-gtk broke altogether.

I think a fix will require some other package re-builds first (python-apt, vte ?

If there is a rare occasion where gdebi is preferred over other means (installing a non repo package that needs add. packages installed from avail. repos) then gdebi itself is fine as in
sudo gdebi /path/to/<whatever.deb>
That may be why I haven't had any trouble with it.  Didn't even realise it is supposed to be broken.

---

### Post by nilarimogard on 2010-08-30
Use this instead:

```
sudo dpkg -i *.deb
```

---

### Post by zenarcher on 2010-08-30
> **Starks said:**
> Confirm. I get this with all debs when using gdebi.

Need to manaully dpkg everything now.

Same situation here.  I also must manually dpkg everything now.

Cheers,
zenarcher

---

### Post by zenarcher on 2010-08-30
> **dino99 said:**
> bug 621696 : add your vote " yes, it affects me" on top page

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/621696](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/621696)

Done.

Cheers,
zenarcher

---

### Post by dino99 on 2010-09-03
> **dino99 said:**
> bug 620297 : add your vote " yes, it affects me" on top page

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/620297](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/620297)

problem identified

---

