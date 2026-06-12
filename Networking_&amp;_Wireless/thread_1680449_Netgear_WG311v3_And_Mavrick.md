---
title: "Netgear WG311v3 And Mavrick"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by gdonwallace on 2011-02-02
I am running Maverick on an older computer.

I have installed ndiswrapper, and installed the winXP drivers for this PCI wireless card.

ndiswrapper -l shows that the card is installed, when I run additional drivers from the admin menu, all I see are the drives for my Nvidia card.

I do not have any signal coming from the wireless card.  The only option that I have for networking is my on-board nic.

Not sure what I have missed in getting this card set up.

thanks.

---

### Post by chaosdx on 2011-02-02
Do you have ndisgtk installed? If yes, do the drivers show up there? If no, please do install it - it's a very handy GUI tool for ndiswrapper, it will show up in your Administration menus.

Also, check if the windows drivers you chose are suitable for your system: that is, WinXp for Ubuntu 32-bit, or WinXP64 for Ubuntu 64-bit.

---

### Post by gdonwallace on 2011-02-02
I do have ndisgtk installed, and the drivers do show up there.  I installed the only inf file that was in the .zip that I downloaded from Netgear's website.  I saw a directory for WinXP, but there was nothing in it.

I am assuming that the one I installed is the correct one, but I can't be 100% sure.

The zip file extracts several Win version directories, but they are all empty.  There is only 1 .inf file that gets extracted and it is outside any of those directories.

---

### Post by chaosdx on 2011-02-02
You don't provide any details so far, which makes it difficult to help you...

Which is your system, 64-bit or 32-bit? What file exactly did you download for Windows driver? There seem to be several versions on the Netgear support site. Did you take the latest? It might be a good idea to go there and do that.

---

### Post by gdonwallace on 2011-02-02
I am running 32 bit Ubuntu. T

The file I downlaoded is **WG311v3 Software Version 5.0.0.3**.  Per website it is the most recent.

---

### Post by gdonwallace on 2011-02-04
Anyone have any thoughts on this??

---

### Post by CJ_Hudson on 2011-03-10
I have been trying for weeks to get my WG311v3 working in 64 bit Ubuntu.
However even in 64 bit it did not give me all the RAM so I went back to 32 bit.
Thanks guys, I now have a working wireless driver thanks to you!
(-:
I tried the Windows 2000 WG311v3 driver first, with no success, but then the XP driver worked a treat.

---

