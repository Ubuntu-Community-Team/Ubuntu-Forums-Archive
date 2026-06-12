---
title: "Some sound is broken (vlc, flash in firefox) for external USB audio"
date: 2008-12-22
forum: Multimedia Software
---

### Post by tnunamak on 2008-12-22
My headphone jack in my laptop is broken so I use a usb sound adapter for audio. This has worked fine for me, but when I recently reinstalled and upgrade KDE 4, only system sounds worked (I'm using 4.2 beta 2 right now, but had the same problems in 4.1). After a recent amarok update, amarok sound started working. I still cannot get sound in flash to work in firefox (or konqueror), and sound in VLC also does not work.

I kept getting messages about pulseaudio failing, so I ran 'sudo apt-get install pulseaudio' and the message went away, I presume that means that pulseaudio is working now. I thought it shipped with KDE, was I mistaken?

When I try to run "alsamixer" I get the following message:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```



By the way, I've disabled my onboard sound by blacklisting snd_hda_intel.

When I try to play sound in VLC, I get the following command-line output:

```
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[00000477] oss audio output error: cannot open audio device (/dev/dsp)
[00000477] main audio output error: couldn't find a filter for the conversion
[00000477] main audio output error: couldn't create audio output pipeline
```

When I run kmix I get

```
kmix(9037) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::SSS_USB_Headphone_Set:1"  control= "PCM:0"                                                           	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:0': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:1': " found                         	
kmix(9037) Mixer_ALSA::open: Setting m_recommendedMaster to  "PCM:0"                               	
kmix(9037) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"                             	
kmix(9037) MixerToolBox::possiblyAddMixer: mixerNums entry of added mixer is now:  1               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:2': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:3': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:4': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:5': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:6': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:7': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:8': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:9': " not found: snd_ctl_open err= No such file or directory                                                                               	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:10': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:11': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:12': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:13': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:14': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:15': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:16': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:17': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:18': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) Mixer_ALSA::openAlsaDevice: "Trying ALSA Device 'hw:19': " not found: snd_ctl_open err= No such file or directory                                                                              	
kmix(9037) MixerToolBox::initMixer: "Sound drivers supported: ALSA + OSS                           	
Sound drivers used: ALSA"                                                                          	
Total number of detected Mixers:  1                                                                	
kmix(9037) KMixerWidget::loadConfig: KMixerWidget::loadConfig()                                    	
kmix(9037) KMixerWidget::loadConfig: KMixerWidget::loadConfig() "Base"                             	
kmix(9037) KMixToolBox::loadView: KMixToolBox::loadView() grp= "View.Base"
```

Any ideas?

---

### Post by tnunamak on 2008-12-29
The following command solved my problem. I wonder if there's a way to do this from KDE?

```
asoundconf set-default-card 1
```

---

### Post by deejaybiggs on 2009-01-09
I found the answer to the VLC problem in another thread. I'm not sure if you've found it yet so I will replay anyway.

Go to tools>preferences>audio...
in the output settings select OSS from drop down....
where you see /dev/dsp 
change it to /dev/dsp1

that worked for the poster and for me after reading it.
hope this works for you as well. Good luck. :D

---

### Post by markbuntu on 2009-01-09
The easiest way to get a usb headset under control is to use the Pulse Audio Volume Control which unfortunately is not included in the Ubuntu install along with a bunch of other necessary stuff. But you can fix a lot of that by going here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

