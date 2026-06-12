---
title: "Problem compiling V4L in Feisty"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by Dirt Diver on 2007-10-21
I want to install my Hauppauge WinTV Nova-T 500 tunder card,
so I have been trying to compile v4l by following the instructions on this page. But I recieve error messages and the make stops with this error..

```
 LD [M] /home/jo/v4l-dvb/v4l/snd-bt87x.o
  CC [M] /home/jo/v4l-dvb/v4l/aci.o
/home/jo/v4l-dvb/v4l/aci.c:67:26: error: sound_config.h: No such file or directory
/home/jo/v4l-dvb/v4l/aci.c: In function 'busy_wait':
/home/jo/v4l-dvb/v4l/aci.c:160: warning: implicit declaration of function 'set_current_state'
/home/jo/v4l-dvb/v4l/aci.c:160: error: 'TASK_UNINTERRUPTIBLE' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:160: error: (Each undeclared identifier is reported only once
/home/jo/v4l-dvb/v4l/aci.c:160: error: for each function it appears in.)
/home/jo/v4l-dvb/v4l/aci.c:161: warning: implicit declaration of function 'schedule_timeout'
/home/jo/v4l-dvb/v4l/aci.c: In function 'aci_mixer_ioctl':
/home/jo/v4l-dvb/v4l/aci.c:377: error: 'SOUND_MIXER_WRITE_VOLUME' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:379: error: 'SOUND_MIXER_WRITE_CD' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:381: error: 'SOUND_MIXER_WRITE_MIC' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:383: error: 'SOUND_MIXER_WRITE_LINE' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:385: error: 'SOUND_MIXER_WRITE_SYNTH' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:387: error: 'SOUND_MIXER_WRITE_PCM' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:389: warning: implicit declaration of function 'MIXER_WRITE'
```

I'm using a clean installation of Feisty I think the kernel that it's running is 2.6.20-14-generic and the kernel from 
```
sudo apt-get install linux.source
```
is 2.6.20

What can be my problem?

---

### Post by dalejefferson on 2007-10-23
> **Dirt Diver said:**
> I want to install my Hauppauge WinTV Nova-T 500 tunder card,
so I have been trying to compile v4l by following the instructions on this page. But I recieve error messages and the make stops with this error..

```
 LD [M] /home/jo/v4l-dvb/v4l/snd-bt87x.o
  CC [M] /home/jo/v4l-dvb/v4l/aci.o
/home/jo/v4l-dvb/v4l/aci.c:67:26: error: sound_config.h: No such file or directory
/home/jo/v4l-dvb/v4l/aci.c: In function 'busy_wait':
/home/jo/v4l-dvb/v4l/aci.c:160: warning: implicit declaration of function 'set_current_state'
/home/jo/v4l-dvb/v4l/aci.c:160: error: 'TASK_UNINTERRUPTIBLE' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:160: error: (Each undeclared identifier is reported only once
/home/jo/v4l-dvb/v4l/aci.c:160: error: for each function it appears in.)
/home/jo/v4l-dvb/v4l/aci.c:161: warning: implicit declaration of function 'schedule_timeout'
/home/jo/v4l-dvb/v4l/aci.c: In function 'aci_mixer_ioctl':
/home/jo/v4l-dvb/v4l/aci.c:377: error: 'SOUND_MIXER_WRITE_VOLUME' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:379: error: 'SOUND_MIXER_WRITE_CD' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:381: error: 'SOUND_MIXER_WRITE_MIC' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:383: error: 'SOUND_MIXER_WRITE_LINE' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:385: error: 'SOUND_MIXER_WRITE_SYNTH' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:387: error: 'SOUND_MIXER_WRITE_PCM' undeclared (first use in this function)
/home/jo/v4l-dvb/v4l/aci.c:389: warning: implicit declaration of function 'MIXER_WRITE'
```

I'm using a clean installation of Feisty I think the kernel that it's running is 2.6.20-14-generic and the kernel from 
```
sudo apt-get install linux.source
```
is 2.6.20

What can be my problem?

I've just added a fix for this bug to Mythtv's wiki
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

---

