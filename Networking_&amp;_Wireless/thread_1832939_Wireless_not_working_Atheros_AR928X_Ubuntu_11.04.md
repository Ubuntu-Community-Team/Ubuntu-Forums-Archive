---
title: "Wireless not working Atheros AR928X Ubuntu 11.04"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by pizzaman711 on 2011-08-25
So I'm new to ubuntu and decided to dual boot it on my Acer Aspire 1551 with Windows 7 as the other operating system on it. I installed if off a usb drive following the tutorial on the Ubuntu website. However I can't figure out how to get the wireless to work with ubuntu 11.04.

I ran ```
lspci | grep Wireless
``` and got
```
Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

When I run lshw I get 
```
*-network UNCLAIMED
```
not sure if that helps any though.

Also I ran another command, can't think of it off the top of my head however and it said the wireless network was disabled.

As of right now I only have access to the internet through the wireless under Windows 7 as my apartment doesn't have an ethernet port so if it's possible to download what I need off the internet through Windows that'd be great otherwise if I have to I can go to the library to use an ethernet port there. 

Any help is greatly appreciated!

---

### Post by praseodym on 2011-08-25
Hello,

the driver ath9k needs an additional parameter with 11.04:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
sudo service network-manager restart
```
Additionally, please show the following outputs afterwards:

```
iwconfig
rfkill list
lsmod
dmesg | egrep 'ath|wmi|radio|switch'
sudo iwlist scan
```

---

### Post by pizzaman711 on 2011-08-25
Thanks for the quick response!

So I started putting in what you said and got:
```
paul@paul-Aspire-1551:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for paul: 
options ath9k nohwcrypt=1
paul@paul-Aspire-1551:~$ sudo modprobe -rf ath9k
paul@paul-Aspire-1551:~$ sudo modprobe -v ath9k
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko 
WARNING: Error inserting ath (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_hw (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Should I keep going to the next command?

So, I did some more reading and it seems that when other people get it to start working they seem to be having trouble keeping a strong signal or losing connection off and on. So it brings me to my next question would it have a better advantage to go with a usb wireless adapter instead of the internal one?
[http://www.thinkpenguin.com/gnu-linux/penguin-80211g-usb-wireless-network-adapter-w-linux-gnu-support](http://www.thinkpenguin.com/gnu-linux/penguin-80211g-usb-wireless-network-adapter-w-linux-gnu-support)
Possibly one like that?

---

### Post by praseodym on 2011-08-25
Show the outputs, please, then we will see more.

---

### Post by pizzaman711 on 2011-08-25
After first set of commands:
```
paul@paul-Aspire-1551:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf[sudo] password for paul: 
options ath9k nohwcrypt=1
paul@paul-Aspire-1551:~$ sudo modprobe -rf ath9k
paul@paul-Aspire-1551:~$ sudo modprobe -v ath9k
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko 
WARNING: Error inserting ath (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_hw (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
paul@paul-Aspire-1551:~$ sudo service network-manager restart
network-manager start/running, process 3729


```

After second set:
```


paul@paul-Aspire-1551:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

paul@paul-Aspire-1551:~$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
paul@paul-Aspire-1551:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                896428  3 
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            13213  1 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
acer_wmi               23123  0 
joydev                 17322  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
sparse_keymap          13666  1 acer_wmi
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               66851  0 
i2c_algo_bit           13184  1 radeon
videodev               75143  1 uvcvideo
psmouse                73312  0 
shpchp                 32345  0 
soundcore              12600  1 snd
sp5100_tco             13456  0 
serio_raw              12990  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0 
k10temp                12951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  1 
uas                    17676  0 
ahci                   21591  2 
pata_atiixp            12968  0 
libahci                25548  1 ahci
atl1c                  36237  0 
paul@paul-Aspire-1551:~$ dmesg | egrep 'ath|wmi|radio|switch'
[    0.672395]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.672409]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    0.688660] wmi: Mapper loaded
[    1.728543] device-mapper: multipath: version 1.2.0 loaded
[    1.728546] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.366092] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[   11.366220] ath: Unknown symbol freq_reg_info (err 0)
[   12.114006] acer-wmi: Acer Laptop ACPI-WMI Extras
[   12.114258] acer-wmi: Function bitmap for Communication Button: 0x1
[   12.114719] acer-wmi: Brightness must be controlled by generic video driver
[   12.131667] acer-wmi: Get Device Status failed: 0xe1 - 0x0
[   13.413775] Console: switching to colour frame buffer device 170x48
[ 2104.784477] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 2104.784746] ath: Unknown symbol freq_reg_info (err 0)
[ 2810.328541] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 2810.328811] ath: Unknown symbol freq_reg_info (err 0)
[ 3382.422538] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 3382.422808] ath: Unknown symbol freq_reg_info (err 0)
paul@paul-Aspire-1551:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

EDIT: Now that I've done this under the connections at the top it doesn't list wireless anymore.

---

### Post by praseodym on 2011-08-25
Ok, first remove the driver option:

```
sudo rm /etc/modprobe.d/ath9k.conf
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
```
Is wlan0 displayed again? Try 

