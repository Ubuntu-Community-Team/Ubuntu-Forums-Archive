---
title: "NVIDIA &amp; Matrox together?"
date: 2011-10-22
forum: Multimedia Software
---

### Post by hyperanalysis on 2011-10-22
Hi All,

I have an NVIDIA GeForce 9600 GT which serves 2 identical monitors in a dual-screen twinview setup, this functions perfectly.

However, I also have a Matrox Millenium G450 PCI graphics card that I want to use in the same system, so that I can use my 37" plasma monitor as a 3rd monitor on the same system.

I previously had the 37" setup on dual-screen twinview with one of my 19" monitors, but quickly became despondant at not being able to use both 19"'s together, as they look so lovely side by side. :)

So, my first question is; as I am using the NVIDIA X Server Settings to configure my NVIDIA card, are there any outright complications with using a Matrox card as well, that would stop a multi-monitor solution being possible?

If the above answer is no, then I am having some issues; I have located and downlaoded the linux drivers kindly supplied by Matrox for my card, however when trying to install, I receive the following errors:

iain@socrates:~/Downloads/matrox_driver-x86_32-4.4.0$ sudo sh install.sh
[sudo] password for iain: 
[: 43: i686: unexpected operator
install.sh: 57: function: not found
install.sh: 69: function: not found
install.sh: 78: function: not found
install.sh: 95: function: not found

Please enter the full path to your current X11R6 directory: 
Example: /usr/X11R6

-e \E[31mERROR: The X11R6 path could not be found. Please make
-e        sure that an X server is installed.

I am using Ubuntu 11.10. Any suggestions or insights would be greatly appreciated, I'd prefer to not have to buy a quad-card!

Kind regards,
Iain.

---

