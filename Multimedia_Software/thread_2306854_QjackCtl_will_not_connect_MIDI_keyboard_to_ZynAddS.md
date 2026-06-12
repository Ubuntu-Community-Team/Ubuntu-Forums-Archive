---
title: "QjackCtl will not connect MIDI keyboard to ZynAddSubfx"
date: 2015-12-19
forum: Multimedia Software
---

### Post by Elwro on 2015-12-19
I have an Impact LX 25 MIDI keyboard. It's working nicely under Windows, and everything seems to be fine hardware-wise. But in Linux I have the most basic problem: connecting it to a synthesizer. My system is Ubuntu 14.04. Here are my steps:

1. Run QjackCtl.
2. Run ZynAddSubfx.
3. In the 'Audio' tab of QjackCtl, connect 'zynaddsubfx' to 'system' : now when I press the little keys on the screen of the synth, sounds play.
4. Check the 'MIDI' tab of QjackCtl. Only 'system' in both 'readable clients' and 'writable clients'.
5. Check the 'ALSA'  tab of QjackCtl. Notice '24:IMPACT LX25' on the 'readable clients' list [why here and not MIDI?] and 130:ZynAddSubfx on the 'writable clients' list. Unfortunately, no connection is possible. I press both items, left click on 'Connect' and nothing happens.

In contrast, when I run 'vkeybd', '131"Virtual Keyboard' appears in the 'readable clients' list in 'ALSA' tab of QjackCtl and can be connected with no problems to ZynAddSubfx.

What am I doing wrong?

edit: Running
```

lsusb
amidi -l
```

produces the following:

```
leszek@leszek-MS-7758:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 001 Device 005: ID 09da:c10a A4 Tech Co., Ltd 
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2467:2012  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
leszek@leszek-MS-7758:~$ amidi -l
Dir Device    Name
IO  hw:2,0,0  IMPACT LX25 MIDI 1
I   hw:2,0,1  IMPACT LX25 MIDI 2
```

Also, each click on 'Connect' in QjackCtl produces the message "ALSA connection change". [But nothing seems to happen.]

---

