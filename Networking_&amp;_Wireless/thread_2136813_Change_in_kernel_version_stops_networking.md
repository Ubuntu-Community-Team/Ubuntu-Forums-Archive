---
title: "Change in kernel version stops networking"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by johncroc on 2013-04-18
I'm running 12.10 and have an Atheros 8161 chipset  wired ethernet card.  My understanding is that support for my eth is now built-in to the kernel, but everytime the kernel changes, I have to re-compile my driver (compat-wireless) to get networking operational again.  It happened when I went from 3.5.0.-17 to -26 a few weeks ago; and again earlier today when I went from -26 to -27.

Is it possible that my compiled driver is getting in the way of the native kernel driver, and if so, how do I get rid of the compiled driver so the native one can be  "first in line"?  Or is there some other way to accomplish the same thing?  Or do I just have the wrong hypothesis in the first place?

Thanks, in advance, for your help.

John

---

### Post by David1957 on 2013-04-20
Same problem here, any advice?

---

### Post by johncroc on 2013-04-20
Assuming you're not "down" and that you know how to do the recompile, I don't have a clue (yet) regarding the need to recompile.  If, however, you are asking for advice on doing the recompile, I'm happy to help.  It's very simple really (assuming you still have the compat-wireless package).  First, in a terminal window, go to the directory where that stuff is stored, then issue a 
```
make
```
Next:
```
sudo make unload
```
Then:
```
sudo make install
```
Finally:
```
sudo modprobe alx
```

At least for me, that always works.

---

### Post by johncroc on 2013-05-02
bump

---

### Post by chili555 on 2013-05-02
> At least for me, that always works. And are you saying that this time it did not? May we see:```
sudo modprobe alx
dmesg | grep alx
```The process I'd recommend instead is:```
cd Desktop/compat-wherever
sudo su
modprobe -r alx
./scripts/driver-select restore
./scripts/driver-select alx
[COLOR="#FF0000"]make clean[/COLOR]
make
make install
modprobe alx
exit
```Note any errors and post them here.

---

