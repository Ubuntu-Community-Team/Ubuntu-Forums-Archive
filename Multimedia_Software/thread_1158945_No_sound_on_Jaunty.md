---
title: "No sound on Jaunty"
date: 2009-05-14
forum: Multimedia Software
---

### Post by tpask56 on 2009-05-14
I have a new computer (ASUS M51TA-AS008C) on which I have installed kubuntu 9.04.  I am very happy with it apart from the fact that the sound does not work.  I have looked through the forums and followed the instructions from other people with similar problems to no avail.

aplay -l gives me

```

**** List of PLAYBACK Hardware Devices ****
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
card 0: SB [HDA ATI SB], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I have made sure nothing is muted with alsamixer.  I have added myself as a user using 

```
sudo nano /etc/group
```and changed 
```
audio:x:
```to 

```
audio:x:root:pask
```When I run pulseaudio I get the following error

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling wasrequested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resourcelimits.
N: main.c: For enabling real-time/high-priority scheduling please acquire theappropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0 tsched=0"):initialization failed.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```Any ideas?

---

### Post by tpask56 on 2009-05-14
I have now opened /etc/modprobe.d/alsa-base.conf and added the line options snd-hda-intel model=6stack-dig which has got rid of my pulseaudio error and I can now open the volume control without getting an error.  However I can still not hear anything.  

By the way if I plug my headphones I can get sound on them.

---

