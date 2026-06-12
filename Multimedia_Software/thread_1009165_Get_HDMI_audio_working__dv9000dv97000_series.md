---
title: "Get HDMI audio working  dv9000/dv97000 series"
date: 2008-12-12
forum: Multimedia Software
---

### Post by hoffman462 on 2008-12-12
Friends,

I am trying to get my HDMI output on my laptop to also transmit audio to the TV which it is connected to (currently video works fine).  I have a dv9700 series laptop from HP (which should function similarly to the dv9000 series laptops from the reading that I have been doing).

I am currently running NVIDIA Driver Version 177.80

Here is uname -a
```

uname -a
Linux TALEOS 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

And aplay -l lists:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Right here, I see my first problem (I think), because I don't have a digital device, listed (where the HDMI output should connect).

According to this forum, [http://forums.fedoraforum.org/showthread.php?t=185519](http://forums.fedoraforum.org/showthread.php?t=185519), I tried adding some lines on the bottom of my **/etc/modprobe.d/alsa-base** file.

This *sounded* to good to be true, and I really didn't think that it would do anything.  Of course, it didn't.  
I placed this line at the bottom, and the restarted.  I didn't get any audio on the TV from my HDMI connection.  Also, I noticed that aplay -l didn't' change its output.

```

options snd-hda-intel model=laptop

```


So, I looked towards the Ubuntu forums looking for more specific advise.  I saw some information on how to upgrade Alsa.  Now my capabilities are far from a power user, or a system admin.  So I followed this tutorial: 

[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(hda))

But it fails for some reason and I end up with: 
```

sudo ./configure --with-cards=hda-intel

...
...
...
checking for which soundcards to compile driver for... configure: error: Unknown soundcard hda-intel

```

I know that this works -- with audio in the windows world, its documented here:  [http://forum.notebookreview.com/showthread.php?p=3559314](http://forum.notebookreview.com/showthread.php?p=3559314)) 


Something else that is worth noting, in this Ubunut bug report, I think that this is interesting:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/148097](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/148097)

Someone comments: 
> 
Open the mixer ans select "Realtek ALC833 (OSS Mixer)" as the device.
Edit / Preferences. Check "Digital-1" and select Close.
In the Recording tab, ajust the volume of the Digital-1 to the preferred level.

Your HDMI audio should now work. My understanding is that the "SPDIF" digital output is the one that's used under HDMI, but this output gets classified in the recording / input class (bug?).


Ok, so on my panel, I have a sound widget (well it looks like a sound widget).  And when I right click on this, I am able to select the mixer.  I follow these steps, and I do have a Realtek choice.  However, I do not have ALC833 by Realtek.   I have Realtek ALC268.  This only offers the options of Volume, PCM-2 and In Gain.

So right now. Thats my diagnostics.  

Thanks for any tips.  help is greatly appreciated in getting the audio working

---

