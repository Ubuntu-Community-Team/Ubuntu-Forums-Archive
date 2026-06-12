---
title: "ATI x700 &amp; Big screen"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by gaea on 2007-01-05
Hi,

First of all; all the best wishes and a bugfree health.


Recently I bought a 22 inch acer AL2216W widescreen flatpanel to replace a 15 inch flatpanel.
With the old monitor everything worked fine.
After the swap I got normal X in 1680x1050 without configuring anything.
But when the monitor went into standby or I shutdown X by 'ctrl-alt F1' or 'ctrl-alt-backspace' or shutdown X in order to reboot/halt the pc the problem started.
The monitor said: 'no signal' and standby light lit.
Keyboard didn't work either, so I had to push the reset button.

Does anybody recognise this?

I have been looking on the net and here in the archive, but I get so many hits....](*,) 

the configuration is;

Kubuntu Edgy 64 bit
Xorg-fglrx-driver 
MSI K8N sli Mobo
Ati radeon X700 pro PCI-E, MSI branded and connected with a dvi cable.
Athlon64 +3500
512 mb memory

After a lot of reading I think it' s a driver issue, but I'm not shure
I also tried a vga cable, that did not help.
I also add a line in xorg.conf;  Option "AGPMask" "0x0000000" which would be a bugfix 
Did not help either.

On this system there is also Mandriva 2007 x86_64 with similar probs and winxp without probs.

Anybody an idea?

TIA,

Gerard

---

### Post by lowang on 2008-02-07
I've got same problem with ati x1350, it's caused by fglrx driver. 
All we can do is to wait for next driver release.
Although ati drivers are getting better you can still expect less problems with nvidia cards :(

---

