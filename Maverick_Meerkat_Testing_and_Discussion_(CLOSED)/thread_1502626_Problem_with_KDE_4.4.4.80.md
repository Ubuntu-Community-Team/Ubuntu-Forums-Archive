---
title: "Problem with KDE 4.4.4.80"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by xeddog on 2010-06-05
I'm not sure if this belongs in the Maverick forum or somewhere else, but since I am testing Maverick I'll put it here.

I just installed Ubuntu Maverick 64-bit as a virtual machine in VirtualBox.  That is a long story, but most of the problems I had were of my own design.  I Installed Ubuntu with the gnome desktop and had everything finally working the way I wanted, and then I went and installed the KDE desktop too.

The KDE installation seems to have run fine with no errors that I can see, but when I logout of Gnome and try to log into kde, I get

kstartupconfig4 does not exist or fails - error code is 139.

I have tried looking for a solution but haven't found one yet.  There were a couple of older posts in another forum that indicated perhaps some incompatibilities with the QT4 libraries.  Don't really know what to look for to see if that is an issue or not.  So the question is:  Does anyone know what that error means, and how to fix it?

Thanks,

xeddog

Computer - Gigabyte EX58-UD3R motherboard with Intel I7-920 processor.  6GB ram, nVidia 9500 gx graphics card, dual monitors.  One IDE 300GB disk and one 1TB SATA disk (this is the primary disk and the one I usually run with). OS is Lucid 64-bit, and I switch back and forth between gnome and kde with this machine too.

Virtualbox 3.2.2.  Maverick is the only VM at present

KDE 4.4.4.80

---

### Post by vikrant82 on 2010-06-05
What's the version of 'kdebase-workspace-bin' package ?

---

### Post by xeddog on 2010-06-06
According to Synaptic kdebase-workspace-bin is 4:4.4.80-0ubuntu2 and it is the only version listed.  All kde packages were installed using synaptic, and all of them are the same version.

xeddog

---

