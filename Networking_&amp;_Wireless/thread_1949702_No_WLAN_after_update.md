---
title: "No WLAN after update"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by tuximero on 2012-03-30
I recently updated my ubuntu 11.10 system running on a ThinkPad T410 using the package manager incl. linux kernel 3.0.0-17.

After doing a reboot my wlan is corrupted.

I am able to find out that the corresponding module iwlagn has not been loaded.

Trying to install manually leads to the following error message:
```

> sudo modprobe -v iwlagn
insmod /lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument

```

There are a couple of error messages in dmesg too:
```

> dmesg | grep iwlagn
[   38.267297] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_session
[   38.267302] iwlagn: Unknown symbol ieee80211_stop_tx_ba_session (err -22)
[   38.267316] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   38.267318] iwlagn: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err -22)
[   38.267337] iwlagn: disagrees about version of symbol ieee80211_chswitch_done
[   38.267339] iwlagn: Unknown symbol ieee80211_chswitch_done (err -22)
[   38.267370] iwlagn: disagrees about version of symbol ieee80211_free_hw
[   38.267372] iwlagn: Unknown symbol ieee80211_free_hw (err -22)
[   38.267395] iwlagn: disagrees about version of symbol ieee80211_alloc_hw
[   38.267397] iwlagn: Unknown symbol ieee80211_alloc_hw (err -22)
[   38.267405] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[   38.267407] iwlagn: Unknown symbol ieee80211_start_tx_ba_session (err -22)
[   38.267418] iwlagn: disagrees about version of symbol ieee80211_register_hw
[   38.267420] iwlagn: Unknown symbol ieee80211_register_hw (err -22)
[   38.267432] iwlagn: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   38.267434] iwlagn: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   38.267438] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[   38.267440] iwlagn: Unknown symbol ieee80211_restart_hw (err -22)
[   38.267447] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[   38.267449] iwlagn: Unknown symbol ieee80211_rate_control_unregister (err -22)
[   38.267453] iwlagn: disagrees about version of symbol __ieee80211_get_radio_led_name
[   38.267455] iwlagn: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   38.267464] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[   38.267466] iwlagn: Unknown symbol ieee80211_wake_queue (err -22)
[   38.267491] iwlagn: Unknown symbol ieee80211_get_tkip_key (err 0)
[   38.267500] iwlagn: disagrees about version of symbol ieee80211_find_sta
[   38.267502] iwlagn: Unknown symbol ieee80211_find_sta (err -22)
[   38.267511] iwlagn: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   38.267513] iwlagn: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   38.267524] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   38.267526] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   38.278635] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   38.278639] iwlagn: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err -22)
[   38.278704] iwlagn: disagrees about version of symbol ieee80211_sta_block_awake
[   38.278707] iwlagn: Unknown symbol ieee80211_sta_block_awake (err -22)
[   38.278717] iwlagn: disagrees about version of symbol ieee80211_remain_on_channel_expired
[   38.278719] iwlagn: Unknown symbol ieee80211_remain_on_channel_expired (err -22)
[   38.278733] iwlagn: disagrees about version of symbol ieee80211_rx
[   38.278735] iwlagn: Unknown symbol ieee80211_rx (err -22)
... and so on...

```

I have no clue what I can do to repair this thing. I would really appreciate any expert advise on this.

