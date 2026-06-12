---
title: "nvidia driver problem after upgrade to Oneiric"
date: 2011-10-14
forum: Multimedia Software
---

### Post by samiller25 on 2011-10-14
I just upgraded my Mythbuntu box from Maverick to Oneiric, and now the display manager fails.  I'm stuck at the purple Mythbuntu screen.  However, I can log in through ssh, and other services such as mythbackend are running ok.

I have a GeForce 9300 IGP on the motherboard, and I use the nvidia proprietary driver (nvidia-current 280.13-0ubuntu6).  There are two reasons I suspect the nvidia driver is at fault.  The first is that when I replace /etc/X11/xorg.conf with xorg.conf.failsafe (which uses the vesa driver) and remove the nvidia kernel module, the GUI starts as usual.  The second is that /var/log/syslog reports the following error, with nvidia at the top of the call stack:

```
Oct 14 13:48:06 htpc kernel: [   19.073203] Pid: 1169, comm: Xorg Tainted: P         C  3.0.0-12-generic #20-Ubuntu NVIDIA MCP7A/MCP7A
Oct 14 13:48:06 htpc kernel: [   19.073207] EIP: 0060:[<f9c6bcf2>] EFLAGS: 00013246 CPU: 0
Oct 14 13:48:06 htpc kernel: [   19.073363] EIP is at _nv008508rm+0xe6/0x106 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.073365] EAX: 00000000 EBX: 00000000 ECX: 00000010 EDX: 00000000
Oct 14 13:48:06 htpc kernel: [   19.073366] ESI: 00000000 EDI: f1c12000 EBP: f73c1e28 ESP: f3fe5b78
Oct 14 13:48:06 htpc kernel: [   19.073368]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 14 13:48:06 htpc kernel: [   19.073370] Process Xorg (pid: 1169, ti=f3fe4000 task=f6c74c80 task.ti=f3fe4000)
Oct 14 13:48:06 htpc kernel: [   19.073372] Stack:
Oct 14 13:48:06 htpc kernel: [   19.073373]  f1d2b000 00000000 00000000 f1c86000 f1d2b000 f9c6be59 f1d2b000 f1c86000
Oct 14 13:48:06 htpc kernel: [   19.073378]  00000000 00000000 f1c86000 00000000 f9c445bc f1d2b000 f1c86000 f1c86000
Oct 14 13:48:06 htpc kernel: [   19.073382]  f1c12000 f73c1e6c f9c61075 f1d2b000 f1c86000 f73c1e6c f73c1e70 00040000
Oct 14 13:48:06 htpc kernel: [   19.073387] Call Trace:

Oct 14 13:48:06 htpc kernel: [   19.073545]  [<f9c6be59>] ? _nv008321rm+0xd4/0xe0 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.073697]  [<f9c445bc>] ? _nv022711rm+0x1a8/0x2ff [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.073854]  [<f9c61075>] ? _nv022709rm+0xdb/0xfb [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.073986]  [<f9b3d967>] ? _nv007694rm+0xbe/0xe7 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074118]  [<f9b3daeb>] ? _nv007693rm+0x15b/0x197 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074254]  [<f9b66e6f>] ? _nv008025rm+0x261/0xe65 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074388]  [<f9b51046>] ? _nv007691rm+0x3f/0x45 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074522]  [<f9b50655>] ? _nv019319rm+0x9b5/0xd0d [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074665]  [<f9bdffd0>] ? _nv009945rm+0x1ed/0x306 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074823]  [<f9c7ef6b>] ? _nv009942rm+0x22/0x43 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.074999]  [<f9dcb90e>] ? _nv015078rm+0x1fa/0x3c9 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075174]  [<f9dca6c9>] ? _nv015371rm+0xc3/0x126 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075281]  [<f9a2082c>] ? _nv015551rm+0xb/0xf [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075433]  [<f9fca3dc>] ? _nv002299rm+0x15d/0x24b [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075580]  [<f9fcb1b2>] ? _nv002293rm+0x3f6/0x5dc [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075727]  [<f9fd1325>] ? rm_init_adapter+0x91/0x1a4 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075875]  [<f9ff15e0>] ? nv_kern_open+0x3d0/0x740 [nvidia]
Oct 14 13:48:06 htpc kernel: [   19.075881]  [<c112bd55>] ? chrdev_open+0xb5/0x1e0
Oct 14 13:48:06 htpc kernel: [   19.075885]  [<c11262a1>] ? __dentry_open+0x121/0x2d0
Oct 14 13:48:06 htpc kernel: [   19.075887]  [<c112bca0>] ? cdev_put+0x20/0x20
Oct 14 13:48:06 htpc kernel: [   19.075889]  [<c11278f6>] ? nameidata_to_filp+0x86/0x90
Oct 14 13:48:06 htpc kernel: [   19.075893]  [<c11346e7>] ? do_last+0x327/0x640
Oct 14 13:48:06 htpc kernel: [   19.075895]  [<c113595d>] ? path_openat+0x9d/0x350
Oct 14 13:48:06 htpc kernel: [   19.075898]  [<c1134de3>] ? path_lookupat+0x63/0x650
Oct 14 13:48:06 htpc kernel: [   19.075901]  [<c1140524>] ? setattr_copy+0xa4/0x120
Oct 14 13:48:06 htpc kernel: [   19.075903]  [<c1135c41>] ? do_filp_open+0x31/0x80
Oct 14 13:48:06 htpc kernel: [   19.075906]  [<c1141303>] ? alloc_fd+0xa3/0xe0
Oct 14 13:48:06 htpc kernel: [   19.075909]  [<c11318a5>] ? getname_flags+0xf5/0x130
Oct 14 13:48:06 htpc kernel: [   19.075911]  [<c11279e1>] ? do_sys_open+0xe1/0x1f0
Oct 14 13:48:06 htpc kernel: [   19.075914]  [<c1141929>] ? vfsmount_lock_local_unlock+0x19/0x20
Oct 14 13:48:06 htpc kernel: [   19.075916]  [<c1127b1e>] ? sys_open+0x2e/0x40
Oct 14 13:48:06 htpc kernel: [   19.075920]  [<c152c8e4>] ? syscall_call+0x7/0xb
Oct 14 13:48:06 htpc kernel: [   19.075922] Code: 55 00 ff 92 08 01 00 00 83 c4 04 85 c0 75 02 89 de 68 90 2c 00 00 57 ff 57 78 83 c4 08 ba 00 00 00 00 85 c0 75 10 56 ff 74 24 14 <ff> 96 5c 06 00 00 83 c4 08 89 c2 85 d2 0f 94 c0 0f b6 c0 89 86
Oct 14 13:48:06 htpc kernel: [   19.075950] EIP: [<f9c6bcf2>] _nv008508rm+0xe6/0x106 [nvidia] SS:ESP 0068:f3fe5b78
Oct 14 13:48:06 htpc kernel: [   19.076001] CR2: 000000000000065c
Oct 14 13:48:06 htpc kernel: [   19.076123] ---[ end trace e6d80b590ec937e5 ]---
```

