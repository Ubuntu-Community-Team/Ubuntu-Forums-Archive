---
title: "hp pavilion g6-1142sl wireless problems with ubuntu 11.04 after update"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by Zira on 2011-08-23
Hi everybody! i need some help!
i have got an HP Pavilion g6-1142sl and i installed on it ubuntu 11.04. 
i have some problems with the wireless. i have already read a post on this forum wich explained how to get drivers 

here the link: [http://ubuntuforums.org/showthread.php?t=1779005](http://ubuntuforums.org/showthread.php?t=1779005)

i got them and the wireless started working (a month ago)

now, a couple of days ago it stopped working  when i did a restart due to an automatic update.

and that is what i can see with terminal:

 *-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:c2500000-c250ffff

what can i do in order to have a working wireless?

i am sorry if my english is not properly good but i am italian.

---

### Post by praseodym on 2011-08-23
Hello,

did you install [DKMS]("https://help.ubuntu.com/community/DKMS")?

```
sudo apt-get install --reinstall dkms
```
Reboot and check the wireless. If it doesn't work you have to compile the driver again.

---

### Post by Zira on 2011-08-23
Thanks for your answer.

> **praseodym said:**
> Hello,

did you install [DKMS]("https://help.ubuntu.com/community/DKMS")?

```
sudo apt-get install --reinstall dkms
```Reboot and check the wireless. 

i have succesfully done it, but when i check the wireless it does not work.


> **praseodym said:**
> 

If it doesn't work you have to compile the driver again.

i did this:
```

sudo su  
cp RT2860STA.dat RT5390STA.dat 
mkdir -p /etc/Wireless/RT5390STA 
cp RT5390STA.dat /etc/Wireless/RT5390STA 
make clean 
make 
make install 
modprobe rt5390sta 
exit

```
Is it correct?

After this wireless doesn't work again.

any suggest?

---

### Post by praseodym on 2011-08-23
Did you install the kernel headers for the new kernel?

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
Then try compiling again, (maybe) reboot, and post the following outputs:

```
lspci -nnk | grep -iA2 Ralink
lsmod
modinfo rt5390sta | egrep 'versi|filen'
locate rt5390sta.ko | grep lib
iwconfig
sudo iwlist scan
rfkill list
```

---

### Post by Zira on 2011-08-24
here they are:
> sara@Sara-PC:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
[sudo] password for sara: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 3 reinstallati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 5920 B/892 kB di archivi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Scaricamento di:1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) natty/main build-essential i386 11.5ubuntu1 [5920 B]
Recuperati 5920 B in 0s (14,3 kB/s)      
(Lettura del database... 185965 file e directory attualmente installati.)
Preparativi per sostituire build-essential v.11.5ubuntu1 (utilizzando .../build-essential_11.5ubuntu1_i386.deb)...
Estrazione del sostituto di build-essential...
Preparativi per sostituire dkms v.2.1.1.2-5ubuntu1 (utilizzando .../dkms_2.1.1.2-5ubuntu1_all.deb)...
Estrazione del sostituto di dkms...
Preparativi per sostituire linux-headers-2.6.38-11-generic v.2.6.38-11.48 (utilizzando .../linux-headers-2.6.38-11-generic_2.6.38-11.48_i386.deb)...
Estrazione del sostituto di linux-headers-2.6.38-11-generic...
Elaborazione dei trigger per man-db...
Configurazione di build-essential (11.5ubuntu1)...
Configurazione di dkms (2.1.1.2-5ubuntu1)...
Configurazione di linux-headers-2.6.38-11-generic (2.6.38-11.48)...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic         
 *       fglrx (8.840)...                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
sara@Sara-PC:~$ lspci -nnk | grep -iA2 Ralink
04:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
    Kernel driver in use: rt2860
sara@Sara-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  451033  2 
fglrx                2434640  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
rts_pstor             348243  0 
uvcvideo               66851  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
drm                   184164  3 i915,drm_kms_helper
soundcore              12600  1 snd
rt5390sta            1266990  0 
videodev               75143  1 uvcvideo
psmouse                73312  0 
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 
sara@Sara-PC:~$ modinfo rt5390sta | egrep 'versi|filen'
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.5.0.1
srcversion:     A5DDD0453DFBFF7571C142D
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
sara@Sara-PC:~$ locate rt5390sta.ko | grep lib
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt5390sta.ko
sara@Sara-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sara@Sara-PC:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.

sara@Sara-PC:~$ rfkill list
sara@Sara-PC:~$ 


thank you again

---

### Post by praseodym on 2011-08-24
Did you reinstall the driver? Kernelheaders are version 11:

```

run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic

```
Driver is installed in Kernel 10:

```
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt5390sta.ko
```
Check which kernel is on your system:

```
uname -a
```

---

### Post by Zira on 2011-08-24
that is my kernel:

> sara@Sara-PC:~$ uname -a
Linux Sara-PC 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux


---

### Post by praseodym on 2011-08-24
Reinstall the driver with this kernel:

```
sudo apt-get install linux-headers-generic
cd NameOfDriverFolder/
sudo make clean
sudo make
sudo make uninstall
sudo make install
sudo modprobe -rf rt5390sta
sudo modprobe -v rt5380sta
sudo service network-manager restart
```

---

### Post by Zira on 2011-08-24
i changed this instruction:
sudo modprobe -v rt5380sta
[FONT=monospace]
in:
[/FONT]sudo modprobe -v rt5390sta


i am sorry but i've got the same problem... it does not work :(

---

### Post by praseodym on 2011-08-24
Ups, typo, sorry. Please show:

