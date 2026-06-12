---
title: "Sound Driver Installation!"
date: 2011-11-27
forum: Multimedia Software
---

### Post by programmer.robin on 2011-11-27
Hello,
I just installed ubuntu 11.10 and i'm completely new to this.
I have got a problem of sound.The sound card is Realtek AC'97. There is no sound at all.
I downloaded sound driver from realtek website.
It is not installed and how can i get my sound to work.

Please help me.
I'm in trouble :confused: :confused: :confused:

Thanks

---

### Post by 2F4U on 2011-11-27
Can you post the output of 

```
lspci | grep Audio sudo lshw -c multimedia
```

The AC97 driver should be included in Ubuntu.

---

### Post by programmer.robin on 2011-11-29
Thanks for response,

Output of lspci | grep Audio


robin@Unknown-OEM:~$ lspci | grep Audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)

AND Output of sudo lshw -c multimedia


robin@Unknown-OEM:~$ sudo lshw -c multimedia
[sudo] password for robin: 
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801G (ICH7 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: ioport:f000(size=256) ioport:fa00(size=64) memory:fdffe000-fdffe1ff memory:fdffd000-fdffd0ff



And if i do all together -> lspci | grep Audio sudo lshw -c multimedia

output is :


robin@Unknown-OEM:~$ lspci | grep Audio sudo lshw -c multimedia
grep: sudo: No such file or directory
grep: lshw: No such file or directory
grep: multimedia: No such file or directory

:confused::confused::confused:


And, I hope you'll reply soon:P

---

