---
title: "Using radeon graphics card on MacBookPro8,2"
date: 2013-05-24
forum: Multimedia Software
---

### Post by miguelnegrao on 2013-05-24
Hi

After having a read a bunch of posts I'm still unclear on how to 
1) Use the radeon graphics card
2) Switch between graphics card.

My current configuration is ubuntu13.04 with  kernel 3.8.0-19-lowlatency and I'm booting in efi mode using efit. I'm currently using the integrated intel graphics card by using the following grub option

```
 
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod btrfs
    set root='hd4,gpt3'
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    outb 0x750 0
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd4,gpt3 --hint-efi=hd4,gpt3 --hint-baremetal=ahci4,gpt3  f2e4e4d3-2d8e-4764-a818-de9176405c4b
    else
      search --no-floppy --fs-uuid --set=root f2e4e4d3-2d8e-4764-a818-de9176405c4b
    fi
    echo    'A carregar Linux 3.8.0-19-lowlatency ...'
    linux    /@/boot/vmlinuz-3.8.0-19-lowlatency root=UUID=f2e4e4d3-2d8e-4764-a818-de9176405c4b ro rootflags=subvol=@   video=efifb i915.modeset=1 i915.lvds_channel_mode=2 i915.lvds_use_ssc=0 nosplash
    echo    'A carregar ramdisk inicial ...'
    initrd    /@/boot/initrd.img-3.8.0-19-lowlatency

```

This is the only configuration where I've ever managed to boot ubuntu.

If I try booting with 

```
  linux    /@/boot/vmlinuz-3.8.0-19-lowlatency  root=UUID=f2e4e4d3-2d8e-4764-a818-de9176405c4b ro rootflags=subvol=@  nosplash
```

The boot procedure just hangs with the message "Cannot initialize Agpart Module".

If I try booting with 

```

recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod btrfs
    set root='hd4,gpt3'
    outb 0x728 1
    outb 0x710 2
    outb 0x740 2
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd4,gpt3 --hint-efi=hd4,gpt3 --hint-baremetal=ahci4,gpt3  f2e4e4d3-2d8e-4764-a818-de9176405c4b
    else
      search --no-floppy --fs-uuid --set=root f2e4e4d3-2d8e-4764-a818-de9176405c4b
    fi
    echo    'A carregar Linux 3.8.0-19-lowlatency ...'
    linux    /@/boot/vmlinuz-3.8.0-19-lowlatency root=UUID=f2e4e4d3-2d8e-4764-a818-de9176405c4b ro rootflags=subvol=@ i915.lvds_use_ssc=0 nosplash
    echo    'A carregar ramdisk inicial ...'
    initrd    /@/boot/initrd.img-3.8.0-19-lowlatency

```

I get

```

[    6.849787] [drm] radeon defaulting to kernel modesetting.
[    6.849790] [drm] radeon kernel modesetting enabled.
[    6.849846] fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
[    7.223532] radeon 0000:01:00.0: Invalid ROM contents
[    7.223631] radeon 0000:01:00.0: Invalid ROM contents
[    7.223675] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
[    7.223723] radeon 0000:01:00.0: Fatal error during GPU init
[    7.223764] [drm] radeon: finishing device.
[    7.224999] radeon: probe of 0000:01:00.0 failed with error -22

```

I would like to be able to use the radeon graphics card and to be able to switch between cards.

Any help apreciated.

Miguel Negrão

---

### Post by 2F4U on 2013-05-24
Getting a switchable graphics to work properly can be difficult. As far as I know (but I am no expert since I do not own a device with switchable graphics) you need the proprietary AMD graphics drivers:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by Bucky Ball on 2013-05-24
*Thread moved to **Multimedia & Video**.*

---

### Post by miguelnegrao on 2013-05-25
> **2F4U said:**
> Getting a switchable graphics to work properly can be difficult. As far as I know (but I am no expert since I do not own a device with switchable graphics) you need the proprietary AMD graphics drivers:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

I tried installing the proprietary amd drivers but they fail to load. Find attached the dmesg log.

```

dmesg | grep fglrx

[    5.513870] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    5.528335] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7667 MBytes.
[    5.528507] <6>[fglrx]   vendor: 1002 device: 6760 count: 1
[    5.531777] <6>[fglrx] ioport: bar 4, base 0x2000, size: 0x100
[    5.531873] <6>[fglrx] Kernel PAT support is enabled
[    5.531905] <6>[fglrx] module loaded - fglrx 12.10.5 [Mar 28 2013] with 1 minors
[    6.500443] <3>[fglrx:hal_read_VBIOS] *ERROR* Invalid AMD VBIOS at bus 1!
[    6.500446] <3>[fglrx:hal_init_gpu] *ERROR* Failed to read VBIOS!
[    6.500448] <6>[fglrx] device open failed with code -1
[    6.505330] <6>[fglrx] ATIF platform detected with notification ID: 0x81
[    6.505686] <3>[fglrx:firegl_get_vbios_image] *ERROR* Invalid image size requested
[    6.505722] <3>[fglrx:firegl_cail_query_parameter] *ERROR* CAIL_QueryParameter failed
```

Would I need to also add some settings to grub ? Do the proprietary amd drivers work with ubuntu and unity in 13.04 ?

best,
Miguel

---

### Post by 2F4U on 2013-05-25
What ATI card is it? It seems as if the driver is not recognising the card.

---

### Post by miguelnegrao on 2013-05-25
I'ts a macbookpro 8,2 with a Radeon HD 6490M:

[TABLE="class: handcursor"]
[TR]
[TD="class: mocklink, width: 133, bgcolor: #F3F3E9"][/TD]
 [TD="width: 133, bgcolor: #F3F3E9"]Radeon HD 6490M*[/TD]
 [TD="class: mocklink, width: 133, bgcolor: #F3F3E9"]VRAM Type:[/TD]
 [TD="width: 133, bgcolor: #F3F3E9"]GDDR5[/TD]
 [/TR]
 [/TABLE]
   [TABLE="class: switchgroup1"]
[TR]
[TD="width: 129, bgcolor: #F3F3E9"]Details:[/TD]
 [TD="width: 400, bgcolor: #F3F3E9"]*This system has dual graphics processors -- an AMD Radeon HD 6490M graphics processor with 256 MB of dedicated GDDR5 SDRAM *and* Intel HD Graphics 3000 with 384 MB of DDR3 SDRAM shared with main memory.[/TD]
[/TR]
[/TABLE]

---

### Post by miguelnegrao on 2013-05-30
I was able to get the radeon working by booting directly through refind using efi stub boot. This should be documented !!!! I've lost countless hours on this ! (I'm willing to document, if I know where to go)

---

### Post by Bucky Ball on 2013-05-30
I heard the Tutorials sub-forum was reopened recently. That's the place for it. 

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

Just list the steps you took to get it going in easy to follow point form, elaborate where necessary, and it's documented. ;)

I usually find it easiest to knock it up in a word processor and get it right and presentable there then just copy/paste that into the first post of the thread and tweak a little more there. Add a link to it in your signature if you fancy (you might need to have fifty beans to do that, though, not sure) but definately post a link to it here to wrap things up if and when you write it up. Good luck.

---

### Post by miguelnegrao on 2013-05-31
I've documented the steps needed in [https://help.ubuntu.com/community/MacBookPro8-2/Raring](https://help.ubuntu.com/community/MacBookPro8-2/Raring)

---

