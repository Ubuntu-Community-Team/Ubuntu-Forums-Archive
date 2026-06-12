---
title: "ATI Wonder Card Pro cx88"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by srwilde on 2006-09-03
Hello,

I have an ATI TV Wonder Card that I'm having problems getting to work correcty.  The composite in features work fine but when I try to use the NTSC signal I only get two channels (5 & 6) and they are in black and white and fuzzy.  I've tried unloading the cx88xx/cx8800 modules and loading the bttv modules but TVTime then says it can't find /dev/video0 (because unloading the cx88 modules removes the device).  The cx88 output below looks correct for my card.  Any ideas?

# lsmod
...
tuner                  42276  0
cx8800                 32268  0
v4l1_compat            14468  1 cx8800
cx88xx                 62368  1 cx8800
ir_common               9988  1 cx88xx
video_buf              22148  2 cx8800,cx88xx
i2c_algo_bit            9608  1 cx88xx
v4l2_common             6016  1 cx8800
btcx_risc               5128  2 cx8800,cx88xx
tveeprom               15248  1 cx88xx
videodev                9856  2 cx8800,cx88xx
...

# dmesg
...
[17179819.484000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179819.484000] CORE cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[17179819.484000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179819.708000] cx88[0]/0: found at 0000:02:03.0, rev: 5, irq: 201, latency: 32, mmio: 0xfd000000
[17179819.732000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179819.732000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179819.732000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[17179819.784000] tda9887 0-0043: chip found @ 0x86 (cx88[0])
[17179819.796000] cx88[0]/0: registered device video0 [v4l2]
[17179819.800000] cx88[0]/0: registered device vbi0
...

---

