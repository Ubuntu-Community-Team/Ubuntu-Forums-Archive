---
title: "Flash Player"
date: 2008-06-02
forum: Multimedia Software
---

### Post by spearball on 2008-06-02
I know that there was no adobe flash player for the ppc ubuntu so someone told me to try the swf-player instead. I used sudo apt-get install swf-player. It seemed to have installed a bunch of stuff but i still have no flash in firefox. Can someone help me out?  Thanks

---

### Post by gandaran on 2008-06-02
> **spearball said:**
> I know that there was no adobe flash player for the ppc ubuntu so someone told me to try the swf-player instead. I used sudo apt-get install swf-player. It seemed to have installed a bunch of stuff but i still have no flash in firefox. Can someone help me out?  Thanks
 
go to your synaptic package manager, find swf-player or swfdec and check mark it for complete removal, next find the flashplugin-nonfree (adobe flash) mark for install and click the apply button.

if you want to use commands to install flash run this;
**sudo apt-get install flashplugin-nonfree**
or you can install this package, the flash is included,
**sudo apt-get install ubuntu-restricted-extras**

---

### Post by Pjotr123 on 2008-06-02
For 100 % multimedia support, apply this simple how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Greetz, Pjotr.

---

### Post by spearball on 2008-06-03
I deleted swf-player. Then i installed everything on the site but ubuntu restricted extras, Gstreamer ffmpeg plugin, Audacious and gxine were not found. Also when i typed openjdk nothing came up. Guess it was never installed. And as for java that doesn't want to install either.

---

