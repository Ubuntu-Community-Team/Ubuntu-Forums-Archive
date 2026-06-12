---
title: "Someone is going to die or Me and RTL8185"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by c2h5oh on 2006-07-07
I've just spent two great, sunny days indoors with a soft glow of pc screen because of RTL8185. 

1. Driver included with distro (the one for 8180/8185)
The PCI card is detected (Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
) and r818x is assigned to it. The driver loads fine and works fine until I decide to actually use it. 
[B]
ifconfig wlan0 up = system freeze.[/B]

to be more specific it freezes just after RTL8180: card successfully reset

2. ndiswrapper, round 1
Installed ndiswrapper-utils, installed winblows driver (tested with driver for xp, 2k and 2k3), verified if it was loaded (yes it was - device detected, correct driver assigned every time), modprobe ndiswrapper working ok and...

**ifconfig wlan0 up = system freeze**

as if nothing has changed.. another 2-3h of research and experimentation and I find out that driver included with distro is still used.

3. ndiswrapper, round 2
After blacklisting r818x in /etc/modprobe.d I tried again to get ndiswrapper working. Everything work just fine, up until the point I was to modprobe the module, which ends in **segmentation fault**. 

dmesg:
```

[42949531.100000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[42949531.190000] ndiswrapper: driver net8185 (802.11g Wireless LAN PCI Card,10/20/2005,5.103.1020.2005) loaded
[42949531.190000] PCI: Enabling device 0000:00:0a.0 (0114 -> 0117)
[42949531.190000] **** SET: Misaligned resource pointer: c5a172e2 Type 07 Len 0
[42949531.190000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[42949531.190000] PCI: setting IRQ 11 as level-triggered
[42949531.190000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[42949531.200000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[42949531.210000]  printing eip:
[42949531.210000] c8b60147
[42949531.210000] *pde = 0377b001
[42949531.220000] Oops: 0002 [#1]
[42949531.220000] SMP
[42949531.220000] Modules linked in: ndiswrapper nls_cp437 isofs udf dm_mod ipv6 md_mod lp af_packet parport_pc parport 8139cp pcspkr 8139too psmouse serio_raw i2c_piix4 i2c_core 3c59x mii shpchp pci_hotplug intel_agp agpgart evdev ext3 jbd ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[42949531.220000] CPU:    0
[42949531.220000] EIP:    0060:[<c8b60147>]    Tainted: P      VLI
[42949531.220000] EFLAGS: 00010202   (2.6.15-25-server)
[42949531.220000] EIP is at 0xc8b60147
[42949531.220000] eax: 00000000   ebx: 00000000   ecx: 0000003d   edx: c8b87052
[42949531.220000] esi: c8c19051   edi: c8ba003d   ebp: c2629b8c   esp: c2629b28
[42949531.220000] ds: 007b   es: 007b   ss: 0068
[42949531.220000] Process loadndisdriver (pid: 3736, threadinfo=c2628000 task=c7a28070)
[42949531.220000] Stack: c8c19051 c8ba1000 c8b8d4e9 c8b604f3 c8c19051 c8b8bbf8 0000003d 00000000
[42949531.220000]        c2670790 00000000 00000000 00000000 00000001 00000286 c271a400 00629ba8
[42949531.220000]        c2629ba8 c8b3636b c8b33ad0 c8ba1aac c6674220 c2670790 000000c7 c6670000
[42949531.220000] Call Trace:
[42949531.220000]  [<c8b3636b>] NdisInitializeEvent+0x1b/0x30 [ndiswrapper]
[42949531.220000]  [<c8b33ad0>] NdisAllocateSpinLock+0x10/0x20 [ndiswrapper]
[42949531.220000]  [<c8b4375c>] miniport_init+0x8c/0x130 [ndiswrapper]
[42949531.220000]  [<c8b455e1>] ndis_start_device+0x31/0x5c0 [ndiswrapper]
[42949531.220000]  [<c01f701d>] vsnprintf+0x35d/0x640
[42949531.220000]  [<c01f701d>] vsnprintf+0x35d/0x640
[42949531.220000]  [<c0124d68>] call_console_drivers+0x158/0x180
[42949531.220000]  [<c01252a9>] release_console_sem+0x79/0xc0
[42949531.220000]  [<c012512a>] vprintk+0x27a/0x300
[42949531.220000]  [<c8b3cbf3>] IofCompleteRequest+0xe3/0x1f0 [ndiswrapper]
[42949531.220000]  [<c0282c31>] eisa_set_level_irq+0x71/0xa0
[42949531.220000]  [<c8b42114>] pdoDispatchPnp+0x44/0x190 [ndiswrapper]
[42949531.220000]  [<c012b5fc>] __request_region+0x5c/0x90
[42949531.220000]  [<c8b3caf9>] IofCallDriver+0x69/0x80 [ndiswrapper]
[42949531.220000]  [<c8b45529>] NdisDispatchPnp+0xc9/0x150 [ndiswrapper]
[42949531.220000]  [<c8b3caf9>] IofCallDriver+0x69/0x80 [ndiswrapper]
[42949531.220000]  [<c8b4289d>] pnp_start_device+0x7d/0x130 [ndiswrapper]
[42949531.220000]  [<c8b42d22>] wrap_pnp_start_device+0x112/0x1b0 [ndiswrapper]
[42949531.220000]  [<c0201f06>] __pci_device_probe+0x56/0x70
[42949531.220000]  [<c0201f4f>] pci_device_probe+0x2f/0x50
[42949531.220000]  [<c025db74>] driver_probe_device+0x54/0xf0
[42949531.220000]  [<c025dc90>] __driver_attach+0x0/0x50
[42949531.220000]  [<c025dcd3>] __driver_attach+0x43/0x50
[42949531.220000]  [<c025d09d>] bus_for_each_dev+0x5d/0x80
[42949531.220000]  [<c025dd05>] driver_attach+0x25/0x30
[42949531.220000]  [<c025dc90>] __driver_attach+0x0/0x50
[42949531.220000]  [<c025d5f9>] bus_add_driver+0x89/0xf0
[42949531.220000]  [<c02021e7>] __pci_register_driver+0x87/0xb0
[42949531.220000]  [<c8b305e8>] register_devices+0x388/0x650 [ndiswrapper]
[42949531.220000]  [<c018f669>] mntput_no_expire+0x29/0xb0
[42949531.220000]  [<c8b309cd>] wrapper_ioctl+0x11d/0x140 [ndiswrapper]
[42949531.220000]  [<c012a2ab>] current_fs_time+0x5b/0x80
[42949531.220000]  [<c0184cb3>] do_ioctl+0x93/0xa0
[42949531.220000]  [<c0184eab>] vfs_ioctl+0x6b/0x230
[42949531.220000]  [<c01850f8>] sys_ioctl+0x88/0xa0
[42949531.220000]  [<c010335b>] sysenter_past_esp+0x54/0x75
[42949531.220000]  [<c013007b>] __exit_signal+0x8b/0x180
[42949531.220000] Code: 03 8b 45 fc 5e 5b c9 c2 04 00 56 8b 74 24 08 57 66 8b 7c 24 14 0f b7 cf 33 c0 85 c9 7e 16 53 8b 54 24 14 8b 52 04 8a 14 42 8b 1e <88> 14 18 40 3b c1 7c ec 5b 66 89 7e 04 5f 33 c0 5e c2 0c 00 cc
[42949531.220000]  <3>ndiswrapper (wrapper_init:173): loadndiswrapper failed (11); check system log for messages from 'loadndisdriver'
[42949531.660000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[42949531.670000]  printing eip:
[42949531.680000] c0306a40
[42949531.680000] *pde = 06cd4001
[42949531.690000] Oops: 0002 [#2]
[42949531.690000] SMP
[42949531.690000] Modules linked in: ndiswrapper nls_cp437 isofs udf dm_mod ipv6 md_mod lp af_packet parport_pc parport 8139cp pcspkr 8139too psmouse serio_raw i2c_piix4 i2c_core 3c59x mii shpchp pci_hotplug intel_agp agpgart evdev ext3 jbd ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[42949531.690000] CPU:    0
[42949531.690000] EIP:    0060:[<c0306a40>]    Tainted: P      VLI
[42949531.690000] EFLAGS: 00010296   (2.6.15-25-server)
[42949531.690000] EIP is at _spin_lock+0x0/0x10
[42949531.690000] eax: 00000000   ebx: 00000000   ecx: c01f39a0   edx: 00000000
[42949531.690000] esi: c8b58d68   edi: 08053078   ebp: c26ec000   esp: c26edf14
[42949531.690000] ds: 007b   es: 007b   ss: 0068
[42949531.690000] Process modprobe (pid: 3731, threadinfo=c26ec000 task=c7d0a550)
[42949531.690000] Stack: c0304668 c8b58d08 c8b58d08 00000001 c025d6ab c8b58d68 c8b58d08 c8b58d08
[42949531.690000]        c025e1d0 c8b58d08 c8b58ce0 c0202223 c8b58d08 00000000 c8b30abf c8b58ce0
[42949531.690000]        00000000 c8b41f0a c8b4c4fc 00000000 00000001 c896907e c8b4c4fc c8b47699
[42949531.690000] Call Trace:
[42949531.690000]  [<c0304668>] klist_remove+0x18/0x40
[42949531.690000]  [<c025d6ab>] bus_remove_driver+0x4b/0x80
[42949531.690000]  [<c025e1d0>] driver_unregister+0x10/0x20
[42949531.690000]  [<c0202223>] pci_unregister_driver+0x13/0x20
[42949531.690000]  [<c8b30abf>] loader_exit+0x4f/0x100 [ndiswrapper]
[42949531.690000]  [<c8b41f0a>] module_cleanup+0xa/0xb0 [ndiswrapper]
[42949531.690000]  [<c896907e>] wrapper_init+0x7e/0x1d4 [ndiswrapper]
[42949531.690000]  [<c0143f54>] sys_init_module+0xd4/0x1f0
[42949531.690000]  [<c010335b>] sysenter_past_esp+0x54/0x75
[42949531.690000] Code: 00 00 01 74 05 e8 39 e0 ff ff c3 ba 00 e0 ff ff 21 e2 81 42 14 00 01 00 00 f0 81 28 00 00 00 01 74 05 e8 1c e0 ff ff c3 8d 76 00 <f0> fe 08 79 09 f3 90 80 38 00 7e f9 eb f2 c3 90 f0 81 28 00 00
[42949531.690000]

```

