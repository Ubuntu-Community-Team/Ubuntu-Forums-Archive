---
title: "Nvidia 180 Intrepid"
date: 2009-02-04
forum: Multimedia Software
---

### Post by ricardo_78 on 2009-02-04
I have been experiencing some problems which I believe is to do with Nvidia 177 Drivers and Firefox 3 - Dropping out with seg fault.  I read that this was fixed in the new Nvidia 180 Drivers.

I have installed new 180 Drivers but machine will only boot in low res mode and says "failed to detect settings you will have to configure manually"

Hardware Drivers says 180 Driver installed and working 
but "nvidia-settings" throws an error ..."you do not appear to be using Nvidia Drivers"

I read about a symbolic link being screwed up from previous install but cannot find the reference....

So I aint given up but I am struggling a bit!!

oh yeah my kernel is now 2.6.27-11

---

### Post by xc3RnbFO8P on 2009-02-04
Try to Deactivate 180 and restart the computer,
then Activate it again.

---

### Post by norwoods on 2009-02-04
i upgraded from hardy to intrepid recently and was at the point you describe.  i used synaptic to install nvidia driver 180.27 from

[https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

and all seems good.  be sure to change the 

apt sources.list entries
Display sources.list entries for: 

drop down list box from jaunty to intrepid and follow the instructions.

---

### Post by ricardo_78 on 2009-02-04
Great that fixed it...

---