Here is some info about my system environment:
```

> uname -a
Linux speedy 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

> lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

> lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
	Subsystem: Lenovo Device [17aa:2153]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)
	Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
	Kernel modules: iwlagn

> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


> rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

> lsmod
Module                  Size  Used by
hidp                   22326  0 
hid                    95463  1 hidp
tp_smapi               28400  0 
thinkpad_ec            14449  1 tp_smapi
bnep                   18139  2 
rfcomm                 46621  12 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18288  2 
bluetooth             168639  24 hidp,bnep,rfcomm,btusb
joydev                 17693  0 
snd_hda_codec_hdmi     32040  4 
snd_hda_codec_conexant    62197  1 
mxm_wmi                12979  0 
nvidia              11713772  125 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
thinkpad_acpi          81819  0 
nvram                  14413  1 thinkpad_acpi
tpm_tis                18546  0 
mac80211              492160  0 
wmi                    19256  1 mxm_wmi
cfg80211              204021  1 mac80211
snd                    68266  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
soundcore              12680  1 snd
intel_ips              18089  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
xts                    12756  4 
lrw                    12756  0 
gf128mul               14951  2 xts,lrw
dm_crypt               23199  1 
aesni_intel            55586  16 
cryptd                 20530  5 aesni_intel
aes_x86_64             17208  1 aesni_intel
vesafb                 13809  1 
video                  19412  0 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
firewire_ohci          40722  0 
ahci                   26002  4 
libahci                26861  1 ahci
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                160582  0 

> iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

---

### Post by titantux on 2012-03-30
Hi, as workaround I had to roll back to use previously kernel 3.0.0-16-generic. :( 

I've tryed as well setting all those paremeters with 0 but same issue:

FATAL: Error inserting iwlagn (/lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument

Regards,
titantux

---

### Post by tuximero on 2012-03-31
Hi titantux,

your're a real titan! Thanks for the tip!

Selecting 3.0.0-16 from grub menu works just like before.

I never the less hope there will be a fix for this problem in the near future. I'm really curious if there are not a lot more people having the same issue...

---

### Post by praseodym on 2012-03-31
Please show

> dmesg | grep iwl

---

### Post by tuximero on 2012-03-31
I have already shown dmesg | grep iwlagn in my first post. I hope this shows the relevant messages.

I'm currently back to using kernel 3.0.0-16 which works fine like before. If you need another look at dmesg I have to reboot again and post it here.

This is what I've got on using 3.0.0-17:
```

> dmesg | grep iwlagn
[   38.267297] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_session
[   38.267302] iwlagn: Unknown symbol ieee80211_stop_tx_ba_session (err -22)
[   38.267316] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   38.267318] iwlagn: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err -22)
[   38.267337] iwlagn: disagrees about version of symbol ieee80211_chswitch_done
[   38.267339] iwlagn: Unknown symbol ieee80211_chswitch_done (err -22)
[   38.267370] iwlagn: disagrees about version of symbol ieee80211_free_hw
[   38.267372] iwlagn: Unknown symbol ieee80211_free_hw (err -22)
[   38.267395] iwlagn: disagrees about version of symbol ieee80211_alloc_hw
[   38.267397] iwlagn: Unknown symbol ieee80211_alloc_hw (err -22)
[   38.267405] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[   38.267407] iwlagn: Unknown symbol ieee80211_start_tx_ba_session (err -22)
[   38.267418] iwlagn: disagrees about version of symbol ieee80211_register_hw
[   38.267420] iwlagn: Unknown symbol ieee80211_register_hw (err -22)
[   38.267432] iwlagn: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   38.267434] iwlagn: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   38.267438] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[   38.267440] iwlagn: Unknown symbol ieee80211_restart_hw (err -22)
[   38.267447] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[   38.267449] iwlagn: Unknown symbol ieee80211_rate_control_unregister (err -22)
[   38.267453] iwlagn: disagrees about version of symbol __ieee80211_get_radio_led_name
[   38.267455] iwlagn: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   38.267464] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[   38.267466] iwlagn: Unknown symbol ieee80211_wake_queue (err -22)
[   38.267491] iwlagn: Unknown symbol ieee80211_get_tkip_key (err 0)
[   38.267500] iwlagn: disagrees about version of symbol ieee80211_find_sta
[   38.267502] iwlagn: Unknown symbol ieee80211_find_sta (err -22)
[   38.267511] iwlagn: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   38.267513] iwlagn: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   38.267524] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   38.267526] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   38.278635] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   38.278639] iwlagn: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err -22)
[   38.278704] iwlagn: disagrees about version of symbol ieee80211_sta_block_awake
[   38.278707] iwlagn: Unknown symbol ieee80211_sta_block_awake (err -22)
[   38.278717] iwlagn: disagrees about version of symbol ieee80211_remain_on_channel_expired
[   38.278719] iwlagn: Unknown symbol ieee80211_remain_on_channel_expired (err -22)
[   38.278733] iwlagn: disagrees about version of symbol ieee80211_rx
[   38.278735] iwlagn: Unknown symbol ieee80211_rx (err -22)
... and so on...

