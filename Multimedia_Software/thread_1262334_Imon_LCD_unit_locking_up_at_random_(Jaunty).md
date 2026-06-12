---
title: "Imon LCD unit locking up at random (Jaunty)"
date: 2009-09-09
forum: Multimedia Software
---

### Post by Wyldfire on 2009-09-09
Ok... first, everything works. I can boot up, and the remote and LCD display works. However, after an unspecified amount of time, the Imon device locks up, and I have to completely power down the machine to reset it. This is an ffdc device, BTW.

BTW, am using lirc v.0.8.6 and lcdproc v0.5.2 with the imon_lcd patch

As an experiment, I tried stopping the LCDd service to just use the IR, but it still locked up.

Each time, I get repeated messages like these in the syslog:

Sep  9 08:00:40 Media kernel: [52221.252208] lirc_imon: usb_rx_callback: status(-32): ignored

Also, I have added a "usleep (2000)" line to my imon_lcd.c (to give a bit of delay in the updates to the LCD unit.

Does anyone have any idea what could be causing this? I can post logs as appropriate, but I'm not sure which ones would be useful.

Thanks, 
Leif

---

### Post by Wyldfire on 2009-09-10
Bump for a second glance... anyone there?

---

### Post by Magellan on 2010-10-08
My syslog is also filling up with these messages.

---

### Post by Wyldfire on 2010-10-10
I eventually had to send my LCD unit in to be replaced... the LCD was bad.

---

