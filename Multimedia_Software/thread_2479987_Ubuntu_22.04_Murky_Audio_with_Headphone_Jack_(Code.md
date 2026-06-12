---
title: "Ubuntu 22.04 Murky Audio with Headphone Jack (Codec: Realtek ALC1150)"
date: 2022-10-14
forum: Multimedia Software
---

### Post by soyboy8991 on 2022-10-14
Hi there, I'm having issues on a fresh installation with my headphone audio sounding very murky and seeming to pick up only certain frequencies. 

I attempted to build pulseaudio from source and install it but may have further broken some stuff.

I came across a thread where it was suggested to run ```
journalctl -b | grep puls
``` so here is the output:

```

Oct 14 07:47:45 kodi-MS-7845 pipewire-pulse[1625]: mod.rt: Can't find xdg-portal: (null)
Oct 14 07:47:45 kodi-MS-7845 pipewire-pulse[1625]: mod.rt: found session bus but no portal
Oct 14 07:47:45 kodi-MS-7845 pipewire-pulse[1658]: 536870912
Oct 14 07:47:53 kodi-MS-7845 pipewire-pulse[1984]: mod.rt: Can't find xdg-portal: (null)
Oct 14 07:47:53 kodi-MS-7845 pipewire-pulse[1984]: mod.rt: found session bus but no portal
Oct 14 07:47:53 kodi-MS-7845 pipewire-pulse[2013]: 536870912
Oct 14 09:07:10 kodi-MS-7845 pipewire-pulse[1984]: mod.protocol-pulse: client 0x558d07f549e0: send channel:4294967295 83, error -32: Broken pipe
Oct 14 10:22:47 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Consumed 2min 10.028s CPU time.
Oct 14 10:22:57 kodi-MS-7845 pipewire-pulse[26499]: mod.rt: RTKit error: org.freedesktop.DBus.Error.InvalidArgs
Oct 14 10:22:57 kodi-MS-7845 pipewire-pulse[26499]: mod.rt: could not set nice-level to -11: Input/output error
Oct 14 10:22:58 kodi-MS-7845 pipewire-pulse[26756]: 536870912
Oct 14 10:25:07 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Main process exited, code=killed, status=7/BUS
Oct 14 10:25:07 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Failed with result 'signal'.
Oct 14 10:25:07 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Consumed 2.890s CPU time.
Oct 14 10:25:07 kodi-MS-7845 update-notifier-crash[27057]: pipewire-pulse
Oct 14 10:25:07 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Scheduled restart job, restart counter is at 1.
Oct 14 10:25:07 kodi-MS-7845 systemd[1974]: pipewire-pulse.service: Consumed 2.890s CPU time.
Oct 14 10:25:07 kodi-MS-7845 pipewire-pulse[27064]: mod.rt: RTKit error: org.freedesktop.DBus.Error.InvalidArgs
Oct 14 10:25:07 kodi-MS-7845 pipewire-pulse[27064]: mod.rt: could not set nice-level to -11: Input/output error
Oct 14 10:25:07 kodi-MS-7845 pipewire-pulse[27066]: 536870912
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] pid.c: Stale PID file, overwriting.
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] module.c: module-detect is deprecated: Please use module-udev-detect instead of module-detect!
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] module-detect.c: failed to detect any sound hardware.
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] module.c: Failed to load module "module-detect" (argument: ""): initialization failed.
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] authkey.c: Failed to open cookie file '/home/kodi/.config/pulse/cookie': No such file or directory
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] authkey.c: Failed to load authentication key '/home/kodi/.config/pulse/cookie': No such file or directory
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] authkey.c: Failed to open cookie file '/home/kodi/.pulse-cookie': No such file or directory
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] authkey.c: Failed to load authentication key '/home/kodi/.pulse-cookie': No such file or directory
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] socket-server.c: bind(): Address already in use
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] module.c: Failed to load module "module-native-protocol-unix" (argument: ""): initialization failed.
Oct 14 16:07:54 kodi-MS-7845 pulseaudio[53145]: [pulseaudio] cli-command.c: stat('/usr/local/etc/pulse/default.pa.d'): No such file or directory

```

Additionally here is the output of ```
sudo lshw -c multimedia
```

```
*-multimedia              
       description: Audio device
       product: TU116 High Definition Audio Controller
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: card1
       logical name: /dev/snd/controlC1
       logical name: /dev/snd/hwC1D0
       logical name: /dev/snd/pcmC1D10p
       logical name: /dev/snd/pcmC1D11p
       logical name: /dev/snd/pcmC1D3p
       logical name: /dev/snd/pcmC1D7p
       logical name: /dev/snd/pcmC1D8p
       logical name: /dev/snd/pcmC1D9p
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:18 memory:f7080000-f7083fff
  *-multimedia
       description: Audio device
       product: 9 Series Chipset Family HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       logical name: card0
       logical name: /dev/snd/controlC0
       logical name: /dev/snd/hwC0D0
       logical name: /dev/snd/pcmC0D0c
       logical name: /dev/snd/pcmC0D0p
       logical name: /dev/snd/pcmC0D1p
       logical name: /dev/snd/pcmC0D2c
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:36 memory:f7310000-f7313fff

```

I'm unsure how to proceed and can't find any other posts about this issue. Would like to know how to debug it further, any help is appreciated!

---

