---
title: "Netgear WNA1100 isn't active on Ubuntu 10.04"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by Lotica on 2012-04-09
Hello. I'm currently using the Netgear WNA1100 USB wireless adapter and it isn't active with Ubuntu 10.04 LTS, even on a clean installation of the operating system. Sure, I could use a new version, but this version of Ubuntu works really fast with my machine at the moment, and until I get 2GB of RAM, I want to use this one.

Please help.

---

### Post by praseodym on 2012-04-09
Please show
```
uname -a
lsusb
lsmod
iwconfig
```
Normally you need the module ath9k_htc, which comes with 11.04. So you need to install compat-wireless and the firmware:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install 
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/10/2640681-15888a2-Atheros_Firmware.tar.gz
sudo tar xvf 2640681-15888a2-Atheros_Firmware.tar.gz -C /lib/firmware 
```

Reboot

---

### Post by Lotica on 2012-04-09
> **praseodym said:**
> Please show
```
uname -a
lsusb
lsmod
iwconfig
```
Normally you need the module ath9k_htc, which comes with 11.04. So you need to install compat-wireless and the firmware:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install 
wget http://media.cdn.ubuntu-de.org/forum/attachments/44/10/2640681-15888a2-Atheros_Firmware.tar.gz
sudo tar xvf 2640681-15888a2-Atheros_Firmware.tar.gz -C /lib/firmware 
```

Reboot

I'm really sorry, I'm kind of still new to this whole Ubuntu experience. Can you please tell me where to do that?

---

### Post by praseodym on 2012-04-09
Open a terminal with CTRL+ALT+T and type in/copy-paste these lines.

---

### Post by Lotica on 2012-04-09
Here's that information you wanted.

```
lotica@lotica-desktop:~$ uname -a
Linux lotica-desktop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
```

```
lotica@lotica-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lotica@lotica-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
snd_emu10k1_synth       5156  0 
snd_emux_synth         31695  1 snd_emu10k1_synth
snd_seq_virmidi         4213  1 snd_emux_synth
snd_seq_midi_emul       5492  1 snd_emux_synth
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_emu10k1           131163  3 snd_emu10k1_synth
snd_intel8x0           25652  2 
snd_ac97_codec        100646  2 snd_emu10k1,snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_util_mem            3106  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5412  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6003  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47263  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
snd_timer              19130  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5700  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49847  1 nouveau
emu10k1_gp              1492  0 
drm_kms_helper         29329  1 nouveau
joydev                  8740  0 
ppdev                   5259  0 
snd                    54244  22 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
gameport                9089  2 emu10k1_gp
drm                   163747  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
soundcore               6620  1 snd
dell_wmi                1793  0 
dcdbas                  5422  0 
psmouse                63677  0 
serio_raw               3978  0 
intel_agp              24375  1 
parport_pc             25962  1 
snd_page_alloc          7076  3 snd_emu10k1,snd_intel8x0,snd_pcm
usbhid                 36110  0 
hid                    67288  1 usbhid
shpchp                 28835  0 
agpgart                31724  3 ttm,drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usb_storage            40033  1 
ohci1394               26950  0 
e100                   28211  0 
floppy                 53016  0 
mii                     4381  1 e100
ieee1394               81181  1 ohci1394
```

```
lotica@lotica-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by praseodym on 2012-04-09
Yep, as I mentioned above. You should update your system first (kernel -40 is the latest), reboot, and replace "linux-headers-$(uname -r)" with "linux-headers-generic" in the 1st command line

---

### Post by Lotica on 2012-04-09
Okay, I'm connected to a wired connection and I'm getting the updates right now. Why do I need to update in regards to the adapter?

Also, when do I need to insert the adapter?

---

### Post by praseodym on 2012-04-09
The package "linux-headers-$(uname -r)" only installs the headers for the current kernel -38. The metapackage "linux-headers-generic" updates the latest headers automatically (-40 after the updates).

Do not remove the driver folder. After another kernel upgrade you need to compile again via:

```
cd compat-wireless-20*
make clean
./scripts/driver-select atheros 
make
sudo make install 
```
After installation load the driver

```
sudo modprobe ath9k_htc
```
and replug the stick

---

### Post by Lotica on 2012-04-09
Nevermind, I got the download. Still working on the issue though.

---

