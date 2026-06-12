---
title: "jack server is not running and cannot be started- Audacity"
date: 2014-07-07
forum: Multimedia Software
---

### Post by OhHamburgers on 2014-07-07
Hello everyone!  been a while since my last post but I am completely stumped on this one.  I've been an Ubuntu user since 10.04 but I am still pretty new when it comes to to some of the configurations.

I noticed that Audacity was no longer launching so I ran it from the terminal to see where it was hanging.  here is the output:

```
User@DT:~$ audacityExpression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rearALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfeALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.sideExpression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924Expression 'alsa_snd_pcm_hw_params_set_period_size_near( pcm, hwParams, &alsaPeriodFrames, &dir )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM hdmiALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.hdmi.0:CARD=0,AES0=4,AES1=130,AES2=0,AES3=2'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM hdmiALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.modem.0:CARD=0'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.modem.0:CARD=0'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline:CARD=0,DEV=0ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.modem.0:CARD=0'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM phonelineALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.AV200.pcm.modem.0:CARD=0'ALSA lib conf.c:4248:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directoryALSA lib conf.c:4727:(snd_config_expand) Evaluate error: No such file or directoryALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM phonelineCannot connect to server socket err = No such file or directoryCannot connect to server request channeljack server is not running or cannot be started
```

I have a Xonar D1 as my soundcard.  Works really well. 

I have messed with Jack server settings and it is able to run by itself when I run it manually.  I'm not really sure where to go from here.  I'm a bit of a newbie.

Thanks!

---

### Post by OhHamburgers on 2014-07-10
Does anyone have any idea on what might be the issue?  I was really hoping not to have to reinstall to solve this :(  

If you need more information from my system I would be happy to get it for you!

---

