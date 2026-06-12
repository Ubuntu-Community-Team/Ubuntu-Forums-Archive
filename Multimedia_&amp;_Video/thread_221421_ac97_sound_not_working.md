---
title: "ac97 sound not working"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by nismohasan on 2006-07-23
> 0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 810a
        Flags: medium devsel, IRQ 5
        I/O ports at bc00 [size=256]
        Capabilities: [c0] Power Management version 2


i'm trying to install realtek-linux-audiopack-4.04c

i've extracted it, typed "sudo ./install" let it do its thing, edited /etc/modules and added the following to the end of the file.

> alias char-major-116 snd
alias snd-card-0 snd-via82xx    
alias char-major-14 soundcore
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

rebooted, theres no sound. i try to go into alsamixer but it says "alsamixer: function snd_ctl_open failed for default: No such file or directory"

whats the problem?

---

