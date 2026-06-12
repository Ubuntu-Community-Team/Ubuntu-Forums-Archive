---
title: "Creative SB Live! 24-bit internal... need 5.1 set up"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by Fire_Missionary on 2006-12-27
Hello to everyone. I am a newbie to Linux by any standard.

I have everything set up and working with Ubuntu, with the exception of my sound card working in 5.1. I have generally crappy speakers and the satellites only have a frequency response of 160hz-22khz so all the low range goes through the sub. But my sound card only does this when I have a low frequency bypass setup. 

I have 2 main problems with my rig.

1. I cannot get the 5.1 to work at all. It will just do stereo from the front 2 channels.

2. I cannot get a low freq. bypass set up so that I may experience the full range of sound from my music and videos.

For reference I have a Creative SoundBlaster Live! 24-bit *internal* PCI sound card. I am not at all sure what chipset it uses, as I am currently at work and do not have direct access to my computer.

I would greatly appreciate any and all help that anyone could provide. I did do a general search on these forums for about 30 minutes and did not catch anything that might help, although I'm not too familiar with the layout of these forums yet. If I have missed something, please link to it if you think it will help.

Tutorials are greatly appreciated, as I know next-to-nothing about Linux at the moment, but I do plan on learning more.

I am using the Dapper Drake Ubuntu 6.06 LTS IIRC. I will double check these when I return home this evening.

Thanks in advance for any help!

Fire_Missionary

---

### Post by budgie9 on 2006-12-27
These URLs are a good place to start. Take a look at the Ubuntu site support as well, there is simply tons of useful information related to Ubuntu.
Some time spent reading these could save you a lot of time in the future.
You may wish to download the ALSA mixer which is a little more complex, but does allow you to alter a good deal more than the installed mixer tool.
 
https://help.ubuntu.com/community/Sound[/url]
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

Do you also have an internal sound card installed? This will get in the way of the SB card.

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

---

### Post by tenjin1 on 2007-01-24
You have a SB Live! 24bit you should be using CA0106 driver and not emu10K1, that is for the Audigy.

---

