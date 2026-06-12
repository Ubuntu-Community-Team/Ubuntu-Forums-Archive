---
title: "no nvidia.ko since dist-upgrade"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by loswillios on 2007-08-23
Hi,

I've dist-upgraded to 7.10 last week and since then I'm struggling to get my nVidia GeForce3 Ti 200 to work. I've installed all the necessary packages:

```
ii  nvidia-glx                                 1:1.0.9639+2.6.22.3-10.1       NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                       20051028+1ubuntu7              NVIDIA binary kernel module common files
ii  linux-restricted-modules-2.6.22-10-386     2.6.22.3-10.1                  Non-free Linux 2.6.22 modules on 386
```

But somehow, the nvidia.ko kernel module isn't generated. It isn't in /lib/modules/2.6.22-10-386/volatile/ and slocate doesn't find it either. What should I do? What are the commands to compile the module 'the ubuntu-way'? Is there a package which ships nvidia.ko?

---

### Post by Bachstelze on 2007-08-23
Why should it be in volatile/ ? It is in kernel/drivers/video/...

---

### Post by loswillios on 2007-08-23
I have only 

/lib/modules/2.6.22-10-386/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.22-10-386/kernel/drivers/char/agp/nvidia-agp.ko

in there

---

### Post by tseliot on 2007-08-23
type:
```
sudo apt-get install linux-generic
```

and post the output

---

### Post by loswillios on 2007-08-23
```
~$ LANG=C sudo aptitude install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  linux-headers-2.6.22-9-generic
The following NEW packages will be automatically installed:
  linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
The following NEW packages will be installed:
  linux-generic linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
0 packages upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 16.3MB of archives. After unpacking 36.6MB will be used.
Do you want to continue? [Y/n/?]
```

What is it with -generic? I always thought -386 is a little more optimized

---

### Post by tseliot on 2007-08-23
> **loswillios said:**
> ```
~$ LANG=C sudo aptitude install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  linux-headers-2.6.22-9-generic
The following NEW packages will be automatically installed:
  linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
The following NEW packages will be installed:
  linux-generic linux-restricted-modules-2.6.22-10-generic linux-restricted-modules-generic
0 packages upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 16.3MB of archives. After unpacking 36.6MB will be used.
Do you want to continue? [Y/n/?]
```

What is it with -generic? I always thought -386 is a little more optimized
Say "Y" to the package manager and reboot.

-386 is no "more optimised" than -generic

---

### Post by loswillios on 2007-08-23
Oki, thanks for your help. I have installed the above packages, however, it doesn't work yet. Should I remove all the stuff with -386?

```
~$ dpkg -l|grep 386
ii  linux-headers-2.6.22-9-386                 2.6.22-9.25                    Linux kernel headers for version 2.6.22 on i
ii  linux-image-2.6.22-10-386                  2.6.22-10.30                   Linux kernel image for version 2.6.22 on i38
ii  linux-image-2.6.22-9-386                   2.6.22-9.25                    Linux kernel image for version 2.6.22 on i38
ii  linux-restricted-modules-2.6.22-10-386     2.6.22.3-10.1                  Non-free Linux 2.6.22 modules on 386
ii  linux-restricted-modules-2.6.22-9-386      2.6.22.2-9.8                   Non-free Linux 2.6.22 modules on 386
ii  linux-ubuntu-modules-2.6.22-9-386          2.6.22-9.22                    Ubuntu supplied Linux modules for version 2.
```

