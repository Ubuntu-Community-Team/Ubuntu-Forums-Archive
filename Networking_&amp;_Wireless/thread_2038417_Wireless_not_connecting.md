---
title: "Wireless not connecting"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2012-08-06
I have an older i386 with Ubuntu 12.04 LTS and am having trouble connecting to wireless networks.  I can see some networks and not others, but not connect to either.  Are there any guides on how to connect uptodate for 12.04?

If I look at the output from ifconfig, wlan0 does not show up.

---

### Post by praseodym on 2012-08-06
Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
```

---

### Post by Lars Noodén on 2012-08-06
Thanks

```

$ lspci -nnk | grep -iA2 net
00:06.0 Network controller [0280]: Ralink corp. RT2561/RT61 802.11g PCI [1814:0301]
	Subsystem: Ralink corp. EW-7108PCg [1814:2561]
	Kernel driver in use: rt61pci
--
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
	Subsystem: Packard Bell B.V. Device [1631:c015]
	Kernel driver in use: via-rhine

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lsmod
Module                  Size  Used by
via                    45249  1 
drm                   197692  2 via
bnep                   17830  2 
bluetooth             158438  7 bnep
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
arc4                   12473  2 
joydev                 17393  0 
snd_via82xx            24718  2 
rt61pci                27493  0 
crc_itu_t              12627  1 rt61pci
rt2x00pci              14202  1 rt61pci
gameport               15060  1 snd_via82xx
rt2x00lib              48805  2 rt61pci,rt2x00pci
snd_mpu401_uart        13865  1 snd_via82xx
snd_seq_midi           13132  0 
mac80211              436455  2 rt2x00pci,rt2x00lib
i2c_viapro             12969  0 
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
cfg80211              178679  2 rt2x00lib,mac80211
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac_hid                13077  0 
snd_pcm                80845  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72919  0 
via_ircc               26781  0 
snd_timer              28931  2 snd_pcm,snd_seq
irda                  185517  1 via_ircc
snd_page_alloc         14108  3 snd_via82xx,snd_via82xx_modem,snd_pcm
serio_raw              13027  0 
snd                    62064  13 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
shpchp                 32325  0 
crc_ccitt              12595  1 irda
eeprom_93cx6           12653  1 rt61pci
soundcore              14635  1 snd
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_via               13428  3 
via_rhine              27413  0 

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

---

### Post by praseodym on 2012-08-06
Doesnt look bad. Uninstall the package "resolvconf", reboot, and check:
```

iwconfig
dmesg | egrep 'rt6|country'
sudo iwlist scan
iwlist chan
```

---

### Post by Lars Noodén on 2012-08-06
Ok.  I've removed resolvconf.

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

maintenance@easynote:~$ dmesg | egrep 'rt6|country'
[    7.507668] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[    7.507682] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[    7.507700] rt61pci 0000:00:06.0: setting latency timer to 64
[    7.765634] Registered led device: rt61pci-phy0::radio
[    7.765668] Registered led device: rt61pci-phy0::assoc
maintenance@easynote:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

maintenance@easynote:~$ iwlist chan
lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.



```

---

### Post by praseodym on 2012-08-06
> ```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]0 dBm[/COLOR] 
```

The card is "off". Any button/switch/key or key combination (e.g. Fn+F2)? Check the BIOS settings and you may reset the BIOS to default.

---

### Post by Lars Noodén on 2012-08-07
> **praseodym said:**
> The card is "off". Any button/switch/key or key combination (e.g. Fn+F2)? Check the BIOS settings and you may reset the BIOS to default.
I can get it to alternate between "Tx-Power=off" and "Tx-Power=0 dBm", but that is all.

---

### Post by praseodym on 2012-08-07
Maybe the "other" driver works?!
> 
sudo modprobe -rfv rt61pci
sudo modprobe -v rt2500pci

---

### Post by Lars Noodén on 2012-08-07
> **praseodym said:**
> Maybe the "other" driver works?!

```

$ sudo modprobe -rfv rt61pci
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt61pci.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/lib/crc-itu-t.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/misc/eeprom/eeprom_93cx6.ko

$ sudo modprobe -v rt2500pci
insmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
insmod /lib/modules/3.2.0-27-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-27-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
insmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
insmod /lib/modules/3.2.0-27-generic-pae/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko 

$ sudo iwconfig wlan0
wlan0     No such device



```

That seems to have removed the wireless option from the network pull-down menu on Unity.

---

### Post by Lars Noodén on 2012-08-07
dhclient says the device is busy, if that is any clue.

```

$ sudo dhclient wlan0
RTNETLINK answers: Device or resource busy

