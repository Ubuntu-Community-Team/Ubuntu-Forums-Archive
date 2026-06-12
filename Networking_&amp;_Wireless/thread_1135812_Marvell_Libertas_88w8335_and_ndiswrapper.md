---
title: "Marvell Libertas 88w8335 and ndiswrapper"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by dogwoodlover on 2009-04-24
I apologize if this problem has been handled elsewhere--I searched some of the other threads and found nothing helpful.

I have a Marvell Libertas 88w8335 wireless PCI card (Netgear WG311v3). I had no problems in previous versions of Ubuntu getting the card to work via ndiswrapper (7.10, 8.04). I also have it running under FreeBSD 7.1 using the malo driver. I have a set of 64-bit Windows XP drivers since I'm using a 64-bit installation of Ubuntu (9.04 AMD64).

I installed ndiswrapper and ndisgtk, and I used the '-i' switch to install the INF file which seemed to go smoothly. Upon invoking the '-l' switch, it returns this:

```
**darkstar@darkstar-ubuntu:~$ sudo ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mrv8335x64 : driver installed
	device (11AB:1FAA) present

```

I've done the usual commands to get it working (as sudo): 'ndiswrapper -m', 'depmod -a', 'modprobe ndiswrapper', etc.

However, despite this, my card does not seem to be functioning. The light on the back shows no activity, and the card does not show up in NetworkManager or ifconfig/iwconfig:

```
**darkstar@darkstar-ubuntu:~$ ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
[B]
darkstar@darkstar-ubuntu:~$ iwconfig[/B]
lo        no wireless extensions.

pan0      no wireless extensions.
```

Here is some other information:

```
**darkstar@darkstar-ubuntu:~$ lsmod**
Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
ndiswrapper           250624  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
i2c_nforce2            16136  0 
pcspkr                 11136  0 
k8temp                 13440  0 
usblp                  22656  0 
usbhid                 47040  0 
usb_storage            94912  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

It seems, anyway, that the ndiswrapper module has been loaded.

```
**darkstar@darkstar-ubuntu:~$ lspci**
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)

```

```
**darkstar@darkstar-ubuntu:~$ sudo lshw -C network**
[sudo] password for darkstar: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:66:25:81:8d:55
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I noticed some interesting output in dmesg, which I excerpted here:

