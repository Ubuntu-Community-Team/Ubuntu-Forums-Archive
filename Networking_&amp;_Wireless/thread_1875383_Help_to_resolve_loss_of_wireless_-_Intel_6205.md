---
title: "Help to resolve loss of wireless - Intel 6205"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by simeonipicker on 2011-11-04
Hi,

I'm looking for some troubleshooting tips with my wireless. I tried to follow some instructions to load the latest wireless drivers for 6205 via compat-wireless. Everything was going fine and I successfully compiled and installed drivers, I unloadeded my old drivers and now I cant get any wireless working at all.

I'd appreciate any help on where I even start to try and debug the problem?

Thanks in advance

---

### Post by praseodym on 2011-11-04
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
sudo iwlist scan
```

---

### Post by simeonipicker on 2011-11-04
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
sudo iwlist scan
```

simon@simon-ubuntu:~$ **lspci -nnk | grep -iA2 net**
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
	Subsystem: Lenovo Device [17aa:21ce]
	Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
	Kernel modules: iwlagn
simon@simon-ubuntu:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

simon@simon-ubuntu:~$ **rfkill list**
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
simon@simon-ubuntu:~$ **lsmod**
Module                  Size  Used by
bnep                   17711  2 
rfcomm                 37292  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
vesafb                 13489  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  4 
nvidia              10390874  45 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
uvcvideo               67271  0 
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
videodev               85626  1 uvcvideo
psmouse                63474  0 
serio_raw              12990  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              281428  0 
btusb                  17912  2 
snd_rawmidi            25241  1 snd_seq_midi
bluetooth             151637  23 bnep,rfcomm,btusb
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              173231  1 mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
thinkpad_acpi          73942  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nvram                  14029  1 thinkpad_acpi
tpm_tis                14002  0 
video                  18908  0 
wmi                    18744  0 
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
mei                    36466  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
xhci_hcd               72957  0 
ahci                   21634  2 
libahci                25761  1 ahci
firewire_ohci          35846  0 
sdhci_pci              13658  0 
firewire_core          56937  1 firewire_ohci
e1000e                139775  0 
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
simon@simon-ubuntu:~$ **sudo iwlist scan**
[sudo] password for simon: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

simon@simon-ubuntu:~$

---

### Post by praseodym on 2011-11-04
First of all, the driver has to be loaded:

```
sudo modprobe -v iwlagn
```
If you are using Ubuntu 11.10 with kernel 3 you should _first_ shut off the N-mode (driver bug):

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
```

---

### Post by simeonipicker on 2011-11-04
> **praseodym said:**
> First of all, the driver has to be loaded:

```
sudo modprobe -v iwlagn
```
If you are using Ubuntu 11.10 with kernel 3 you should _first_ shut off the N-mode (driver bug):

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
```
Ok, I tried what you said and got:

simon@simon-ubuntu:~$ sudo modprobe -v iwlagn
insmod /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument
simon@simon-ubuntu:~$

---

### Post by praseodym on 2011-11-04
Error messages?

```
dmesg | grep iwl
```

---

### Post by simeonipicker on 2011-11-04
Thanks. Did that and got:

