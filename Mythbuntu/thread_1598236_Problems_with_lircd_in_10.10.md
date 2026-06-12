---
title: "Problems with lircd in 10.10"
date: 2010-10-16
forum: Mythbuntu
---

### Post by alien878 on 2010-10-16
It seems that lirc is now in the kernel.  How do I configure it?

Background:

After upgrading, I would get the following in syslog every time lircd started:
```
Oct 16 15:02:13 violet kernel: [  297.854291] BUG: unable to handle kernel NULL pointer dereference at (null)
Oct 16 15:02:13 violet kernel: [  297.854305] IP: [<f808df2f>] store_protocols+0x6f/0x340 [ir_core]
Oct 16 15:02:13 violet kernel: [  297.854322] *pde = 6ef34067 
Oct 16 15:02:13 violet kernel: [  297.854328] Oops: 0000 [#2] SMP 
Oct 16 15:02:13 violet kernel: [  297.854334] last sysfs file: /sys/devices/virtual/rc/rc0/protocols
Oct 16 15:02:13 violet kernel: [  297.854341] Modules linked in: nvidia(P) lirc_i2c(C) lirc_dev snd_hda_codec_nvhdmi snd_hda_codec_via rc_vp1041 ir_sony_decoder snd_hda_intel ir_jvc_decoder snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ir_rc6_decoder ir_rc5_decoder mantis ir_nec_decoder lnbp21 mb86a16 ir_core snd_timer stb6100 snd_seq_device tda10021 tda10023 stb0899 stv0299 snd asus_atk0110 dvb_core soundcore shpchp snd_page_alloc agpgart i2c_nforce2 lp parport usbhid hid r8169 ahci libahci mii
Oct 16 15:02:13 violet kernel: [  297.854414] 
Oct 16 15:02:13 violet kernel: [  297.854422] Pid: 2338, comm: lirc Tainted: P      D  C  2.6.35-22-generic #34-Ubuntu AT3N7A-I/System Product Name
Oct 16 15:02:13 violet kernel: [  297.854430] EIP: 0060:[<f808df2f>] EFLAGS: 00010246 CPU: 1
Oct 16 15:02:13 violet kernel: [  297.854439] EIP is at store_protocols+0x6f/0x340 [ir_core]
Oct 16 15:02:13 violet kernel: [  297.854445] EAX: 00000000 EBX: f247d800 ECX: 00000000 EDX: 00000000
Oct 16 15:02:13 violet kernel: [  297.854451] ESI: 00000001 EDI: 00000000 EBP: ee43ff28 ESP: ee43fefc
Oct 16 15:02:13 violet kernel: [  297.854458]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Oct 16 15:02:13 violet kernel: [  297.854464] Process lirc (pid: 2338, ti=ee43e000 task=f2426580 task.ti=ee43e000)
Oct 16 15:02:13 violet kernel: [  297.854469] Stack:
Oct 16 15:02:13 violet kernel: [  297.854473]  00000001 00000041 c0800080 00000000 00000000 010080d0 c0800a40 c0800000
Oct 16 15:02:13 violet kernel: [  297.854487] <0> f808dec0 00000005 00000005 ee43ff3c c03fc9fa 00000005 c06043ec f26548a0
Oct 16 15:02:13 violet kernel: [  297.854503] <0> ee43ff64 c026fd39 00000005 08800700 c06043ec f69db814 f247d808 f0257f80
Oct 16 15:02:13 violet kernel: [  297.854519] Call Trace:
Oct 16 15:02:13 violet kernel: [  297.854532]  [<f808dec0>] ? store_protocols+0x0/0x340 [ir_core]
Oct 16 15:02:13 violet kernel: [  297.854545]  [<c03fc9fa>] ? dev_attr_store+0x2a/0x40
Oct 16 15:02:13 violet kernel: [  297.854555]  [<c026fd39>] ? sysfs_write_file+0x99/0xf0
Oct 16 15:02:13 violet kernel: [  297.854566]  [<c02186e2>] ? vfs_write+0xa2/0x190
Oct 16 15:02:13 violet kernel: [  297.854574]  [<c026fca0>] ? sysfs_write_file+0x0/0xf0
Oct 16 15:02:13 violet kernel: [  297.854582]  [<c0218fa2>] ? sys_write+0x42/0x70
Oct 16 15:02:13 violet kernel: [  297.854592]  [<c05c9114>] ? syscall_call+0x7/0xb
Oct 16 15:02:13 violet kernel: [  297.854596] Code: f8 89 f0 e8 c4 7c 2c c8 85 c0 0f 85 dc 00 00 00 8d 46 07 31 ff 31 f6 e8 50 7d 2c c8 80 38 00 0f 85 87 01 00 00 8b 83 68 01 00 00 <8b> 10 85 d2 0f 84 87 00 00 00 8b 8b 6c 01 00 00 80 7d f0 00 8b 
Oct 16 15:02:13 violet kernel: [  297.854677] EIP: [<f808df2f>] store_protocols+0x6f/0x340 [ir_core] SS:ESP 0068:ee43fefc
Oct 16 15:02:13 violet kernel: [  297.854690] CR2: 0000000000000000
Oct 16 15:02:13 violet kernel: [  297.854696] ---[ end trace 4b6f98c430f19c78 ]---
```I managed to "fix" it by commenting out the following lines in /etc/init.d/lirc:
```
        if [ -d /sys/devices/virtual/rc ]; then
                for file in `find /sys/devices/virtual/rc/ -name protocols`; do
                        for protocol in rc5 nec rc6 jvc sony; do
                                echo "${action}${protocol}" > $file
                        done
                done
        fi
```However, this doesn't seem right.

I noticed that most configs are now setting START_LIRCD="false" in hardware.conf.  I.e. using the kernel lirc.  However, if I do this in my config, nothing happens.  I suspect it is looking somewhere else for a config.  How to I set up devices and drivers for the kernel lircd?

---

