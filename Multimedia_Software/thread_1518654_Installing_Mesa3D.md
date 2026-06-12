---
title: "Installing Mesa3D"
date: 2010-06-26
forum: Multimedia Software
---

### Post by mikeglaz on 2010-06-26
I'm trying to install Mesa3D (the OpenGL alternative for Linux) on my computer.  Does anyone know how to do this?  When I run ./configure it tells me "DRI2PROTO... configure: error: Package requirements (dri2proto >= 2.1) were not met:".  So then I try to install dri2proto and when I type *make* I get the following message: "make: Nothing to be done for `all'."  Does anyone know how to get around this problem?

thanx,
mike

---

### Post by Yellow Pasque on 2010-06-27
Mesa should be installed by default, or easily installed through synaptic. If you're using nvidia or ati proprietary/binary drivers, installing mesa could cause conflicts. If you need a newer version of mesa, see: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

BTW, you don't have the necessary -dev packages for what you were trying to do:
```
sudo apt-get build-dep mesa-glx-dri
```

---

### Post by mikeglaz on 2010-06-27
> **Temüjin said:**
> Mesa should be installed by default, or easily installed through synaptic. If you're using nvidia or ati proprietary/binary drivers, installing mesa could cause conflicts. If you need a newer version of mesa, see: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

BTW, you don't have the necessary -dev packages for what you were trying to do:
```
sudo apt-get build-dep mesa-glx-dri
```

It says "Couldn't find package mesa-glx-dri"

---

### Post by mikeglaz on 2010-06-27
I also went in to Synaptic and tried installing anything to do with Mesa from there.  Now when I try to configure Mesa I get a new error: "checking for INTEL... configure: error: Package requirements (libdrm_intel >= 2.4.19) were not met: Requested 'libdrm_intel >= 2.4.19' but version of libdrm is 2.4.18"

---

### Post by Darkus1984 on 2010-10-12
Hi man,

Can you fix this error? for libdrm_intel >= 2.4.19.

---

### Post by truk77 on 2010-12-06
> **Darkus1984 said:**
> Hi man,

Can you fix this error? for libdrm_intel >= 2.4.19.

I'm in this same boat as well.  I'm about to try compiling the most recent  libdrm from source to see how far that gets me.

---

### Post by Yellow Pasque on 2010-12-06
Just use this PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 
It has the whole open-source graphics stack from git and conveniently packaged/updated. Yeah, you can do it yourself if you want to learn, but you're going to need to update a lot of libraries and you're going to end up "reinventing the wheel."

---

### Post by truk77 on 2010-12-06
> **Temüjin said:**
> Just use this PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) 
It has the whole open-source graphics stack from git and conveniently packaged/updated. Yeah, you can do it yourself if you want to learn, but you're going to need to update a lot of libraries and you're going to end up "reinventing the wheel."

Sweet, I'm not a big fan of having to do things by hand.  I'll give this a try.

---

