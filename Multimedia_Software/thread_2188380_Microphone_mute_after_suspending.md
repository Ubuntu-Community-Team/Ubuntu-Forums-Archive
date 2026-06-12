---
title: "Microphone mute after suspending"
date: 2013-11-16
forum: Multimedia Software
---

### Post by evgeny.oleynikov on 2013-11-16
I use ubunu 12.04 TLS desktop. Logitech c270 usb web camera is used as microphone. When I turn on the computer after suspend mode the microphone is muted. And I need every time to turn it on in pavucontrol. Can I to do it in any script? How?
Thanks.

---

### Post by evgeny.oleynikov on 2013-11-17
Ok, now I can to turn on mic from command line:
```

echo set-source-mute alsa_input.usb-046d_0825_46923FD0-02-U0x46d0x825.analog-mono 0 | pacmd

```
But how to run it on suspend resume? It's not work from /etc/pm/sleep.d/ because there it running from root

---

### Post by evgeny.oleynikov on 2013-11-17
I know, this is hook. But it's work:
In file /usr/lib/pm-utils/sleep.d/01PulseAudio
String 59, change:
set-${1}-mute ${index} yes
to:
set-${1}-mute ${index} no

---

