---
title: "Who knows how to install/compile linuxsampler in Feisty"
date: 2007-05-18
forum: Multimedia Production
---

### Post by miguelinux on 2007-05-18
I,ve tried to compile Linuxsampler from sources and after some problems I did it, including Qsampler and its libraries but when I start Qsampler I get this error:

qsampler: error while loading shared libraries: liblscp.so.0: cannot open shared object file: No such file or directory

What Can I do? Thanks

---

### Post by akudewan on 2007-05-18
Its a missing dependency. Try this:
```

sudo apt-get install liblscp liblscp-dev

```

---

### Post by miguelinux on 2007-05-20
Actually I had installed Llinuxsampler from edgy and the rest (Qsampler and dependencies) from Feisty.

Qsampler start linuxsampler well:

23:48:15.624 Client connecting...
23:48:15.627 Server is starting...
23:48:15.627 linuxsampler
23:48:15.636 Server was started with PID=6749.
lscp_client_create: cmd: connect: ConexiÃ³n rechazada
LinuxSampler 0.3.3
Copyright (C) 2003, 2004 by Benno Senoner and Christian Schoenebeck
Copyright (C) 2005 Christian Schoenebeck
Detected features: disabled at compile time
Creating Sampler...OK
Registered MIDI input drivers: ALSA
Registered audio output drivers: ALSA
Starting LSCP network server (0.0.0.0:8888)...OK
23:48:18.853 Client connecting...
23:48:18.856 Client receive timeout is set to 1000 msec.
23:48:18.859 Client connected.
23:48:18.863 New session: "Untitled1".
LinuxSampler initialization completed. :-)
LSCPServer: Client connection established on socket:4.
LSCPServer: Client connection established on socket:6.

But when I try configure audio or midi devices, can't find any card:

23:51:04.517 New Audio device lscp_get_audio_driver_info: AudioOutputDeviceAlsa (errno=0)
ALSA lib control.c:785:(snd_ctl_open_conf) symbol _snd_ctl_hw_open is not defined inside (null)
AudioOutputDeviceAlsa: Cannot open sound control for card 0 - No such device or address
AudioOutputDeviceAlsa: Can't find any card

After search in the net it seems a problem with alsa libs, but I don't find any solution.
Somebody knows the answer? Thanks all.

---