simon@simon-ubuntu:~$ dmesg | grep iwl
[   14.609373] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_session
[   14.609388] iwlagn: Unknown symbol ieee80211_stop_tx_ba_session (err -22)
[   14.609451] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   14.609461] iwlagn: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err -22)
[   14.609537] iwlagn: disagrees about version of symbol ieee80211_chswitch_done
[   14.609546] iwlagn: Unknown symbol ieee80211_chswitch_done (err -22)
[   14.609734] iwlagn: disagrees about version of symbol ieee80211_free_hw
[   14.609743] iwlagn: Unknown symbol ieee80211_free_hw (err -22)
[   14.609828] iwlagn: disagrees about version of symbol ieee80211_alloc_hw
[   14.609836] iwlagn: Unknown symbol ieee80211_alloc_hw (err -22)
[   14.609868] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[   14.609881] iwlagn: Unknown symbol ieee80211_start_tx_ba_session (err -22)
[   14.609932] iwlagn: disagrees about version of symbol ieee80211_register_hw
[   14.609945] iwlagn: Unknown symbol ieee80211_register_hw (err -22)
[   14.609985] iwlagn: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   14.609994] iwlagn: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   14.610026] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[   14.610033] iwlagn: Unknown symbol ieee80211_restart_hw (err -22)
[   14.610056] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[   14.610064] iwlagn: Unknown symbol ieee80211_rate_control_unregister (err -22)
[   14.610081] iwlagn: disagrees about version of symbol __ieee80211_get_radio_led_name
[   14.610089] iwlagn: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   14.610115] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[   14.610122] iwlagn: Unknown symbol ieee80211_wake_queue (err -22)
[   14.610158] iwlagn: Unknown symbol ieee80211_get_tkip_key (err 0)
[   14.610191] iwlagn: disagrees about version of symbol ieee80211_find_sta
[   14.610199] iwlagn: Unknown symbol ieee80211_find_sta (err -22)
[   14.610245] iwlagn: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   14.610254] iwlagn: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   14.610276] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   14.610284] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   14.610353] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   14.610360] iwlagn: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err -22)
[   14.610561] iwlagn: disagrees about version of symbol ieee80211_sta_block_awake
[   14.610571] iwlagn: Unknown symbol ieee80211_sta_block_awake (err -22)
[   14.610603] iwlagn: disagrees about version of symbol ieee80211_remain_on_channel_expired
[   14.610610] iwlagn: Unknown symbol ieee80211_remain_on_channel_expired (err -22)
[   14.610636] iwlagn: disagrees about version of symbol ieee80211_rx
[   14.610643] iwlagn: Unknown symbol ieee80211_rx (err -22)
[   14.610730] iwlagn: disagrees about version of symbol ieee80211_wake_queues
[   14.610738] iwlagn: Unknown symbol ieee80211_wake_queues (err -22)
[   14.610753] iwlagn: disagrees about version of symbol ieee80211_rate_control_register
[   14.610762] iwlagn: Unknown symbol ieee80211_rate_control_register (err -22)
[   14.610966] iwlagn: disagrees about version of symbol ieee80211_stop_queue
[   14.610975] iwlagn: Unknown symbol ieee80211_stop_queue (err -22)
[   14.610991] iwlagn: disagrees about version of symbol ieee80211_ready_on_channel
[   14.610999] iwlagn: Unknown symbol ieee80211_ready_on_channel (err -22)
[   14.611029] iwlagn: disagrees about version of symbol ieee80211_stop_queues
[   14.611037] iwlagn: Unknown symbol ieee80211_stop_queues (err -22)
[   14.611098] iwlagn: disagrees about version of symbol ieee80211_scan_completed
[   14.611106] iwlagn: Unknown symbol ieee80211_scan_completed (err -22)
[   14.611142] iwlagn: disagrees about version of symbol rate_control_send_low
[   14.611150] iwlagn: Unknown symbol rate_control_send_low (err -22)
[   14.611178] iwlagn: disagrees about version of symbol ieee80211_unregister_hw
[   14.611185] iwlagn: Unknown symbol ieee80211_unregister_hw (err -22)
[   14.611205] iwlagn: disagrees about version of symbol ieee80211_beacon_get_tim
[   14.611214] iwlagn: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   14.611242] iwlagn: disagrees about version of symbol ieee80211_request_smps
[   14.611250] iwlagn: Unknown symbol ieee80211_request_smps (err -22)
simon@simon-ubuntu:~$ 

Doesn't look healthy!

---

### Post by praseodym on 2011-11-04
No, it doesnt. Uninstall the driver:

```
make clean
make
sudo make uninstall
sudo rm -r /lib/modules/$(uname -r)/updates/net/
sudo depmod -a
sudo update-initramfs -u
```
Reboot and show
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
uname -a
lsmod
sudo iwlist scan
dmesg | grep iwl
```
again

---

### Post by simeonipicker on 2011-11-04
That's actually got it working now! I'm going to disable N as per you said and hopefully, it should be ok.

Thank you!

---

### Post by praseodym on 2011-11-04
You're welcome. Is that 11.10? Dont forget to set the thread "solved" by editing the first posting.

---

### Post by simeonipicker on 2011-11-04
Yes it's 11.10. Now to try and fix poor flash performance....

marked as solved

---

