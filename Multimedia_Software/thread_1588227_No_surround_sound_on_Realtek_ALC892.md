---
title: "No surround sound on Realtek ALC892"
date: 2010-10-04
forum: Multimedia Software
---

### Post by Hideaki on 2010-10-04
I've been trying to get my surround sound(5.1) to work for the past couple of of days, followed a number of guides, but nothing seems to get it working at all. I'm connecting the speakers using 3 analogue audio cables, I have tested and they work fine under Windows. When I go into the Sound options in Ubuntu I don't see a 5.1 profile listed under the Hardware tab, only stereo(and that works fine).

The sound controller is a Realtek ALC892 built-in to my mobo(Gigabyte P55A-UD3).

Here is some info I've seen requested in other threads, I'm running 10.10 RC, but I can assure you it doesn't work under earlier versions.

```
Linux Yurippe 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

```
hideaki@Yurippe:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC892

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID 12

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID 12

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID 12

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID 12

```

Any help on this would be greatly appreciated!

---

### Post by Phosphoric on 2010-10-05
Hate to say this, but I went all round the houses on this one also.  My solution for the moment is to fit a PCI sound card, works a treat!

All the solutions that I've seen so far will break if there is a Linux header update.

I'm now waiting for Alsa sound modules that support this chipset to be officially incorporated in to Ubuntu.

---

### Post by Hideaki on 2010-10-12
That makes sense. I suppose it's just a matter of time then...

At least stereo audio works great.

---

### Post by lores on 2011-01-20
Any progress here?

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by lores on 2011-01-20
rm

---

### Post by Phosphoric on 2011-02-14
Well, I'm pleased to say I've had some success!

I went to Realtek's web site and downloaded their HD Audio driver package 5.16.  This includes the drivers for the ALC892 chipset.

I managed to untar it and get it installed eventually (don't ask me for a detailed run through, I'm not that skilled, so it must be fairly easy)

I'm now able to select a variety of configurations up to 5.1 surround sound and, after fiddling with Alsamixer in the terminal, I now have most of the functionality that I require.

I have stereo duplex plus headphones, line in and microphone. Also my front headphones and mike work on my desktop tower.

I've not been able to test surround sound as I don't have it.

The only thing outstanding for me is that when I plug headphones in to the front connection, it doesn't mute the main speakers.

Dead chuffed :D

---

### Post by blup on 2011-05-11
> **Phosphoric said:**
> Well, I'm pleased to say I've had some success!

I went to Realtek's web site and downloaded their HD Audio driver package 5.16.  This includes the drivers for the ALC892 chipset.

I managed to untar it and get it installed eventually (don't ask me for a detailed run through, I'm not that skilled, so it must be fairly easy)

I'm now able to select a variety of configurations up to 5.1 surround sound and, after fiddling with Alsamixer in the terminal, I now have most of the functionality that I require.

I have stereo duplex plus headphones, line in and microphone. Also my front headphones and mike work on my desktop tower.

I've not been able to test surround sound as I don't have it.

The only thing outstanding for me is that when I plug headphones in to the front connection, it doesn't mute the main speakers.

Dead chuffed :D
I've tried this solution and the latest HD Audio driver from Realtek screwed up my ALSA up to the point where my sound card was not recognized anymore. This happened even on a clean installation of 11.04! I had to re-install ubuntu to get my sound back, even the upgrade script that can be found on this forum didn't work. :o

---

### Post by Phosphoric on 2011-05-11
> **blup said:**
> I've tried this solution and the latest HD Audio driver from Realtek screwed up my ALSA up to the point where my sound card was not recognized anymore. This happened even on a clean installation of 11.04! I had to re-install ubuntu to get my sound back, even the upgrade script that can be found on this forum didn't work. :o

Well, I'm sorry that it dosen't work for you, I'm on 10.04 and it works perfectly. The only pain is that with each Linux Header Upgrade, I have to add it all again.  This is really p******g me off.  Why can't these modules be included after such a long time?

---

### Post by lores on 2011-05-11
Well, that's a good question, but I don't know how complex such an inclusion would be...
(Still suffering from the lack of out-of-the-box surround).

---

### Post by ericwdanielson on 2011-06-03
I was also having problems with ALC892 and ubuntu. I installed all the latest ALSA drivers and still no luck. It would detect my surround as 4 channel not 8 and there sould be no sound out of the rear speakers. Things started working after removing pulseaudio. sudo apt-get remove pulseaudio
I have great surround now...although I cant set the sound level in System->Preferences->Sound anymore...

---

### Post by lores on 2011-06-03
Well, that's hardly a "solution"...

---

### Post by Phosphoric on 2011-07-16
> **Phosphoric said:**
> Well, I'm pleased to say I've had some success!

I went to Realtek's web site and downloaded their HD Audio driver package 5.16.  This includes the drivers for the ALC892 chipset.

I managed to untar it and get it installed eventually (don't ask me for a detailed run through, I'm not that skilled, so it must be fairly easy)

I'm now able to select a variety of configurations up to 5.1 surround sound and, after fiddling with Alsamixer in the terminal, I now have most of the functionality that I require.

I have stereo duplex plus headphones, line in and microphone. Also my front headphones and mike work on my desktop tower.

I've not been able to test surround sound as I don't have it.

The only thing outstanding for me is that when I plug headphones in to the front connection, it doesn't mute the main speakers.

Dead chuffed :D

I'm getting really fed up now.  I have to go through the above procedure every bloomimg time I get an update to Linux headers ......at least once a month.:x  The wretched updates break my audio every time.  

When's this going to be sorted?

---

### Post by alpha-buntu on 2011-08-05
I have a Asus P8Z68 Mainboard with alc892 realtek, after 11.04 installation, everything is working nicely.

---

### Post by jonpday on 2011-08-21
> **blup said:**
> I've tried this solution and the latest HD Audio driver from Realtek screwed up my ALSA up to the point where my sound card was not recognized anymore. This happened even on a clean installation of 11.04! I had to re-install ubuntu to get my sound back, even the upgrade script that can be found on this forum didn't work. :o

The same has happened to me :(  When you say you "reinstalled Ubuntu" what process did you follow?  Did you lose all your custom installations and settings from before?  Thanks.

---

### Post by bbossola on 2011-11-29
> **jonpday said:**
> The same has happened to me :(  When you say you "reinstalled Ubuntu" what process did you follow?  Did you lose all your custom installations and settings from before?  Thanks.

Same here. Suggestion: DO NOT do that.

To recover, open a terminal and type
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```

See here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Jabss on 2012-07-03
I have the same issue with Ubuntu 12.04 runing on a ASRock A75M-ITX Motherboard.

I have opened a bug report [https://bugs.launchpad.net/bugs/1014897](https://bugs.launchpad.net/bugs/1014897)

So far, no news....

Let me know if you have any (good) news!

BR,
Jabss

---

