---
title: "Need RT2870sta.ko file for WUSB600N v1"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by tegskywalker on 2011-01-12
Ran into an issue with the driver and when I try to make and make-install under Linux Mint 10 (Ubuntu 10.10), I get errors. If anyone has a RT2870sta.ko file to download, then that would be great so I can get this WUSB600N v1 up and going.

---

### Post by PatchesTheCaveman on 2011-01-12
Some modifications are needed to make that driver compile:
[http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/](http://www.smachado.com/2010/11/how-to-make-ralink-rt2870-driver-work-on-ubuntu-10-10/)

Unfortunately, we can't just upload the rt2870sta.ko file, as the compiling process is target to the specific conditions of your computer (e.g. architecture, kernel version, etc.)

---

### Post by tegskywalker on 2011-01-12
Thanks for the help in building it. There is a rt2870sta.ko file in /kernel/drivers/staging/rt2870/ to be used.

I did run into another problem though. If I boot into Windows XP with the USB device in the same USB slot, Windows detects it and I'm able to get online as usual.

But with the USB drive in the same slot, I do not see my wireless networks in NetworkManager and just see the options for the wired ethernet ports.

Does this mean the driver isn't loading or the device isn't getting recognized? If either or both are the case, how can I resolve this on boot?

---

### Post by PatchesTheCaveman on 2011-01-12
Run this command:
```
lsmod
```

Copy and paste what appears.  That will tell me whether the driver you just built is loaded and if some old drivers we need to get rid of are loaded.

---

### Post by tegskywalker on 2011-01-12
After typing lsmod in terminal:

```

Module                  Size  Used by
binfmt_misc             6599  1 
dm_crypt               11385  0 
snd_wavefront          33066  0 
snd_intel8x0           25632  2 
snd_cs4236             25734  0 
snd_ac97_codec         99227  1 snd_intel8x0
snd_wss_lib            22074  2 snd_wavefront,snd_cs4236
ac97_bus                1014  1 snd_ac97_codec
snd_opl3_lib            8850  2 snd_wavefront,snd_cs4236
snd_hwdep               5040  2 snd_wavefront,snd_opl3_lib
snd_pcm                71475  4 snd_cs4236,snd_intel8x0,snd_wss_lib,snd_ac97_codec
snd_mpu401              5123  0 
snd_mpu401_uart         5661  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi            4588  0 
snd_rawmidi            17783  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ppdev                   5556  0 
snd_timer              19067  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device          5744  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
ns558                   3068  0 
gameport                9327  2 ns558
ndiswrapper           224162  1 
parport_pc             26058  1 
psmouse                59033  0 
snd                    49006  18 snd_wavefront,snd_cs4236,snd_intel8x0,snd_wss_lib,snd_ac97_codec,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
shpchp                 29886  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_intel8x0,snd_wss_lib,snd_pcm
lp                      7342  0 
i2c_nforce2             5179  0 
parport                31492  3 ppdev,parport_pc,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
radeon                825934  3 
usb_storage            40172  0 
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168054  5 radeon,ttm,drm_kms_helper
firewire_ohci          21106  0 
3c59x                  32011  0 
nvidia_agp              4495  1 
i2c_algo_bit            5168  1 radeon
firewire_core          46643  1 firewire_ohci
pata_amd                8746  2 
mii                     4425  1 3c59x
forcedeth              49433  0 
crc_itu_t               1383  1 firewire_core
agpgart                32011  3 ttm,drm,nvidia_agp

```

---

### Post by PatchesTheCaveman on 2011-01-12
Okay, it's not loading at all.  Try running:
```
sudo modprobe rt2870sta
```

If that fixes it, run this command to make that fix permanent:
```
sudo bash -c "modprobe rt2870sta >> /etc/modules"
```

---

### Post by tegskywalker on 2011-01-12
> **PatchesTheCaveman said:**
> Okay, it's not loading at all.  Try running:
```
sudo modprobe rt2870sta
```

If that fixes it, run this command to make that fix permanent:
```
sudo bash -c "modprobe rt2870sta >> /etc/modules"
```

If I do sudo modprobe rt2870sta and hit enter, it asks for my password and after I provide it, it stays there. I wait about 10 minutes and try to close terminal but it says there is a process going on. Plus I never get the option to type in a new command probably showing the one I just did is not finished.

I waited 10 minutes then 20 minutes and nothing. The green light on the USB adapter never lit up once and I do not see wireless options in network manager.

---

### Post by PatchesTheCaveman on 2011-01-13
That's *no bueno*.  Please run that first command again, wait a minute, and then open another terminal and run:
```
dmesg | tail
```

You can then kill the first terminal.

Do not run the second command yet!  Otherwise your computer might freeze like that on boot.

---

### Post by tegskywalker on 2011-01-13
Thanks for your help. Before I got your response, I actually booted off of a LiveCD to see if there was a bigger issue at hand and interestingly enough, I booted off of the Linux Mint Debian LiveCD and it found my wireless adapter instantly. All I had to do was blacklist rt2800usb in my blacklist.conf, restart, and here I am now posting on that OS.

I looked around the OS and rt2870.bin was in /lib/firmware/ so I guess I am good to go. I'm guessing that the 20110101 CD is based on the testing version of Debian Squeeze and had it in there.

---

