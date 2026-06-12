---
title: "ipw3945 not working"
date: 2006-05-26
forum: Networking &amp; Wireless
---

### Post by asv on 2006-05-26
I recently upgraded to RC1 with fresh install to try and get my wireless card working on my new Thinkpad X60. Dapper loads the module automatically:
```

[4294688.148000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4294688.163000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4294688.164000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.165000] ieee80211_crypt: registered algorithm 'NULL'
[4294688.166000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294688.166000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.192000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.3m
[4294688.192000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[4294688.192000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 66
[4294688.192000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4294688.192000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```
But no interface is ever created and adding eth1 in /etc/network/interfaces doesn't help either. 

Any help would be greatly appreciated..

more dmesg output 

```

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006

<snip>
[4294687.860000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[4294687.860000] Copyright (c) 1999-2005 Intel Corporation.
[4294687.860000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[4294687.860000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[4294687.912000] e1000: 0000:02:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:16:d3:21:ad:c5
[4294687.954000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[4294688.136000] Real Time Clock Driver v1.12
[4294688.148000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[4294688.163000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[4294688.164000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.165000] ieee80211_crypt: registered algorithm 'NULL'
[4294688.166000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[4294688.166000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4294688.192000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.3m
[4294688.192000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[4294688.192000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 66
[4294688.192000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[4294688.192000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[4294688.538000] irda_init()
[4294688.538000] NET: Registered protocol family 23
[4294688.674000] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[4294688.674000] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:201c]
[4294688.703000] **** SET: Misaligned resource pointer: f7cd7c42 Type 00 Len 42
[4294688.703000] **** SET: Misaligned resource pointer: f7cd7cc6 Type 07 Len 0
[4294688.703000] pnp: Device 00:09 activated.
[4294688.703000] nsc_ircc_pnp_probe() : Found cfg_base 0x000 ; firbase 0x2F8 ; irq 3 ; dma 1.
[4294688.703000] nsc-ircc, Found chip at base=0x000
[4294688.703000] nsc-ircc, driver loaded (Dag Brattli)
[4294688.703000] IrDA: Registered device irda0
[4294688.703000] nsc-ircc, Found dongle: No dongle connected
[4294688.703000] nsc_ircc_init_dongle_interface(), No dongle connected
[4294688.704000] nsc-ircc, Found chip at base=0x164e
[4294688.704000] nsc-ircc, driver loaded (Dag Brattli)
[4294688.704000] nsc_ircc_open(), can't get iobase of 0x2f8
[4294688.729000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[4294688.750000] input: TPPS/2 IBM TrackPoint as /class/input/input2
[4294688.767000] ts: Compaq touchscreen protocol output
[4294688.798000] Yenta: ISA IRQ mask 0x04b0, PCI irq 201
[4294688.798000] Socket status: 30000006
[4294688.798000] Yenta: Raising subordinate bus# of parent bus (#15) from #18 to #19
[4294688.798000] pcmcia: parent PCI bridge I/O window: 0x9000 - 0xcfff
[4294688.798000] cs: IO port probe 0x9000-0xcfff: clean.
[4294688.799000] pcmcia: parent PCI bridge Memory window: 0xe4300000 - 0xe7ffffff
[4294688.799000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe3ffffff
[4294688.815000] Unable to handle kernel NULL pointer dereference at virtual address 00000004
[4294688.815000]  printing eip:
[4294688.815000] c013112f
[4294688.815000] *pde = 00000000
[4294688.815000] Oops: 0002 [#1]
[4294688.815000] PREEMPT 
[4294688.815000] Modules linked in: tsdev irtty_sir sir_dev nsc_ircc yenta_socket rsrc_nonstatic irda pcmcia_core crc_ccitt psmouse ipw3945 ieee80211 ieee80211_crypt ieee80211_1_1_13 ieee80211_1_1_13_crypt rtc serio_raw e1000 pcspkr hw_random snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd shpchp pci_hotplug soundcore intel_agp agpgart snd_page_alloc evdev sg ext3 jbd dm_mod ide_generic ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore sd_mod ahci libata scsi_mod piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4294688.815000] CPU:    0
[4294688.815000] EIP:    0060:[<c013112f>]    Not tainted VLI
[4294688.815000] EFLAGS: 00010002   (2.6.15-23-386) 
[4294688.815000] EIP is at finish_wait+0x2f/0x70
[4294688.815000] eax: dfaa4000   ebx: 00000286   ecx: 00000000   edx: 00000000
[4294688.815000] esi: dfaa5fd8   edi: dfaa5fcc   ebp: 00000000   esp: dfaa5fbc
[4294688.815000] ds: 007b   es: 007b   ss: 0068
[4294688.815000] Process kIrDAd (pid: 3202, threadinfo=dfaa4000 task=dfa35550)
[4294688.815000] Stack: dfaa4000 00000000 00000000 f8c6f840 00000000 dfa35550 c0118940 00000000 
[4294688.815000]        00000000 f8c6f790 00000000 c0101385 f7d5bf98 00000000 00000000 cccccccc 
[4294688.815000]        cccccccc 
[4294688.815000] Call Trace:
[4294688.815000]  [<f8c6f840>] irda_thread+0xb0/0xf0 [sir_dev]
[4294688.815000]  [<c0118940>] default_wake_function+0x0/0x20
[4294688.815000]  [<f8c6f790>] irda_thread+0x0/0xf0 [sir_dev]
[4294688.815000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294688.815000] Code: d7 b8 00 e0 ff ff 21 e0 8b 00 c7 00 00 00 00 00 8d 72 0c 3b 72 0c 74 34 9c 5b fa b8 00 e0 ff ff 21 e0 ff 40 14 8b 4f 0c 8b 56 04 <89> 51 04 89 0a 89 77 0c 89 76 04 53 9d ff 48 14 8b 40 08 a8 08 
[4294688.815000]  <6>note: kIrDAd[3202] exited with preempt_count 1
[4294689.161000] cs: IO port probe 0x100-0x3af: excluding 0x1f0-0x1f7
[4294689.163000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[4294689.164000] cs: IO port probe 0x820-0x8ff: clean.
[4294689.164000] cs: IO port probe 0xc00-0xcf7: clean.
[4294689.165000] cs: IO port probe 0xa00-0xaff: clean.
[4294689.473000] ipw3945: Radio Frequency Kill Switch is On:
[4294689.473000] Kill switch must be turned off for wireless networking to work.
[4294689.753000] NET: Registered protocol family 17
[4294690.295000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[4294690.295000] sdhci: Copyright(c) Pierre Ossman
[4294690.295000] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 74
[4294690.295000] PCI: Setting latency timer of device 0000:15:00.2 to 64
[4294690.345000] sdhci: ============== REGISTER DUMP ==============
[4294690.345000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[4294690.345000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[4294690.345000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[4294690.345000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[4294690.345000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[4294690.345000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[4294690.345000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[4294690.345000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[4294690.345000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[4294690.345000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[4294690.345000] sdhci: ===========================================
[4294690.396000] mmc0: SDHCI at 0xe4301800 irq 74 DMA
[4294690.688000] e1000: eth0: e1000_watchdog_task: NIC Link is Up 100 Mbps Full Duplex
[4294690.688000] e1000: eth0: e1000_watchdog_task: 10/100 speed: disabling TSO
[4294693.385000] lp: driver loaded but no devices found
[4294693.412000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[4294693.412000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[4294693.412000] ieee1394: sbp2: Try serialize_io=0 for better performance
[4294693.499000] Adding 2396152k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1 across:2396152k
[4294693.611000] EXT3 FS on dm-0, internal journal
[4294693.770000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294693.770000] md: bitmap version 4.39
[4294695.452000] kjournald starting.  Commit interval 5 seconds
[4294695.452000] EXT3 FS on sda5, internal journal
[4294695.452000] EXT3-fs: mounted filesystem with ordered data mode.
[4294696.765000] NET: Registered protocol family 10
[4294696.765000] lo: Disabled Privacy Extensions
[4294696.766000] IPv6 over IPv4 tunneling driver
[4294697.593000] ACPI: AC Adapter [AC] (on-line)
[4294697.604000] ACPI: Battery Slot [BAT0] (battery present)
[4294697.668000] ACPI: Power Button (FF) [PWRF]
[4294697.668000] ACPI: Lid Switch [LID]
[4294697.668000] ACPI: Sleep Button (CM) [SLPB]
[4294697.748000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[4294697.748000] ibm_acpi: http://ibm-acpi.sf.net/
[4294697.751000] ibm_acpi: dock device not present
[4294697.766000] pcc_acpi: loading...
[4294697.834000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294697.834000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294701.999000] [drm] Initialized drm 1.0.1 20051102
[4294702.002000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 201
[4294702.002000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[4294703.954000] ppdev: user-space parallel port driver
[4294704.237000] apm: BIOS not found.
[4294707.351000] Non-volatile memory driver v1.2
[4294707.374000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[4294707.587000] eth0: no IPv6 routers present
[4294707.898000] Bluetooth: Core ver 2.8
[4294707.898000] NET: Registered protocol family 31
[4294707.898000] Bluetooth: HCI device and connection manager initialized
[4294707.898000] Bluetooth: HCI socket layer initialized
[4294708.016000] Bluetooth: L2CAP ver 2.8
[4294708.016000] Bluetooth: L2CAP socket layer initialized
[4294708.019000] Bluetooth: RFCOMM socket layer initialized
[4294708.019000] Bluetooth: RFCOMM TTY layer initialized
[4294708.019000] Bluetooth: RFCOMM ver 1.7
[4294724.110000] eth0: no IPv6 routers present

```

