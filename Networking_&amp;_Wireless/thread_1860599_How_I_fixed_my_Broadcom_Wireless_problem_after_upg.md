---
title: "How I fixed my Broadcom Wireless problem after upgrade to 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by rosielarose on 2011-10-14
I use a Dell Inspiron 1720 that has one of the B43 wireless cards that causes so much heartbreak.  My usual fix didn't work after this upgrade, so here is what I did to get myself working again.  Results may vary, of course.

I went into Synaptic after plugging my machine into the wall.

I typed in b43 into the search and saw that the firmware-b43-installer and the b43-fwcutter were both installed (but I remembered an error message during upgrade saying the firmware-b43-installer had an error and wasn't loaded properly).  I marked each for removal and applied the changes. 

I typed in STA into the search, saw the BCMWL-kernel-source had the neat Ubuntu icon beside it but wasn't installed.  I liked the write-up in the info box, and I figured since the wireless ain't working already, why not? I marked it for installation, applied those changes, and the wireless was working even before the installation was done. 

I hope this helps. I google and search a ton every few upgrades because of this driver, and since I got it to work by myself for once, I figured I should share!

---

