---
title: "cifs - error during copy"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by johnsdoeuf on 2012-08-05
hello,

i have a nas "icybox" nas901 and i use cifs for connect to share file. 

the command line to mount is :
```
sudo mount -t cifs -o iocharset=utf8,nounix //192.168.1.99/public /media/partage

```then i see my shared files 

but if i read  a file, the operation stop.
dmesg give that:
> [  308.716646] BUG: unable to handle kernel paging request at f77feda2
[  308.716655] IP: [<f8fd6713>] CIFSSMBQAllEAs+0x2a3/0x440 [cifs]
[  308.716669] *pde = 01bfb067 *pte = 00000000 
[  308.716674] Oops: 0000 [#1] SMP 
[  308.716679] Modules linked in: des_generic md4 nls_utf8 cifs bnep rfcomm bluetooth parport_pc ppdev binfmt_misc dm_crypt snd_hda_codec_via snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore mac_hid snd_page_alloc psmouse serio_raw lp parport jfs btrfs zlib_deflate libcrc32c vesafb firewire_ohci radeon firewire_core crc_itu_t pata_via usbhid hid r8169 ttm drm_kms_helper drm i2c_algo_bit
[  308.716732] 
[  308.716736] Pid: 2159, comm: pool Not tainted 3.2.0-27-generic #43-Ubuntu To Be Filled By O.E.M. To Be Filled By O.E.M./P5B-DE
[  308.716744] EIP: 0060:[<f8fd6713>] EFLAGS: 00010202 CPU: 2
[  308.716752] EIP is at CIFSSMBQAllEAs+0x2a3/0x440 [cifs]
[  308.716756] EAX: f77feda0 EBX: 000000f5 ECX: 00000000 EDX: 346c36bd
[  308.716759] ESI: 0000f873 EDI: 346c36b9 EBP: f711bf24 ESP: f711bed4
[  308.716762]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  308.716766] Process pool (pid: 2159, ti=f711a000 task=efc74bc0 task.ti=f711a000)
[  308.716768] Stack:
[  308.716770]  ef2a8000 f711bf14 00000000 0001fe01 ef2e6fc0 f20bc300 02473075 0000f77e
[  308.716781]  f77ef52c 00000000 346c36bd 00001054 f711bf10 f711bf0c ef2a8000 ef2a8000
[  308.716791]  0000004f ef2e6fc0 f0618600 fffffff4 f711bf60 f8feee71 00000000 00000000
[  308.716801] Call Trace:
[  308.716813]  [<f8feee71>] cifs_listxattr+0xc1/0x160 [cifs]
[  308.716825]  [<f8feedb0>] ? cifs_getxattr+0x410/0x410 [cifs]
[  308.716832]  [<c1151aca>] vfs_listxattr+0x3a/0x70
[  308.716837]  [<c1151b4a>] listxattr+0x4a/0xb0
[  308.716842]  [<c11523ca>] sys_llistxattr+0x3a/0x50
[  308.716848]  [<c1574104>] syscall_call+0x7/0xb
[  308.716853]  [<c157007b>] ? iommu_attach_domain+0x5f/0x8c
[  308.716858]  [<c1570000>] ? verify_pmtmr_rate+0x79/0x95
[  308.716860] Code: c0 89 d7 89 5d c8 89 75 c4 83 c0 04 eb 14 66 90 8b 55 d0 8d 44 32 01 8b 55 d8 85 d2 0f 84 06 01 00 00 83 ef 04 0f 88 cd 00 00 00 <0f> b7 48 02 0f b6 58 01 89 ce 01 de 89 f2 f7 d2 01 fa 85 d2 89 
[  308.716922] EIP: [<f8fd6713>] CIFSSMBQAllEAs+0x2a3/0x440 [cifs] SS:ESP 0068:f711bed4
[  308.716934] CR2: 00000000f77feda2
[  308.716938] ---[ end trace 63a9c8ecc007d824 ]---the same command line works  fine with jaunty but not with precise 12.04

if i don't use nounix parameter, mount don't works
i precise that, on the same computer, with windows XP  i acceed correctly to my nas.

thanks

---

### Post by johnsdoeuf on 2012-08-06
when i mount directory with "nautilus-file -connect to server - ...", the copy works fine. but there are some inconvénients.

i think that there is a solution because it works with "connect to server"

What difference between mount.cifs and "connect to server"

Thanks

---

### Post by johnsdoeuf on 2012-08-07
hello, 

my english is quite bad, so have you understand my problem.

thanks

---

### Post by johnsdoeuf on 2012-08-08
My ubuntu 12.04 was an update from a 10.11 and somethink is probably broken. 

With à new instal of ubuntu 12.04 64, there is no problem with cifs and my nas. 

good think

bye

---

### Post by linuxgeoff on 2013-06-09
I have very similar problem.  .Terminal crash during copy from CIFS drive mounted in fstab.  Worked fine before 12.04.  There seem to be some relevant bug reports on launchpad, but they are unassigned or even unconfirmed.  Seems likea pretty serious problem.:(

Anyone know a work around, other than a clean install of an older version?

---