```
**dmesg**
...
[    9.610144] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    9.677147] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[    9.678286] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
[    9.678992] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[    9.679004] ndiswrapper 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[    9.680462] ndiswrapper: using IRQ 17
[    9.694193] BUG: unable to handle kernel paging request at ffffc210b1a10148
[    9.694198] IP: [<ffffc200041885d1>] 0xffffc200041885d1
[    9.694205] PGD 9f804067 PUD 0 
[    9.694208] Oops: 0000 [#1] SMP 
[    9.694211] last sysfs file: /sys/devices/virtual/misc/ndiswrapper/dev
[    9.694215] Dumping ftrace buffer:
[    9.694217]    (ftrace buffer empty)
[    9.694219] CPU 1 
[    9.694220] Modules linked in: ndiswrapper(+) lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event
 k8temp snd_seq snd_timer snd_seq_device snd pcspkr soundcore snd_page_alloc i2c_nforce2 usblp usbhid usb_storage fbcon tileblit font bitblit softcursor
[    9.694240] Pid: 1686, comm: modprobe Tainted: P           2.6.28-11-generic #42-Ubuntu
[    9.694242] RIP: 0010:[<ffffc200041885d1>]  [<ffffc200041885d1>] 0xffffc200041885d1
[    9.694246] RSP: 0018:ffff88009d1d5730  EFLAGS: 00010216
[    9.694248] RAX: 00000010ad83f7c0 RBX: ffff88009d0b3e00 RCX: 0000000000000000
[    9.694250] RDX: 0000000042b60fdf RSI: 0000000000000004 RDI: ffff88009d0103c0
[    9.694252] RBP: ffff88009d1d58b8 R08: ffffc200041d0950 R09: 0000000000000001
[    9.694254] R10: ffffffffa01fbc10 R11: 0000000000000000 R12: ffff88009e4c2800
[    9.694256] R13: ffff88009d0b3c00 R14: ffff88009e4c2800 R15: ffff88009d0b3830
[    9.694259] FS:  00007f59751036f0(0000) GS:ffff88009f803a80(0000) knlGS:0000000000000000
[    9.694261] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[    9.694263] CR2: ffffc210b1a10148 CR3: 000000009d1a8000 CR4: 00000000000006a0
[    9.694265] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[    9.694267] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[    9.694270] Process modprobe (pid: 1686, threadinfo ffff88009d1d4000, task ffff88003796d980)
[    9.694272] Stack:
[    9.694273]  ffffffffa01f400d ffff88009dce0c00 0000000000000000 ffffc20004188739
[    9.694277]  ffff88009e4c2800 ffff88009e4c2800 ffff88009d0103c0 0000000000000004
[    9.694280]  ffff88009d0b3e00 ffffc20004185062 ffffc2000007b000 ffffc200041a66b7
[    9.694284] Call Trace:
[    9.694286]  [<ffffffffa01f400d>] ? NdisMAllocateMapRegisters+0x8d/0x220 [ndiswrapper]
[    9.694328]  [<ffffffff8042da9d>] ? pci_request_region+0x10d/0x1d0
[    9.694334]  [<ffffffffa01fd0c0>] ? IofCompleteRequest+0x60/0x1e0 [ndiswrapper]
[    9.694352]  [<ffffffffa0204eea>] ? mp_init+0x6a/0x210 [ndiswrapper]
[    9.694370]  [<ffffffff8069e7a3>] ? _spin_unlock_bh+0x13/0x20
[    9.694375]  [<ffffffffa01fd0c0>] ? IofCompleteRequest+0x60/0x1e0 [ndiswrapper]
[    9.694392]  [<ffffffffa01fef39>] ? pdoDispatchPnp+0x49/0x190 [ndiswrapper]
[    9.694410]  [<ffffffffa0205e17>] ndis_start_device+0x27/0x790 [ndiswrapper]
[    9.694427]  [<ffffffffa01fc419>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[    9.694445]  [<ffffffffa01fc445>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
[    9.694462]  [<ffffffff8069e7a3>] ? _spin_unlock_bh+0x13/0x20
[    9.694465]  [<ffffffffa01fc419>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[    9.694481]  [<ffffffffa01fcb12>] ? IoSyncForwardIrp+0x92/0xd0 [ndiswrapper]
[    9.694500]  [<ffffffffa020661a>] NdisDispatchPnp+0x9a/0x150 [ndiswrapper]
[    9.694517]  [<ffffffffa0208557>] win2lin2+0xe/0x11 [ndiswrapper]
[    9.694535]  [<ffffffffa01fc419>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[    9.694552]  [<ffffffffa01fc445>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
[    9.694569]  [<ffffffff8069e7a3>] ? _spin_unlock_bh+0x13/0x20
[    9.694572]  [<ffffffffa01fc419>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
[    9.694589]  [<ffffffffa01fe187>] IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
[    9.694606]  [<ffffffff8069e7a3>] ? _spin_unlock_bh+0x13/0x20
[    9.694609]  [<ffffffffa01fe437>] pnp_start_device+0x47/0x90 [ndiswrapper]
[    9.694627]  [<ffffffffa01fe840>] wrap_pnp_start_device+0x230/0x280 [ndiswrapper]
[    9.694644]  [<ffffffff802fc48b>] ? iput+0x2b/0x70
[    9.694649]  [<ffffffffa01fe9d1>] wrap_pnp_start_pci_device+0x51/0x60 [ndiswrapper]
[    9.694667]  [<ffffffff80418a2a>] ? kobject_get+0x1a/0x30
[    9.694671]  [<ffffffff8069e569>] ? _spin_lock+0x9/0x10
[    9.694674]  [<ffffffff80430296>] ? pci_match_device+0xc6/0xd0
[    9.694678]  [<ffffffff80430c3c>] pci_device_probe+0x7c/0xa0
[    9.694681]  [<ffffffff804b98fd>] really_probe+0x6d/0x1a0
[    9.694686]  [<ffffffff804b9a7b>] driver_probe_device+0x4b/0x60
[    9.694689]  [<ffffffff804b9b2b>] __driver_attach+0x9b/0xa0
[    9.694692]  [<ffffffff804b9a90>] ? __driver_attach+0x0/0xa0
[    9.694695]  [<ffffffff804b90eb>] bus_for_each_dev+0x6b/0xa0
[    9.694698]  [<ffffffff804b977c>] driver_attach+0x1c/0x20
[    9.694700]  [<ffffffff804b88dd>] bus_add_driver+0x14d/0x250
[    9.694703]  [<ffffffffa005c000>] ? wrapper_init+0x0/0xf2 [ndiswrapper]
[    9.694716]  [<ffffffff804b9d1c>] driver_register+0x6c/0x150
[    9.694719]  [<ffffffffa005c000>] ? wrapper_init+0x0/0xf2 [ndiswrapper]
[    9.694732]  [<ffffffff80430f1d>] __pci_register_driver+0x6d/0xc0
[    9.694736]  [<ffffffffa005c000>] ? wrapper_init+0x0/0xf2 [ndiswrapper]
[    9.694749]  [<ffffffffa01f0bb1>] loader_init+0xa1/0x150 [ndiswrapper]
[    9.694763]  [<ffffffffa005c0dd>] wrapper_init+0xdd/0xf2 [ndiswrapper]
[    9.694776]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[    9.694780]  [<ffffffff802d0225>] ? __vunmap+0xc5/0x110
[    9.694784]  [<ffffffff802d02c5>] ? vfree+0x25/0x30
[    9.694786]  [<ffffffff8027eee8>] ? load_module+0x11c8/0x11d0
[    9.694792]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
[    9.694795]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[    9.694799] Code: cc cc cc cc cc cc cc cc cc cc 53 56 57 41 54 48 83 ec 28 4c 8d 05 90 83 04 00 8b 15 9a 84 04 00 48 85 c9 75 11 8b c2 48 c1 e0 06 <4a> 39 4c 00 38 0f 84 83 00 00 00 8b ca 48 c1 e1 06 bb 02 00 00 
[    9.694824] RIP  [<ffffc200041885d1>] 0xffffc200041885d1
[    9.694826]  RSP <ffff88009d1d5730>
[    9.694828] CR2: ffffc210b1a10148
[    9.694831] ---[ end trace 1431be80dd27ec2e ]---
```

