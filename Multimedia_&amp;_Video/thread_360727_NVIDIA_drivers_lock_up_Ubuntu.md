---
title: "NVIDIA drivers lock up Ubuntu"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by Megatog615 on 2007-02-13
Hi. If I enable the "nvidia" driver in my xorg.conf, Ubuntu hard locks within seconds of using X. Bootup works fine(probably because of it being the console and all), but it locks up if I have the nvidia driver enabled, so I have to switch back to the "nv" driver. I've heard some old Via chipsets had problems like this.
Here's my lspci output:
```
[17179574.376000] VP_IDE: chipset revision 6
[17179600.456000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
megatog615@kolopodus:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 USB Controller: NEC Corporation USB (rev 43)
00:09.1 USB Controller: NEC Corporation USB (rev 43)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
```

/proc/cpuinfo:
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) processor
stepping        : 2
cpu MHz         : 1333.206
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips        : 2668.93
```

uname -r:
```
2.6.17-10-generic
```

---

### Post by mr.v. on 2007-02-14
what nvidia driver version are you using? where did you get it from and how did you install it?

---

