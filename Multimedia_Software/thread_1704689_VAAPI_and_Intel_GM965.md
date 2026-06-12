---
title: "VAAPI and Intel GM965"
date: 2011-03-11
forum: Multimedia Software
---

### Post by SleepWalkerX on 2011-03-11
Does vaapi support the intel gm965 video card?

---

### Post by SleepWalkerX on 2011-03-11
Apparently the answer looks like a yes, but you have to compile iegd.  

I followed this guide but I got to a snag when trying to compile.  

[http://www.nanoant.com/linux/compiling-kernel-iegd-10x-module-for-any-linux-distribution](http://www.nanoant.com/linux/compiling-kernel-iegd-10x-module-for-any-linux-distribution)

dave@thinklinux:~/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM$ make
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM
make[1]: Entering directory `/usr/src/linux-headers-2.6.36-999-generic'
  CC [M]  /home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/pci.o
  CC [M]  /home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/global.o
  CC [M]  /home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_alm.o
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_alm.c:67: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_alm.c: In function ‘iegd_alm_insert_entries’:
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_alm.c:396: warning: passing argument 2 of ‘agp_bridge->driver->mask_memory’ makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_alm.c:396: note: expected ‘dma_addr_t’ but argument is of type ‘struct page *’
  CC [M]  /home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_nap.o
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_nap.c:63: warning: initialization from incompatible pointer type
  CC [M]  /home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.o
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:76: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c: In function ‘iegd_plb_insert_entries’:
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:625: warning: passing argument 2 of ‘agp_bridge->driver->mask_memory’ makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:625: note: expected ‘dma_addr_t’ but argument is of type ‘struct page *’
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:637: warning: passing argument 2 of ‘agp_bridge->driver->mask_memory’ makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:637: note: expected ‘dma_addr_t’ but argument is of type ‘struct page *’
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:639: warning: passing argument 2 of ‘agp_bridge->driver->mask_memory’ makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:639: note: expected ‘dma_addr_t’ but argument is of type ‘struct page *’
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:692: error: ‘file_rss’ undeclared (first use in this function)
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:692: error: (Each undeclared identifier is reported only once
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:692: error: for each function it appears in.)
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c: In function ‘iegd_plb_remove_entries’:
/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.c:801: error: ‘file_rss’ undeclared (first use in this function)
make[2]: *** [/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM/agp/drv_plb.o] Error 1
make[1]: *** [_module_/home/dave/iegd/IEGD_10_3_Linux/IEGD_10_3_Linux/IKM] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.36-999-generic'
make: *** [modules] Error 2


If anyone successfully compiled iegd lmk.

---

### Post by Yellow Pasque on 2011-03-11
> **SleepWalkerX said:**
> Does vaapi support the intel gm965 video card?
I'm pretty sure it doesn't support H.264 or VC-1

---

### Post by SleepWalkerX on 2011-03-11
> **Temüjin said:**
> I'm pretty sure it doesn't support H.264 or VC-1

Maybe not fully, but even partial acceleration would be nice.  I need some docs.

---

### Post by SleepWalkerX on 2011-03-12
I downloaded IEGD 10.4 (just came out last month!). Getting one step further just trying to compile these things..  

[http://developer.windriver.com/thread/1207](http://developer.windriver.com/thread/1207)

I made some more modifications and it compiles further.  It gets stuck on mmap.  I guess the kernel made some changes recently?

dave@thinklinux:~/iegd/IEGD_10_4_Linux/IKM$ make
/home/dave/iegd/IEGD_10_4_Linux/IKM
make[1]: Entering directory `/usr/src/linux-headers-2.6.36-999-generic'
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/pci.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/global.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_alm.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_alm.c:67: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_alm.c: In function &#8216;iegd_alm_insert_entries&#8217;:
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_alm.c:396: warning: passing argument 2 of &#8216;agp_bridge->driver->mask_memory&#8217; makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_alm.c:396: note: expected &#8216;dma_addr_t&#8217; but argument is of type &#8216;struct page *&#8217;
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_nap.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_nap.c:63: warning: initialization from incompatible pointer type
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:79: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c: In function &#8216;iegd_plb_insert_entries&#8217;:
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:637: warning: passing argument 2 of &#8216;agp_bridge->driver->mask_memory&#8217; makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:637: note: expected &#8216;dma_addr_t&#8217; but argument is of type &#8216;struct page *&#8217;
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:649: warning: passing argument 2 of &#8216;agp_bridge->driver->mask_memory&#8217; makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:649: note: expected &#8216;dma_addr_t&#8217; but argument is of type &#8216;struct page *&#8217;
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:651: warning: passing argument 2 of &#8216;agp_bridge->driver->mask_memory&#8217; makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_plb.c:651: note: expected &#8216;dma_addr_t&#8217; but argument is of type &#8216;struct page *&#8217;
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_cmn.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_cmn.c: In function &#8216;iegd_cmn_insert_entries&#8217;:
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_cmn.c:646: warning: passing argument 2 of &#8216;agp_bridge->driver->mask_memory&#8217; makes integer from pointer without a cast
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_cmn.c:646: note: expected &#8216;dma_addr_t&#8217; but argument is of type &#8216;struct page *&#8217;
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_gn4.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_gn4.c:66: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_4_Linux/IKM/agp/drv_gn4.c:91: warning: initialization from incompatible pointer type
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_drv.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_265.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2611.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2615.o
  CC [M]  /home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2624.o
/home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2624.c:742: error: request for member &#8216;mmap&#8217; in something not a structure or union
/home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2624.c:782: warning: initialization from incompatible pointer type
/home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2624.c:824: warning: initialization from incompatible pointer type
make[2]: *** [/home/dave/iegd/IEGD_10_4_Linux/IKM/drm/iegd_interface_2624.o] Error 1
make[1]: *** [_module_/home/dave/iegd/IEGD_10_4_Linux/IKM] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.36-999-generic'
make: *** [modules] Error 2


edit:  I commented out some code (mmap, poll, and fasync) which is probably a dangerous thing to do.. but it does compile now.. hmm.  Maybe I'll go back and do some research..

---

### Post by SleepWalkerX on 2011-03-12
I ran the driver, but my screen blacked.  I guess that code is important.  :P

I'm going to have to see what's different.

edit:  Ok, I resolved the issue and got it compiling, but it still gives me a blank screen when I insmod the iegd_mod.ko module..  Maybe it has something to do with how I created the driver code using intel's software..

---

### Post by SleepWalkerX on 2011-03-12
To those reading, I fixed the problem above by moving the .mmap, .poll, and .fasync initializations above the .unlocked_ioctl one.  

I successfully compiled with default settings but I got some kind of kernel panic when loading the module. :(

edit:  Here's my kernel panic.

Mar 12 22:36:24 thinklinux kernel: [  740.509052] [IEGD]: Unregister agpgart name agpgart-intel
Mar 12 22:36:24 thinklinux kernel: [  740.511941] [IEGD]: Registering iegd gart module
Mar 12 22:36:24 thinklinux kernel: [  740.511971] [IEGD]: Initialize IEGD agpgart and drm
Mar 12 22:36:24 thinklinux kernel: [  740.511992] [IEGD]: Intel GM965 chipset detected
Mar 12 22:36:24 thinklinux kernel: [  740.532409] Modules linked in: iegd_mod(+) binfmt_misc ppdev arc4 snd_hda_codec_conexant i915 snd_hda_intel iwl3945 drm_kms_helper thinkpad_acpi pcmcia drm snd_hda_codec psmouse iwlcore i2c_algo_bit snd_hwdep snd_pcm snd_seq_midi snd_rawmidi yenta_socket intel_agp agpgart pcmcia_rsrc snd_seq_midi_event lp parport snd_seq snd_timer snd_seq_device serio_raw led_class video pcmcia_core mac80211 snd soundcore output cfg80211 nvram snd_page_alloc usbhid hid usb_storage ahci tg3 libahci
Mar 12 22:36:24 thinklinux kernel: [  740.532409] 
Mar 12 22:36:24 thinklinux kernel: [  740.532409] Pid: 3174, comm: insmod Not tainted 2.6.36-999-generic #201010021408 7649CTO/7649CTO
Mar 12 22:36:24 thinklinux kernel: [  740.532409] EIP: 0060:[<fb68b3b8>] EFLAGS: 00210282 CPU: 0
Mar 12 22:36:24 thinklinux kernel: [  740.532409] EIP is at iegd_igm45_sizes+0x8/0xffffd3b7 [iegd_mod]
Mar 12 22:36:24 thinklinux kernel: [  740.532409] EAX: c15e7380 EBX: fb68b3e0 ECX: fb68b3b0 EDX: f4fe232c
Mar 12 22:36:24 thinklinux kernel: [  740.532409] ESI: f4fe2300 EDI: ffffffed EBP: d56f3dec ESP: d56f3dcc
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  f83ae1ba d56f3ddc c037c2c8 f70c9800 d56f3dec fb68bba0 f4fe2300 ffffffed
Mar 12 22:36:24 thinklinux kernel: [  740.532409] <0> d56f3e10 f83ae482 f70c99f8 f70c9bf4 f70c9800 f4fe2300 f70c9800 f4fe2300
Mar 12 22:36:24 thinklinux kernel: [  740.532409] <0> 00000000 d56f3e34 fb688725 fb689068 fb688c63 00200292 00000000 d56f3e50
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<f83ae1ba>] ? agp_backend_initialize+0x4a/0x280 [agpgart]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c037c2c8>] ? pci_fixup_device+0x28/0x80
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<f83ae482>] ? agp_add_bridge+0x62/0x180 [agpgart]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<fb688725>] ? iegd_intel_probe+0x1d5/0x217 [iegd_mod]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0377100>] ? local_pci_probe+0x40/0x90
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c037716c>] ? pci_call_probe+0x1c/0x20
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0378374>] ? __pci_device_probe+0x54/0x60
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c03783ab>] ? pci_device_probe+0x2b/0x50
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040cc4e>] ? really_probe+0xde/0x150
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0413ebe>] ? pm_runtime_barrier+0x4e/0xa0
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040ccfc>] ? driver_probe_device+0x3c/0x60
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040cfda>] ? __driver_attach+0x7a/0x80
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040bf59>] ? bus_for_each_dev+0x49/0x70
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040ca5e>] ? driver_attach+0x1e/0x20
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040cf60>] ? __driver_attach+0x0/0x80
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040c7bb>] ? bus_add_driver+0xbb/0x200
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c035d257>] ? kset_find_obj+0x57/0x70
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0377090>] ? pci_device_shutdown+0x0/0x30
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0377090>] ? pci_device_shutdown+0x0/0x30
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c040d1f2>] ? driver_register+0x52/0xd0
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<fb682140>] ? iegd_gart_init+0x0/0xd0 [iegd_mod]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0378015>] ? __pci_register_driver+0x45/0x90
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<fb682140>] ? iegd_gart_init+0x0/0xd0 [iegd_mod]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<fb682191>] ? iegd_gart_init+0x51/0xd0 [iegd_mod]
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c010124a>] ? do_one_initcall+0xba/0x100
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0186316>] ? sys_init_module+0x76/0x1c0
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c021e9ce>] ? sys_close+0x6e/0xc0
Mar 12 22:36:24 thinklinux kernel: [  740.532409]  [<c0102cdf>] ? sysenter_do_call+0x12/0x28
Mar 12 22:36:24 thinklinux kernel: [  740.895190] ---[ end trace 4e7ba1cd939cbc9d ]---

---

### Post by natomasboy on 2011-11-18
Any update on getting VAAPI to work on GM965?

---

### Post by hugmenot on 2011-11-19
I’ve compiled it and it works in my GM45 laptop. Not sure of all the version numbers of components you need to meet but it basically boils down to getting stuff from git.

Get these

[http://cgit.freedesktop.org/vaapi/libva/](http://cgit.freedesktop.org/vaapi/libva/)
[http://cgit.freedesktop.org/vaapi/intel-driver/](http://cgit.freedesktop.org/vaapi/intel-driver/)

And checkout the g45-h264 branch from both repos. I merged master into g45-h264 and it worked afterwards with both mplayer-vaapi and gstreamer-vaapi. Some files made it choke randomly at certain timestamps though.

---

### Post by hugmenot on 2011-11-19
Here:

```

~/src/X/intel-driver/debian.build$ vainfo 
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.16.pre1)
vainfo: Driver version: Intel i965 driver - 1.0.16.pre1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
~/src/X/intel-driver/debian.build$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

---

