---
title: "Pulseaudio on ubuntu server = wireless speakers HELP"
date: 2009-07-09
forum: Multimedia Software
---

### Post by meatlover on 2009-07-09
I have a laptop running ubuntu 9.04 and a headless server running ubuntu 9.04.  

I want every sound that is played on my laptop to be routed to the server instead of my laptop (we're on the same lan), so that I can plug speakers into my server and essentially have wireless speakers.  I'm not sure if mpd (Music Player Daemon) could do this.  I believe Pulse Audio can based on this link:

[http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers](http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers)

Would I have to install audio drivers on my server in order to play the music, or is something like that already pre-installed?  At the moment the server only has an ssh server installed on it.

Also, after installing pulseaudio via "apt-get pulseaudio" on my ubuntu server I get the following output for the following commands:

```
$ pulseaudio load-module module-rtp-recv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_24c5_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_24c5_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
^CE: module-gconf.c: Unable to read or parse data from client.

```

Can anyone help me get this working?

---

### Post by kerry_s on 2009-07-09
you need to install "alsa-base alsa-utils"

---

### Post by meatlover on 2009-07-09
OK I am installing those now.  How do I load modules as in the pulseaudio link I posted above, in order to make the server discoverable to the lan?  Also, how do I load the modules on the sender side?  I have padevchooser installed.

After installing and running "pulseaudio" i get the following

```
 pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_24c5_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: No such file or directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_24c5_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.


```

---

### Post by meatlover on 2009-07-09
Well, I figured out how to load the modules:

Type pacmd on the command line, then copy and paste the commands on the pulseaudio site.  The sender modules load fine, however, the receiver module wont load it just returns

```
>>> load-module module-rtp-recv
Module load failed.


```

Any idea why this is?

---

### Post by kerry_s on 2009-07-09
the alsa sound diver is loaded at boot, have you rebooted?

---

### Post by meatlover on 2009-07-09
You're right: I forgot to reboot however, now when I try to run pacmd I get

```

$ pacmd
E: pacmd.c: No PulseAudio daemon running, or not running as session daemon.

```

---

### Post by meatlover on 2009-07-09
I checked my syslog and the it said the following after loading the module with pactl instead of pacmd

```

pulseaudio[2506]: module.c: Failed to open module "module-rtp-recv": file not found

```

However, if I go to /usr/lib/pulse-0.9/modules, it is actually there.

---

### Post by meatlover on 2009-07-10
Looks like this is a confirmed bug in pulseaudio.  rtp recv isn't working right now.  Here is the launchpad information:

[http://ubuntuforums.org/showthread.php?p=7591043#post7591043](http://ubuntuforums.org/showthread.php?p=7591043#post7591043)

---

