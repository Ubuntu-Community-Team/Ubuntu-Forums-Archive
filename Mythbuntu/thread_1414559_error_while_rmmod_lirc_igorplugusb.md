---
title: "error while rmmod lirc_igorplugusb"
date: 2010-02-23
forum: Mythbuntu
---

### Post by ice0rl on 2010-02-23
Hi, 

I'm trying to get my pc ready to use the suspend feature. As suspend failes with the infared receiver pluged in, I tried to unload the following modules: 

lirc_igorplugusb
lirc_dev

after unloading the lirc_igorplugusb i tried to unload lirc_dev  but it fails:

> ice@sonnendeck1:~$ sudo rmmod lirc_igorplugusb
Killed
ice@sonnendeck1:~$ rmmod lirc_dev
ERROR: Module lirc_dev is in use by lirc_igorplugusb


I checked the syslog and found an kernel error which is caused by unloading  lirc_igorplugusb.

```
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186372] usbcore: deregistering interface d                                                                                            river lirc_igorplugusb
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186425] lirc_igorplugusb[3]: usb remote di                                                                                            sconnected
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186608] BUG: unable to handle kernel NULL                                                                                             pointer dereference at 0000000000000028
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186618] IP: [<ffffffffa02360a8>] usb_remot                                                                                            e_disconnect+0x58/0xb0 [lirc_igorplugusb]
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186636] PGD 6e033067 PUD 6dcd7067 PMD 0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186644] Oops: 0000 [#1] SMP
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186650] last sysfs file: /sys/module/lirc_                                                                                            igorplugusb/initstate
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186657] CPU 1
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186661] Modules linked in: binfmt_misc ppd                                                                                            ev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_                                                                                            oss lirc_igorplugusb(-) lirc_dev snd_pcm iptable_filter ip_tables x_tables snd_seq_du                                                                                            mmy snd_seq_oss psmouse snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer                                                                                             snd_seq_device serio_raw snd soundcore snd_page_alloc amd64_edac_mod edac_core k8tem                                                                                            p w83627ehf hwmon_vid i2c_nforce2 lp parport usbhid radeon ttm drm i2c_algo_bit force                                                                                            deth
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186725] Pid: 2626, comm: rmmod Not tainted                                                                                             2.6.31-19-generic #56-Ubuntu MS-7250
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186731] RIP: 0010:[<ffffffffa02360a8>]  [<                                                                                            ffffffffa02360a8>] usb_remote_disconnect+0x58/0xb0 [lirc_igorplugusb]
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186744] RSP: 0018:ffff88006c4a5d78  EFLAGS                                                                                            : 00010296
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186749] RAX: ffff880078737300 RBX: ffff880                                                                                            07a51c840 RCX: ffff880037996670
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186754] RDX: 0000000000000000 RSI: ffffea0                                                                                            000c298d0 RDI: 0000000000000000
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186759] RBP: ffff88006c4a5d88 R08: 0000000                                                                                            000000000 R09: 0000000000000000
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186764] R10: ff694ea05c437407 R11: ffff880                                                                                            06a8288f4 R12: ffff8800378ea090
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186769] R13: ffff8800378ea000 R14: fffffff                                                                                            fa02374c8 R15: 0000000000000000
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186775] FS:  00007f4017eaa6f0(0000) GS:fff                                                                                            f880001a14000(0000) knlGS:0000000000000000
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186781] CS:  0010 DS: 0000 ES: 0000 CR0: 0                                                                                            00000008005003b
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186785] CR2: 0000000000000028 CR3: 0000000                                                                                            06e08f000 CR4: 00000000000006e0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186791] DR0: 0000000000000000 DR1: 0000000                                                                                            000000000 DR2: 0000000000000000
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186796] DR3: 0000000000000000 DR6: 0000000                                                                                            0ffff0ff0 DR7: 0000000000000400
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186802] Process rmmod (pid: 2626, threadin                                                                                            fo ffff88006c4a4000, task ffff88006d4816b0)
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186806] Stack:
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186810]  ffff880037951030 ffff880037951000                                                                                             ffff88006c4a5dd8 ffffffff813a31ac
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186818] <0> ffffffffa02374c8 ffffffffa0237                                                                                            460 ffffffffa02374c8 ffff880037951030
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186827] <0> ffffffffa02374c8 ffff880037951                                                                                            090 ffffffffa02374b8 0000000000000001
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186837] Call Trace:
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186854]  [<ffffffff813a31ac>] usb_unbind_i                                                                                            nterface+0x11c/0x160
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186866]  [<ffffffff813210d3>] __device_rel                                                                                            ease_driver+0x53/0xb0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186874]  [<ffffffff813211f8>] driver_detac                                                                                            h+0xc8/0xd0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186885]  [<ffffffff81320215>] bus_remove_d                                                                                            river+0x95/0xc0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186892]  [<ffffffff813217ca>] driver_unreg                                                                                            ister+0x5a/0x90
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186900]  [<ffffffff813a2747>] usb_deregist                                                                                            er+0xb7/0xd0
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186909]  [<ffffffffa0236794>] usb_remote_e                                                                                            xit+0x10/0x12 [lirc_igorplugusb]
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186920]  [<ffffffff8108f2a8>] sys_delete_m                                                                                            odule+0x1a8/0x280
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186931]  [<ffffffff8107cdb9>] ? up_read+0x                                                                                            9/0x10
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186943]  [<ffffffff81012002>] system_call_                                                                                            fastpath+0x16/0x1b
Feb 23 23:32:23 sonnendeck1 kernel: [  230.186947] Code: 8b 64 24 08 c9 c3 8b 73 10 4                                                                                            8 c7 c7 48 68 23 a0 31 c0 e8 ed 12 2f e1 48 8b 43 40 8b 78 28 e8 e0 73 ff ff 48 8b 43                                                                                             40 48 8b 78 60 <48> 8b 47 28 48 85 c0 74 10 48 89 c7 e8 f7 2d e4 e0 48 8b 43 40
Feb 23 23:32:23 sonnendeck1 kernel: [  230.187013] RIP  [<ffffffffa02360a8>] usb_remo                                                                                            te_disconnect+0x58/0xb0 [lirc_igorplugusb]
Feb 23 23:32:23 sonnendeck1 kernel: [  230.187023]  RSP <ffff88006c4a5d78>
Feb 23 23:32:23 sonnendeck1 kernel: [  230.187027] CR2: 0000000000000028
Feb 23 23:32:23 sonnendeck1 kernel: [  230.187033] ---[ end trace 95432ccb2a064c9f ]-                                                                                            --

```


do you have a clue what caused this problem?

Thanks a lot! :)

greetings Ice


ps:
ice@sonnendeck1:~$ uname -a
Linux sonnendeck1 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

---

### Post by SiHa on 2010-02-24
Are you using pm-suspend?

I had to do something similar - unload a module - prior to suspending. I used the modunload function available in pm-utils.

See post #3 here: [http://ubuntuforums.org/showthread.php?t=909195](http://ubuntuforums.org/showthread.php?t=909195)

---

### Post by rustikus on 2010-03-09
Hi,

do you have any news regarding this bug? I experience exactly the same behaviour when I try to suspend via pm-suspend.

Linux XBMCLive 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux

Thanks and regards,
rustikus

---

### Post by alda2 on 2010-08-13
Hi, Is there any solution for this problem ? I have the same problem

Thanks A.

---

