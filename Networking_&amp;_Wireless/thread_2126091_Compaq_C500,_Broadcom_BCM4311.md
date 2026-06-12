---
title: "Compaq C500, Broadcom BCM4311"
date: 2013-03-15
forum: Networking &amp; Wireless
---

### Post by foltajr on 2013-03-15
I am at wits end I have read other post and still have not found solution to getting my LAN and Wifi to work.... Any ideas or suggestions?

---

### Post by matt_symes on 2013-03-16
Thread moved to **wireless and networking**

---

### Post by Hadaka on 2013-03-16
Hi, please copy and paste..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks

---

### Post by foltajr on 2013-03-16
Usage: **lspci **[<switches>] 


Basic display modes: 
-mm		Produce machine-readable output(single -m for an obsolete format) 
-t		Show bus tree 


Display options: 
-v		Be verbose (-vv for very verbose) 
-k		Show kernel drivers handling eachdevice 
-x		Show hex-dump of the standard partof the config space 
-xxx		Show hex-dump of the whole configspace (dangerous; root only) 
-xxxx		Show hex-dump of the 4096-byteextended config space (root only) 
-b		Bus-centric view (addresses andIRQ's as seen by the bus) 
-D		Always show domain numbers 


Resolving of device ID's to names: 
-n		Show numeric ID's 
-nn		Show both textual and numeric ID's(names & numbers) 
-q		Query the PCI ID database forunknown ID's via DNS 
-qq		As above, but re-query locallycached entries 
-Q		Query the PCI ID database for allID's via DNS 


Selection of devices: 
-s[[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Showonly devices in selected slots 
-d [<vendor>]:[<device>]			Showonly devices with specified ID's 


Other options: 
-i <file>	Use specified IDdatabase instead of /usr/share/misc/pci.ids.gz 
-p <file>	Look up kernel modulesin a given file instead of default modules.pcimap 
-M		Enable `bus mapping' mode(dangerous; root only) 


PCI access options: 
-A <method>	Use the specified PCIaccess method (see `-A help' for a list) 
-O <par>=<val>	Set PCIaccess parameter (see `-O help' for a list) 
-G		Enable PCI access debugging 
-H <mode>	Use direct hardwareaccess (<mode> = 1 or 2) 
-F <file>	Read PCI configurationdump from a given file 
mike@mike-Presario-C500-RQ334UA-ABA:~$ 


Usage: lspci [<switches>] 


Basic display modes: 
-mm		Produce machine-readable output(single -m for an obsolete format) 
-t		Show bus tree 


Display options: 
-v		Be verbose (-vv for very verbose) 
-k		Show kernel drivers handling eachdevice 
-x		Show hex-dump of the standard partof the config space 
-xxx		Show hex-dump of the whole configspace (dangerous; root only) 
-xxxx		Show hex-dump of the 4096-byteextended config space (root only) 
-b		Bus-centric view (addresses andIRQ's as seen by the bus) 
-D		Always show domain numbers 


Resolving of device ID's to names: 
-n		Show numeric ID's 
-nn		Show both textual and numeric ID's(names & numbers) 
-q		Query the PCI ID database forunknown ID's via DNS 
-qq		As above, but re-query locallycached entries 
-Q		Query the PCI ID database for allID's via DNS 


**LSMOD:**


Selection of devices: 
-s[[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Showonly devices in selected slots 
-d [<vendor>]:[<device>]			Showonly devices with specified ID's 


Other options: 
-i <file>	Use specified IDdatabase instead of /usr/share/misc/pci.ids.gz 
-p <file>	Look up kernel modulesin a given file instead of default modules.pcimap 
-M		Enable `bus mapping' mode(dangerous; root only) 


PCI access options: 
-A <method>	Use the specified PCIaccess method (see `-A help' for a list) 
-O <par>=<val>	Set PCIaccess parameter (see `-O help' for a list) 
-G		Enable PCI access debugging 
-H <mode>	Use direct hardwareaccess (<mode> = 1 or 2) 
-F <file>	Read PCI configurationdump from a given file 
mike@mike-Presario-C500-RQ334UA-ABA:~$lsmod 
Module                  Size  Used by 
snd_hda_codec_conexant    52202  1 
coretemp               13168  0 
hp_wmi                 13616  0 
sparse_keymap          13658  1 hp_wmi 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2snd_hda_codec_conexant,snd_hda_intel 
snd_hwdep              13272  1snd_hda_codec 
snd_pcm                80163  2snd_hda_intel,snd_hda_codec 
microcode              18209  0 
snd_seq_midi           13132  0 
b43                   347284  0 
snd_rawmidi            25382  1snd_seq_midi 
mac80211              461161  1 b43 
rfcomm                 37276  0 
bnep                   17707  2 
parport_pc             31968  0 
snd_seq_midi_event     14475  1snd_seq_midi 
psmouse                84843  0 
ppdev                  12817  0 
bluetooth             183228  10rfcomm,bnep 
joydev                 17161  0 
cfg80211              175375  2b43,mac80211 
serio_raw              13031  0 
i915                  457161  3 
bcma                   34483  1 b43 
ssb_hcd                12749  0 
snd_seq                51255  2snd_seq_midi,snd_seq_midi_event 
snd_timer              24411  2snd_pcm,snd_seq 
drm_kms_helper         45271  1 i915 
snd_seq_device         14137  3snd_seq_midi,snd_rawmidi,snd_seq 
drm                   230463  4i915,drm_kms_helper 
i2c_algo_bit           13197  1 i915 
lpc_ich                16925  0 
snd                    61991  15snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd 
wmi                    18590  1 hp_wmi 
snd_page_alloc         14036  2snd_hda_intel,snd_pcm 
mac_hid                13037  0 
video                  18847  1 i915 
lp                     13299  0 
parport                40753  3parport_pc,ppdev,lp 
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2hid_generic,usbhid 
8139too                23071  0 
8139cp                 26619  0 
ssb                    50087  2b43,ssb_hcd 


**rfkill list all **
0: hp-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: yes

---

### Post by Hadaka on 2013-03-16
Hi, that first command is all one line.
please copy and paste the entire line.

```
lspci -nn | egrep '0200|0280'
```
thanks.

---

### Post by foltajr on 2013-03-16
lspci -nn | egrep '0200|0200'

08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/813 9c/8139C+  [10ec:8139] (rev 10)

---

### Post by Hadaka on 2013-03-16
Hi, this is what that command looks like when
issued as one single line.
code: lspci -nn | egrep '0200|0280'
 output example: from my pc

```
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
 
```
2 lines output.
please try again.

#   lspci -nn | egrep 'zero-two-zero-zero|zero-two-eight-zero'  <- example,,Not a ccommand

thanks.

---

### Post by foltajr on 2013-03-16
06:00.0 Network controller [0280]:Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
08:08.0 Ethernet controller [0200]:Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139](rev 10)

---

### Post by Hadaka on 2013-03-16
Hi, thanks ! do you have a function key as in
fn/f2 to turn on/off your wireless, I see that its
hardblocked. If you know the key fucntion please 
press it one time. also please do..
for ease please copy and paste the commands.
```
sudo rfkill unblock all
sudo apt-get install linux-firmware-nonfree
modprobe b43
```
thanks.

---

### Post by foltajr on 2013-03-17
It says it was unable to locate for the second command. There is a wireless button that you can push and it lights up however its not working either

---

### Post by wildmanne39 on 2013-03-17
"Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

---