I've tried uninstalling and reinstalling nvidia-current.  I've tried regenerating xorg.conf using nvidia-xconfig.  I've tried booting an earlier kernel (2.6.38).  Nothing has helped so far.

Before I go through the drastic step of installing NVIDIA's latest driver (285.05.09) -- a move strongly opposed at ubuntu.com's [NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") wiki -- I was hoping to get some advice from this forum regarding other steps I can take to diagnose or fix the problem.  Or, if anyone knows that this problem is fixed by the newer driver, please let me know.

I can supply other logs or config files if requested, but since I don't have a GUI on the mythbuntu box it takes a bit of effort so I'm not going to try to guess what people want to see.

Thanks to anyone who can help!

---

### Post by samiller25 on 2011-10-14
I figured I could at least upload the Xorg log.  I don't see anything interesting in there, though.  See attached.

---

### Post by jaezcurra on 2011-10-15
Bump

---

### Post by samiller25 on 2011-10-15
I'm gonna do it!  Somebody stop me before I install NVIDIA's driver!  I'm just that crazy!

---

### Post by emunson on 2011-10-15
I am having a similar problem without the stack trace in syslog, however, I do have a bunch of these:

```
Oct 15 19:58:33 grover kernel: [   23.779608] unity-greeter[1632]: segfault at 0 ip 00381cbb sp bfe78ee0 error 4 in libgio-2.0.so.0.3000.0[2e9000+142000]

```

Any ideas or is this a wait for nVidia to get their act together?

---

### Post by paulisdead on 2011-10-15
I was getting a bunch of segfaults from the nvidia drivers with gnome-shell causing it to run in failsafe, with a clean install of 11.10.  I'd get a segfault from glxinfo and glxgears, as well.  The opengl/glx info tab in nvidia-settings would cause a segfault too.  Weird thing is, it worked initially, but after I configured my second monitor, wrote out an xorg.conf with nvidia-settings, and set it to auto login with gnome, I started getting the segfaults.  I even tried not using auto login.  After that unity would run, but I'd still get segfaults from from doing the same things.  I did have full gnome-shell running, but for some reason after reboot, I keep getting segfaults that cause it to use failsafe.

I tried the updated drivers option restricted drivers had, but that didn't help.  I also installed the latest from a ppa, I forget the name of the ppa right now, though.

The weird thing is, I decided to give kubuntu a spin, and it's not having any of the issues with the nvidia drivers.  No segfaults at all.  I'm not particularly thrilled with kde, but I'm not really thrilled by any of the other options either.  I guess I'm leaning towards gnome-shell, but ubuntu seems to hate my graphics card.  BTW, it's a gigabyte 460GTX.  I think this is more of an ubuntu issue rather than an issue with the drivers.  I might give it a go again, there certain things about kde that are driving me a bit nuts.

*edit* So I reinstalled ubuntu with gnome shell, and it's working fine now, go figure.

---

### Post by jaezcurra on 2011-10-16
Bump

---

### Post by paulisdead on 2011-10-16
Give this a try, I think it might've been related to the problem I had, it just hasn't happened again since I reinstalled.

[http://ubuntuforums.org/showthread.php?t=1722306&highlight=libgl.so](http://ubuntuforums.org/showthread.php?t=1722306&highlight=libgl.so)

---

### Post by emunson on 2011-10-16
This isn't a failure of 3D (at least for me) it is a failure of XWindows completely, I get no gui and no error messages.

---

### Post by samiller25 on 2011-10-17
> **emunson said:**
> This isn't a failure of 3D (at least for me) it is a failure of XWindows completely, I get no gui and no error messages.

**Exactly**.  There are lots of complaints out there about Unity3D or glxgears or whatever not working, but I can't get that far.  No X11 at all with nvidia installed.

By the way, I just purged nvidia-common and installed the driver from nvidia's website, and ... no difference (surprise!).  I still get the Xorg failure reported in syslog, and it still fails in nvidia code.

The only option I can think of at this point is a fresh install, and I'm not convinced I have the skills to do that while preserving my MythTV setup.  Anyone have any other suggestions?

---

### Post by emunson on 2011-10-18
A fresh install on Oneiric did not help.  I have opened a bug here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/877628](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/877628)
Please click the "This affects me" link.

---

### Post by samiller25 on 2011-10-18
> **emunson said:**
> A fresh install on Oneiric did not help.  I have opened a bug here: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/877628](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/877628)
Please click the "This affects me" link.

