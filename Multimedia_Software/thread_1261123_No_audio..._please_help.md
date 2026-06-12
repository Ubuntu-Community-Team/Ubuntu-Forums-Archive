---
title: "No audio... please help"
date: 2009-09-08
forum: Multimedia Software
---

### Post by anirudhpalla on 2009-09-08
hello friends...
i've installed ubuntu 9.04 .. i am not getting audio... 
i have installed VLC player and amarok thinking that there's a problem with the player...
but not a single player giving an audio output...but... i can c the audio symbol on top of the screen...
i think there's some problem with audio drivers/settings... 

can anyone please help me regarding this...?

:confused::confused::confused::confused:

---

### Post by NinjaNumberNine on 2009-09-08
Do you know that the speakers work?

---

### Post by NinjaNumberNine on 2009-09-08
-If there is a driver problem, which I doubt, go in [COLOR=SeaGreen]**System> Administration> Hardware Drivers**[/COLOR] and if there are any audio drivers available install them. However, it's more likely you should go in** [COLOR=RoyalBlue]System> Preferences> Sound[/COLOR]** and make sure everything is set to ALSA and your card is selected at the bottom.

Hope it helps!

---

### Post by anirudhpalla on 2009-09-08
@ninja.

yeah...bro... my speakers r working...

---

### Post by anirudhpalla on 2009-09-08
i tried the first thing... i didnt find any hardware to be installed.. and... i have set all the sound options to ALSI... but no use :(

---

### Post by NinjaNumberNine on 2009-09-08
Did you try to play the test sound in the "Sound" configuration?
If it did not play sound, go[ here]("https://answers.launchpad.net/ubuntu/+question/82028") (Try installing what Mark mentions). Or [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") (where someone else there referred to).
Tell me whatever happens. :)

---

### Post by anirudhpalla on 2009-09-09
nani@nani-desktop:~$ cat /proc/asound/cards;  sudo aptitude install gnome-alsamixer asoundconf-gtk alsa-utils flashplugin-nonfree-extrasound;  asoundconf list;  aplay -l;  sudo lshw -C sound;  ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl;  lsmod | grep snd 
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with ALC655 at irq 17
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Names of available sound cards:
ICH6
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Multimedia audio controller
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
total 0
crw-rw----+  1 root audio 116,  2 2009-09-09 11:09 timer
crw-rw----+  1 root audio 116,  3 2009-09-09 11:09 seq
crw-rw----+  1 root audio 116,  4 2009-09-09 11:09 pcmC0D4p
crw-rw----+  1 root audio 116,  5 2009-09-09 11:09 pcmC0D3c
crw-rw----+  1 root audio 116,  6 2009-09-09 11:09 pcmC0D2c
crw-rw----+  1 root audio 116,  7 2009-09-09 11:09 pcmC0D1c
crw-rw----+  1 root audio 116, 10 2009-09-09 11:09 controlC0
drwxr-xr-x   2 root root      220 2009-09-09 11:09 .
crw-rw----+  1 root audio 116,  9 2009-09-09 11:17 pcmC0D0c
crw-rw----+  1 root audio 116,  8 2009-09-09 11:36 pcmC0D0p
drwxr-xr-x  16 root root     3860 2009-09-09 11:40 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux nani-desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Intel ICH6 with ALC655 at irq 17

Audio devices:
0: Intel ICH6 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC655 rev 0
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 0e)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 0e)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
/sbin/alsactl
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm

---

### Post by anirudhpalla on 2009-09-09
didnt get the audio yet :((

---

### Post by NinjaNumberNine on 2009-09-10
Is [this]("http://ubuntuforums.org/showthread.php?t=1256050") your problem? I know it is not solved, but it will give me an idea of what you are doing. :)

---

### Post by NinjaNumberNine on 2009-09-10
Here's a good one: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
Or click [here]("http://www.google.com/search?q=no+audio+in+ubuntu+9.04&btnG=Search&hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=uZi&sa=2") for googling.

---

