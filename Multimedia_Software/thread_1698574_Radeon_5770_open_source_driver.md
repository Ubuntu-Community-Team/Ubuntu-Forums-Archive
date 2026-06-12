---
title: "Radeon 5770 open source driver"
date: 2011-03-02
forum: Multimedia Software
---

### Post by pszpak on 2011-03-02
Hey,

I just upgraded my rig from a 4770 to a 5770 video card.

My 4770 had basic 3d support out of the box with the open source radeon driver. My 5770 doesn't seem to (basic rendering only with no compositing), although this page suggests it does:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Is there anyone out there who is running a 5770 or knows how I can upgrade to a newer version of the open source driver? I'd rather not use catalyst (Id don't game with ubuntu) and I found the open source driver to be quite nice.

---

### Post by Yellow Pasque on 2011-03-02
Use the xorg-edgers ppa: [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers)
You need the newer kernel to support your GPU.

---

### Post by pszpak on 2011-03-04
Thank you. This was exactly what I was looking for.

---

