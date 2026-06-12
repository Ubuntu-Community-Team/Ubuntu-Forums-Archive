---
title: "Getting the ATI fglrx mess to work..."
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by itsidefix on 2006-12-02
Hi,

I know there are many guides on how to do this, but none seems to work for me.  I have a GeCube Radeon X1600 PRO 512MB and every attempt to get it to work ends with the following:

[17179589.296000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179589.296000] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[17179589.296000] [fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
[17179600.760000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179600.760000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179600.760000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[17179600.760000] [fglrx:firegl_unlock] *ERROR* Process 4170 using kernel context 0

The fglrx error shown is the only error showing in my log (dmesg).
Any ideas? Any comments what this error stands for?

I also changed my xorg.conf as shown in the guides, including the extras section and blacklisted the old fglrx.

Thanks,
Chris

---

### Post by klecu on 2006-12-02
How did you install the proprietary drivers? I recommend using [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).

---

### Post by itsidefix on 2006-12-03
This is what I did- it just doesn't seem to work for me.  I'd like to try and disable the kernel agp driver and see if it helps, but for some reason passing the agp=off kerner parameter does not do the job.  I also tried to blacklist agpgart- again with no success.

Chris

---

### Post by itsidefix on 2006-12-03
Anyone any thoughts on how to disable the kernel agp probing? passing agp=off along with grub doesn't do it... blacklisting also didn't work.

Thanks,
Chris

---

### Post by Forceflow on 2006-12-03
Have you tried a total Xorg reconfig ?

---

### Post by itsidefix on 2006-12-03
Apart of making sure that xorg.conf is fine? No. I tried method 1 & 2, as well as installing instead of creating a distribution package- all with the same result.  However, if you could provide some details regarding what to re-configure... 

Thanks,
Chris

---

### Post by iramhernandez on 2006-12-19
I'm having problems with x1600 agp also.  Built in ATI drivers don't seem to work (VESA is used instead).  fglrx that comes with edgy don't work (8.28).  Newest ATI drivers don't seem to work either (8.32.5). 

I get the following in dmesg:

```
[17179698.820000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[17179700.360000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179700.360000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179700.360000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)

```

The drivers appear to work correctly, regardless but I have very slow performance (less than previously installed (and very old) ATI Radeon 9250.

I suspect the problem lies with fglrx trying to use the kenerl's AGP instead of internal AGP.

Have you any luck?

---

