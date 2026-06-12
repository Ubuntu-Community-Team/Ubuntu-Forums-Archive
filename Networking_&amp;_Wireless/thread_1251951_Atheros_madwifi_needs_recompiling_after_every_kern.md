---
title: "Atheros madwifi needs recompiling after every kernel update"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by izziere on 2009-08-28
Forgive the noob question, but I run a notebook on *buntu Hardy with an Atheros 5000 series wireless card.  Works fine with madwifi settings, but everytime I download an update to the kernel I have to recompile using the following brief script:

```
#!/bin/sh
cd /xxx/madwifi-hal-0.10.5.6-r3875-20081105
sudo make
sudo make install
sudo modprobe ath_pci
sudo reboot
```

It's not a problem, but it is a pain.  Is there something I can do to work round this, or have I done something wrong to make this occur in first place?

Thanks!

---

### Post by chili555 on 2009-08-28
I suggest amending your script as follows:```
#!/bin/sh
cd /xxx/madwifi-hal-0.10.5.6-r3875-20081105
[COLOR="Red"]sudo make clean[/COLOR]
sudo make
sudo make install
sudo modprobe ath_pci
sudo reboot
```> Is there something I can do to work round thisNope.> have I done something wrong to make this occur in first place?Nope.

You have built the module against a certain kernel, 2.6-xx. When a new kernel and headers are added to your system, 2.6-xy, it knows nothing about your compiled module. You must add it to the new kernel. Your script does a fine job.

I also suggest you check Madwifi's site periodically to see if there is a newer version than November 5, 2008 (20081105). Download and unpack the newer version and amend your script to suit.

---

### Post by izziere on 2009-08-29
Great - thanks for clarifying.

---

