---
title: "k3b Won't Work on New Machine"
date: 2007-04-11
forum: Multimedia &amp; Video
---

### Post by Ingla on 2007-04-11
Hello.

I'm running Dapper. I recently got a new computer and, after some xorg reconfiguration, got the hard disk to boot into the GUI on the new machine. Everything seemed to work fine until I tried to burn a CD using k3b.

It throws an error saying that k3b does not have permission to open the device and that I can fix this by using k3bsetup2. Only problem is there is no k3bsetup2 ... no such module (I don't know what it does or how to use it anyway).

I opened Synaptic and reinstalled k3b. No change. Then I did a complete removal and installed it again (if complete removal really works). I was hoping it would configure itself to handle the new CD/DVD burner (SATA drive). No such luck.

I managed to burn the disk using the default Gnome tools, but really like k3b and hate to lose it.

Does anyone know how to fix this?

Thanks.

---

### Post by ggaaron on 2007-04-11
Hi,
I'm not sure if it helps, but you can try - I often had problems with k3b when running it as a standard user, run it as root (using sudo for example), it had fixed my problems with permissions to devices.

Aaron

---

### Post by Ingla on 2007-04-11
Thank you very much. That worked! It still won't work as my user, but at least if I run it as root I can burn.

Thanks again.

---

### Post by Ingla on 2007-04-11
I went into k3b configuration and it said that I might need to change permissions for the CD/DVD burner. Looking at the properties in the file browser, I see k3b's owner and group are both "unknown". I don't know how to chown it because Linux might call it any number of things ( chown username ????).

Any ideas?

Thanks.

---

