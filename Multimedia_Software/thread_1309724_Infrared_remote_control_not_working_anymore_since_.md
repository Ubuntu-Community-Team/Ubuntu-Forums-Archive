---
title: "Infrared remote control not working anymore since Karmic beta"
date: 2009-11-01
forum: Multimedia Software
---

### Post by TaTaE on 2009-11-01
First, I would like to congratulate all the Ubuntu developers and thank them for their hard work. The results of their work are really incredible.

       Second, I want to say that I have experienced a problem: my Winfast 2000xp infrared remote control is dead since Karmic Beta.
       This is the relevant section in dmesg BEFORE when remote was working:
```

[   15.526184] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   15.526350]   alloc irq_desc for 22 on node 0
[   15.526355]   alloc kstat_irqs on node 0
[   15.526367] cx8800 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.526913] cx88[0]: subsystem: 107d:6611, board: Leadtek Winfast 2000XP Expert [card=5,autodetected], frontend(s): 0
[   15.526920] cx88[0]: TV tuner type 44, Radio tuner type -1
[   15.579573] i801_smbus 0000:00:1f.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.118760] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   16.450371] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.450375] Bluetooth: BNEP filters: protocol multicast
[   16.494154] Bridge firewalling registered
[   17.269354] All bytes are equal. It is not a TEA5767
[   17.269444] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   17.286260] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   17.294217] tda9887 1-0043: creating new instance
[   17.294226] tda9887 1-0043: tda988[5/6/7] found
[   17.347048] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=38, eeprom[0]=0x01
[   17.356798] tuner-simple 1-0060: creating new instance
[   17.356804] tuner-simple 1-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   17.360377] input: cx88 IR (Leadtek Winfast 2000XP as /devices/pci0000:00/0000:00:1e.0/0000:06:01.0/input/input7
[   17.360461] cx88[0]/0: found at 0000:06:01.0, rev: 5, irq: 22, latency: 32, mmio: 0xf8000000
[   17.360478] IRQ 22/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.360561] cx88[0]/0: registered device video0 [v4l2]
[   17.360618] cx88[0]/0: registered device vbi0
[   17.360669] cx88[0]/0: registered device radio0

```

And dmesg now shows NOTHING:

[   15.411473] type=1505 audit(1257054262.221:22): operation="profile_replace" pid=1082 name=/usr/sbin/cupsd
[   17.691880] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.908249] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   17.908446] usbcore: registered new interface driver btusb
[   17.914577] parport_pc 00:08: reported by Plug and Play ACPI
[   17.914611] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

Does anyone have this kind of problems ? Is this a feature or a bug ?

---

### Post by TaTaE on 2009-11-02
...bump (?)

---

### Post by TaTaE on 2009-11-05
bum

p

---