```

---

### Post by praseodym on 2012-08-07
Ok, this does not work.
> 
sudo modprobe -rfv rt2500pci
sudo modprobe -v rt61pci
Maybe updating the driver with "linuxwireless"?

---

### Post by Lars Noodén on 2012-08-07
> **praseodym said:**
> Maybe updating the driver with "linuxwireless"?

Which package would that be in?  I'm not finding it in any package name or description.

---

### Post by praseodym on 2012-08-07
You need to compile it on your own, see:

[http://www.linuxwireless.org/](http://www.linuxwireless.org/)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential dkms linux-firmware
wget http://www.orbit-lab.org/kernel/compat-wireless/compat-wireless.tar.bz2
tar jxvf compat-wireless.tar.bz2 
cd compat-*
make [COLOR="Red"]#this will take a while[/COLOR]
sudo make install
```
Reboot.

Alternatively, you can search for the package "backports-modules" something with "cw" in the name, in your software center

---

### Post by Lars Noodén on 2012-08-08
The manual build took away Unity's "enable wireless" option.  Adding  linux-backports-modules-cw-3.3-3.2.0-23-generic-pae from backports didn't seem to change anything.  The menu still says "device not ready" and iwlist scan says "Failed to read scan data : Network is down", but the network is available.

---

### Post by praseodym on 2012-08-08
Check:

```
iwconfig
lsmod
sudo iwlist scan
rfkill list
dmesg | grep rt6
modinfo rt61pci | egrep 'versi|filen'
locate rt61pci.ko | grep lib
```

---

### Post by Lars Noodén on 2012-08-08
Here is the output.  I see the 0dBm again.

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

maintenance@easynote:~$ lsmod
Module                  Size  Used by
via                    45249  1 
drm                   197692  2 via
vesafb                 13516  1 
arc4                   12473  2 
bnep                   17711  2 
rfcomm                 37291  0 
bluetooth             164346  8 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_via82xx            24718  2 
rt61pci                27030  0 
gameport               15060  1 snd_via82xx
snd_mpu401_uart        13865  1 snd_via82xx
crc_itu_t              12627  1 rt61pci
rt2x00pci              14116  1 rt61pci
rt2x00lib              48261  2 rt61pci,rt2x00pci
snd_seq_midi           13132  0 
snd_via82xx_modem      18377  0 
snd_ac97_codec        106082  2 snd_via82xx,snd_via82xx_modem
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25424  2 snd_mpu401_uart,snd_seq_midi
snd_pcm                80845  3 snd_via82xx,snd_via82xx_modem,snd_ac97_codec
mac80211              440734  2 rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
i2c_viapro             12969  0 
via_ircc               26781  0 
irda                  185517  1 via_ircc
psmouse                72919  0 
snd                    62064  13 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178818  2 rt2x00lib,mac80211
serio_raw              13027  0 
snd_page_alloc         14108  3 snd_via82xx,snd_via82xx_modem,snd_pcm
eeprom_93cx6           13134  1 rt61pci
soundcore              14635  1 snd
crc_ccitt              12595  1 irda
shpchp                 32325  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
via_rhine              27413  0 
pata_via               13428  3 
maintenance@easynote:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

maintenance@easynote:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
maintenance@easynote:~$ dmesg | grep rt6
[   20.025056] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   20.025069] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   20.025085] rt61pci 0000:00:06.0: setting latency timer to 64
[   20.107573] Registered led device: rt61pci-phy0::radio
[   20.107752] Registered led device: rt61pci-phy0::assoc
maintenance@easynote:~$ modinfo rt61pci | egrep 'versi|filen'
filename:       /lib/modules/3.2.0-27-generic-pae/updates/cw-3.3/rt61pci.ko
version:        2.3.0
srcversion:     30EC5D56ADED808831143CD
vermagic:       3.2.0-27-generic-pae SMP mod_unload modversions 686 
maintenance@easynote:~$ locate rt61pci.ko | grep lib
/lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/rt2x00/rt61pci.ko

```

Edit: In the above settings, I have linux-backports-modules-cw-3.3-3.2.0-27-generic-pae 
 installed from backports.

---

### Post by praseodym on 2012-08-08
Did I ask before, what computer it is?

---

### Post by Lars Noodén on 2012-08-08
> **praseodym said:**
> Did I ask before, what computer it is?

It's an old Packard Bell EasyNote.  It's pretty worn.

---

### Post by praseodym on 2012-08-08
What about Fn+F1? Button/switch on any side?

---

### Post by Lars Noodén on 2012-08-09
> **praseodym said:**
> What about Fn+F1? Button/switch on any side?

There's a stylized antenna on F1 but pressing fn+F1 has no effect that I can tell.

---

### Post by praseodym on 2012-08-09
Please run:

```
dmesg >> dmesg.txt
```
and upload the file "dmesg.txt" in your home folder

---

### Post by Lars Noodén on 2012-08-09
Here is the output from dmesg.

Edit-  The output exceeded the max size uncompressed text file.  I wasn't catching the error message.

---

### Post by Lars Noodén on 2012-08-09
2nd try.

---

### Post by Lars Noodén on 2012-08-09
Had trouble with the upload form.

---

### Post by praseodym on 2012-08-09
If the file is too big you can zip it

---

### Post by Lars Noodén on 2012-08-09
> **praseodym said:**
> If the file is too big you can zip it

Thanks. The limit for text files is very small, but after enough mistakes I was able to attach the dmesg output to [#22](http://ubuntuforums.org/showpost.php?p=12159509&postcount=22) above.

---

### Post by praseodym on 2012-08-09
> [   18.549947] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using [COLOR="Red"]pci=biosirq[/COLOR]
Try this boot parameter in grub. Dont forget to

> sudo update-grub
before rebooting.

---

### Post by praseodym on 2012-08-09
Double posting

---

### Post by Lars Noodén on 2012-08-09
I'm very unfamiliar with grub.  Where in the grub configuration file should "pci=nobios" go and in which file?

```