```
modinfo rt5390sta | egrep 'versi|filen'
locate rt5390sta.ko | grep lib
iwconfig
rfkill list
lsmod
dmesg | egrep 'rt5|rt2'
sudo iwlist scan
```
Tried to reboot?

---

### Post by Zira on 2011-08-25
Never mind :)

Is this correct?
> sara@Sara-PC:~$ modinfo rt5390sta | egrep 'versi|filen'
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.5.0.1
srcversion:     A5DDD0453DFBFF7571C142D
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
sara@Sara-PC:~$ locate rt5390sta.ko | grep lib
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt5390sta.ko
sara@Sara-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sara@Sara-PC:~$ rfkill list
sara@Sara-PC:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
binfmt_misc            13213  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i915                  451033  2 
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
fglrx                2434640  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
snd                    55295  17  snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               66851  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
rt5390sta            1266990  0 
drm                   184164  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
rts_pstor             348243  0 
psmouse                73312  0 
videodev               75143  1 uvcvideo
video                  18951  1 i915
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 
sara@Sara-PC:~$ dmesg | egrep 'rt5|rt2'
[   12.658635] rt5390sta: module license 'unspecified' taints kernel.
[   12.671272] register rt2860
[   12.671330] rt2860 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.671383] rt2860 0000:04:00.0: setting latency timer to 64
sara@Sara-PC:~$ sudo iwlist scan
[sudo] password for sara: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.

rebooted but nothing changed

---

### Post by praseodym on 2011-08-26
Did you update the driver database?

```
sudo depmod -a
modinfo rt5390sta | egrep 'versi|filen'
locate rt5390sta.ko | grep lib
```

---

### Post by Zira on 2011-09-01
is it correct?

> sara@Sara-PC:~$ sudo depmod -a
[sudo] password for sara: 
sara@Sara-PC:~$ modinfo rt5390sta | egrep 'versi|filen'
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.5.0.1
srcversion:     A5DDD0453DFBFF7571C142D
vermagic:       2.6.38-11-generic SMP mod_unload modversions 686 
sara@Sara-PC:~$ locate rt5390sta.ko | grep lib
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt5390sta.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt5390sta.ko


---

### Post by praseodym on 2011-09-01
You may remove your current wireless profile in the network-manager applet and setup a new one because the interface name changed to ra0. Check afterwards:

```
iwconfig
rfkill list
sudo iwlist scan
lsmod
```

---

### Post by Zira on 2011-09-01
done

> sara@Sara-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sara@Sara-PC:~$ rfkill list
sara@Sara-PC:~$ sudo iwlist scan
[sudo] password for sara: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.

sara@Sara-PC:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17322  0 
snd_seq_midi           13132  0 
fglrx                2434640  0 
i915                  451033  2 
drm_kms_helper         40745  1 i915
snd_rawmidi            25269  1 snd_seq_midi
hp_wmi                 13418  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13666  1 hp_wmi
drm                   184164  3 i915,drm_kms_helper
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
rt5390sta            1266990  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
rts_pstor             348243  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
psmouse                73312  0 
lp                     13349  0 
serio_raw              12990  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  42534  0 

---

### Post by praseodym on 2011-09-01
Try to unload the module hp_wmi:

```
sudo modprobe -rf hp_wmi
sudo service network-manager restart
```
Controls:

```
iwconfig
sudo iwlist scan
dmesg | egrep 'hp|rt5|rt2'
```

---

### Post by Zira on 2011-09-01
done
> sara@Sara-PC:~$ sudo modprobe -rf hp_wmi
[sudo] password for sara: 
sara@Sara-PC:~$ sudo service network-manager restart
network-manager start/running, process 3174
sara@Sara-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sara@Sara-PC:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.

sara@Sara-PC:~$ dmesg | egrep 'hp|rt5|rt2'
[    0.000000] hpet clockevent registered
[    0.781339] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.781355] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.783393] Switching to clocksource hpet
[    0.907931] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.361810] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.902833] ata5.00: ATAPI: hp       CDDVDW TS-L633J, HH00, max UDMA/100
[    1.931954] scsi 4:0:0:0: CD-ROM            hp       CDDVDW TS-L633J  HH00 PQ: 0 ANSI: 5
[   13.090058] rt5390sta: module license 'unspecified' taints kernel.
[   13.103090] register rt2860
[   13.103148] rt2860 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.103201] rt2860 0000:04:00.0: setting latency timer to 64
[   13.195386] hp-wmi: probe of hp-wmi failed with error -22
[   13.319058] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400


---

### Post by praseodym on 2011-09-01
Hmmm, strange. Lets see:

```
lspci -nnk | grep -iA2 net
lsusb
```

---

### Post by Zira on 2011-09-01
what' s wrong?
> sara@Sara-PC:~$ lspci -nnk | grep -iA2 net
04:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
    Subsystem: Hewlett-Packard Company Device [103c:1636]
    Kernel driver in use: rt2860
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1670]
    Kernel driver in use: r8169
sara@Sara-PC:~$ lsusb
Bus 002 Device 003: ID 0c45:6321 Microdia 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by praseodym on 2011-09-01
This driver is version 2.5.0.1, try 2.5.0.3 according to this:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747)

---

### Post by Zira on 2011-09-01
IT WORKS!!! 
Thanks :)))

---

### Post by mekky1985 on 2011-09-19
i know practically nothing about ubuntu and have spent all day tryin to set up wireless on my new laptop. after searchin for hours i followed this thread and tried and understand what you guys were saying. failing that, in the end i just put in the code that you linked to, and a few seconds later the WiFi light on my hp pavilion g6 changed colour and it is now working great. cheers praseodym you rock!!!

---