Each and every time I started with a fresh install. 
It doesn't seem to be kernel specific - tested with 2.6.15-23-server, 2.6.15-25-386 and 2.6.15-25-server

Any clues what to do next?

---

### Post by c2h5oh on 2006-07-07
I gave it another shot:

4. Realtec 8185 driver
Downloaded, compiled, insmoded without problem
```

[17180000.436000] ieee80211_crypt: registered algorithm 'NULL'
[17180041.000000] ieee80211_crypt: registered algorithm 'WEP'
[17180048.168000] ieee80211_crypt: registered algorithm 'TKIP'
[17180056.552000] ieee80211_crypt: registered algorithm 'CCMP'
[17180508.652000] r8180: no version for "ieee80211_reset_queue" found: kernel tainted.
[17180508.668000]
[17180508.668000] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[17180508.668000] Copyright (c) 2004-2005, Andrea Merello
[17180508.668000] rtl8180: Initializing module
[17180508.668000] rtl8180: Wireless extensions version 19
[17180508.668000] rtl8180: Initializing proc filesystem
[17180508.668000] rtl8180: Configuring chip resources
[17180508.672000] PCI: Enabling device 0000:00:0a.0 (0114 -> 0117)
[17180508.672000] **** SET: Misaligned resource pointer: c75ce4c2 Type 07 Len 0
[17180508.672000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17180508.672000] PCI: setting IRQ 11 as level-triggered
[17180508.672000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17180508.672000] rtl8180: Memory mapped space @ 0xfedffc00
[17180508.672000] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[17180508.672000] rtl8180: This is a PCI NIC
[17180508.676000] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[17180508.680000] rtl8180: Card MAC address is 00:12:0e:32:c2:e3
[17180508.696000] rtl8180: EEPROM version 105
[17180508.700000] rtl8180: Card reports RF frontend Realtek 8225
[17180508.700000] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[17180508.700000] rtl8180: WW:use it with care and at your own risk and
[17180508.700000] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17180508.700000] rtl8180: Energy threshold: b
[17180508.700000] rtl8180: PAPE from CONFIG2: 6
[17180508.700000] rtl8180: IRQ 11
[17180508.704000] rtl8180: Driver probe completed

```