$ ls /etc/grub.d/
00_header        20_linux_xen     40_custom        
05_debian_theme  20_memtest86+    41_custom        
10_linux         30_os-prober     README  

```

---

### Post by praseodym on 2012-08-09
It is:

```
gksu gedit /etc/default/grub
```
Into this line (example):

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap acpi_enforce_resources=lax cgroup_disable=memory"
```
Save, close, and:

```
sudo update-grub
```
Reboot.

---

### Post by Lars Noodén on 2012-08-09
I edited GRUB_CMDLINE_LINUX_DEFAULT="pci=nobios quiet splash" in /etc/default/grub and then ran sudo update-grub and rebooted.  What should I expect to have changed?

```

$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.


```

---

### Post by praseodym on 2012-08-09
Strange. Check:

```
rfkill list
dmesg | egrep 'rt6|acpi'
sudo iwlist scan
iwlist chan
```

---

### Post by Lars Noodén on 2012-08-09
> **praseodym said:**
> Strange. Check:

```
rfkill list
dmesg | egrep 'rt6|acpi'
sudo iwlist scan
iwlist chan
```

Ok

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
$ dmesg | egrep 'rt6|acpi'
[    0.000000] ACPI: BIOS age (520) fails cutoff (2000), acpi=force is required to enable ACPI
[   19.897048] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   19.897061] rt61pci 0000:00:06.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   19.897079] rt61pci 0000:00:06.0: setting latency timer to 64
[   19.975496] Registered led device: rt61pci-phy0::radio
[   19.975754] Registered led device: rt61pci-phy0::assoc
$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

$ iwlist chan
lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
eth0      no frequency information.

```

---

### Post by praseodym on 2012-08-09
> [    0.000000] ACPI: BIOS age (520) fails cutoff (2000), [COLOR="Red"]acpi=force[/COLOR] is required to enable ACPI
Add this one to /etc/default/grub, too. You BIOS is too old.

---

### Post by Lars Noodén on 2012-08-09
> **praseodym said:**
> Add this one to /etc/default/grub, too. You BIOS is too old.

I've added acpi=force via grub and rebooted.  Should I try pci=noacpi or acpi=off?

```

$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
$ dmesg | egrep 'rt6|acpi'
[    0.000000] ACPI: BIOS age (520) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-27-generic-pae root=UUID=aab64a3e-a566-4ada-bcb2-be14d49a60dd ro acpi=force pci=nobios quiet splash vt.handoff=7
[    0.186322] Switching to clocksource acpi_pm
[    0.204204] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.220079] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.236066] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.252072] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.395327] ACPI: acpi_idle registered with cpuidle
[    0.525732] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.525813] pata_acpi 0000:00:11.1: PCI INT A disabled
[    0.526886] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.536912] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.537534] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    0.538038] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[    1.250457] acpi device:0f: hash matches
[   18.910904] rt61pci 0000:00:06.0: enabling device (0000 -> 0002)
[   18.910942] rt61pci 0000:00:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.910960] rt61pci 0000:00:06.0: setting latency timer to 64
[   19.078168] Registered led device: rt61pci-phy0::radio
[   19.078251] Registered led device: rt61pci-phy0::assoc
$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.

```

---

### Post by praseodym on 2012-08-09
First try "noacpi"

---

### Post by Lars Noodén on 2012-08-09
> **praseodym said:**
> First try "noacpi"

This is what I have so far:

```
GRUB_CMDLINE_LINUX_DEFAULT="noacpi pci=nobios quiet splash"

```

sudo dhclient wlan0 still gives the error message "RTNETLINK answers: Device or resource busy"

---

### Post by praseodym on 2012-08-10
It needs to be "pci=noacpi" or "acpi=off", respectively.

---

### Post by Lars Noodén on 2012-08-10
> **praseodym said:**
> It needs to be "pci=noacpi" or "acpi=off", respectively.

Thanks for your help and patience.  I've tried both, but I'm not that familiar with grub.

GRUB_CMDLINE_LINUX_DEFAULT="acpi=off pci=nobios quiet splash"

and

GRUB_CMDLINE_LINUX_DEFAULT="pci=noacpi pci=nobios quiet splash"

Currently it's the latter.
I'm still not seeing the network:

$ /sbin/iwlist scan
lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2012-08-10
Have you tried an earlier Ubuntu version, e.g. 10.04? Maybe you can update the BIOS?!

---

