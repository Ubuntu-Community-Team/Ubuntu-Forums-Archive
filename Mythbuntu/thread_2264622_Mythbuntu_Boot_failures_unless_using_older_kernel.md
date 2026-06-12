---
title: "Mythbuntu Boot failures unless using older kernel"
date: 2015-02-08
forum: Mythbuntu
---

### Post by greg71 on 2015-02-08
Hello:

Long time mythbuntu user, first time poster. 

I have been running Mythbuntu 14.04 with no problems until a few days ago when I started experiencing failures on reboots. Most boots fail after the GRUB menu, with the message that it cannot find the root drive. If I use the GRUB 2 menu on boot to choose an older kernel (3.2.0-70-generic) then it boots fine every time. But if I choose the default current kernel (3.13.0-44-generic), the boot fails "most" of the time (but, strangely, it will occasionally boot just fine.) Logs are no help. I re-generated the grub.cfg file but the problem recurred. 

Does anyone have any ideas of where to start looking for the problem? Thank you for your time!

/Greg

---

### Post by v3.xx on 2015-02-08
If the 3.2 kernel works for you, why not just use it?  Its supported till 2017.

Could of been a hiccup when installing the 3.13 kernel.
3.13.0-45 is the latest kernel out.  Give it a try.
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by greg71 on 2015-02-09
Thanks for the quick reply, v3.xx 

Good suggestion on trying the new kernel, so I updated to the 3.13.0-45 kernel as you suggested, there were no apparent errors on the install but it still has the same symptoms (sometimes it will boot, sometimes it won't.) 

For some reason if I boot into the 3.2 kernel my graphics card is no longer recognized. Before I dig into solving that problem I was hoping to get the current kernel working, but so far no luck. Thanks for the help!

/Greg

---

### Post by v3.xx on 2015-02-10
I wonder if nomodeset would do any good.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by greg71 on 2015-02-12
Turns out the problem was not with the kernel directly, but was being caused by a bad disk drive (not my boot drive) on the SATA bus. For whatever mysterious reason, that drive was causing the boot to fail; when I took that mechanism off the SATA, boots started working fine again.

---