```
~$ dpkg -l|grep generic
ii  linux-generic                              2.6.22.10.11                   Complete Generic Linux kernel
ii  linux-headers-2.6.20-15-generic            2.6.20-15.27                   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.20-16-generic            2.6.20-16.29                   Linux kernel headers for version 2.6.20 on x
ii  linux-headers-2.6.22-10-generic            2.6.22-10.30                   Linux kernel headers for version 2.6.22 on x
ii  linux-headers-generic                      2.6.22.10.11                   Generic Linux kernel headers
ii  linux-image-2.6.20-15-generic              2.6.20-15.27                   Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.20-16-generic              2.6.20-16.29                   Linux kernel image for version 2.6.20 on x86
ii  linux-image-2.6.22-10-generic              2.6.22-10.30                   Linux kernel image for version 2.6.22 on x86
ii  linux-image-2.6.22-9-generic               2.6.22-9.25                    Linux kernel image for version 2.6.22 on x86
ii  linux-image-generic                        2.6.22.10.11                   Generic Linux kernel image
rc  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20                 Non-free Linux 2.6.20 modules on x86/x86_64
rc  linux-restricted-modules-2.6.20-16-generic 2.6.20.5-16.29                 Non-free Linux 2.6.20 modules on x86/x86_64
ii  linux-restricted-modules-2.6.22-10-generic 2.6.22.3-10.1                  Non-free Linux 2.6.22 modules on x86/x86_64
rc  linux-restricted-modules-2.6.22-9-generic  2.6.22.2-9.7                   Non-free Linux 2.6.22 modules on x86/x86_64
ii  linux-restricted-modules-generic           2.6.22.10.11                   Restricted Linux modules for generic kernels
ii  linux-ubuntu-modules-2.6.22-10-generic     2.6.22-10.23                   Ubuntu supplied Linux modules for version 2.
ii  linux-ubuntu-modules-2.6.22-9-generic      2.6.22-9.22                    Ubuntu supplied Linux modules for version 2.
```

because menu.lst from grub still points to 2.6.22-10-386, which is booted now.

---

### Post by tseliot on 2007-08-23
You can either post your menu.lst or you can simply keep using the -386 and type:
```
sudo apt-get install linux-386
```

and post the output.

this will install the restricted modules you need for your 386 kernel

---

### Post by loswillios on 2007-08-23
great, I have it working now! Thanks.

well, kind of ;) But I think this is one is for the nvidia guys?

