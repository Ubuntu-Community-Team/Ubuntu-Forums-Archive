---
title: "bluetooth headset - connected, but not playing"
date: 2009-06-05
forum: Multimedia Software
---

### Post by kartoffel1337 on 2009-06-05
I have a problem with a Motorola H550 bluetooth headset, which works fine with my cell phone.

On Jaunty I connected to its headset service using blueman, but I can't get it to play any sound.
I tried several players (selecting Alsa device "bluetooth" in the configuration): Skype, aplay, etc. They all give me this error:
```
> aplay -D bluetooth test.mp3 
ALSA lib conf.c:976:(parse_value) pcm is not a string
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:12:0:Invalid argument
ALSA lib conf.c:2850:(snd_config_hook_load) /home/user/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: main:590: audio open error: Invalid argument
```

My .asoundrc looks like this:
```
pcm.bluetooth {
   type bluetooth
   device xx:xx:xx:xx:xx:xx
}
```
(xx:xx:xx:xx:xx:xx is my headset's bluetooth mac address)

---