aaaandd?

**ifconfig wlan0 up = system freeze**

my comment becomes nonexistant after censoring

---

### Post by c2h5oh on 2006-07-08
Bump.

Any ideas?

---

### Post by c2h5oh on 2006-07-09
Bump again.
I'd really appreciate any new ideas to test. Is it any different with previous versions of ubuntu (I've been using it for a while, but not with wireless)?

---

### Post by c2h5oh on 2006-07-10
The final bump. 

Anyone?

---

### Post by andersja on 2006-08-02
... I've got the same problem. I installed network-manager and network-manager-gnome and this problem froze my system at login-time, even - had to reboot in recovery mode, apt-get remove network-manager to even be allowed to log in graphically again.

I too found the same error messages in my message log (warning this driver is experimental etc)...

Anywhere one can find more recent drivers for this?

---

### Post by andersja on 2006-08-03
There are some 'fedore 2' drivers here, incl WPA-PSK source code. Anyone want to take a short at fitting this into ubuntu?

[http://safecom.cn/code/support/DMF.aspx?pid=319&pos=1#1]("http://safecom.cn/code/support/DMF.aspx?pid=319&pos=1#1")

---

### Post by c2h5oh on 2006-08-03
At least I can confirm it's not distro related - I've got the very same error with Slackware 10.2 (compiled the opensource driver for 2.4.x kernel) and Ubuntu 5.10.. 

Anyone?

---

### Post by andersja on 2006-08-09
Doing some further digging; the device shows up on lspci as:

0000:00:14.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown devic e 8185 (rev 20)

lspci -n reveals:
0000:00:14.0 0200: 10ec:8185 (rev 20)

Disturbingly, there is no entry for this card in the ndiswrapper wiki:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

Anyone got any ideas except going out and buying another wifi card? ](*,)

