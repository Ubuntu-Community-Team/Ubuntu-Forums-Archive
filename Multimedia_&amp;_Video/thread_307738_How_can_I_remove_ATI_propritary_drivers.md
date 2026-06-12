---
title: "How can I remove ATI propritary drivers"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Saubazi on 2006-11-27
I got a bit lost with drivers and wanted to try out older ati drivers and see if the recent driver update was a problem for my nonfunctioning wine applications.

Anyway I went and used "method 2" 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Installing drivers from ati.com

I did:
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod

So I reckon this builds kernel modules and they are now in kernel?
How can I remoce them and go back to the normal xorg-fgrlx-driver from repository without breaking my computer?

---

### Post by pay on 2006-11-27
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by hardyn on 2006-11-27
i have had no trouble removing them through synaptic, and replacing xorg.conf with the backup the install makes.

---

### Post by Saubazi on 2006-11-27
> **pay said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```

So simple???In Linux???

And afterwards if I want to use method 1 again:

sudo apt-get install xorg-driver-fglrx
and
sudo apt-get install fglrx-control

I don't have to mess anything again with module-assistant in order to remove it?

---

