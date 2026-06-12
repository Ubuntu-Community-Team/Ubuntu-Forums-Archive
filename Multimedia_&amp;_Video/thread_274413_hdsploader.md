---
title: "hdsploader"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by Dr.Who on 2006-10-09
Hello,

my RME Hammerfull pcmcia /Multiface combo stopped working, hdsploader cant load while it worked some time ago. here is the output
```

hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : SiS SI7012 with ALC650F at 0xe400, irq 193
Card 1 : Syntek Semicon.     USB2.0 Video        at usb-0000:00:03.3-4, high speed
Card 2 : RME Hammerfall DSP at 0x52000000, irq 169
Upload firmware for card hw:2
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.hwdep.device'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_igetenv returned error: No such file or directory
ALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib hwdep.c:151:(snd_hwdep_open_noupdate) Unknown HwDep hw:2
Error opening hwdep device on card hw:2.
```

so what could it be? :-k

---

### Post by Dr.Who on 2006-10-09
ok, seems I got it. I messed a bit with .asoundrc to change a behaviour. Its a notebook and the builtin webcam always claims to be an audiointerface, mixing it all up. When I change to ```

# ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
#</home/herrsteiner/.asoundrc.asoundconf>

```

so it basicly does nothing, hdsloader is doing his job.

---

