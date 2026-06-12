---
title: "agpgart loaded but no module"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by spacedoubtman on 2008-04-19
Hello,

First of all I've spent the last three hours reading heaps of forum posts to resolve this and can't.

I've been experiencing problems with xv and sometimes causing serious system freezes and I want to try the nvidia apg driver to see if it will help. My question is not regarding the xv problems but just removing agpgart

From this I can see that I have agpgart and thats why the nvidia agp isn't working:
```

# dmesg | grep -i agp
[   64.257076] agpgart: Detected AGP bridge 0
[   64.272522] agpgart: AGP aperture is 256M @ 0xe0000000
[   66.538810] Linux agpgart interface v0.102 (c) Dave Jones
[   96.832559] NVRM: not using NVAGP, an AGPGART backend is loaded!

```

Everywhere I read it says to just remove the agp modules from my system but I don't think they are there (or quite normal)

I get nothing when I do this:
```

lsmod | grep -i agp

```



And when I do this It seems I don't have an agpgart module in my kernel.:
```

find /lib/modules/2.6.22-14-generic/ | grep -i agp
/lib/modules/2.6.22-14-generic/kernel/drivers/char/agp
/lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/sis-agp.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/via-agp.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/intel-agp.ko

```


I realize it could perhaps be compiled into the kernel but I don't know how to find out whats compiled in. Also I'm not too keen on using custom built kernel because I don't want to have to recompile and reconfigure each time there is an updated kernel.

I'm using the ubuntu fiesty fully updated
Linux iii 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

I have these packages installed (as well as others of course):
nvidia-glx-new version 100.14.19+2.6.22.4-14
nvidia-kernel-common version 20051028+1ubuntu7
linux-image-2.6.22-14 generic version 2.6.22-14.52
linux-restricted-modules-2.6.22-14 generic version 2.6.22-14 10


I have an asus k8v se motherboard which is mostly VIA a gforce 7600gt video card also have a dvb tv card - dont think it should make a difference though

```

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0d.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0d.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0d.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)

```




Thanks,
Adam

---

### Post by spacedoubtman on 2008-04-19
more reading and found that agp=off as a kernel option works

don't know if this will fix my probs but we'll see

---

