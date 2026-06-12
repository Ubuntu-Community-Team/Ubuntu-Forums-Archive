---
title: "Setting default port for a sink in pulseaudio system-wide"
date: 2010-05-07
forum: Multimedia Software
---

### Post by Ludwik on 2010-05-07
Hi,

The default output audio port Ubuntu doesn't work on my system. It should be "Analog Mono Output/Amplifier", instead of "Analog Output/Amplifier". I can easily change that in sound preferences, just by choosing the right port in the "Output" tab, or by issuing the following command:

```
pacmd 'set-sink-port' 'alsa_output.pci-0000_00_1f.5.analog-stereo analog-output-mono;output-amplifier-on'

```

The problem is both solutions apply only to a single account, while I would like to change it system-wide, so it applies to all accounts on the system (there are more then 100 accounts - it's a set up for a school).

I'm using Ubuntu 10.04.

---

### Post by Ludwik on 2010-05-07
I've got he answer, thanks to Ford_Perfect in #pulseaudio IRC channel.

I needed to add the following line to `/etc/pulse/default.pa`:

    ```
set-sink-port alsa_output.pci-0000_00_1f.5.analog-stereo analog-output-mono;output-amplifier-on
```

This solved the problem, but for some mysterious reason also made sound muted by default, and set default volume level at a very low. So as a workaround I added the following lines to the same file:

```
    set-sink-mute alsa_output.pci-0000_00_1f.5.analog-stereo False
    set-sink-volume alsa_output.pci-0000_00_1f.5.analog-stereo 50000
```

**One more important piece of information**: to use the above instructions you need your sink name (in my case `alsa_output.pci-0000_00_1f.5.analog-stereo`) and name of your sink's ports (in my case I used `analog-output-mono;output-amplifier-on`). You can get them running `pacmd list-sinks` command - it will list all your avialiable sinks, together with their ports.

---

