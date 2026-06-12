---
title: "Lirc stopped working after reboot."
date: 2011-03-09
forum: Multimedia Software
---

### Post by VoiDeR on 2011-03-09
I have a bare Ubuntu install that I use to run Xbmc. It has been working perfect for a month. I reboot it every few days. This morning I decided to reboot when it came back up my remote stopped working. I hadn't done any updates since I build the box. Unless Ubuntu does them without asking. Here is the dmesg log 

```
[  378.197085] BUG: unable to handle kernel NULL pointer dereference at 00000038
[  378.197101] IP: [<f953af51>] store_protocols+0x91/0x390 [ir_core]
[  378.197119] *pde = 6f07b067 
[  378.197126] Oops: 0000 [#1] SMP 
[  378.197132] last sysfs file: /sys/devices/virtual/rc/rc0/protocols
[  378.197139] Modules linked in: joydev hid_logitech ff_memless usbhid hid nls_utf8 udf crc_itu_t binfmt_misc parport_pc ppdev snd_hda_codec_nvhdmi snd_hda_codec_via snd_hda_intel snd_hda_codec snd_hwdep nvidia(P) snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ir_lirc_codec lirc_dev ir_sony_decoder ir_jvc_decoder rc_rc6_mce ir_rc6_decoder ir_rc5_decoder snd_timer snd_seq_device mceusb ir_nec_decoder snd psmouse ir_core soundcore lp i2c_nforce2 agpgart serio_raw snd_page_alloc shpchp parport ahci libahci forcedeth
[  378.197216] 
[  378.197224] Pid: 1957, comm: lirc Tainted: P            2.6.35-22-generic #35-Ubuntu A330ION /To Be Filled By O.E.M.
[  378.197232] EIP: 0060:[<f953af51>] EFLAGS: 00010202 CPU: 3
[  378.197241] EIP is at store_protocols+0x91/0x390 [ir_core]
[  378.197247] EAX: f6954900 EBX: f53a6600 ECX: 00000000 EDX: 00000001
[  378.197253] ESI: 00000001 EDI: 00000000 EBP: f5ca7f28 ESP: f5ca7efc
[  378.197260]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  378.197267] Process lirc (pid: 1957, ti=f5ca6000 task=f52fb2c0 task.ti=f5ca6000)
[  378.197272] Stack:
[  378.197276]  00000001 00000041 c0800080 00000000 00000000 000080d0 c0800a40 c0800001
[  378.197291] <0> f953aec0 00000005 00000005 f5ca7f3c c03fc9fa 00000005 c06043ec f4cdf540
[  378.197306] <0> f5ca7f64 c026fd39 00000005 08824688 c06043ec f2f23094 f53a6608 f6b2ba00
[  378.197323] Call Trace:
[  378.197338]  [<f953aec0>] ? store_protocols+0x0/0x390 [ir_core]
[  378.197353]  [<c03fc9fa>] ? dev_attr_store+0x2a/0x40
[  378.197363]  [<c026fd39>] ? sysfs_write_file+0x99/0xf0
[  378.197376]  [<c02186e2>] ? vfs_write+0xa2/0x190
[  378.197384]  [<c026fca0>] ? sysfs_write_file+0x0/0xf0
[  378.197392]  [<c0218fa2>] ? sys_write+0x42/0x70
[  378.197401]  [<c05c9114>] ? syscall_call+0x7/0xb
[  378.197406] Code: ff 31 f6 e8 42 ad e1 c6 80 38 00 0f 85 89 01 00 00 8b 83 68 01 00 00 8b 10 85 d2 0f 84 89 00 00 00 8b 8b 6c 01 00 00 80 7d f0 00 <8b> 49 38 89 4d e4 8b 8b 6c 01 00 00 8b 49 3c 89 4d ec 0f 84 83 
[  378.197487] EIP: [<f953af51>] store_protocols+0x91/0x390 [ir_core] SS:ESP 0068:f5ca7efc
[  378.197501] CR2: 0000000000000038
[  378.197554] ---[ end trace ad5e8dd3b79c385f ]---

```

---

### Post by laceration on 2011-03-09
```
lirc Tainted
```
Hope I am not talking out of my a**, but this seems like the kind of problem that just needs another reboot.  If that doesn't work I try reinstalling lirc.

---

### Post by VoiDeR on 2011-03-10
Lol talking out your a**! Thats funny! I tried all that. I ended up just "wiping" clean and starting over.

---

