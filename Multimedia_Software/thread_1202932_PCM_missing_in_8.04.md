---
title: "PCM missing in 8.04"
date: 2009-07-02
forum: Multimedia Software
---

### Post by Ole Juul on 2009-07-02
How do I add PCM sound control to Kubuntu 8.04? There is no PCM slider or switch in alsamixer or Kmix. The hardware device is HDA Intel (ALC880).

I just upgraded to 8.04 and (first) changed from USB to onboard sound. I can get some streaming radio but there is no YouTube sound nor anything else that I have tested.

---

### Post by Ole Juul on 2009-07-04
I've now spent about 20 hours searching and reading, and I still have no idea of how one might enable PCM.

I've uninstalled and reinstalled alsa-utils numerous times. /var/lib/alsa/asound.state does not have a PCM entry, but /etc/init.d/alsa-utils does. Could it be that the sound chip doesn't support it?

asound -l returns:
```
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
aplay returns:
```
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.namehint.extended'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm_direct.c:1440:(_snd_pcm_direct_get_slave_ipc_offset) Unknown slave PCM hw:0
aplay: main:546: audio open error: No such file or directory
ole@SCO:/var/lib/alsa$
```
I would really appreciate **ANY** hints whatsoever!

---

### Post by Ole Juul on 2009-07-05
I gave up on getting the Intel/Realtek onboard audio to work and took the easy way out and intalled an SB-Live card. This gave me PCM and some other options in Alsamixer. I reinstalled the sound system (just to be on the safe side) but the situation is the same regarding which parts work. It would seem that the problem is with Kubuntu 8.04 and not with the hardware. 

From my experience so far, and judging by the response here, I don't think it will be possible for me to get sound working properly with this OS. I give up! However, knowing that some people have had (at least) limited success with sound in Linux, I will try to set up another computer for that purpose. :)

---

