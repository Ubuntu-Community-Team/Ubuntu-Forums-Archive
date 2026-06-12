---
title: "No sound in KUbuntu 14.10, only Dummy output device listed"
date: 2015-01-11
forum: Multimedia Software
---

### Post by fly66 on 2015-01-11
Fresh and new installation of Kubuntu 14.10. Same problem with some recent live dvd (ubuntu gnome 14.10 and others). This issue is not present with Ubuntu 14.04. My soundcard is Hercules "Game Theater XP 5.1".
Tried this command:

```
sudo alsa force-reload
```

output:

```
Unloading ALSA sound driver modules: snd-cs46xx snd-ac97-codec snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Loading ALSA sound driver modules: snd-cs46xx snd-ac97-codec snd-pcm snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
```

So it seems ok to me.

I tried to uninstall and reinstall with these commands:

```
sudo apt-get remove --purge alsa-base pulseaudio
```

and

```
sudo apt-get install alsa-base pulseaudio
```

This is the output of the second command:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pulseaudio-module-x11
Suggested packages:
  apmd alsa-oss oss-compat pavumeter paman pavucontrol paprefs
  pulseaudio-module-raop pulseaudio-esound-compat
The following NEW packages will be installed:
  alsa-base pulseaudio pulseaudio-module-x11
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/895 kB of archives.
After this operation, 4419 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Selecting previously unselected package alsa-base.
(Reading database ... 142700 files and directories currently installed.)
Preparing to unpack .../alsa-base_1.0.25+dfsg-0ubuntu4_all.deb ...
Unpacking alsa-base (1.0.25+dfsg-0ubuntu4) ...
Selecting previously unselected package pulseaudio.
Preparing to unpack .../pulseaudio_1%3a4.0-0ubuntu22_amd64.deb ...
Unpacking pulseaudio (1:4.0-0ubuntu22) ...
Selecting previously unselected package pulseaudio-module-x11.                  
Preparing to unpack .../pulseaudio-module-x11_1%3a4.0-0ubuntu22_amd64.deb ...   
Unpacking pulseaudio-module-x11 (1:4.0-0ubuntu22) ...                           
Processing triggers for man-db (2.7.0.2-2) ...                                  
Processing triggers for dbus (1.8.8-1ubuntu2.1) ...                             
Processing triggers for ureadahead (0.100.0-16) ...                             
ureadahead will be reprofiled on next reboot                                    
Setting up alsa-base (1.0.25+dfsg-0ubuntu4) ...                                 
Setting up pulseaudio (1:4.0-0ubuntu22) ...
Adding user pulse to group audio
update-rc.d: warning: start and stop actions are no longer supported; falling back     to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match pulseaudio         Default-Stop values (0 1 6)
Processing triggers for dbus (1.8.8-1ubuntu2.1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Setting up pulseaudio-module-x11 (1:4.0-0ubuntu22) ...
Processing triggers for libc-bin (2.19-10ubuntu2.1) ...
```

I noticed these errors:

```
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
update-rc.d: warning: stop runlevel arguments (1) do not match pulseaudio Default-Stop values (0 1 6)
```

Thanks,
Flavio

---

### Post by Yellow Pasque on 2015-01-11
The needed firmware files used to be a part of the kernel, but got moved out for legal reasons in kernel 3.14:
[https://github.com/torvalds/linux/commit/ad233a5f0f33a894f48c7d968ec207f46cbcae03](https://github.com/torvalds/linux/commit/ad233a5f0f33a894f48c7d968ec207f46cbcae03)

This should fix you (reload alsa or reboot when finished):
```
cd ~
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.28.tar.bz2
tar xjf alsa-firmware-1.0.28.tar.bz2
cd alsa-firmware-1.0.28
./configure
cd cs46xx/
make
sudo make install
```

---

### Post by fly66 on 2015-01-11
Thanks Temüjin,
first three commands ran fine. Fourth command gave an error because I don't have a compiler installed in my syst

```
flavio@PC-Test:~/alsa-firmware-1.0.28$ sudo ./configure
[sudo] password for flavio: 
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/flavio/alsa-firmware-1.0.28':
configure: error: no acceptable C compiler found in $PATH                       
See `config.log' for more details
```

Flavio

---

### Post by Yellow Pasque on 2015-01-11
```
sudo apt-get install build-essential
```

EDIT: Actually, you probably don't need a compiler. It looks like the files are already built:
```
cd ~/alsa-firmware-1.0.28/cs46xx
sudo mkdir /lib/firmware/cs46xx
sudo cp * /lib/firmware/cs46xx
```

---

### Post by fly66 on 2015-01-11
Thanks Temüjin compilation went well.
Now the command make:

```
flavio@PC-Test:~/alsa-firmware-1.0.28/cs46xx$ LANG=C make
```

gives:

```
make: Nothing to be done for 'all'.
```

---

### Post by Yellow Pasque on 2015-01-11
```
make: Nothing to be done for 'all'.
```
That's okay. Just run 'sudo make install'' and be done with it.

---

### Post by fly66 on 2015-01-11
Perfect! It works! Now the sound card works like in Ubuntu 14.04: I have problems with audio too loud and with 5.1 output but this is another story.

Thanks for your great support,

Flavio

---

### Post by Motkue_Bowles on 2015-02-17
could you please break up the commands post #2 as I should type them? somehow it's not working for me

---

### Post by peterhocking on 2015-04-15
Hi
I have this problem & am interested in trying installing the firmware, but my sound card is different.
The driver that appears to be being used is reported as snd-hda, so I assume that I wouldnt want to "make" cs46xx firmware. Which one should I use?
TIA
Peter

---

### Post by Yellow Pasque on 2015-04-15
> **peterhocking said:**
> I have this problem & am interested in trying installing the firmware, but my sound card is different. The driver that appears to be being used is reported as snd-hda

Your soundcard probably doesn't need proprietary firmware. I suggest you start a new thread and give more information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

