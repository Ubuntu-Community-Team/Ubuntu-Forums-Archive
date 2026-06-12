---
title: "Lenovo W510 wireless not working"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by thgis05 on 2010-08-17
[FONT=Arial][SIZE=3][COLOR=#000000][FONT=Arial]Hi.

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Im not able to get wlan to work on my new Lenovo W510.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have tried:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo apt-get install linux-backports-modules-karmic-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo rmmod -f iwlagn[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo modprobe iwlagn[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]but without result[/FONT][/COLOR].

when I run dmesg | grep wifi
I get the following:
[   15.361640] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6000-3.ucode
[   15.364170] iwlagn 0000:03:00.0: iwlwifi-6000-3.ucode firmware file req failed: -2
[   15.364314] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6000-2.ucode
[   15.366928] iwlagn 0000:03:00.0: iwlwifi-6000-2.ucode firmware file req failed: -2
[   15.367132] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6000-1.ucode
[   15.369742] iwlagn 0000:03:00.0: iwlwifi-6000-1.ucode firmware file req failed: -2


I guess the problem could be the driver but I have no idea how to fix it. Any suggestions are much welcome.

I'm running ubuntu karmic koala 32 bit by the way

Regards,
Thomas
[COLOR=#000000][FONT=Arial][/FONT][/COLOR][/SIZE][/FONT]

---

