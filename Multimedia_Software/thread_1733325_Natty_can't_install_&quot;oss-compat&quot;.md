---
title: "Natty: can't install &quot;oss-compat&quot;"
date: 2011-04-19
forum: Multimedia Software
---

### Post by Dingo_aus on 2011-04-19
I am trying to get a /dev/dsp so that I can get sound in the game ETQW.

Under Natty (11.04) when I try to install oss-compat I get:

After this operation, 61.4 kB of additional disk space will be used.
Selecting previously deselected package oss-compat.
(Reading database ... 394771 files and directories currently installed.)
Unpacking oss-compat (from .../oss-compat_0.0.4+nmu3_all.deb) ...
Setting up oss-compat (0.0.4+nmu3) ...
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module snd_seq_oss not found.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module snd_mixer_oss not found.
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Module snd_pcm_oss not found

---

### Post by cascarbj on 2011-05-30
Hello,

Try installing the linux-source package and rebuilding the kernel/modules with these options:

Device Drivers  ---> 
    <M> Sound card support  --->   
       <M>   Advanced Linux Sound Architecture  --->   
            <M>   OSS Mixer API   
            <M>   OSS PCM (digital audio) API 
            
[*]     OSS PCM (digital audio) API - Include plugin system 
            
[*]   OSS Sequencer API

---

### Post by Toz on 2011-05-30
I believe alsa-oss will also work. See: [http://ubuntuforums.org/showthread.php?t=1750994](http://ubuntuforums.org/showthread.php?t=1750994)

---