Just did.  Your bug report is a little confusing though: it mentions your upgrade from natty, but the UpgradeStatus says it's a fresh install and you just mentioned the fresh install didn't help.  So is the upgrade relevant?

---

### Post by jaezcurra on 2011-10-18
Posted at the Launchpad too.

---

### Post by emunson on 2011-10-19
Not any more, I will post that.

---

### Post by Gromit83 on 2011-10-22
try running

nvidia-xconfig --no-composite

---

### Post by samiller25 on 2011-10-22
> **Gromit83 said:**
> try running

nvidia-xconfig --no-composite

Why?

---

### Post by Xor001 on 2011-10-23
I have the same problem.  When I boot with nvidia-current or nvidia-current-updates on Ubuntu 11.10, the screen freeze and all I see is the Ubuntu logo with the dots under it and nothing moves, cannot change TTY, NumLock don't turn on/off anymore when pressed.  If I SSH to the box, everything still works.  I cannot kill X from the SSH session.

I did a lot of tests, including replacing LightDM by GDM, but nVidia drivers never boot.  I can use the "nouveau" driver, but off course, only with Unity2D.  The nVidia driver seems to crash, I tried also the latest version from the nVidia website, no success.  I was working great in Ubuntu 11.04.

Here what I have in "dmesg" after I try to start X:
```

[   78.595996] ------------[ cut here ]------------
[   78.596004] WARNING: at /build/buildd/linux-3.0.0/arch/x86/mm/ioremap.c:102 __ioremap_caller+0x322/0x3a0()
[   78.596006] Hardware name: System Product Name
[   78.596008] Modules linked in: nvidia(P) nfs lockd fscache auth_rpcgss nfs_acl sunrpc bnep rfcomm bluetooth parport_pc dm_crypt ppdev binfmt_misc nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_hdmi joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm eeepc_wmi asus_wmi sparse_keymap snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse serio_raw wmi snd mei(C) soundcore lp snd_page_alloc parport usbhid hid ahci libahci video r8169 xhci_hcd [last unloaded: nvidia]
[   78.596038] Pid: 1895, comm: Xorg Tainted: P         C  3.0.0-12-generic #20-Ubuntu
[   78.596040] Call Trace:
[   78.596044]  [<ffffffff8105e83f>] warn_slowpath_common+0x7f/0xc0
[   78.596047]  [<ffffffff8105e89a>] warn_slowpath_null+0x1a/0x20
[   78.596050]  [<ffffffff81039882>] __ioremap_caller+0x322/0x3a0
[   78.596053]  [<ffffffff810329b9>] ? default_spin_lock_flags+0x9/0x10
[   78.596191]  [<ffffffffa152c895>] ? os_map_kernel_space+0x85/0xf0 [nvidia]
[   78.596195]  [<ffffffff814bc7e3>] ? pci_conf1_read+0xc3/0x120
[   78.596198]  [<ffffffff81039934>] ioremap_cache+0x14/0x20
[   78.596316]  [<ffffffffa152c895>] os_map_kernel_space+0x85/0xf0 [nvidia]
[   78.596435]  [<ffffffffa14f7d57>] _nv023390rm+0xfb/0x11b [nvidia]
[   78.596508]  [<ffffffffa0ee71ce>] ? _nv025862rm+0x62/0x11b [nvidia]
[   78.596580]  [<ffffffffa0ee7320>] ? _nv022528rm+0x99/0xcb [nvidia]
[   78.596651]  [<ffffffffa0ee77b6>] ? _nv022591rm+0x58/0x9e [nvidia]
[   78.596722]  [<ffffffffa0ee29f8>] ? _nv022548rm+0xcf/0x301 [nvidia]
[   78.596792]  [<ffffffffa0ee2cd5>] ? _nv022598rm+0xab/0x174 [nvidia]
[   78.596862]  [<ffffffffa0ee2dee>] ? _nv022547rm+0x50/0x5d [nvidia]
[   78.596934]  [<ffffffffa0ee9a5d>] ? _nv022539rm+0x6e/0x78 [nvidia]
[   78.597048]  [<ffffffffa14fe134>] ? _nv019309rm+0x69/0x121 [nvidia]
[   78.597162]  [<ffffffffa14fe0b2>] ? _nv019323rm+0xe8/0x101 [nvidia]
[   78.597246]  [<ffffffffa0f26421>] ? _nv004632rm+0x68/0x1f4 [nvidia]
[   78.597403]  [<ffffffffa12c4387>] ? _nv015073rm+0x176/0x4c3 [nvidia]
[   78.597557]  [<ffffffffa12c2eeb>] ? _nv015366rm+0xe9/0x165 [nvidia]
[   78.597623]  [<ffffffffa0ead748>] ? _nv015546rm+0xd/0x12 [nvidia]
[   78.597739]  [<ffffffffa14fde79>] ? _nv002297rm+0x19d/0x28a [nvidia]
[   78.597853]  [<ffffffffa14feee8>] ? _nv002291rm+0x4a5/0x684 [nvidia]
[   78.597965]  [<ffffffffa1505c84>] ? rm_init_adapter+0x9e/0x1b6 [nvidia]
[   78.598078]  [<ffffffffa1525624>] ? nv_kern_open+0x414/0x7a0 [nvidia]
[   78.598087]  [<ffffffff8116ae30>] ? mount_fs+0x1b0/0x1b0
[   78.598091]  [<ffffffff8116b87a>] ? chrdev_open+0xda/0x230
[   78.598095]  [<ffffffff811653d4>] ? __dentry_open+0x144/0x320
[   78.598098]  [<ffffffff8116b7a0>] ? cdev_put+0x30/0x30
[   78.598102]  [<ffffffff81166b1d>] ? nameidata_to_filp+0xad/0xb0
[   78.598107]  [<ffffffff81175550>] ? do_last+0x3a0/0x700
[   78.598111]  [<ffffffff81176ada>] ? path_openat+0xca/0x3f0
[   78.598116]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
[   78.598120]  [<ffffffff81176e42>] ? do_filp_open+0x42/0xa0
[   78.598124]  [<ffffffff812f4761>] ? strncpy_from_user+0x31/0x40
[   78.598128]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
[   78.598131]  [<ffffffff811841f7>] ? alloc_fd+0xf7/0x150
[   78.598135]  [<ffffffff81166c0d>] ? do_sys_open+0xed/0x220
[   78.598138]  [<ffffffff811867ef>] ? mntput+0x1f/0x30
[   78.598142]  [<ffffffff81166d60>] ? sys_open+0x20/0x30
[   78.598148]  [<ffffffff815f22c2>] ? system_call_fastpath+0x16/0x1b
[   78.598151] ---[ end trace 98c73d4bb7b1de1e ]---
[   78.598527] BUG: unable to handle kernel paging request at ffffc90001c9b000
[   78.598532] IP: [<ffffffffa0ee7628>] _nv027219rm+0xd4/0x20a [nvidia]
[   78.598632] PGD 23e819067 PUD 23e81a067 PMD 232443067 PTE 0
[   78.598637] Oops: 0000 [#1] SMP
[   78.598641] CPU 0
[   78.598643] Modules linked in: nvidia(P) nfs lockd fscache auth_rpcgss nfs_acl sunrpc bnep rfcomm bluetooth parport_pc dm_crypt ppdev binfmt_misc nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_hdmi joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm eeepc_wmi asus_wmi sparse_keymap snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse serio_raw wmi snd mei(C) soundcore lp snd_page_alloc parport usbhid hid ahci libahci video r8169 xhci_hcd [last unloaded: nvidia]
[   78.598680]
[   78.598683] Pid: 1895, comm: Xorg Tainted: P        WC  3.0.0-12-generic #20-Ubuntu System manufacturer System Product Name/P8H67-M LE
[   78.598688] RIP: 0010:[<ffffffffa0ee7628>]  [<ffffffffa0ee7628>] _nv027219rm+0xd4/0x20a [nvidia]
[   78.598785] RSP: 0018:ffff88022de158c8  EFLAGS: 00010202
[   78.598788] RAX: 000000000000003c RBX: 0000000000000000 RCX: 000000000000003c
[   78.598790] RDX: 0000000000000008 RSI: 0000000000000000 RDI: 0000000000000000
[   78.598793] RBP: ffff88022e522f30 R08: 00000000bf479fff R09: ffff880000000000
[   78.598796] R10: 0000000000000001 R11: 0000000000000001 R12: 0000000000000059
[   78.598799] R13: ffffc90001c9aff8 R14: ffff88022f742000 R15: ffff88022f741800
[   78.598802] FS:  00007f7e2e1558a0(0000) GS:ffff88023f400000(0000) knlGS:0000000000000000
[   78.598806] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   78.598808] CR2: ffffc90001c9b000 CR3: 000000022f141000 CR4: 00000000000406f0
[   78.598811] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   78.598814] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   78.598817] Process Xorg (pid: 1895, threadinfo ffff88022de14000, task ffff88022ea9ae40)
[   78.598819] Stack:
[   78.598821]  ffff88022f742000 ffff88022f741800 ffff88022f742000 ffff88022faea000
[   78.598826]  000000000000001b ffffffffa0ee77ec ffff88022d535000 ffff88022d535000
[   78.598831]  ffff88022faea000 ffffffffa0ee29f8 ffff88022d535000 ffff88022faea000
[   78.598836] Call Trace:
[   78.598925]  [<ffffffffa0ee77ec>] ? _nv022591rm+0x8e/0x9e [nvidia]
[   78.598997]  [<ffffffffa0ee29f8>] ? _nv022548rm+0xcf/0x301 [nvidia]
[   78.599067]  [<ffffffffa0ee2cd5>] ? _nv022598rm+0xab/0x174 [nvidia]
[   78.599138]  [<ffffffffa0ee2dee>] ? _nv022547rm+0x50/0x5d [nvidia]
[   78.599209]  [<ffffffffa0ee9a5d>] ? _nv022539rm+0x6e/0x78 [nvidia]
[   78.599324]  [<ffffffffa14fe134>] ? _nv019309rm+0x69/0x121 [nvidia]
[   78.599438]  [<ffffffffa14fe0b2>] ? _nv019323rm+0xe8/0x101 [nvidia]
[   78.599522]  [<ffffffffa0f26421>] ? _nv004632rm+0x68/0x1f4 [nvidia]
[   78.599678]  [<ffffffffa12c4387>] ? _nv015073rm+0x176/0x4c3 [nvidia]
[   78.599833]  [<ffffffffa12c2eeb>] ? _nv015366rm+0xe9/0x165 [nvidia]
[   78.599899]  [<ffffffffa0ead748>] ? _nv015546rm+0xd/0x12 [nvidia]
[   78.600015]  [<ffffffffa14fde79>] ? _nv002297rm+0x19d/0x28a [nvidia]
[   78.600128]  [<ffffffffa14feee8>] ? _nv002291rm+0x4a5/0x684 [nvidia]
[   78.600241]  [<ffffffffa1505c84>] ? rm_init_adapter+0x9e/0x1b6 [nvidia]
[   78.600355]  [<ffffffffa1525624>] ? nv_kern_open+0x414/0x7a0 [nvidia]
[   78.600357]  [<ffffffff8116ae30>] ? mount_fs+0x1b0/0x1b0
[   78.600360]  [<ffffffff8116b87a>] ? chrdev_open+0xda/0x230
[   78.600363]  [<ffffffff811653d4>] ? __dentry_open+0x144/0x320
[   78.600365]  [<ffffffff8116b7a0>] ? cdev_put+0x30/0x30
[   78.600368]  [<ffffffff81166b1d>] ? nameidata_to_filp+0xad/0xb0
[   78.600370]  [<ffffffff81175550>] ? do_last+0x3a0/0x700
[   78.600373]  [<ffffffff81176ada>] ? path_openat+0xca/0x3f0
[   78.600376]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
[   78.600379]  [<ffffffff81176e42>] ? do_filp_open+0x42/0xa0
[   78.600382]  [<ffffffff812f4761>] ? strncpy_from_user+0x31/0x40
[   78.600385]  [<ffffffff815e9efe>] ? _raw_spin_lock+0xe/0x20
[   78.600387]  [<ffffffff811841f7>] ? alloc_fd+0xf7/0x150
[   78.600389]  [<ffffffff81166c0d>] ? do_sys_open+0xed/0x220
[   78.600392]  [<ffffffff811867ef>] ? mntput+0x1f/0x30
[   78.600394]  [<ffffffff81166d60>] ? sys_open+0x20/0x30
[   78.600397]  [<ffffffff815f22c2>] ? system_call_fastpath+0x16/0x1b
[   78.600399] Code: ff 97 88 02 00 00 49 89 c5 48 85 c0 75 0c c7 45 08 32 00 00 00 e9 24 01 00 00 ba 00 00 00 00 8b 45 0c 48 89 c1 48 83 f8 00 76 0d
[   78.600415]  02 64 15 00 48 ff c2 48 39 d1 77 f3 45 84 e4 74 0c c7 45 08
[   78.600422] RIP  [<ffffffffa0ee7628>] _nv027219rm+0xd4/0x20a [nvidia]
[   78.600495]  RSP <ffff88022de158c8>
[   78.600496] CR2: ffffc90001c9b000
[   78.600498] ---[ end trace 98c73d4bb7b1de1f ]---

```

