---
title: "&quot;Unknown symbol in module&quot; after installing alsa 1.0.16 from sources"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by g0nzo on 2008-03-08
Hi,

after automatic kernel update my sound card (SB Live 24 CA0106) stopped working. I've found a tutorial describing installation of alsa from sources. Here it is:
```

cd ~/alsa/alsa-driver-1.0.16
./configure
make
sudo make install
cd ..
cd alsa-lib-1.0.16
./configure
make
sudo make install
cd ..
cd alsa-utils-1.0.16
./configure
make
sudo make install
sudo alsaconf
sudo depmod -a
sudo /etc/init.d/alsasound restart

```
Everyhting went fine except the last step. Here are the error messages:
```

$ sudo /etc/init.d/alsasound restart
Shutting down sound driver: /usr/sbin/alsactl: save_state:1497: No soundcards found...
done
Starting sound driver: snd-ca0106 WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)
done
$dmesg | grep snd
[   35.582903] snd-ca0106: Model 1009 Rev 00000000 Serial 10091462
[ 3240.200838] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[ 3240.200844] snd_ac97_codec: Unknown symbol ac97_bus_type
[ 3240.211361] snd_ca0106: Unknown symbol snd_ac97_mixer
[ 3240.211407] snd_ca0106: Unknown symbol snd_ac97_bus

```
I'm quite new to Linux, so I'd really grateful for some tips.

---

### Post by g0nzo on 2008-03-08
Uhm after restarting the system and configuring & restarting alsa again I didn't get any errors and I can get at least playback working. Unfortunately recording still doesn't work like before the kernel update.

When I go to System => Preferences => Sound => Sound capture test with ALSA or CA0106 selected, I get the following error:
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

---

### Post by g0nzo on 2008-03-08
Uhm once again I managed to solve the problem myself :) I didn't have MIC selected in Gnome Volume Applet => Volume Control => Analog Source. However I had MIC selected in Sound preferences mentioned in the previous post - quite confusing. 

I'm still getting the same "pipeline" error when testing the recording in Sound preferences, but mic works correctly in Skype.

---

