---
title: "No display on boot after fresh install"
date: 2011-06-07
forum: Multimedia Software
---

### Post by shasan on 2011-06-07
I just performed a fresh install of 11.04 *Server*. The installation went smoothly and as expected. As soon as I leave the BIOS and Ubuntu boots, however, I lose my display (my monitor says "Cannot display this video mode"). I am able to ssh into the machine just fine, so I know it is booting up fine; I just don't have a local console. 

Other threads related to this topic suggest adding something like "vga=771" to the boot options in grub/menu.lst, but I don't see that file anywhere in my 11.04 server install. Where can I configure display settings now?

I am using the following video card:

$ lspci -nn | grep VGA
01:04.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27)

Any suggestions?


(note: this is crossposted from server issues... not sure where to file it; mods feel free to delete if this violates forum etiquette)

---