Anyone had progress ?

---

### Post by emunson on 2011-10-26
I reinstalled natty as this is likely to be a really low priority bug.

---

### Post by samiller25 on 2011-10-26
> **emunson said:**
> I reinstalled natty as this is likely to be a really low priority bug.

Super.

BTW, what's the best way to revert an upgrade?  Or is a fresh install the only realistic option?

---

### Post by emunson on 2011-10-26
AFAIK a fresh install is really the only way.  You might be able to make a downgrade work if you apt-fu is strong.  Mine isn't so it was reinstall for me.

---

### Post by jaezcurra on 2011-11-02
Bump

---

### Post by emunson on 2012-02-08
Do we still have no solution here?

---

### Post by samiller25 on 2012-02-08
> **emunson said:**
> Do we still have no solution here?
Nope.  I did a fresh install of Oneiric months ago, and it worked *as long as I did not touch the nvidia driver.*  As soon as I tried to upgrade the version or install the proprietary driver, something would go wrong.

---

### Post by emunson on 2012-02-08
That is dissapointing, so now I won't be able to update to 12.04, it will have to be a fresh install and pray that it works.  I may hang around on Natty a while still

---

### Post by Cavsfan on 2012-02-08
I am on Lucid 10.04 LTS but I installed the latest Nvidia driver 290.10 and have a way 
(from someone on here) to install the driver into a new kernel when one gets installed.

