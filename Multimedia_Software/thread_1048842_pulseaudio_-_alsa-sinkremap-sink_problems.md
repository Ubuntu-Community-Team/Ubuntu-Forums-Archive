---
title: "pulseaudio - alsa-sink/remap-sink problems"
date: 2009-01-23
forum: Multimedia Software
---

### Post by Dr. Kylstein on 2009-01-23
I'm trying to split my surround sound card into multiple virtual stereo cards. I've entered the following in default.pa:
```

load-module module-alsa-sink sink_name=surround device=hw:0,0 channels=8 channel_map=front-left,front-right,back-left,back-right,center,subwoofer,aux0,aux1
load-module module-remap-sink sink_name=v_stereo master=surround channels=2 master_channel_map=aux0,aux1 channel_map=front-left,front-right

```
But I get the following errors:
> 
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
E: module-alsa-sink.c: Failed to parse sample specification and channel map
E: module.c: Failed to load  module "module-alsa-sink" (argument: "sink_name=surround device=hw:0 channels=8 channel_map=front-left,front-right,back-left,back-right,center,subwoofer,aux0,aux1"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.


Also, why doesn't pulseaudio start automatically?

Edit: I found out about the pre-defined channel names. I've changed to:
```

load-module module-alsa-sink sink_name=surround device=hw:0,0 channels=8 channel_map=front-left,front-right,rear-left,rear-right,center,lfe,aux0,aux1
load-module module-remap-sink sink_name=v_stereo master=surround channels=2 master_channel_map=aux0,aux1 channel_map=left,right

```
but I still get the same errors.

Edit: Nevermind, I fixed it. I loaded module-cli and copied the parameters autoload was using into my manual configuration.

---

