---
title: "HVR 1290 no composite video"
date: 2015-10-16
forum: Multimedia Software
---

### Post by Dukenukemx on 2015-10-16
Can't get composite video working on this card.  TVTime shows nothing.  I'm using Ubuntu 14.04 and the capture card is a Hauppauge HVR 1290.  What can I do to get this working?

This is what I see with "dmesg | grep cx23885".
```

[   77.559905] cx23885 driver version 0.0.4 loaded
[   77.560038] CORE cx23885[0]: subsystem: 0070:8551, board: Hauppauge WinTV-HVR1290 [card=26,autodetected]
[   77.885773] cx23885[0]: hauppauge eeprom: model=85721
[   78.326507] cx25840 16-0044: cx23888 A/V decoder found @ 0x88 (cx23885[0])
[   80.854866] cx25840 16-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
[   80.888637] cx23885_dvb_register() allocating 1 frontend(s)
[   80.888640] cx23885[0]: cx23885 based dvb card
[   82.271565] DVB: registering new adapter (cx23885[0])
[   82.271577] cx23885 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
[   82.271977] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   82.271983] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfd600000
[   82.667199] input: cx23885 IR (Hauppauge WinTV-HVR1290) as /devices/pci0000:00/0000:00:06.0/0000:03:00.0/rc/rc0/input12
[   82.667450] rc0: cx23885 IR (Hauppauge WinTV-HVR1290) as /devices/pci0000:00/0000:00:06.0/0000:03:00.0/rc/rc0
[   82.824744] input: MCE IR Keyboard/Mouse (cx23885) as /devices/virtual/input/input13
[   83.067612] rc rc0: lirc_dev: driver ir-lirc-codec (cx23885) registered at minor = 0
[  128.654745] cx23885 0000:03:00.0: DVB: adapter 0 frontend 0 frequency 0 out of range (54000000..858000000)

```

"dmesg | grep -i Hauppauge"
```

[   77.560038] CORE cx23885[0]: subsystem: 0070:8551, board: Hauppauge WinTV-HVR1290 [card=26,autodetected]
[   77.885761] tveeprom 14-0050: Hauppauge model 85721, rev C4F5, serial# 4031627320
[   77.885773] cx23885[0]: hauppauge eeprom: model=85721
[   82.666854] Registered IR keymap rc-hauppauge
[   82.667199] input: cx23885 IR (Hauppauge WinTV-HVR1290) as /devices/pci0000:00/0000:00:06.0/0000:03:00.0/rc/rc0/input12
[   82.667450] rc0: cx23885 IR (Hauppauge WinTV-HVR1290) as /devices/pci0000:00/0000:00:06.0/0000:03:00.0/rc/rc0

```

---

### Post by Dukenukemx on 2015-10-16
I also have a HVR 1250 that I threw in and it does find the S-Video and Composite inputs but in TVTime it shows it working for a fews seconds and then the pictures goes black.

---

### Post by Dukenukemx on 2015-10-18
I put Ubuntu Mate 15.04 on another machine to see if it was better at handling the capture cards, and no it isn't.  The HVR 1250 shows a working video on composite but after 20 seconds the screen goes black and the only way to fix it is rebooting the machine.  The HVR 1290 won't even show a working composite or S-Video input without making a /etc/modeprobe.d./cx23885.conf and putting "options cx23885 card=20" in there.  And like the HVR 1250 you would see working composite video for 20 seconds and the screen goes black, and the only fix is to reboot the machine.  Also the "card=20" is meant for the HVR 1255 and while it somewhat gets the S-Video and Composite working it stops the ATSC tuner from working.  

What the freakin hell?

---

