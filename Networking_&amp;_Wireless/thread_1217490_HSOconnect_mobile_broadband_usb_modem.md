---
title: "HSOconnect mobile broadband usb modem"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by Elvis99 on 2009-07-19
Hi there,

When I run HSOconnect I get the following:

[I]
zeppelin39@dell-desktop:~$ HSOconnect
Path to hsolinkcontrol: /usr/bin/hsolinkcontrol
Mode 36333
in ui.run()
Serial<id=0x8a443cc, open=True>(port='/dev/ttyHS1', baudrate=115200, bytesize=8, parity='N', stopbits=1, timeout=1, xonxoff=0, rtscts=0)
checkpin() returned: ERROR
Missing SIM or Erro[/I]r

I have the rights on the device:

[I]zeppelin39@dell-desktop:~$ ls -al /dev/ttyHS1
crwxrwxrwx 1 zeppelin39 dialout 250, 1 2009-07-19 17:55 /dev/ttyHS1[/I]

The GUI shows up for a few seconds and when the error occurs it quits with this error message:
"Check the SIM and try again."

The stick works perfectly under XP, there is no PIN required.

I am running Ubuntu 9.04 and hsoconnect 1.2.18

Thanks a lot in advance!

---

