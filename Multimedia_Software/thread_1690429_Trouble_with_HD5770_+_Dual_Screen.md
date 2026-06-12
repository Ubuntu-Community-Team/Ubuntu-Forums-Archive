---
title: "Trouble with HD5770 + Dual Screen"
date: 2011-02-18
forum: Multimedia Software
---

### Post by Evostorm on 2011-02-18
Okay, as a complete newbie to Linux, I still have to learn a lot of things. But the first thing I forcibly had to learn is how to make Ubuntu 10.04 Lucid work with my Sapphire HD5770, combined with my dual screen setting.

The standard driver supports my card, but doesn't use my card's full potential. That's why I installed the ATI catalyst (11.1, 11.2 screwed my system up).

Problem is, my PC starts in the tty1 terminal, but the desktop starts a little while after that. Which is of course strange, but I think this has something to do with it:

```
Feb 16 16:24:28 EvoPC kernel: [   52.350011] tda10048_firmware_upload: waiting for firmware upload (dvb-fe-tda10048-1.0.fw)...
Feb 16 16:24:28 EvoPC kernel: [   52.350016] saa7134 0000:05:05.0: firmware: requesting dvb-fe-tda10048-1.0.fw
Feb 16 16:24:28 EvoPC kernel: [   52.351267] tda10048_firmware_upload: Upload failed. (file not found?)
Feb 16 16:24:31 EvoPC kernel: [   55.301269] tda18271_write_regs: ERROR: idx = 0x1, len = 7, i2c_transfer returned: -5
Feb 16 16:24:31 EvoPC kernel: [   55.301273] tda18271_channel_configuration: error -5 on line 184
Feb 16 16:24:31 EvoPC kernel: [   55.301277] tda18271_set_analog_params: error -5 on line 1041
Feb 16 16:24:34 EvoPC kernel: [   58.433775] tda18271_write_regs: ERROR: idx = 0x6, len = 1, i2c_transfer returned: -5
Feb 16 16:24:36 EvoPC kernel: [   60.530019] tda18271_write_regs: ERROR: idx = 0x25, len = 1, i2c_transfer returned: -5
Feb 16 16:24:36 EvoPC kernel: [   60.530023] tda18271_channel_configuration: error -5 on line 119
Feb 16 16:24:36 EvoPC kernel: [   60.530026] tda18271_set_analog_params: error -5 on line 1041
Feb 16 16:24:36 EvoPC kernel: [   60.710019] tda18271_write_regs: ERROR: idx = 0x5, len = 1, i2c_transfer returned: -5
Feb 16 16:24:36 EvoPC kernel: [   60.710023] tda18271c2_rf_tracking_filters_correction: error -5 on line 264
Feb 16 16:24:37 EvoPC kernel: [   61.510014] tda18271_write_regs: ERROR: idx = 0x13, len = 1, i2c_transfer returned: -5
```

As I said, I'm a complete n00b at this, so I need a little help. I think there are some guys on this forum who can help me out. :D

---

