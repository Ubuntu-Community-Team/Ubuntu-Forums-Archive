---
title: "Mythbuntu was working great and then the motherboard died re-install?"
date: 2012-10-06
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-06
So I put in another model MSI motherboard in place of the older MSI motherboard.  The new setup booted right up with the original mythbuntu hard drive and everything was working great for about 2 hours and then the network interface just plain stopped working. I get flashing lights on the RJ45 Ethernet connector, everything else on the network is working just fine.

So my question is, since I changed mother boards do you think I need to reinstall 12.04 mythbuntu as new drivers need to be installed, or is there another way to sort this out......?

:mad:

---

### Post by nickrout on 2012-10-07
> **RTIInstaller said:**
> So I put in another model MSI motherboard in place of the older MSI motherboard.  The new setup booted right up with the original mythbuntu hard drive and everything was working great for about 2 hours and then the network interface just plain stopped working. I get flashing lights on the RJ45 Ethernet connector, everything else on the network is working just fine.

So my question is, since I changed mother boards do you think I need to reinstall 12.04 mythbuntu as new drivers need to be installed, or is there another way to sort this out......?

:mad:

The kernel works out which modules to load for the hardware it finds on boot, so there is no point in a reinstall.

If you have played with what modules are loaded on boot, you may need to look at what changes you made. 

Questions: what was the network chipset and module on the old machine?

Same question for the new machine.

lspci and modprobe are your friends to find out, as well as the manufacturers website/specifications.

---

### Post by RTIInstaller on 2012-10-07
> **nickrout said:**
> The kernel works out which modules to load for the hardware it finds on boot, so there is no point in a reinstall.

If you have played with what modules are loaded on boot, you may need to look at what changes you made. 

Questions: what was the network chipset and module on the old machine?

Same question for the new machine.

lspci and modprobe are your friends to find out, as well as the manufacturers website/specifications.

Thanks, I already went ahead and did an install as an upgrade retaining files and it came out ok, network problem solved, it also fixed some of the nvidea problems I was having trouble with. I had also added a new sound card so that was also installed correctly.   

A funny thing happened this time around, it saw my old raid stack  that was originally installed with myth 5 and freaked out. Put up an angry nag screen that said "THIS VERSION OF MYTH TV IS 35 GENERATIONS OUT OF DATE" I closed the nag screen and all is well now I hope :smile:

Thanks again for all of your help!

---

