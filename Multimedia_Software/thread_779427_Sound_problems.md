---
title: "Sound problems"
date: 2008-05-02
forum: Multimedia Software
---

### Post by ubrox on 2008-05-02
Ok .. I am totally confused. I cant seem to understand the sound sub system in Ubuntu / Linux. I am a very linux person but  a totally newbie Sound. I have been using Ubuntut since 7.10 release. 

I tried PulseAudio on 7.10, had issues, removed it. After upgrade to hardy, PulseAudio is the default. Now, forzen bubble cant open the sound device to enable music and sounds. From the messages, it looks like it is using the ALSA interface. I tried modifying the asound.conf etc. No success.

Most other apps are just fine. Flash playback is fine, system sounds are fine etc. System sound preferences are set to "Autodetect".

Any help is highly appreciated.

Thanks,
Kalyan

---

### Post by ajmorris on 2008-05-03
hi there,
yes, im not a big fan of pulseaudio myself either, although for some cards it was a big improvement, others it just kills them.

What card do you have? (post the output of sudo lspci if you dont know)
Also, have you tried running sudo alsaconf in a terminal?

AJ

---

### Post by ubrox on 2008-05-03
AJ,

This is the sound card.

Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

I dont have alsaconf on the system even though alsa-utils is installed.

Here are some messages:
 pulseaudio[5901]: alsa-util.c: Unable to load mixer: No such file or directory

 pulseaudio[5901]: module-rtp-send.c: connect() failed: Network is unreachable
 pulseaudio[5901]: module.c: Failed to load  module "module-rtp-send" (argument: "source=rtp.monitor loop=1"): initialization failed.
 pulseaudio[5901]: module-gconf.c: pa_module_load() failed
 pulseaudio[5901]: module.c: Failed to load  module "module-rtp-recv" (argument: ""): initialization failed.
 pulseaudio[5901]: module-gconf.c: pa_module_load() failed
 pulseaudio[5901]: socket-server.c: socket(PF_INET6): Address family not supported by protocol
pulseaudio[5901]: socket-server.c: socket(PF_INET6): Address family not supported by protocol
 pulseaudio[5901]: module.c: Failed to open module "module-zeroconf-publish": module-zeroconf-publish.so: cannot open shared object file: No such file or directory
 pulseaudio[5901]: module-gconf.c: pa_module_load() failed
 pulseaudio[5901]: module.c: Failed to open module "module-zeroconf-discover": module-zeroconf-discover.so: cannot open shared object file: No such file or directory
 pulseaudio[5901]: module-gconf.c: pa_module_load() failed

This appears during boot, I tried enabling boot logging so I can post the whole this here, but did not work for me though. So I am just typing here
amixer: Mixer default load error: No such file or directory


Thanks,
Kalyan

---

### Post by ajmorris on 2008-05-04
that card uses the snd-hda-intel driver, what happens if you do sudo modprobe snd-hda-intel ?
(if this command doesnt work, there may be a problem with the kernel module....)

also try sudo apt-remove --purge alsa-utils && sudo apt-get install alsa-utils then run alsaconf again.

---

### Post by ubrox on 2008-05-05
The sound works fine without loading any additional modules. It looks like the ALSA interface is not working on some applications like frozen-bubble. But when I tinker with the multimedia systems selector tool and sound preferences tool, its fine. I am not sure why it is so complicated. I gues, openness and freedom to choose anything you want is not always good ... :) There should be a single interface for all purposes ... eSound, gstreamer, pulseaudio, OSS ... cant get my head wrapped around all these .. and I am an expert user with Linux since 1997. I hate to be a novice home user ... 

Its tough ..

-Kalyan

---

