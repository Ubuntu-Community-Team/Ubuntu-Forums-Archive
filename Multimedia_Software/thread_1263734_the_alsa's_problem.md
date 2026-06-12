---
title: "the alsa's problem"
date: 2009-09-11
forum: Multimedia Software
---

### Post by fanglinyong on 2009-09-11
hello,everybody:
  today, i installed the new kernel 2.6.31 ,but after i reboot my pc ,i found that my pc not play sound in the new kernel,i used the code like this:```
lspci -v 
```,and the terminal output this information:
```
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 0080
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    I/O ports at d800 [size=256]
    I/O ports at dc00 [size=128]
    Memory at ee004000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

```can any one help me ,what should i do ,and the pc will play sound again?

---

### Post by instantkarma on 2009-09-11
Did you try ```
alsamixer
```?

maybe play around with the controls...

---

### Post by fanglinyong on 2009-09-11
when i exce the code,the terminal said 
```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

---

### Post by kotnik on 2009-09-11
If you compiled your kernel yourself, you'd have to do it again, this time paying attention to audio subsystem.

---

### Post by fanglinyong on 2009-09-11
without rebuild the kernel ,no way to resolved  the problem?

---

### Post by fanglinyong on 2009-09-13
ok, i download the deb packages from kernel.org!and found that the sound card's prolem had been solved!
at last , thanks everyone!

---

