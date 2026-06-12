---
title: "New User with No Sound"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by ice2257 on 2007-02-28
Hell Everyone


I am very new to Ubuntu, but I love everything about it. I have one slight problem I can not get my sound to work. I keep getting this error " No volume control GStreamer plug ins and/or devices found'.

I have an onboard sound card and am running Ubuntu 6.10.

Any help would be greatly appreciated

Regards

---

### Post by renzokuken on 2007-02-28
could you post the output of 

```
lspci
```

---

### Post by ice2257 on 2007-02-28
Here is the output requested

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Tue Feb 27 09:19:47 2007 from 192.168.1.105
craigcaruso@craigcaruso-linux:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 03ea (rev a1)
00:01.0 ISA bridge: nVidia Corporation Unknown device 03e0 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 03eb (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 03f5 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 03f4 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 03f1 (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 03f2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 03f3 (rev a1)
00:05.0 Audio device: nVidia Corporation Unknown device 03f0 (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 03ec (rev a2)
00:08.0 IDE interface: nVidia Corporation Unknown device 03f6 (rev a2)
00:09.0 PCI bridge: nVidia Corporation Unknown device 03e8 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 03e9 (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation Unknown device 03d1 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

---

### Post by ice2257 on 2007-02-28
Any additional help would be greatly appreciated

Thanks

---

### Post by wesley_of_course on 2007-02-28
Wesley here ;

      'Noob myself but might try this ?

         [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

