---
title: "Darktable Upgrade"
date: 2020-01-08
forum: Multimedia Software
---

### Post by jeffmorasco on 2020-01-08
I have been using Darktable 2.6.3 on ubuntu 18.04. There is now a release of Darktable 3.0. Neither Synaptic or Ubuntu software lists an upgrade. Is the upgrade available? How did you install it? Thanks, Jeff

---

### Post by Holger_Gehrke on 2020-01-08
Once a release of Ubuntu gets 'frozen', no new versions of packages are put into the repositories only bug-fixes for critical bugs. PPAs or snaps are the normal ways of getting versions that are closer to the current state of development. There used to be a ppa for darktable, but it's deprecated by the developers. If you go to darktable.org and click on 'install' you'll find a link to 'third party packages' in the section on Ubuntu. This leads to three links, 'stable release' leads to 2.6.**2**, 'snapshot from the stable release branch' leads to 2.6.**3** and 'snapshot from the master branch' leads to 3.1.0. The way this is presented makes me think that 3 might not be quite stable yet. In all three variants you can then either directly download a .deb package or add a repository on openSUSE build servers.

Holger

---

### Post by jeffmorasco on 2020-01-08
Sounds like I would do best to wait until 3.0.1 or something similar comes out.
Jeff

---

### Post by jeffmorasco on 2020-01-31
I came across this:
[http://ubuntuhandbook.org/index.php/2019/12/install-darktable-3-0-0-ubuntu-18-04-19-10/](http://ubuntuhandbook.org/index.php/2019/12/install-darktable-3-0-0-ubuntu-18-04-19-10/)

Jeff

---

### Post by andrew.46 on 2020-02-01
Looks like the newest version can be installed easily enough on 18.04:

```

wget https://download.opensuse.org/repositories/graphics:/darktable/xUbuntu_18.04/amd64/darktable_3.0.0-1.1_amd64.deb
sudo dpkg -i darktable_3.0.0-1.1_amd64.deb 
sudo apt --fix-broken install

```

Worked nicely on my system and no extra PPAs needed :)

---

### Post by guiverc on 2020-02-01
Upgraded packages do sometimes get released for older releases, but it's only if the work needed to back-port security fixes is more work than just packaging the later version of the software (*which isn't very common*).

Ubuntu though can use snaps, ie. [https://snapcraft.io/darktable](https://snapcraft.io/darktable) shows 3.0.0 available, or you have these options [https://snapcraft.io/search?q=darktable](https://snapcraft.io/search?q=darktable)

---

### Post by andrew.46 on 2020-02-01
@guiverc I did not know that you were active here as well, these are my old stamping grounds and excitingly less restrictive than AU :)

---