```
**darkstar@darkstar-ubuntu:~$ uname -mr**
2.6.28-11-generic x86_64
```

Any help would be greatly appreciated, as I'm not sure what is wrong. I apologize once again if I am being redundant.

**_EDIT_**:

ndisgtk returns the error "*Unable to see if hardware is present.*" when I attempt to install the INF file.

---

### Post by snickity on 2009-04-24
I can't help you, but I can give you hope : )

I have the same identical card and it is working for me in 8.10. Initially got it working in 8.04 and then upgraded to 8.10 last week without a problem. 

-network:0             
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 9
       bus info: pci@0000:03:09.0
       logical name: wlan0
       version: 03
       serial: 08:10:74:17:d8:a0
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8000c driverversion=1.53+Marvell,09/17/2004,3.1.0.19 ip=192.168.1.101 latency=32 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11b

---

### Post by dogwoodlover on 2009-04-24
Yes, I did have it working briefly in 8.10.

If I can't get it to function in 9.04, I'll probably downgrade, though I really would like to get it working in 9.04.

Thanks for the input.

**_EDIT_**:

It seems as if this may be a bug, as [someone else has a similar dmesg output using ndiswrapper for the 88w8335 on ArchLinux (x64)]("http://sourceforge.net/tracker/index.php?func=detail&aid=2496095&group_id=93482&atid=604450"), but from what I can tell, the problem was not solved.

Any advice for solving this?

---

### Post by snickity on 2009-04-24
Sorry, didn't notice you were talking about 9.04. Unfortunately I don't have a solution. But I will be watching this thread, I am going to piggyback on whatever help you are offered : ) 

I think I am going to wait to upgrade to 9.04. : )

---

### Post by dogwoodlover on 2009-04-25
Just "downgraded" to 32-bit 8.10, and the Libertas works perfectly.

I may try upgrading to 9.04 in 32-bit, to see whether it will work.

---

### Post by Krisseh on 2009-05-01
> **dogwoodlover said:**
> Just "downgraded" to 32-bit 8.10, and the Libertas works perfectly.

I may try upgrading to 9.04 in 32-bit, to see whether it will work.

