---
title: "Only some programs can access audio over an SSH session, but pavucontrol is broken"
date: 2015-01-19
forum: Multimedia Software
---

### Post by drinian on 2015-01-19
I am using Lubuntu, but I have installed Pulseaudio, so I think the setup is very similar to stock Ubuntu.

What I want to be able to do is SSH into my media system from my laptop, X tunnel my music player (Quod Libet) to my laptop, and control music playback from my laptop.

After adding my user to the 'audio' group, mplayer works, and reports that it is using the 'pulse' backend. However, playback in quodlibet fails, and opening pavucontrol also fails. However, I can use 'pactl' from the command-line.

Error from pavucontrol:

```

Connection to PulseAudio failed. Automatic retry in 5s

In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured.

This situation can also arrise when PulseAudio crashed and left stale details in the X11 Root Window. If this is the case, then PuseAudio should autospawn again, or if this is not configured you should run start-pulseaudio-x11 manually.

```

Error from start-pulseaudio-x11:
```

Connection failure: Connection refused
pa_context_connect() failed: Connection refused

```

Error from quodlibet:
```

0:00:00.812144565  2751      0x2647b50 ERROR             jackclient gstjackaudioclient.c:35:jack_log_error: Cannot connect to server socket err = No such file or directory
0:00:00.812196936  2751      0x2647b50 ERROR             jackclient gstjackaudioclient.c:35:jack_log_error: Cannot connect to server request channel
0:00:00.814303796  2751      0x2647b50 ERROR             jackclient gstjackaudioclient.c:35:jack_log_error: jack server is not running or cannot be started

```

Any ideas on what magic is necessary to make these programs happy? Thanks.

---