---

### Post by andersja on 2006-08-10
Raised as Ubuntu bug number: 55905

[https://launchpad.net/distros/ubuntu/+bug/55905]("https://launchpad.net/distros/ubuntu/+bug/55905")

---

### Post by c2h5oh on 2006-08-20
I've sent some extra info for the bug. If anyone is experiencing simmilar problems please add any info you find relevant - it will help.

---

### Post by brujoand on 2006-08-20
have u tried compiling ndiswrapper form source? worked for me on my dell, bcm43xx.

---

### Post by Stealth on 2006-08-22
If only I had read this some days ago...-.-

I too have, what seems to be an RTL8185 chipset'd card. That's according to the name of the drivers on the CD. Same thing happened to me, constant freezes using the r818x drivers. Ndiswrapper is also going screwy with segfaults...I don't know what to do...:(

---

### Post by crustyc on 2006-10-03
I have the same chipset and issue as described in previous posts.
However I have found the issue to be hardware specific.

Testing with ubuntu dapper drake:

My two PIII's (two different mainboards) fail when using the r818x driver. When bringing up the interface with ifconfig linux freezes, no core dump or error logs.

When the same card is installed in my AMD1100 it works fine.

I have also tested in my Proliant 3000 Dual PII 333 it works fine there too.

---

### Post by c2h5oh on 2006-10-05
It's worth giving a try - I've tested it only with my Intel BX based PII board - I'll try moving to PIII this weekend (damn.. my media server/router will have a fan :/) and check it.

---

### Post by andersja on 2006-10-17
I've now unscrewed the RTL card from my PC and ordered a linksys USB wifi dongle off ebay. Crossing my fingers for this one...

---

### Post by OPaul on 2006-10-25
My rtl8180 is also constantly locking up, although there seems to be no real pattern to it. Whenever I stop a torrent download the system freezes. Also, when I'm connected to a certain wireless network its always freezing, but then other networks are fine.

---

### Post by OPaul on 2006-10-29
I've managed to make this reproducible with my card (rtl8180, same driver). Whenever I open a .doc file over the network (samba) with OpenOffice. Then make a change and save the file. The laptop then lockups up, and the file becomes corrupt. Same thing every time. Though if I try and save a normal .txt file over the network it saves fine.

Doing **ifconfig wlan0 up**works fine. And I usually can operate fine on my wireless network. Just sometimes, out of the blue, it locks up.

---

### Post by OPaul on 2006-10-30
I tried using the latest rtl8180 drivers from the CVS and had the same results. Switching to the ndiswrapper included in Edgy, however, did solve the problem.

---

### Post by moxfyre on 2006-12-02
Opaul, I have a very similar situation to yours with an Encore card with the RTL 8225 frontend chip.

I have had similar problems with torrents and other random freezing.

I *think* the problem has to to do with uploading (outgoing data): I can download at very high rates for days on end with no problems, but if I start uploading at more than 10 kB/s, the system will usually freeze within a few  seconds to a few minutes.

I emailed the rtl wireless card maintainers with my ideas about the problem, but never got a response.  Anybody else have any luck with them?

---

### Post by ramses55 on 2007-01-21
Hi there,

just surfed the web for helping me out in exactly the situation you guys all describe here. State: System HP prof. XW4100, WLAN card SMC SMCWPCI-G with a RTL8185 chip and a RTL8225 radio unit. Distr.: openSuSE 10.2. NDISWRAPPER: Gave up, freeze all the times. Original RTL driver: Freezes when try to insmod. Please anyone speak up if further information needed, would like to receive assistance, and am definitely willing to give as much input as possible. Any idea what goes wrong?

Last lines in messages:

Jan 21 16:06:12 stay-away kernel: ieee80211_crypt: registered algorithm 'NULL'
Jan 21 16:06:12 stay-away kernel: ieee80211_crypt: registered algorithm 'WEP'
Jan 21 16:06:12 stay-away kernel: ieee80211_crypt: registered algorithm 'TKIP'
Jan 21 16:06:12 stay-away kernel: ieee80211_crypt: registered algorithm 'CCMP'
Jan 21 16:06:12 stay-away kernel: r8180: no version for "ieee80211_reset_queue" found: kernel tainted.
Jan 21 16:06:12 stay-away kernel:
[CRASH/FREEZE]

Brgds

---

### Post by ramses55 on 2007-01-24
Hi everyone,

hope someone reads this at all. Did have another try using ndiswrapper and did not succeed. Following summary output:

lspci
[...]
05:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
[...]

lsmod
[...]
ndiswrapper           185876  0 
[...]

ndiswrapper -l
Installed drivers:
net8185         driver installed, hardware present 

ifconfig
no wlan

iwconfig
no wlan

network manager
no wlan

Any idea?

Brgds

---

### Post by netindividuo on 2007-01-24
Same problem here with a SMC networks wireless PCI adapter 802.11g 54Mbps (SMCWPCI-G) 
that uses a realtek 8185L chipset, in Ubuntu 6.10 (Both alternate and Desktop installs). 

The module r818x takes control over the card and all seems fine but doesn´t work at all. After blacklisting the module ndiswrapper gets the WINXP driver fine, but fails when loading the ndiswrapper module. 

Is not a hardware related problem. With Knoppix 5 and the ndiswrapper it works fine with the driver for WINXP that came on the CD-ROM.

There is only one problem. Is not Ubuntu! and thats what I use on my computers, so I´m still waiting for some kind of fix.

If Anyone knows why this happens, or how to solve it...  (Without installing knoppix!)

---

### Post by tempest1 on 2007-04-09
I'm having the same problems... is there any fix for this?

---

### Post by jfinkels on 2007-04-09
I experienced similar lockups on a RTL8185L (I think...I don't have access to this computer any longer). Not only did it cause troubles during setup, once I was able to get it to work, my system froze when **uploading** data, but not necessarily when downloading.

---

### Post by MrShifty on 2007-04-20
I've got a Gateway MX3225 with (presumably) an RTL8185 network adapter. Same deal, except I haven't tried ndiswrapper yet. The guys at my local computer shop fiddled with it a while back and made it work (dapper), I upgraded to edgy and broke it (wifi radar could see wlan0, but couldn't connect to WEP or WPA enable networks), and when I installed Feisty today, nothing at all. I'll go ask the guys at the shop again and post their results.

---

### Post by jstone00 on 2007-04-20
Grrrr!    Here I thought I'd finally found a version of Linux that played well with my Encore PCI WiFi card Realtek 8185.  Ubuntu 6.1 detected it and ran it flawlessly.  Last night I upgraded to Feisty Fawn (Feisty Goat?) 7.04 and the wirless card dissapeared, and no longer appears in the Network Manager applet.  It seems like this is a common problem and a known bug, and I haven't been able to find a solution.  Ndiswrapper reports "invalid driver" when I attempt to load any of the Windows drivers supplied with the card.  I've even tried editing the /etc/network/interfaces file and managed to make Ubuntu unbootable.  Luckily, another live-CD version of Linux (Puppy Linux)  allowed me to view the Ubuntu partition and re-edit the damaged file so Ubuntu would boot again.

The person who posts a clear solution to this problem will earn my undying gratitude, and maybe a Snickers bar.

Regards.....

---

### Post by marsmissionaries on 2007-04-20
> **jstone00 said:**
> Grrrr!    Here I thought I'd finally found a version of Linux that played well with my Encore PCI WiFi card Realtek 8185.  Ubuntu 6.1 detected it and ran it flawlessly.  Last night I upgraded to Feisty Fawn (Feisty Goat?) 7.04 and the wirless card dissapeared, and no longer appears in the Network Manager applet.  It seems like this is a common problem and a known bug, and I haven't been able to find a solution.  Ndiswrapper reports "invalid driver" when I attempt to load any of the Windows drivers supplied with the card.  I've even tried editing the /etc/network/interfaces file and managed to make Ubuntu unbootable.  Luckily, another live-CD version of Linux (Puppy Linux)  allowed me to view the Ubuntu partition and re-edit the damaged file so Ubuntu would boot again.

The person who posts a clear solution to this problem will earn my undying gratitude, and maybe a Snickers bar.

Regards.....

I had the exact same problem. 

See this page here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

The reason why it does not show up is because the module is black listed, simply remove the blacklist entry as stated in the bug report, and then follow the steps towards the bottom to get it to connect to the network.

---

### Post by zedfrugnug on 2007-04-20
> **marsmissionaries said:**
> I had the exact same problem. 

See this page here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)

The reason why it does not show up is because the module is black listed, simply remove the blacklist entry as stated in the bug report, and then follow the steps towards the bottom to get it to connect to the network.

Are you sure about removing the drivers for the blacklist?
The comment with blacklist: 
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
I've tried feisty herd 5, and it did hang on trying to load the wireless drivers..
Now, with final, it doesn't hang anymore.

---

### Post by luke411 on 2007-04-20
I removed the module from the black list and sure enough, my NIC showed up and even though I can scan for AP's and even change settings for my ESID, I cannot get connected.

---

### Post by luke411 on 2007-04-20
Okay guys, here's what worked for my Realtek 8185. Like you, it worked fine until I upgraded to Fiesty Lemon. You have to remove the entries for the modules from the blacklist as described above and then add a 'dummy' character to your SSID name. Mine is "Lewis" so I named the SSID "Lewiss". I don't know how someone figured this out but it works. Apparently the module is 'eating' the last letter of the SSID and that's why it doesn't connect even after you unlist the modules.

---

### Post by jstone00 on 2007-04-22
OK, this looks like the key that will make things work.  After having searched for how to remove the card drivers from the blacklist, I'm stumped.  Anyone want to help by posting a "How To" remove the blacklisted drivers?

Thanks!

---

### Post by jrlander on 2007-04-22
I had the same problem with my RTL8180.  Modifying the blacklist is pretty easy.

Just use the following command to open up the blacklist:

sudo gedit /etc/modprobe.d/blacklist


Then just comment the line of the driver you want to use.  It should say something like "blacklist r818x" (or whichever driver you are trying to use).


That should do it.  If you still can't connect but you can see your wireless card in Network Manager, then you are probably seeing the SSID issue that was mentioned previously in this thread.

---

### Post by jrobbins88 on 2007-04-25
Well, I took everything off the blacklist, but I don't know what to do, now. It says that I have a manual configuration set when I made my SSID name have a dummy character.

I don't know how to search for wireless networks, though..

---

### Post by Razorwolf on 2007-04-27
I can see my wireless card, and I added an extra letter to the end of my essid but it still will not connect.  The icon just shows two computer screens that never light up, and when I hover over it, it just says "Manual network configuration".  I have tried letting it roam for the network and connecting to another network but none of it works.  The only difference after changing it to manual configuration is that it doesn't say it is connected, but it doesnt say it is either....i need help please :(

---

### Post by steviebrutal on 2007-04-28
I figured I'd add some background to this thread about my situation:

Previous to upgrading to Feisty, my wireless card (Realtek 8185) worked OK but I could only connect to unsecured networks or WEP - WPA just seemed to not be available for my card.  Also when using NetworkManager or ifconfig, my card was not capable of seeing wireless signal strength.

To my surprise after upgrading to Feisty, when I clicked on the NetworkManager icon - not only could I see signal strengths, but I could connect to WPA AP's.  After about 2 hours of usage, in the middle of browsing the web - the wireless connectivity just dropped and I could no longer detect any APs.  In fact, the device (wlan0) didn't even exist in ifconfig.

With that said, I have returned to a working state by using the suggestions posted in this thread, but I am back to the point where I can only connect to WEP or unsecured access points.  What driver (if anyone knows) was Feisty using by default after I upgraded that gave me such an improvement in functionality?

---

### Post by samexner on 2007-07-26
i had luck with the windows 98 driver... no problems at all, there

---

### Post by Andrewie on 2007-08-31
I hope I'm not too late but here is a web site with a open source driver for you to use. It worked on my laptop.

[http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

There should be directions on the web site but post in this thread if you need help

---

### Post by CoolDreamZ on 2008-02-09
And another option from the RealTek website (posted 21st Dec 2007):

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true")

This needs to be built from the source however this worked first time for me using the supplied scripts (there are some compiler warnings which I ignored).

---

### Post by CoolDreamZ on 2008-02-09
Well, I have tried this and I get kernel freezes (from syslog it seems the wireless card/driver is constantly re-setting/crashing). I have moved to using the ndiswrapper solution instead which works fine with command line configuration of the wireless network connection although I have now lost the ability to configure through nm-applet :(

---

### Post by Andrewie on 2008-02-11
ndiswrapper + realtek windows driver

install that, and then download this driver and use it with your linux. It works perfect for me :)

[http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true](http://152.104.125.41/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&ProdID=35&DownTypeID=3&GetDown=false&Downloads=true)

I then downloaded the UI Package and driver (support Win98WinMEWin2KWinXPVista) XP ver.1097.

you may need to install rar to extract it.

rar and ndiswrapper can both be found in your package manager

---

### Post by CoolDreamZ on 2008-02-11
Yep, that's exactly what I ended up doing and I can confirm it works fine and can be configured through the nm-applet (after a re-boot). Thanks :)

---

### Post by unbracketed on 2008-04-18
The Linux driver from the Realtek site would not compile against the Hardy kernel source (2.6.24).  See [this issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285") for reference.

Daniel Wills has made a patch available at:  [http://www.willdaniels.co.uk/index.php/blog/tech-stuff](http://www.willdaniels.co.uk/index.php/blog/tech-stuff)

Apparently the RTL8185 driver is missing from Hardy - not sure when this might be resolved.  My wireless is working fabulously now on my laptop using the realtek driver.

-------------------------
AMD Turion 64x2
nVidia GeForce Go 6100 (PCI-X)
RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
2GB Memory

---

### Post by FleetAdmiral74 on 2008-04-20
I did the ndiswrapper + win98 driver...seemed to work ok. This was on a fresh install of 7.04. I saw the different networks and everything...however, i then restarted because I had to install the million+ updates. Now, it does not work anymore. Still shows up, but no networks are detected...any suggestions?

---

### Post by daflame on 2008-04-28
> **unbracketed said:**
> The Linux driver from the Realtek site would not compile against the Hardy kernel source (2.6.24).  See [this issue]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285") for reference.

Daniel Wills has made a patch available at:  [http://www.willdaniels.co.uk/index.php/blog/tech-stuff](http://www.willdaniels.co.uk/index.php/blog/tech-stuff)

Apparently the RTL8185 driver is missing from Hardy - not sure when this might be resolved.  My wireless is working fabulously now on my laptop using the realtek driver.

-------------------------
AMD Turion 64x2
nVidia GeForce Go 6100 (PCI-X)
RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
2GB Memory

I am trying to use this wireless driver, but I get a kernel panic when I connect to my WEP encrypted router.

---

### Post by wdaniels on 2008-04-29
> **daflame said:**
> I am trying to use this wireless driver, but I get a kernel panic when I connect to my WEP encrypted router.

Sorry to hear that you're having trouble. However, the driver works perfectly for myself and a number of others, which means we have to figure out what's different in your case, so you will need to provide as much information as you think might be relevant about your system and what you did when you compiled/installed the driver...

A couple of specific questions to start with:

1) Did the r8180 driver work for you previously (e.g. on Gutsy)?
2) Does it work without WEP encryption?

---

### Post by thealphamale05 on 2008-05-04
AAAAAAAAAAAGGGGGGGGGGGGGG New laptop, no wireless. I have tried the linux drivers for the 8185 chip and they will never make. I tried the win 98 driver with ndiswrapper and dmesg comes back with 64 bit errors, when I use the xp64 driver dmesg comes back appearing to work but I ifconfig -a just hangs and I cannot get to the gui network manager either. Whats worse is when I reboot it with the 64 bit drivers loaded it hangs and I had to do a reinstall. I am running 8.04 64 bit version with the 8185 (not 8187) chip. Should I be running 32 bit 8.04 or what?


Jay

the hour grows later and later

---

### Post by thealphamale05 on 2008-05-04
SOLVED: Be sure to install gcc and kernel-sources before trying to install the linux driver (./makedrv) with a completely fresh install I totally forgot these crucial steps and dont want others to make the same mistake. 


Jay

---

### Post by trucker33377 on 2008-05-11
has anyone worked this one out yet? all i can add is linux puppy dingo 4.0 works with this wifi

---