---

### Post by Miguel on 2006-05-26
Looking at this part of your output:

```

[4294689.473000] ipw3945: Radio Frequency Kill Switch is On:
[4294689.473000] Kill switch must be turned off for wireless networking to work.

```

I would suggest you to enable your wireless card via Fn+something or the hardswitch that controls it on Lenovo ThinkPads. This is the only unusual part for me of your output (I'm no expert, mind you). AFAIK, you would else get things like EE (errors) and WW (warnings).

BTW: Glad to see Napa platform support in dapper. I'll probably upgrade my laptop with Merom+Santa Rosa, so I will have chances to get Linux there.

---

### Post by asv on 2006-05-26
Whats odd if I've tried alternating the button, loading and unloading the modules, but it still shows up as radio kill switch enabled. I checked the bios and it looked fine. 


[QUOTE=Miguel]Looking at this part of your output:

```

[4294689.473000] ipw3945: Radio Frequency Kill Switch is On:
[4294689.473000] Kill switch must be turned off for wireless networking to work.

```

I would suggest you to enable your wireless card via Fn+something or the hardswitch that controls it on Lenovo ThinkPads. This is the only unusual part for me of your output (I'm no expert, mind you). AFAIK, you would else get things like EE (errors) and WW (warnings).

BTW: Glad to see Napa platform support in dapper. I'll probably upgrade my laptop with Merom+Santa Rosa, so I will have chances to get Linux there.[/QUOTE]

---

### Post by asv on 2006-05-26
From what I found on the web, the way to fix this problem is to "boot in to windows," which I never booted in to..

---

### Post by Miguel on 2006-05-27
Does it work now? I fear that if you bough a new laptop (I assume so because it is a core duo), and you have never booted into windows, you might as well have formatted the whole ntfs partition. It would [autocensored, starts with s, ends with k] to install Winblows just to operate the wireless switch. And, of course, if you leave it on you are missing out some battery life.

On a side note, there might be a way to opetarte Fn+Button things on linux. I mean, if they can make it to work in Sony Vaios,... why not on more linux-friendly thinkpads?

---

### Post by taehher on 2006-05-28
I has a similar problem on my dell inspiron,  I solved it by disabling the wireless switch in the bios, then everything worked fine, but of course you will no longer be able to turn the wireless ff to save battery life.

---

### Post by gerni on 2006-05-31
i also have a thinkpad X60 and the same problem like asv described but starting into windows does not help.
still searching for a solution...

---

### Post by ariel on 2006-06-04
Any update on this one? my problem on an x60s is a bit different, lsmod  and dmesg list the ipw3945, but i don't see the "kill switch activated" message. The wifi led stays off all the time.

What is weidest is that wireless worked in the first boot of my fresh 6.06/final install. 
Then I changed to the SMP kernel, and voila, the wifi interface disappeared. iwconfig does not show any wireless extension at all. Any hint would be greatly appreciated !

UPDATE: just tried the 386 (non smp) kernel: wireless works... there must a bug in the 686 (smp) kernel :-(
 
Thanks
Ari

---

### Post by plaz42 on 2006-06-04
I have an Acer Aspire 5670, with the Intel IPW3945 card.  I recently had the same problem after attempting to reinstall my 3945 driver.  The only way I was able to disable the kill switch was to toggle the switch once while the laptop was booting, before any linux network configuration had occured.  This fixed the problem entirely.

---

### Post by Ipsissimus on 2006-06-05
[QUOTE=ariel]What is weidest is that wireless worked in the first boot of my fresh 6.06/final install. 
Then I changed to the SMP kernel, and voila, the wifi interface disappeared. iwconfig does not show any wireless extension at all. Any hint would be greatly appreciated !

UPDATE: just tried the 386 (non smp) kernel: wireless works... there must a bug in the 686 (smp) kernel :-(
 
Thanks
Ari[/QUOTE]

  Yes, if you look in your sbin folder you will find the /sbin/ipw3945d-2.6.15-23-386 driver for the card, but nothing for the SMP 686 kernel.  I was hoping the official Dapper release would take care of this, sadly the SMP kernel does not seem very supported. 
   As of yet I've not found a solution.  Think I'll just have to compile my own SMP kernel driver.

---

### Post by Ipsissimus on 2006-06-05
Well, I've finally fixed my ipw3945 SMP problem. I noticed that only the linux-image-2.6.15-23-686 package was installed by default. I simply installed the **linux-restricted-modiles-2.6.15-23-686** and I finally had the file /sbin/ipw3945d-2.6.15-23-686 and my SMP wireless works now.

Hope this fixes your problems as well.

---

### Post by ariel on 2006-06-05
[quote=Ipsissimus]Well, I've finally fixed my ipw3945 SMP problem. I noticed that only the linux-image-2.6.15-23-686 package was installed by default. I simply installed the **linux-restricted-modiles-2.6.15-23-686** and I finally had the file /sbin/ipw3945d-2.6.15-23-686 and my SMP wireless works now.

Hope this fixes your problems as well.[/quote]

Yes, that was it :-)

---

### Post by sadrak on 2006-09-26
thats it! just liddle typo: modiles => modules :)

linux-restricted-modules-`uname -r`

and now FN + F2 works! WLAN WORKS! WPA WORKS! i am so happy ... :)

---

### Post by cphil on 2007-07-20
Same problem here on an ASUS A7J. Tried to reboot on Windows (still got one), wireless works fine. No option to kill the switch in the BIOS, switching off/on at startup doesn't work. 

Any idea ?

---