```

---

### Post by Zorael on 2012-03-31
Have you tried the backported wireless modules?
```
$ sudo apt-get install linux-backports-modules-cw-3.2-oneiric-generic linux-backports-modules-headers-oneiric-generic
```
Correct me if I'm wrong about the package names; I'm on 12.04 myself.

---

### Post by tuximero on 2012-03-31
No, I've not tested the backport modules.

I'm back to 3.0.0-16 for now which works fine.

May beI give it a try later on, but it's my main system which should just work without too much testing around with things I'm not able to estimate the results for myself.

I cannot believe that I am the only one around with this problem. It seems to me that there is something wrong within the kernel package of 3.0.0-17 because I have not done anything special around wifi settings.

---

### Post by Punica on 2012-04-02
I have the same problem as you have.

The problem is that you have compat-wireless installed, which apparantly is broken in 3.0.0-17. 

You can run -17 with working iwlagn by removing compat-wireless. This does introduce new problems though, at least for me, as the iwlagn is terrible in N modus whilest the iwlwifi driver is working great.

---

### Post by tuximero on 2012-04-02
Yes indeed you're right. Thanks for the hint. I've installed the compat-wireless package while trying to work around this ugly wifi bug.

So now I may choose which bug fits better :-(

---

### Post by Punica on 2012-04-03
If you dont need wireless N you can modprobe it with the following options:

sudo modprobe iwlagn 11n_disable=1

This solves the instabilities, but ofcourse degrades your speed significantly.

---

### Post by tuximero on 2012-04-03
I've already evaluated this one but it's not really a difference. Without 11n_disable=1 there are more speed ups and downs but no real disconnection or very low performance.

There are many user experiences to be found in various forums belonging to very low performance. So I'm happy to go without this.

---

### Post by titantux on 2012-04-17
Hi again,
Searching over there found info within the BUG [871254]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/871254"). Basically workaorund still and is avoid to use the kernel 3.0.0-17. 

I've installed kernel 3.1.4-030104-generic, downloaded from here: [ Kernel 3.1.4-oneiric]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1.4-oneiric/")

So, you have to install them as usual, in my case was 64 bits:

```
# sudo dpkg -i linux-headers-3.1.4-030104-generic_3.1.4-030104.201111281851_amd64.deb
# sudo dpkg -i linux-headers-3.1.4-030104_3.1.4-030104.201111281851_all.deb
# sudo dpkg -i linux-image-3.1.4-030104-generic_3.1.4-030104.201111281851_amd64.deb
```

Then reboot and works again with different kernel...

```

titantux@titan-ThinkPad-T410:~$ dmesg | grep iw
[   17.002250] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.002259] iwlagn 0000:03:00.0: setting latency timer to 64
[   17.002290] iwlagn 0000:03:00.0: pci_resource_len = 0x00002000
[   17.002292] iwlagn 0000:03:00.0: pci_resource_base = ffffc90011090000
[   17.002294] iwlagn 0000:03:00.0: HW Revision ID = 0x35
[   17.002379] iwlagn 0000:03:00.0: irq 44 for MSI/MSI-X
[   17.002421] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   17.002487] iwlagn 0000:03:00.0: L1 Disabled; Enabling L0S
[   17.012414] iwlagn 0000:03:00.0: device EEPROM VER=0x436, CALIB=0x6
[   17.012416] iwlagn 0000:03:00.0: Device SKU: 0X1f0
[   17.012444] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.012533] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   17.441937] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532
[   17.523795] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   60.192976] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.
[   60.395665] iwlagn 0000:03:00.0: L1 Disabled; Enabling L0S
[   60.395798] iwlagn 0000:03:00.0: Radio type=0x1-0x3-0x1
[   60.631787] iwlagn 0000:03:00.0: L1 Disabled; Enabling L0S
[   60.631919] iwlagn 0000:03:00.0: Radio type=0x1-0x3-0x1
titantux@titan-ThinkPad-T410:~$ uname -r
3.1.4-030104-generic
titantux@titan-ThinkPad-T410:~$ 

```

:popcorn:

---

### Post by tuximero on 2012-04-17
Installed that one and have to say: It just works :-)

Thanks for sharing this.

=D>

---

