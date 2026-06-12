---
title: "Virtual Guest Tools reinstallation issue after update"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-08-31
I just did the latest updates and upgrades for Maverick, restarted and realized I had to reinstall VirtualBox Guest Tools. So I run the installation. Did not work out though. This - see attached screenshot - is what I saw after the program started running in the terminal. I restarted again I found out the tools were not installed and I could not re-size the screen..

---

### Post by jfernyhough on 2010-08-31
This is down to the current guest addition not supporting xorg-server 1.9.

Error message from my Maverick-on-Maverick VM:

```
Warning: unsupported pre-release version of X.Org Server installed.  Not installing the X.Org drivers.
```

Along with a lot of other things we have to wait until other companies update to support Xorg 7.6 (and server 1.9).

---

### Post by Stoneface on 2010-09-02
@Jfernyhough Thanks for the explanation!

---

### Post by techunit on 2010-09-03
Well can't we add the lucid main repository to meerkat and use synaptic to force version. I got a little ways with it but I can't tell you what it really did. Basically what I did was go into the vm add the lucid main sources to the meerkat sources list, disable meerkat main, and revert xorg server core, which interesting removed all the xorg components (I think this is the good part) I then reverted anything else meerkat related, when i rebooted, gnome couldn't load, but I got the command line which allowed me to reinstall the Xorg drivers from lucid.

---

### Post by Stoneface on 2010-09-10
> **techunit said:**
> Well can't we add the lucid main repository to meerkat and use synaptic to force version. I got a little ways with it but I can't tell you what it really did. Basically what I did was go into the vm add the lucid main sources to the meerkat sources list, disable meerkat main, and revert xorg server core, which interesting removed all the xorg components (I think this is the good part) I then reverted anything else meerkat related, when i rebooted, gnome couldn't load, but I got the command line which allowed me to reinstall the Xorg drivers from lucid.

Sounds a bit complicated to me. Hope to see a better solution soon.

---

### Post by algnod on 2010-09-14
I have the same problem. Is there any other way of setting the resolution? Its kind of cumbersome working with 800x600 screen resolution.

---

### Post by cariboo on 2010-09-14
Have a look at [this]("http://ubuntuforums.org/showpost.php?p=9809770&postcount=1") post, that was the solution for me.

---

### Post by algnod on 2010-09-15
Thank you cariboo907 that also solved it for me :-)

---