```
sudo rfkill unblock all
rfkill list                #control
iwconfig
sudo iwlist scan
dmesg | egrep 'ath|wmi'
```
If it doesnt work, try to unload the module acer_wmi:

```
sudo modprobe -rf acer_wmi
```
same controls again (with "rfkill")

---

### Post by pizzaman711 on 2011-08-25
```
paul@paul-Aspire-1551:~$ sudo rm /etc/modprobe.d/ath9k.conf
[sudo] password for paul: 
paul@paul-Aspire-1551:~$ sudo modprobe -rf ath9k
paul@paul-Aspire-1551:~$ sudo modprobe -v ath9k
insmod /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko 
WARNING: Error inserting ath (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_hw (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting ath9k_common (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath9k (/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)
paul@paul-Aspire-1551:~$ 
paul@paul-Aspire-1551:~$ 
paul@paul-Aspire-1551:~$ sudo rfkill unblock all
paul@paul-Aspire-1551:~$ rfkill list                #control
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
paul@paul-Aspire-1551:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

paul@paul-Aspire-1551:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paul@paul-Aspire-1551:~$ dmesg | egrep 'ath|wmi'
[    0.316377]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.316391]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    0.332076] wmi: Mapper loaded
[    1.466366] device-mapper: multipath: version 1.2.0 loaded
[    1.466369] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.170068] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[   11.170196] ath: Unknown symbol freq_reg_info (err 0)
[   11.923468] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.923702] acer-wmi: Function bitmap for Communication Button: 0x1
[   11.924188] acer-wmi: Brightness must be controlled by generic video driver
[   11.950527] acer-wmi: Get Device Status failed: 0xe1 - 0x0
[ 1211.280523] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 1211.280791] ath: Unknown symbol freq_reg_info (err 0)
paul@paul-Aspire-1551:~$ sudo modprobe -rf acer_wmi
paul@paul-Aspire-1551:~$ sudo rfkill unblock all
paul@paul-Aspire-1551:~$ rfkill list                #control
paul@paul-Aspire-1551:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

paul@paul-Aspire-1551:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paul@paul-Aspire-1551:~$ dmesg | egrep 'ath|wmi'
[    0.316377]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.316391]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    0.332076] wmi: Mapper loaded
[    1.466366] device-mapper: multipath: version 1.2.0 loaded
[    1.466369] device-mapper: multipath round-robin: version 1.0.0 loaded
[   11.170068] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[   11.170196] ath: Unknown symbol freq_reg_info (err 0)
[   11.923468] acer-wmi: Acer Laptop ACPI-WMI Extras
[   11.923702] acer-wmi: Function bitmap for Communication Button: 0x1
[   11.924188] acer-wmi: Brightness must be controlled by generic video driver
[   11.950527] acer-wmi: Get Device Status failed: 0xe1 - 0x0
[ 1211.280523] ath: Unknown symbol wiphy_apply_custom_regulatory (err 0)
[ 1211.280791] ath: Unknown symbol freq_reg_info (err 0)
[ 1453.716887] acer-wmi: Acer Laptop WMI Extras unloaded

```

And the wireless still isn't showing up. Is there another distribution of linux that would be more compatible with the hardware of my laptop?

---

### Post by fdrake on 2011-08-25
can you post here
```

less /etc/apt/sources.list
```
 just to check if your back ports are enabled.

---

### Post by pizzaman711 on 2011-08-25
> **fdrake said:**
> can you post here
```

less /etc/apt/sources.list
```
 just to check if your back ports are enabled.

When I run that I get:
```
#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

I'm not sure what to do from there though.

---

### Post by fdrake on 2011-08-25
uncheck this lines please
```

deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

```
then do 
```
sudo apt-get update
sudo aptitude search backports
uname -a
```

post the results of the last 2 commands . I do not use Natty so i don't know the right name of the packs

---

### Post by pizzaman711 on 2011-08-25
This is probably a dumb question, but how do I uncheck them? All I can do is right click on the links but I can't actually change anything in the terminal.

---

### Post by fdrake on 2011-08-25
> **pizzaman711 said:**
> This is probably a dumb question, but how do I uncheck them? All I can do is right click on the links but I can't actually change anything in the terminal.

no problem run this commands:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
sudo gedit /etc/apt/sources.list

```
look for those to lines and delete the "#" symbol. Once you cancel that symbol the urls will take effect. Makes sure you save the file before closing.
 then run my other previous commands and post them here.

---

### Post by pizzaman711 on 2011-08-25
```
paul@paul-Aspire-1551:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
[sudo] password for paul: 
paul@paul-Aspire-1551:~$ sudo gedit /etc/apt/sources.list


(gedit:7630): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.K1ER0V': No such file or directory

(gedit:7630): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:7630): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.EHZQ0V': No such file or directory

(gedit:7630): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:7630): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.I1DW0V': No such file or directory

(gedit:7630): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```

I got that when I tried to change it, and I'll have to run the other commands tomorrow when I can get a chance to run a ethernet cord to the laptop unless I can find a way to tether it off my other computer.

---

