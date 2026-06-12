---
title: "ALSA ubuntu 6.0.6LTS SB Live problems"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Fire_Missionary on 2006-12-31
I was going through the tutorial on [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") and I went through everything... got alsa successfully configured make'd and installed. but when i go to modprobe it i get the following errs

```
fm@Black-Box:~$ sudo modprobe snd-emu10k1
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.15-26-386/kernel/sound/core/snd-rawmidi.ko': No such file or directory
FATAL: Error inserting snd_emu10k1 (/lib/modules/2.6.15-26-386/kernel/sound/pci/emu10k1/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error running install command for snd_emu10k1
fm@Black-Box:~$
```

I dont know how to get around this... i have everything successfully installed with no errors it copys the files to this location but it seems they are dissapearing.

Any help or suggestions you could provide would be most excellent. Thanks in advance.

---