Let me find the links. They have never let me down.

---

### Post by Cavsfan on 2012-02-08
[[COLOR=blue]_Get the latest nVidia driver here._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

[[COLOR=blue]_Instructions on how to install nVida driver._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

You will just need to modify the file name of course.
You will want to print steps 4 through 8 because you will need them when you reboot after installation.
Then once you enter Step 8, you will be back in Ubuntu like you just logged in.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

This was created by **sdennie** (in this forum) and has worked through several versions of Ubuntu.
It just creates a script that installs the driver into the new kernel. If you use the terminal to get your 
updates, you will see a message Building NVIDIA driver for kernel and after that it will say "**success**" if it worked correctly.

Try this before you do a clean install.

---

### Post by emunson on 2012-02-09
FWIW, I was seeing the unity-greeter segfault shown here: [http://ubuntuforums.org/showthread.php?t=1860240](http://ubuntuforums.org/showthread.php?t=1860240)
This fixed the issue for me, though the unity greeter was handling my autologin so I need to track that down in lightdm.

---

### Post by Kalibur on 2012-03-04
I have had similar problems with Nvidia drivers in the ubuntu repos and the proprietary version 2.90 and 2.95.  The good news is I won the battle and got my Mythtv Ubuntu 11.10 64bit box working again with unity 3d.

You may need to ssh into you box and even boot in runlevel one to get some of this working or at least to fix any problems the method may introduce.  So only attempt this if you know how to dig yourself out of a deep hole or if your have nothing important to keep safe.

What I did is purge gcc-4.6 and installed gcc-4.5 in its place.
Also libc6.  

step one :

$ sudo apt-get purge gcc-4.6 libc6* -f

It looks a little messy but it allowed me to install the Nvidia-current drivers.  After that I did the usual nvidia-xconfig nvidia-settings to make sure all works well.

Forgot to mention you need to install gcc-4.5 instead

apt-get install gcc-4.5 -f and if nvidia installer asks you for anything else install it the version it suggests just keep off libc6 until you install nvidia drivers successfully then you can upgrade everything.

Then step two

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

If it breaks go back to step one.

---

