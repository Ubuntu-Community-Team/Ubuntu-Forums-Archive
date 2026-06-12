---
title: "Sound stopped working after 'Update Manager' update"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by bruban on 2008-04-07
Ubuntu 7.10 i386

After an 'Update Manager' update about one week ago I found that sound ceased to work on my PC.

I have a separate install of Ubuntu 7.10 i386 on the same PC that has not been updated for several weeks. Sound works fine under this install.

Therefore my hardware is OK.

I have not been playing with my sound configuration or pc configuration at all. 

In fact the installation has been very stable for around 5 months and only used for email, browsing, multimedia playback etc.

The system update was the only thing that could have changed my PC's configuration.

I have noticed a number of recent postings with the same reported problem, but have not yet found a fix.

Does anyone have any ideas?


Hardware info below:

```
sudo lshw -C sound

  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 12
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```

---

### Post by Metaljaz on 2008-04-08
Go to System>Preferences>Sound
Try setting to auto detect and testing or to your device and testing.

---

