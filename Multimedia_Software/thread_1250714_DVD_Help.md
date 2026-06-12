---
title: "DVD Help"
date: 2009-08-26
forum: Multimedia Software
---

### Post by rkmullins on 2009-08-26
I am completely new to Linux. I just installed Ubuntu on my laptop and all seems ok except for my DVD player. I came play audio CD's just fine, but when I insert a DVD movie it asks me what application to use. The only one listed is "Open Movie Player". I select that and it looks like it is going to play when a message pops up asking to search for a suitable plugin. I select search and it searchs but comers up with a message that "No packages with the requested plugins found" "The requested plugins are: DVD Source"

I have looked in Synaptic Package Manager but nothing is there that spells out "DVD Source"

Can someone assist me?  Thanks!

---

### Post by Revolutionary101 on 2009-08-26
You should install libdvdcss2 and ubuntu-restricted-extras. Just type this into terminal to get them.

```
sudo apt-get install libdvdcss2 ubuntu-restricted-extras
```

---

### Post by rkmullins on 2009-08-26
I tried and here are the results:

sudo apt-get install libdvdcss2 ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by rkmullins on 2009-08-26
libdvdcss is installed but I get this for the other you suggested:
E: Couldn't find package ubunto-restricted-extras

---

### Post by acharseth on 2009-08-27
Hi!

This worked for me:
Install libdvdread4 as explained in [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Install ubuntu-restricted-extras (search for it in Synaptic)

Playback is choppy though and I could not find the /dev/hdc described in [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA) to check if DMA is enabled. I am running Ubuntu 9.04 in a VirtualBox VM so that might be causing the problem too?

Arne

---

### Post by oldos2er on 2009-08-27
You need to enable the Medibuntu repository for libdvdcss2 ([http://medibuntu.org](http://medibuntu.org)).

---

### Post by rkmullins on 2009-08-27
thank you! it now works

---

### Post by Revolutionary101 on 2009-08-28
Glad I could help.

---

