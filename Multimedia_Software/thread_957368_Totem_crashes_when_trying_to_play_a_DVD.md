---
title: "Totem crashes when trying to play a DVD"
date: 2008-10-24
forum: Multimedia Software
---

### Post by Firestrider on 2008-10-24
Whenever I try to play a DVD such as V for Vendetta it gives me the error:

"An error occurred, could not read from resource" or just completely crashes the program and I have to force quit.

Also my computer completely slows down and my whole GUI gets messed up

I don't know if this is a program error or not but it seems like a serious problem.

---

### Post by DrMega on 2008-10-24
> **Firestrider said:**
> Whenever I try to play a DVD such as V for Vendetta it gives me the error:

"An error occurred, could not read from resource" or just completely crashes the program and I have to force quit.

Also my computer completely slows down and my whole GUI gets messed up

I don't know if this is a program error or not but it seems like a serious problem.

Have you installed the package "Linux-restricted-extras"?

Also, are you using the default install of Totem? The first thing I do whenever I do a build is to remove Totem-GStreamer and install Totem-Xine. It seems to work better and use less CPU.

---

### Post by Crandom on 2008-10-24
Need to install DVD CSS decryption capabilities: [https://help.ubuntu.com/8.04/musicvideophotos/C/video.html](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html)

---

### Post by Firestrider on 2008-10-24
I still couldn't get it to work after installing those two libdvd packages, so I'm just going to use VLC.

---

### Post by DrMega on 2008-10-24
> **Firestrider said:**
> I still couldn't get it to work after installing those two libdvd packages, so I'm just going to use VLC.

You also need to install libdvdcss2 which is in the repository. Also, the xine version of Totem works better than the gstreamer version.

---

### Post by Firestrider on 2008-10-24
How do I get libdvdcss2? I tried using the synaptic package manager and doing: sudo apt-get install libdvdcss2 with no avail.

---

### Post by DrMega on 2008-10-27
> **Firestrider said:**
> How do I get libdvdcss2? I tried using the synaptic package manager and doing: sudo apt-get install libdvdcss2 with no avail.

Have you enabled all the repositories? I don't think the standard install has them enabled, so your package list won't be complete unless you have enabled all the extra repositories. You can do this from Synaptic.

---

### Post by Bablefish on 2008-10-27
When all else fails look into Automatrix

---

