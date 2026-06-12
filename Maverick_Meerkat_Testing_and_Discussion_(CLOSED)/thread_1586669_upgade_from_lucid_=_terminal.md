---
title: "upgade from lucid = terminal"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ELD on 2010-10-02
Okay so i decided to upgrade to Maverick from Lucid since it's at the RC stage.

Problem is it only gives me the terminal when i load up Ubuntu now.

Do i need to refresh x removing old catalyst drivers to get it to work? Is there a simple method to get it to boot up gnome?

---

### Post by VMC on 2010-10-02
> **ELD said:**
> Okay so i decided to upgrade to Maverick from Lucid since it's at the RC stage.

Problem is it only gives me the terminal when i load up Ubuntu now.

Do i need to refresh x removing old catalyst drivers to get it to work? Is there a simple method to get it to boot up gnome?

Some hardware info would be helpful. Are you using nvidia, ati?

---

### Post by ELD on 2010-10-03
Sorry thought most people would know Catalyst means ati my bad. ATi 5770.

---

### Post by jarpiw on 2010-10-03
> **ELD said:**
> Sorry thought most people would know Catalyst means ati my bad. ATi 5770.

The driver isn't working. If I knew that yesterday ;) Ati 4670 here.

xorg-driver-radeon driver from the repository did segmentation fault in my case but I added the newer ones from:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

and it's working somehow now.

---

### Post by kansasnoob on 2010-10-03
Possibly a variant of this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

Like:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649534](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649534)

There are at least four variants, but this work-around worked for me:

[http://ubuntuforums.org/showpost.php?p=9893106&postcount=16](http://ubuntuforums.org/showpost.php?p=9893106&postcount=16)

I hope to see these fixed by final.

---

### Post by ELD on 2010-10-03
Actually it was because 10.9 ati drivers didn't support new xorg, removed them and reverted back to open source drivers then installed via hardware manager and works fine.

---

