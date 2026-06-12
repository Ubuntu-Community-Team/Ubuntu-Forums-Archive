---
title: "Still having fglrx problems"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by eudemon on 2005-10-13
Redently upgraded my laptop to the breezy preview, and I'm still not getting 3d hardware acceleration.  Filed a bugzilla report here:  [http://bugzilla.ubuntu.com/show_bug.cgi?id=17644](http://bugzilla.ubuntu.com/show_bug.cgi?id=17644)

> 
While attempting to get the fglrx dri working on my system, I found this in
Xorg.0.log:

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOSPC"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8e02000 at 0xb7b70000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Checked my kern.log and found this:

Oct 12 10:28:09 localhost kernel: [4294788.066000] [fglrx] Maximum main memory
to use for locked dma buffers: 929 MBytes.
Oct 12 10:28:09 localhost kernel: [4294788.066000] ACPI: PCI Interrupt Link
[LNKE] enabled at IRQ 11
Oct 12 10:28:09 localhost kernel: [4294788.066000] ACPI: PCI Interrupt
0000:01:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Oct 12 10:28:09 localhost kernel: [4294788.066000] [fglrx] module loaded - fglrx
8.16.20 [Aug 16 2005] on minor 0
Oct 12 10:28:09 localhost kernel: [4294788.076000] [fglrx] Kernel AGP support
doesn't provide agplock functionality.
Oct 12 10:28:09 localhost kernel: [4294788.076000] [fglrx] AGP detected,
AgpState   = 0x1f00421b (hardware caps of chipset)
Oct 12 10:28:09 localhost kernel: [4294788.076000] mtrr: no more MTRRs available
Oct 12 10:28:09 localhost kernel: [4294788.076000] [fglrx:firegl_unlock] *ERROR*
Process 7304 using kernel context 0

My system has a radeon 9700 mobile graphics card, and amd64 cpu.  This happens
whether I use the 386, 686, or k7 kernel.  I'm running the current Breezy
preview, with xorg-driver-fglrx 8.16.20 from the repositories.


Under Hoary, I was able to get hardware acceleration working, by following these instructions:  [http://ubuntuforums.org/showpost.php?p=77060&postcount=54](http://ubuntuforums.org/showpost.php?p=77060&postcount=54)

I have only a basic understanding of what mtrrs are, and don't know why they would be completely used up.

Also, I just realized that my "cat /proc/mtrr" output might be helpful, so here it is:

reg00: base=0x00000000 (   0MB), size=  16MB: write-back, count=1
reg01: base=0x01000000 (  16MB), size=  16MB: write-back, count=1
reg02: base=0x02000000 (  32MB), size=  32MB: write-back, count=1
reg03: base=0x04000000 (  64MB), size=  64MB: write-back, count=1
reg04: base=0x08000000 ( 128MB), size= 128MB: write-back, count=1
reg05: base=0x10000000 ( 256MB), size= 256MB: write-back, count=1
reg06: base=0x20000000 ( 512MB), size= 512MB: write-back, count=1

I'm going to do a clean install of Breezy final tonight, and I'll see I can get this fixed.  Thanks for any help.

---

