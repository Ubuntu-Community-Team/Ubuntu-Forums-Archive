---
title: "nvidia and glx problems"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by niemand on 2006-07-09
Running glxgears sends X off the edge!

Let me start from the beginning. I have recently switched to the Ubuntu 6.06 distribution and would like to get the game Neverwinter Nights working once again. The current obstruction is openGL is not working well at all. I can do a glxinfo, glxdemo, and glxheads and everything appears to be just fine. However, when I execute glxgears, X freezes or locks up with varying visual affects. Rarely I can recover with a ctrl-c. In all cases, I can ssh in from another machine and inspect what is happening. Basically, X is getting 100% of the CPU but not redrawing anything. I should also note that nothing shows up in /var/log/* about this either.

So, for starters I have:
$> uname -a
Linux elysium 2.6.15-25-k7 #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006 i686 GNU/Linux

$> /sbin/lsmod | grep nvidia
nvidia               4553140  12
agpgart                37072  2 via_agp,nvidia
i2c_core               23168  3 i2c_acpi_ec,i2c_viapro,nvidia

$> lspci
... snip ...
0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

I think that gives the basics. The lspci gives the graphics card, the lsmod shows that I have loaded the correct kernel module, and uname shows which platform I am working on. I think the fact that I have the correct kernel module loaded says that my xorg.conf is good.

Now, I have been searching the net and looking in this forum and have already tried some of the hints and suggestions given at [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper).

I am happy to provide more information if requested. All I am looking for at this forum is to get glxgears working.

Thanks for any and all help.

---

### Post by niemand on 2006-07-15
Updated to the latest set of patches and all is well.

---