```
[   44.372000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000104
[   44.372000]  printing eip:
[   44.372000] dd1209a6
[   44.372000] *pde = 00000000
[   44.372000] Oops: 0000 [#1]
[   44.372000] SMP
[   44.372000] Modules linked in: cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave button ac sbs video container dock battery ipv6 lp fuse snd_via82xx gameport snd_ac97_codec ac97_bus snd_mpu401_uart snd_pcm_oss usbhid snd_pcm hid snd_page_alloc snd_mixer_oss snd_seq_dummy nvidia(P) snd_seq_oss usblp pcspkr serio_raw snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse snd_timer snd_seq_device snd soundcore shpchp via_agp i2c_viapro via686a i2c_isa i2c_core pci_hotplug parport_pc parport agpgart af_packet evdev ext3 jbd mbcache ide_cd cdrom ide_disk 8139cp 8139too mii uhci_hcd usbcore via82cxxx ide_core ata_generic libata scsi_mod thermal processor fan apparmor commoncap aamatch_pcre
[   44.372000] CPU:    0
[   44.372000] EIP:    0060:[<dd1209a6>]    Tainted: P       VLI
[   44.372000] EFLAGS: 00013283   (2.6.22-10-generic #1)
[   44.372000] EIP is at _nv007730rm+0x126/0x198 [nvidia]
[   44.372000] eax: d4c1e000   ebx: d3c74000   ecx: 00000011   edx: d4c1f800
[   44.372000] esi: 00000000   edi: 00000000   ebp: d5227a50   esp: d5227a08
[   44.372000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[   44.372000] Process Xorg (pid: 4400, ti=d5226000 task=db681480 task.ti=d5226000)
[   44.372000] Stack: d4c1e000 d4c1f800 00000000 00000000 00000000 0000016b 00000001 d3c741f8
[   44.372000]        d3c74000 d3c74000 d5227b80 dd0f76b7 d4c1e000 d4c1f800 d3c74000 00000000
[   44.372000]        d4c1f800 00000000 d5227ab0 dd0f77b9 d4c1e000 d3c74000 00000000 dd0f7403
[   44.372000] Call Trace:
[   44.372000]  [<dd0f76b7>] _nv000748rm+0x283/0x52c [nvidia]
[   44.372000]  [<dd0f77b9>] _nv000748rm+0x385/0x52c [nvidia]
[   44.372000]  [<dd0f7403>] _nv000576rm+0x20b/0x23c [nvidia]
[   44.372000]  [<dd0f7a5c>] _nv000614rm+0xfc/0x12c [nvidia]
[   44.372000]  [<dd0f7a7f>] _nv000614rm+0x11f/0x12c [nvidia]
[   44.372000]  [<dd0f7c42>] _nv000629rm+0xe6/0x174 [nvidia]
[   44.372000]  [<c0131300>] do_sysinfo+0xe0/0x130
[   44.372000]  [<c0124b04>] scheduler_tick+0x194/0x1c0
[   44.372000]  [<c0140d56>] getnstimeofday+0x36/0xd0
[   44.372000]  [<c010a446>] pit_next_event+0x36/0x50
[   44.372000]  [<c0143028>] clockevents_program_event+0x88/0x100
[   44.372000]  [<c0144274>] tick_program_event+0x44/0x70
[   44.372000]  [<c013f8e7>] hrtimer_interrupt+0x187/0x1d0
[   44.372000]  [<dd10b55f>] _nv004458rm+0xdf/0xe8 [nvidia]
[   44.372000]  [<dd10aa9b>] _nv000726rm+0x4b/0x140 [nvidia]
[   44.372000]  [<dd10aaa8>] _nv000726rm+0x58/0x140 [nvidia]
[   44.372000]  [<dd031d3d>] _nv002001rm+0x219/0x254 [nvidia]
[   44.372000]  [<dd03279b>] _nv002008rm+0x12f/0x360 [nvidia]
[   44.372000]  [<dd0327e1>] _nv002008rm+0x175/0x360 [nvidia]
[   44.372000]  [<dd037165>] rm_init_adapter+0x59/0x84 [nvidia]
[   44.372000]  [<dd2b3ee2>] nv_kern_open+0x20a/0x2ac [nvidia]
[   44.372000]  [<dd2b3cd8>] nv_kern_open+0x0/0x2ac [nvidia]
[   44.372000]  [<c0183216>] chrdev_open+0xa6/0x190
[   44.372000]  [<c0183170>] chrdev_open+0x0/0x190
[   44.372000]  [<c017eaa8>] __dentry_open+0xb8/0x1c0
[   44.372000]  [<c017ec65>] nameidata_to_filp+0x35/0x40
[   44.372000]  [<c017ecc0>] do_filp_open+0x50/0x60
[   44.372000]  [<c017f135>] sys_chown+0x45/0x60
[   44.372000]  [<c017ed1e>] do_sys_open+0x4e/0xf0
[   44.372000]  [<c017edfc>] sys_open+0x1c/0x20
[   44.372000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[   44.372000]  =======================
[   44.372000] Code: 26 00 00 00 00 31 ff 83 c4 fc 6a 01 68 6b 01 00 00 53 8b 43 74 ff d0 83 c4 10 83 c4 f4 8b 45 f4 50 57 56 8b 55 f8 52 8b 45 08 50 <8b> 86 04 01 00 00 ff d0 83 c4 20 83 c4 f4 56 8b 86 b0 00 00 00
[   44.372000] EIP: [<dd1209a6>] _nv007730rm+0x126/0x198 [nvidia] SS:ESP 0068:d5227a08
```

---

### Post by tseliot on 2007-08-23
> **loswillios said:**
> great, I have it working now! Thanks.

well, kind of ;) But I think this is one is for the nvidia guys?
if it is a problem you might want to ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by loswillios on 2007-08-23
thanks!

here's my post: [http://www.nvnews.net/vbulletin/showthread.php?p=1352377#post1352377](http://www.nvnews.net/vbulletin/showthread.php?p=1352377#post1352377)

---

### Post by kamstrup on 2007-08-25
I have the same problem (lacking nvidia.ko), but installing "linux-386" does not bring in the module. And I can confirm that "dpkg -L linux-restricted-modules-2.6.22-10-386 | grep nvidia" does not list it.

I don't know in what package that driver is supposed to be bundled. If I run the 2.6.22-8-generic kernel then everything is fine. All my problems are in the -10 series.

@loswillios: What exactly did you do to make this work?

---

### Post by loswillios on 2007-08-25
I moved to -generic completely.

---

### Post by kamstrup on 2007-08-26
I removed al *-386 related stuff and installed linux-generic (somehow it was not installed - I have not removed it).

After that I had nvidia.ko, but after the last reboot it was gone again. What is happening!? Sorry, but this just completely baffles me.

---

