---
title: "that mic problem"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by brigit on 2007-04-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/80531](https://bugs.launchpad.net/bugs/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi I know many people have this problem, but seeing as I have gone through every post i could find about it and still no help I thought I'd post my own problem here.
If any one can help i will be so thank full, half the point of the computer is skype to talk to those at home.
I am quite a newbie at this so some things I'm not shore of,please take it easy on me.
There are some things I've come across which others haven't complained of (alsamixer and vumeter) so I've included here, maybe its a different problem.? 
I am running edgy.
My sound is working fine. 
My mic is not. All mic sound setting are as good as i can get them. 
When I have mic2 selected no sound and can't record. Mic2should be correct as its a front of box mic jack. If I select mic 2 constant loud interfirance and no sign of my voice.

when run vumeter says type 
esd at prompt
output when typing esd at promp
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'UART'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

Skype says problem with sound divice when trying to make a call, 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

if i type alsamixer into shell
alsamixer: function snd_ctl_open failed for default: No such device

soundsetting
all sound play back = alsa
sound capture = sis s17012 if anything else problems

mic is not muted and mic boost just makes it all worse

Again if any one can help I would be so thankfull

---

