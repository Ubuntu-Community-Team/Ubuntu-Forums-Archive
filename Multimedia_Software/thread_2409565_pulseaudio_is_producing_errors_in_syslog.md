---
title: "pulseaudio is producing errors in syslog"
date: 2019-01-04
forum: Multimedia Software
---

### Post by artist-wavenet on 2019-01-04
To get audio working I find that every time I boot the computer I have to execute the command:

```
pulseaudio --start
```
While seeking ways to get this started automatically at boot time I examined the syslog file after a fresh reboot and before executing the above command. What I see is:

```

Jan  4 04:57:59 ubuntu indicator-sound[1818]: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files
Jan  4 04:57:59 ubuntu pulseaudio.pulseaudio[1162]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
Jan  4 04:57:59 ubuntu pulseaudio.pulseaudio[1162]: W: [pulseaudio] protocol-native.c: Denied access to client with invalid authentication data.
Jan  4 04:58:01 ubuntu indicator-sound[1818]: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files

```

It appears there is already an instance of pulseaudio running that cannot do anything.

In the error messages is pulseaudio the client, or is it the application that tries to play audio the client?

The error messages also indicate it is expecting the name org.PulseAudio1 in a .service file. What needs to be done to satisfy this?

The OS is Ubuntu 18.04.

---

### Post by wildmanne39 on 2019-01-04
*Thread moved to **Multimedia Software for a more appropriate fit**.*

---

