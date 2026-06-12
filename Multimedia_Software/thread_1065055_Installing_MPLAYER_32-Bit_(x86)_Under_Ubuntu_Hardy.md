---
title: "Installing MPLAYER 32-Bit (x86) Under Ubuntu Hardy 8.04 64 Bit (amd64)"
date: 2009-02-09
forum: Multimedia Software
---

### Post by ouija on 2009-02-09
Hi there,

I am trying to get HD WMV (audio) playback in Ubuntu Hardy AMD64 version and read about how installing the w32codecs and mplayer 32 bit package could do it.

So I looked into my synaptic package manager and found the following packages:

ia32-libs -> installed to allow support of 32 bit on amd64; No errors.
ia32-w32codecs -> installed 32bit codecs; No errors.
ia32-mplayer -> tried to install; failed with the following error:

ia32-mplayer:
Depends: ia32-lib-generic but it is not installable

I've looked high and low for this "ia32-lib-generic" and to no avail; Apparently it doesn't exist or maybe it is no longer supported under Hardy AMD64? -- Anyone have any suggestions?

I have tried everything under the sun to get this to work but no go.  Has anyone managed to install the 32-bit version of Mplayer under Ubuntu Hardy 64 bit? If so, please help!

---

### Post by wolfen69 on 2009-02-09
you will have to install nspluginwrapper also to get it to work. [this]("http://gwenole.beauchesne.info//en/projects/nspluginwrapper") will give you a little more info.

---

### Post by ouija on 2009-02-10
I installed it, but then when i try to install the ia32-mplayer package I still receive the following error:

> ia32-mplayer:
 Depends: ia32-lib-generic  but it is not installable

---