Hi, I'm having a similar problem, cant get my Marvell lib 88w8335 to work with 9.04 in 64 bit, it workd grate in 8.04 and 8.10,  have you tryed 9.04 in 32 bit yet?

---

### Post by Krisseh on 2009-05-02
> **Krisseh said:**
> Hi, I'm having a similar problem, cant get my Marvell lib 88w8335 to work with 9.04 in 64 bit, it workd grate in 8.04 and 8.10,  have you tryed 9.04 in 32 bit yet?

I found a 64 bit driver that work grate,  [http://moosy.blogspot.com/2007/01/netgear-wg311v3.html](http://moosy.blogspot.com/2007/01/netgear-wg311v3.html)  ::and choosie the 64-bit : [http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=)

---

### Post by alexman98 on 2009-05-06
Hello, the same here, I'm having this problem since yesterday. 

I use a Zonet 1602 PCI wifi card, it have the same Marvell Libertas chipset as other models out there. I was using it on previous versions of Ubuntu 32 bits (since 7.10) without problems with ndiswrapper (even on Ubuntu 8.04 the system gave me an option to activate a driver for it) .

Now, I'm using Ubuntu 9.04 64 bits and have no luck with ndiswrapper, I already tested a lot of drivers out there, also, I have seen the same problem with ndiswrapper:

> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release. Programs installed/used:

[LIST]
[*]Ubuntu Jaunty Jackalope 9.04 64 bits edition.
[*]ndiswrapper utils 1.53-2 from Synaptic repository
[*]ndiswrapper common
[*]ndisgtk
[*]64 bits drivers for Marvell Libertas chipset
[/LIST]
I hope this get fixed soon, I already got a lot of headaches because of it... >_>

---

### Post by rasbandm on 2009-05-30
Hey guys, 

I was having a similar problem as you guys until just now.  I stumbled upon this page during a google search and it solved my problem.. I was finding the wrong .inf files.  He has a link to the .inf for the Marvell 88w8335 like we (all) have.
____________________________________________
Just a quick run-through:

Install ndiswrapper via terminal

$ sudo apt-get install ndisgtk

and then download the right .inf (my issue was having the x86)

link to x64: 
[HTML]http://www.versiontracker.com/dyn/moreinfo/win/131948[/HTML]

and then your usual install using ndiswrapper.
_______________________________________________

Here&#347; the link to his page, he just gave me the link to the .inf file through versiontracker.  [HTML]https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k[/HTML]

I hope it works for you like it did for me.

-rasband

ps - I had many of the same readouts as you guys before, but since I got that inf it was fine.

---

### Post by dogwoodlover on 2009-06-06
> **Krisseh said:**
> have you tryed 9.04 in 32 bit yet?


While I have not had the opportunity to test out the proposed solutions in 64-bit, I have in fact upgraded to 9.04 in 32-bit, and it works flawlessly.

For the record, the INF/SYS files I tried under 9.04 64-bit are for 64-bit versions of Windows XP, rather than 32-bit versions.

---

### Post by jmlineb on 2009-07-17
I too have problems with my NetGear WG311v3 card and ndiswrapper under Ubuntu 9.04.  My symptom is that ever 5-7 reboots, I get a kernel oops with a "Bug:  Unable to handle kernel paging request," which one user reports above.

Just so you'll be aware, a bug has been filed by another user about this very issue.  So far, no response.  The URL for the bug report is [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/295120](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/295120).  What are our option for escalation?  I have upgraded to ndiswrapper 1.55 by compiling and installing the source, but I still get this problem.  From this post ([http://lkml.indiana.edu/hypermail/linux/kernel/0812.3/00574.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.3/00574.html)) the issue may lie more in the scheduling mechanism of the 2.6.28 kernel than in ndiswrapper.

Has anyone had good luck compiling and installing a custom kernel in Ubuntu?  I got 2.8.31 to compile, but when I booted into it, I had all kinds of module problems.  How do I transfer existing modules over to the new image directory, such that a graphics boot actually works?

---

### Post by goldenSection on 2009-10-28
Hi All :)

OK I think I may have a solution for this. Please refer to this page [http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64](http://sites.google.com/site/subtlegems/netgear-wg311v3-ndis-driver-for-linux-amd64), has both 32 + 64bit support. 

Install as normal with:

sudo ndiswrapper -i WG311v3.INF

ndiswrapper -m

Worked for me :KS

---

