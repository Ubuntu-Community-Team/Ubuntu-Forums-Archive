---
title: "DSL too slow"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by hyphan on 2011-05-17
With my DSL 16.000 I only get about 500 K/s of the usual 1500 K/s after changing to a new Ubuntu 11.04 64bit based server (previous was a six year old server with Suse 9.3 - full speed). Same DSL modem (even same sync, as did not poweroff modem when changing).

MTU 1492 configured in peers-config "dsl-provider". mss-to-pmtu clamping set with iptables (no difference without).

Tried disabling IPv6 (sysctl.conf and for direct try without reboot the /proc/.. target), "ip a" shows no more inet6, but did not help.

Please note this is a DSL only question, no WLAN, just WAN pppoe connection directly on the server and also with cable-connected LAN clients (forwarding).
Can't believe such problems still exist in 2011..

Provider is T-DSL (Germany, Telekom)

Thanks!

---

### Post by ratcheer on 2011-05-17
I recommend dslreports.com. They have tons of connection tuning info and Java-based tools for seeing what is going on. I have relied on them for this kind of info for over ten years.

Tim

---

### Post by hyphan on 2011-05-19
Very strange. Reboot helped - but then back at slow (probably) after starting VDR using a USB DVB-T stick. Unloading DVB modules did not help. After another reboot OK again.

Loads of modules (see below), all loaded on booting, but only after VDR start the speed problem occurs. As if the USB bus interferes with the NIC (PCI, realtek). USB 3.0 used, H67 board. Sure, can do lots of tests now, but not now..

Why must there always be such strange effects..

```

rc_dib0700_rc5         12508  0
dvb_usb_dib0700       114060  0
dib7000p               38279  2 dvb_usb_dib0700
dib0090                32712  1 dvb_usb_dib0700
dib7000m               22889  1 dvb_usb_dib0700
dib0070                18157  2 dvb_usb_dib0700
dvb_usb                28129  1 dvb_usb_dib0700
dib8000                42669  1 dvb_usb_dib0700
dib9000                42123  1 dvb_usb_dib0700
ir_lirc_codec          12898  0
lirc_dev               19196  1 ir_lirc_codec
dvb_core              109797  4 dib7000p,dvb_usb,dib8000,dib9000
dib3000mc              23206  1 dvb_usb_dib0700
ir_sony_decoder        12549  0
ir_jvc_decoder         12546  0
ir_rc6_decoder         12546  0
ir_rc5_decoder         12546  0
ir_nec_decoder         12546  0
rc_core                26839  10 rc_dib0700_rc5,dvb_usb_dib0700,dvb_usb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
dibx000_common         14624  6 dvb_usb_dib0700,dib7000p,dib7000m,dib8000,dib9000,dib3000mc

```

---

### Post by hyphan on 2011-05-19
Oh, now slow again without starting VDR. Just waiting some minutes. Whatever happens there. Im so tired..

---

### Post by hyphan on 2011-05-19
Probably has to do with following log excerpt

```

May 20 01:46:22 flx kernel: [  116.981623] irq 18: nobody cared (try booting with the "irqpoll" option)
May 20 01:46:22 flx kernel: [  116.981630] Pid: 0, comm: kworker/0:1 Not tainted 2.6.38-8-generic #42-Ubuntu
May 20 01:46:22 flx kernel: [  116.981632] Call Trace:
May 20 01:46:22 flx kernel: [  116.981634]  <IRQ>  [<ffffffff810d511b>] ? __report_bad_irq.clone.2+0x2b/0xa0
May 20 01:46:22 flx kernel: [  116.981647]  [<ffffffff810d551a>] ? note_interrupt+0x19a/0x1e0
May 20 01:46:22 flx kernel: [  116.981651]  [<ffffffff810d640d>] ? handle_fasteoi_irq+0xdd/0x110
May 20 01:46:22 flx kernel: [  116.981655]  [<ffffffff8100e9c2>] ? handle_irq+0x22/0x40
May 20 01:46:22 flx kernel: [  116.981661]  [<ffffffff815caebd>] ? do_IRQ+0x5d/0xe0
May 20 01:46:22 flx kernel: [  116.981664]  [<ffffffff815c3213>] ? ret_from_intr+0x0/0x15
May 20 01:46:22 flx kernel: [  116.981666]  <EOI>  [<ffffffff8133685a>] ?intel_idle+0xca/0x120
May 20 01:46:22 flx kernel: [  116.981673]  [<ffffffff81336839>] ? intel_idle+0xa9/0x120
May 20 01:46:22 flx kernel: [  116.981679]  [<ffffffff814a3bda>] ? cpuidle_idle_call+0xaa/0x1b0
May 20 01:46:22 flx kernel: [  116.981685]  [<ffffffff8100a266>] ? cpu_idle+0xa6/0xf0
May 20 01:46:22 flx kernel: [  116.981689]  [<ffffffff815bc743>] ? start_secondary+0xbc/0xbe
May 20 01:46:22 flx kernel: [  116.981691] handlers:
May 20 01:46:22 flx kernel: [  116.981693] [<ffffffffa006b020>] (rtl8169_interrupt+0x0/0x250 [r8169])
May 20 01:46:22 flx kernel: [  116.981709] Disabling IRQ #18

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at e000 [size=256]
        Region 1: Memory at fe520000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at fe500000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

```The NIC used for DSL has interrupt 18 (lspci -vv), but does _not_ share this with any other device.

Will google that another time (and try that irqpoll), if anyone has an idea about this..

---

### Post by hyphan on 2011-05-28
Changed NIC from RTL (HW or driver seems to be.. not optimal..) to an Intel E1000.
Seems stable now, full speed (knock on wood).

---

