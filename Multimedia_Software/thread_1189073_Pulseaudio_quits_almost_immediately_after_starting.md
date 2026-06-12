---
title: "Pulseaudio quits almost immediately after starting"
date: 2009-06-16
forum: Multimedia Software
---

### Post by Forlornity on 2009-06-16
I'm running Mint with the updated pulseaudio packages from [this page]("http://webupd8.blogspot.com/2009/05/how-to-install-latest-pulseaudio-0915.html"), I updated to these packages as an attempt to fix the issue I'm running into but to no avail:
Prior to updating to 0.9.15 I would get these messages after running ```
$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Soft CPU time limit exhausted, terminating.
E: cpulimit.c: Received request to terminate due to CPU overload.

```
Although I doubt it's related to the matter at hand, I AM in the group pulse-rt.
After updating I assume some error messages are being suppressed as I get this output:
```
Soft CPU time limit exhausted, terminating.
E: cpulimit.c: Received request to terminate due to CPU overload.

```
Although I find this in /var/user.log:
```
Jun 14 20:00:29 mintilith pulseaudio[5419]: module-rtp-send.c: Failed to push chunk into memblockq.
Jun 14 20:00:30 mintilith last message repeated 90 times
Jun 14 20:01:58 mintilith last message repeated 7 times
Jun 14 20:04:22 mintilith pulseaudio[5419]: module-rtp-send.c: Failed to push chunk into memblockq.
Jun 14 20:04:22 mintilith last message repeated 60 times
Jun 14 20:05:14 mintilith pulseaudio[5419]: module-rescue-streams.c: Failed to move sink input 0 "pulseaudio" to alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.
Jun 14 20:05:25 mintilith pulseaudio[6747]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 14 20:05:25 mintilith pulseaudio[6747]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 14 20:07:47 mintilith pulseaudio[6747]: module-rtp-send.c: Failed to push chunk into memblockq.
Jun 14 20:07:47 mintilith last message repeated 340 times
Jun 14 20:07:48 mintilith pulseaudio[6747]: module-tunnel.c: Failed to connect to server '[fe80::21e:8cff:febe:7fb]:4713'
Jun 14 20:07:48 mintilith pulseaudio[6747]: module.c: Failed to load  module "module-tunnel-sink" (argument: "server=[fe80::21e:8cff:febe:7fb]:4713 sink=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 format=s16le channels=2 rate=44100 sink_name=tunnel.monolith.local.alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 channel_map=front-left,front-right"): initialization failed.
Jun 14 20:07:58 mintilith pulseaudio[6747]: cpulimit.c: Received request to terminate due to CPU overload.
Jun 14 20:07:58 mintilith pulseaudio[6747]: module-rescue-streams.c: Failed to move sink input 0 "pulseaudio" to alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.

```
I've deleted all the configuration files I could find, purged and re-installed pulseaudio and obviously upgraded to a more recent version.
I have no idea why this is happening but it's rather annoying indeed as this machine is my media machine.
Thanks, Forlornity

---

### Post by markbuntu on 2009-06-16
root should also be a member of pulse-rt. Yourself and root should also be members of pulse and pulse-access so check that.

You should try turning off the rtp stuff in Pulse Audio Preferences and Simultaneous Output and see of that helps.

---

### Post by Forlornity on 2009-06-16
Is the RTP stuff necessary to allow other machines to output to this machine?
I'm hoping to use it as a sound server for my laptop while at home so I don't have to go through unplugging all my equipment etc.

Both root and I are in all three groups.

In case it's relevant, the hardware is Nvidia CK804.

---

### Post by Forlornity on 2009-06-16
I can make it work:
It only crashes when I enable module-zeroconfig-publish by checking "Allow other machines on the LAN to discover local sound devices" in paprefs.
This isn't a particularly nice fix as I would quite like to have that enabled but you can't win 'em all I suppose.
If anyone comes up with anything I'm still trying to fix it but for now I'll have to put up with it.

---

