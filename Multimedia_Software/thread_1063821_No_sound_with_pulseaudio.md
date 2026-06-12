---
title: "No sound with pulseaudio"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Sussch on 2009-02-08
After upgrading to Ubuntu 8.04 - Hardy Heron 2.6.24-23-generic, there is no sound.

Soundcard: IDT 92HD73C1X5

I read pulseaudio configuration tutorials and tips until I got to the point where no errors are reported, however, there is still no sound.
Actually, volume meters indicate that sound is being played.

For some reason padevchooser does not show any servers, sources or sinks - the lists are just empty.

My default.pa should be the same that came with the installation.

asound.conf and .asoundrc contain the following:```


pcm.pulse {
        type pulse
}

ctl.pulse {
        type pulse
}

pcm.!default {
        type pulse
}

ctl.!default {
        type pulse
}
```

It seems that pulseaudio is running:

```
indrek@sussch-laptop:~$ **ps aux | grep pulse**
root      6121  0.0  0.0   5676  2216 ?        S    14:05   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
indrek    6206  0.7  0.1  37856  5276 ?        S<l  14:05   1:10 /usr/bin/pulseaudio --log-target=syslog
indrek    6211  0.0  0.0   5676  2260 ?        S    14:05   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
root     12421  0.0  0.1  18440  3724 pts/0    S<l  16:14   0:00 pulseaudio
root     12423  0.0  0.0   5676  2212 pts/0    S    16:14   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
pulse    12432  0.0  0.0   8140  2732 pts/0    S<   16:14   0:00 pulseaudio --system
pulse    12433  0.0  0.0   5676  2216 pts/0    S    16:14   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
pulse    12435  0.0  0.1   6852  3964 pts/0    S    16:14   0:00 /usr/lib/libgconf2-4/gconfd-2 4
indrek   13969  0.0  0.0   3008   780 pts/0    S+   16:48   0:00 grep pulse
indrek@sussch-laptop:~$ **pulseaudio -vv**
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: pid.c: Daemon already running.
I: main.c: pa_pid_file_create() failed.

```



PulseAudio manager shows the following:
```

**Server Information:**
Default Sink: alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0
Default Source: alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0

**Modules:**
module-alsa-sink    "device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0"
module-alsa-source    "device_id=0 source_name=alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0"
module-hal-detect
module-esound-protocol-unix
module-native-protocol-unix
module-volume-restore
module-default-device-restore
module-rescue-streams
module-suspend-on-idle
module-combine
module-gconf
module-x11-publish
module-x11-xsmp

```

It seems that even the alsa sink and source modules should be loaded - why doesn't padevchooser show any of them?

With the exception of padevchooser everything seems to be working.
Well, it should report some errors if it isn't working, shouldn't it?

All suggestions are welcome,
Thank You

---

### Post by Sussch on 2009-02-08
Okay, it seems that it only works when the first headphones output is unconnected.

Something strange is going on. Well, at least it works.

Thank You

---

