---
title: "Reboot and now no sound (again)"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by joe1212 on 2008-04-09
Hi, I have a Intel ICH7 integrated audio device (hda-intel). A few weeks ago I randomly lost sound, so I followed the advice of ([https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)) and eventually got my sound to work again by manually compiling the ALSA drivers and using an old version (1.0.15). This worked great for two weeks, but now once again I booted up this morning to no sound. I tried going through the same troubleshooting process but to no avail. lspci -v detects the sound card, but aplay -l says "aplay: device_list:205: no soundcards found...". lsmod shows snd-hda-intel loaded fine.

The one clue I do have is that dmesg | grep intel shows up with "[   35.793056] hda-intel: no codecs found!". This is indicating to me that the driver does get loaded but isn't initialized correctly since it cannot find the codec chip. I have tried a multitude of settings under /etc/modprobe.d/alsa-base with options snd-hda-intel model=XXX, where XXX={generic,default,6stack,6stack-digout,5stack,5stack-digout,ref} etc. etc. However, none of these have allowed the codec chip to be found. I believe it is a SigmaTel although I could be wrong, I cannot remember well and the way I know of checking (aplay -l) doesn't work in this case.

How can I make the codec chip be visible to the driver? Thanks.

---

### Post by joe1212 on 2008-04-09
This is on 7.10 64-bit.

Some more interesting info:

epic@epiclulz:/lib/modules$ find . -name "snd-hda-intel.ko"
./2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko
./2.6.22-14-generic/updates/alsa/pci/hda/snd-hda-intel.ko
./2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
./2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

So there are actually a bunch of different kernel objects that look like they could be loaded. If I ```
rmmod snd-hda-intel
``` and then ```
root@epiclulz:/home/epiclulz# modprobe -v snd-hda-intel
insmod /lib/modules/2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko 

```
So it seems like the updates one is being loaded, but the ALSA 1.0.15/1.0.16 make install into the kernel/sound directory! I've tried fiddling around with this a bit, and replacing the ko thats actually being loaded with the one built from ALSA sources gives me a bunch of undefined symbol errors. Now the module doesn't even load but I have a better idea of whats going on: the module that its loading does not work, and the new version I've been compiling and installing all along is never getting loaded which is why I am not seeing any changes. Any advice on getting it to load the snd-hda-intel.ko from the kernel/sound directory?

---

### Post by deadgobby on 2008-04-09
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28sound%29)
Gobby

---

### Post by Yellow Pasque on 2008-04-09
These scripts seem to work well for most (but not all) people:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by joe1212 on 2008-04-09
Maybe I should have said this earlier, but those are the actual instructions I was following.

After playing around a lot with the /lib/modules folder (always create a backup first at /lib/modules-backup!) I managed to get sound working again somehow, I really don't know. Then my system started to slowly crumble. Messages about /lib/modules/volatile being read only, preventing my restricted drivers from loading, X server not starting... etc. etc.

Time for a reinstall *sigh*

---

### Post by joe1212 on 2008-04-10
I reinstalled and sound was working great for a day or so. And now its back to broken. :(

---

### Post by joe1212 on 2008-04-10
Tried  8.04 beta, broken upon install (same issue). I tried the posted scripts but still nothing. =\

---

### Post by joe1212 on 2008-04-16
Bump. I'm going to give this a couple days before going back to Windows, since I actually need my hardware to work.

Summary:

I have tried _everything_ listed on all the forums and web posts and still am not getting sound despite having it before upon install.

1. Tried recompiling the snd-hda-intel module and getting it to load
2. Played with alsa-base model=XXX
3. Messed with the BIOS to disable and enable random components of sound. Once this worked and gave me sound for a couple days by enabling on-board sound and disabling "front panel legacy audio" and "high definition front panel audio" but now even that trick does not work.

---

### Post by joe1212 on 2008-04-20
I have a STAC9227 codec. Intel 82801G ICH7, Gateway desktop.

I have experimented some more and gotten very weird behaviour: On a day in which sound was working, before I went to sleep I rebooted twice and both times sound still worked. The next morning I booted up and there was no sound. I'm not entirely sure how to explain this, unless the driver loading correctly is completely random.

I have attached the output of cat /proc/asound/card0/codec* during one of the times the driver loaded correctly, so this should be useful in debugging.

---

