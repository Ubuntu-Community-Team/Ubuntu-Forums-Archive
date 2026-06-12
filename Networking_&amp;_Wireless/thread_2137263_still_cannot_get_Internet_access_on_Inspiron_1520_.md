---
title: "still cannot get Internet access on Inspiron 1520 using 12.04 LTS"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by jm44224 on 2013-04-20
I've only been using Ubuntu for about a week. I tried to install 12.04 LTS three different times, but have no wired or wireless connection. I've checked most of the forum posts. 10.04 worked fine, but I noticed the end of life, and tried an upgrade. Still no Internet afterwards.

During my latest attempt:
I did this, although they were there: 
[COLOR=#000000][FONT=Ubuntu Mono]
sudo mv b43 /lib/firmware

[/FONT][/COLOR]I did this, but it wasn't loaded:
sudo rmmod -f b43

I tried this, but got device or resource busy:
sudo rmmod -f ssb

I try this, but it does nothing until I do a CTRL-C to kill the process:
sudo modprobe b43

rfkill list shows bluetooth, wifi and dell-bluetooth only ... none blocked

lsmod does not have b43

I don't know what else to type here, I am too new of a user. If needed, I can return to 10.04; but I don't know what this means as of next month. However, with 12.04 I cannot see the Internet at all.

---

### Post by praseodym on 2013-04-20
Please show:
```

lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```
If b43 was your driver before you need the package 'linux-firmware-nonfree':

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb)

---

### Post by jm44224 on 2013-04-20
Installed the linked firmware deb. No change. 
I may need to take a photo of text displayed at start up. This text display started before the firmware deb; actually at "the first reboot after install". Seems to be a lot of driver feedback. 

lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:01f1]
	Kernel modules: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
	Kernel driver in use: wl
iwconfig
lo        no wireless extensions.


rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
lsmod
Module                  Size  Used by
dm_crypt               22528  0 
bnep                   17830  2 
parport_pc             32114  0 
rfcomm                 38139  12 
ppdev                  12849  0 
binfmt_misc            17292  1 
nvidia              10286823  44 
snd_hda_codec_idt      60251  1 
ssb                    69106  1 
wl                   3032542  1 
joydev                 17393  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
r852                   17901  0 
sm_common              16772  1 r852
snd_seq_midi           13132  0 
nand                   49667  2 r852,sm_common
snd_rawmidi            25424  1 snd_seq_midi
psmouse                96718  0 
btusb                  17948  2 
dell_wmi               12601  0 
cfg80211              178877  1 wl
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
bluetooth             158479  23 bnep,rfcomm,btusb
bch                    21784  1 nand_bch
snd_timer              28931  2 snd_pcm,snd_seq
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
nand_ecc               13105  1 nand
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
sparse_keymap          13658  1 dell_wmi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
r592                   17808  0 
mac_hid                13077  0 
memstick               15857  1 r592
lib80211               14040  1 wl
wmi                    18744  1 dell_wmi
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
video                  19115  0

---

### Post by praseodym on 2013-04-21
Deactivate the Broadcom-STA driver and reboot.

---

### Post by jm44224 on 2013-04-21
What is the command to do that?

---

### Post by praseodym on 2013-04-21
```
sudo apt-get remove --purge bcmwl-kernel-source
```
After that you need to remove the config files:```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
```

---

### Post by jm44224 on 2013-04-21
trying first command now. stopped at triggers for ubutramfs-tools. message box appears on failure to download extra data files. 

files missing ... flashplug-installer

perhaps I should reload from ISO, and run this prior to the first reboot? I think at that point I do have Internet access. Or is this something I can download using another computer and transfer via USB?

---

### Post by jm44224 on 2013-04-21
I killed the process. Not sure if that was a good idea. The remaining three directories were not found. I rebooted. It has Internet. I will mark this as SOLVED once I figure out how, and see if anything is broken after the killed process. Thanks all!

---

### Post by praseodym on 2013-04-21
Repair the system if necessary via
```

sudo dpkg --configure -a
sudo apt-get -f install
```

---

