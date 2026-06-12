---
title: "windows wireless vs ubuntu"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by aeronutt on 2011-12-18
I travel by train about once a month. Trying to use the trains wifi via Ubuntu is fruitless. It finds the signal but reports a low signal strength and web pages are not found/connected. With Windows however, it all works fine (but obviously slowly).

Any ideas? This is certainly frustrating having to use Windows to use the lower strength wifi connections. (I'm using Windows to post this.)

---

### Post by TBABill on 2011-12-18
Do you have wireless in Ubuntu setup properly? Which device is it and what driver are you using?

---

### Post by praseodym on 2011-12-18
Did you check the mtu-values of those providers on tour? Set the mtu-value as number instead of "Automatic". Alternatively try Wicd instead of the network-manager. It can handle mixed/WEP/no encryption of public networks much better than the NM:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```
Choose whatever
```
iwconfig

```shows as wireless interface (e.g. **wlan0**) and **wext** as driver in Wicd.

---

### Post by inobe on 2011-12-18
i found that clearing previous connections eliminates these issues.

---

### Post by aeronutt on 2011-12-18
Thanks for the quick help folks. I'm having to reboot between windows and Ubuntu to answer your questions. From the following commands, here's what I see:

```
$ sudo lshw -short
                description: Wireless interface
                product: Centrino Wireless-N 1030
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 34
                serial: xx:xx:xx:xx:xx:xx
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=17.168.5.1 build 33993 ip=xx.xx.xx.xxx latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

```

```
$ iwconfig

wlan0     IEEE 802.11bgn  ESSID:"AmtrakConnect"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:76   Missed beacon:0


```

---

### Post by praseodym on 2011-12-18
The N-mode of the driver is buggy, deactivate it:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
There is also a bug with the country code settings (only 15 dBm in "iwconfig"):
```
sudo apt-get install iw
iw reg get
sudo iw reg set US # US for United States, you may adjust it
```
Check:
```
iwconfig
iwlist chan
```

---

### Post by aeronutt on 2011-12-18
> **praseodym said:**
> The N-mode of the driver is buggy, deactivate it:

```
echo "options iwlagn 11n_disable=1" | sudo tee /etc/modprobe.d/iwlagn.conf
sudo modprobe -rfv iwlagn
sudo modprobe -v iwlagn
```
There is also a bug with the country code settings (only 15 dBm in "iwconfig"):
```
sudo apt-get install iw
iw reg get
sudo iw reg set US # US for United States, you may adjust it
```
Check:
```
iwconfig
iwlist chan
```

Thanks praseodym, I'll give this a try and see how it works.

---

### Post by aeronutt on 2011-12-19
Here's what I get with those 2 commands. I'll check performance on my home wifi this evening. Note that "Tx-Power=15 dBm" didn't change, if that was supposed to.

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HomeRandom2"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:25:9C:20:9C:30   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:92   Missed beacon:0

```

```
$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)

```

---

### Post by aeronutt on 2012-01-14
Well, here I am on the train again. Ubuntu wireless won't reliably connect. Windows connects fine (but slow). This is what drives me crazy about Ubuntu. Something as fundamental as wireless connection. FYI, I've tried all the above recommendations, and have tried wicd, none have helped.

Any other ideas?

---

### Post by praseodym on 2012-01-15
Try to update the driver with the latest Linux-wireless version

---

### Post by aeronutt on 2012-01-15
> **praseodym said:**
> Try to update the driver with the latest Linux-wireless version

I'd love to try that, where would I find it?

---

### Post by praseodym on 2012-01-15
Here

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/)

---

### Post by aeronutt on 2012-01-16
I ran "lshw -C network" before and afer installing compat-wireless-2012-01-15.tar.bz2, and there was no difference, both revealed the same driver version:


description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: xxxxxxxxxxxxxxxxx
       width: 64 bits
       clock: 33MHz
configuration: broadcast=yes **driver=iwlagn driverversion=3.0.0-12-generic firmware=17.168.5.1 build 33993**

---

### Post by praseodym on 2012-01-16
Try the drivers from the latest kernels:

[http://www.linuxwireless.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases](http://www.linuxwireless.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases)

---

### Post by aeronutt on 2012-01-16
Thanks!  I'll keep trying! :)

---

### Post by aeronutt on 2012-01-16
> **praseodym said:**
> Try the drivers from the latest kernels:

[http://www.linuxwireless.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases](http://www.linuxwireless.org/en/users/Download/stable/#compat-wireless_3.2_stable_releases)

Well crap..that didn't work. Looks like the drivers don't load or aren't recognized. 
sudo lshw -C network shows:

 description: Network controller
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7a00000-f7a01fff

---

### Post by praseodym on 2012-01-16
Did you reboot? Check after that:

```
iwconfig
lsmod
sudo iwlist scan
modinfo iwlagn | egrep 'versi|filen'
locate iwlagn.ko | grep lib
dmesg | grep iwl
```

---

### Post by aeronutt on 2012-01-17
Yea, always rebooted after running 'sudo make install' of the drivers.
Here are the results of the commands after installing compat-wireless-3.2-1-s.tar.bz2

Thanks again for all the help!

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
$ lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
binfmt_misc            17540  1 
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
mac80211              319705  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  566711  3 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
cfg80211              204021  1 mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 dell_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
radeon               1015995  0 
uvcvideo               72711  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
ttm                    76805  1 radeon
drm_kms_helper         42558  2 i915,radeon
drm                   236330  6 i915,radeon,ttm,drm_kms_helper
psmouse                77381  0 
serio_raw              13166  0 
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13423  2 i915,radeon
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               78641  0 
r8169                  52788  0 
```

```
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

```

$ modinfo iwlagn | egrep 'versi|filen'
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
version:        in-tree:
srcversion:     F1AF2D897D96C14B77FE0BA
vermagic:       3.0.0-12-generic SMP mod_unload modversions 

```

```

$ locate iwlagn.ko | grep lib
/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko

```

```

$ dmesg | grep iwl
[   19.051854] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_session
[   19.051859] iwlagn: Unknown symbol ieee80211_stop_tx_ba_session (err -22)
[   19.051870] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   19.051872] iwlagn: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err -22)
[   19.051885] iwlagn: disagrees about version of symbol ieee80211_chswitch_done
[   19.051887] iwlagn: Unknown symbol ieee80211_chswitch_done (err -22)
[   19.051910] iwlagn: disagrees about version of symbol ieee80211_free_hw
[   19.051912] iwlagn: Unknown symbol ieee80211_free_hw (err -22)
[   19.051931] iwlagn: disagrees about version of symbol ieee80211_alloc_hw
[   19.051933] iwlagn: Unknown symbol ieee80211_alloc_hw (err -22)
[   19.051940] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[   19.051942] iwlagn: Unknown symbol ieee80211_start_tx_ba_session (err -22)
[   19.051950] iwlagn: disagrees about version of symbol ieee80211_register_hw
[   19.051952] iwlagn: Unknown symbol ieee80211_register_hw (err -22)
[   19.051960] iwlagn: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   19.051962] iwlagn: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   19.051965] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[   19.051967] iwlagn: Unknown symbol ieee80211_restart_hw (err -22)
[   19.051972] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[   19.051974] iwlagn: Unknown symbol ieee80211_rate_control_unregister (err -22)
[   19.051977] iwlagn: disagrees about version of symbol __ieee80211_get_radio_led_name
[   19.051979] iwlagn: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   19.051986] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[   19.051988] iwlagn: Unknown symbol ieee80211_wake_queue (err -22)
[   19.052003] iwlagn: Unknown symbol ieee80211_get_tkip_key (err 0)
[   19.052011] iwlagn: disagrees about version of symbol ieee80211_find_sta
[   19.052013] iwlagn: Unknown symbol ieee80211_find_sta (err -22)
[   19.052021] iwlagn: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   19.052023] iwlagn: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   19.052029] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   19.052031] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   19.052046] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   19.052048] iwlagn: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err -22)
[   19.052069] iwlagn: disagrees about version of symbol ieee80211_sta_block_awake
[   19.052071] iwlagn: Unknown symbol ieee80211_sta_block_awake (err -22)
[   19.052076] iwlagn: disagrees about version of symbol ieee80211_remain_on_channel_expired
[   19.052078] iwlagn: Unknown symbol ieee80211_remain_on_channel_expired (err -22)
[   19.052083] iwlagn: disagrees about version of symbol ieee80211_rx
[   19.052085] iwlagn: Unknown symbol ieee80211_rx (err -22)
[   19.052094] iwlagn: disagrees about version of symbol ieee80211_wake_queues
[   19.052096] iwlagn: Unknown symbol ieee80211_wake_queues (err -22)
[   19.052098] iwlagn: disagrees about version of symbol ieee80211_rate_control_register
[   19.052100] iwlagn: Unknown symbol ieee80211_rate_control_register (err -22)
[   19.052124] iwlagn: disagrees about version of symbol ieee80211_stop_queue
[   19.052126] iwlagn: Unknown symbol ieee80211_stop_queue (err -22)
[   19.052129] iwlagn: disagrees about version of symbol ieee80211_ready_on_channel
[   19.052131] iwlagn: Unknown symbol ieee80211_ready_on_channel (err -22)
[   19.052134] iwlagn: disagrees about version of symbol ieee80211_stop_queues
[   19.052136] iwlagn: Unknown symbol ieee80211_stop_queues (err -22)
[   19.052148] iwlagn: disagrees about version of symbol ieee80211_scan_completed
[   19.052150] iwlagn: Unknown symbol ieee80211_scan_completed (err -22)
[   19.052159] iwlagn: disagrees about version of symbol rate_control_send_low
[   19.052161] iwlagn: Unknown symbol rate_control_send_low (err -22)
[   19.052168] iwlagn: disagrees about version of symbol ieee80211_unregister_hw
[   19.052170] iwlagn: Unknown symbol ieee80211_unregister_hw (err -22)
[   19.052175] iwlagn: disagrees about version of symbol ieee80211_beacon_get_tim
[   19.052177] iwlagn: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   19.052184] iwlagn: disagrees about version of symbol ieee80211_request_smps
[   19.052186] iwlagn: Unknown symbol ieee80211_request_smps (err -22)
$ 
```

---

### Post by praseodym on 2012-01-18
Tried

> sudo modprobe -v iwlagn
?

---

### Post by aeronutt on 2012-01-21
Not sure if this makes sense, but when I run "sudo modprobe -v iwlagn" using the standard (working) drivers, I get a *blank response*. When I run "sudo modprobe -v iwlagn" with the driver that isn't working ( compat-wireless-3.2-1-s), I get:

```

insmod /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 

FATAL: Error inserting iwlagn (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Invalid argument

```

---

### Post by praseodym on 2012-01-22
Check with that module:

> dmesg | grep iwl

---

### Post by aeronutt on 2012-01-22
Thanks for the help!
Ok, with compat-wireless-3.2-1-s loaded, I get:

```
dmesg | grep iwl 
```
```

[   19.631212] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_session
[   19.631218] iwlagn: Unknown symbol ieee80211_stop_tx_ba_session (err -22)
[   19.631235] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
[   19.631238] iwlagn: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe (err -22)
[   19.631259] iwlagn: disagrees about version of symbol ieee80211_chswitch_done
[   19.631262] iwlagn: Unknown symbol ieee80211_chswitch_done (err -22)
[   19.631297] iwlagn: disagrees about version of symbol ieee80211_free_hw
[   19.631300] iwlagn: Unknown symbol ieee80211_free_hw (err -22)
[   19.631327] iwlagn: disagrees about version of symbol ieee80211_alloc_hw
[   19.631331] iwlagn: Unknown symbol ieee80211_alloc_hw (err -22)
[   19.631342] iwlagn: disagrees about version of symbol ieee80211_start_tx_ba_session
[   19.631345] iwlagn: Unknown symbol ieee80211_start_tx_ba_session (err -22)
[   19.631358] iwlagn: disagrees about version of symbol ieee80211_register_hw
[   19.631362] iwlagn: Unknown symbol ieee80211_register_hw (err -22)
[   19.631373] iwlagn: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   19.631377] iwlagn: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   19.631382] iwlagn: disagrees about version of symbol ieee80211_restart_hw
[   19.631385] iwlagn: Unknown symbol ieee80211_restart_hw (err -22)
[   19.631393] iwlagn: disagrees about version of symbol ieee80211_rate_control_unregister
[   19.631396] iwlagn: Unknown symbol ieee80211_rate_control_unregister (err -22)
[   19.631401] iwlagn: disagrees about version of symbol __ieee80211_get_radio_led_name
[   19.631404] iwlagn: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   19.631415] iwlagn: disagrees about version of symbol ieee80211_wake_queue
[   19.631418] iwlagn: Unknown symbol ieee80211_wake_queue (err -22)
[   19.631458] iwlagn: Unknown symbol ieee80211_get_tkip_key (err 0)
[   19.631470] iwlagn: disagrees about version of symbol ieee80211_find_sta
[   19.631472] iwlagn: Unknown symbol ieee80211_find_sta (err -22)
[   19.631484] iwlagn: disagrees about version of symbol ieee80211_tx_status_irqsafe
[   19.631488] iwlagn: Unknown symbol ieee80211_tx_status_irqsafe (err -22)
[   19.631496] iwlagn: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   19.631499] iwlagn: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   19.631521] iwlagn: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
[   19.631525] iwlagn: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe (err -22)
[   19.631555] iwlagn: disagrees about version of symbol ieee80211_sta_block_awake
[   19.631559] iwlagn: Unknown symbol ieee80211_sta_block_awake (err -22)
[   19.631567] iwlagn: disagrees about version of symbol ieee80211_remain_on_channel_expired
[   19.631571] iwlagn: Unknown symbol ieee80211_remain_on_channel_expired (err -22)
[   19.631579] iwlagn: disagrees about version of symbol ieee80211_rx
[   19.631582] iwlagn: Unknown symbol ieee80211_rx (err -22)
[   19.631595] iwlagn: disagrees about version of symbol ieee80211_wake_queues
[   19.631599] iwlagn: Unknown symbol ieee80211_wake_queues (err -22)
[   19.631604] iwlagn: disagrees about version of symbol ieee80211_rate_control_register
[   19.631607] iwlagn: Unknown symbol ieee80211_rate_control_register (err -22)
[   19.631642] iwlagn: disagrees about version of symbol ieee80211_stop_queue
[   19.631645] iwlagn: Unknown symbol ieee80211_stop_queue (err -22)
[   19.631650] iwlagn: disagrees about version of symbol ieee80211_ready_on_channel
[   19.631654] iwlagn: Unknown symbol ieee80211_ready_on_channel (err -22)
[   19.631659] iwlagn: disagrees about version of symbol ieee80211_stop_queues
[   19.631662] iwlagn: Unknown symbol ieee80211_stop_queues (err -22)
[   19.631680] iwlagn: disagrees about version of symbol ieee80211_scan_completed
[   19.631683] iwlagn: Unknown symbol ieee80211_scan_completed (err -22)
[   19.631697] iwlagn: disagrees about version of symbol rate_control_send_low
[   19.631701] iwlagn: Unknown symbol rate_control_send_low (err -22)
[   19.631711] iwlagn: disagrees about version of symbol ieee80211_unregister_hw
[   19.631714] iwlagn: Unknown symbol ieee80211_unregister_hw (err -22)
[   19.631722] iwlagn: disagrees about version of symbol ieee80211_beacon_get_tim
[   19.631725] iwlagn: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   19.631735] iwlagn: disagrees about version of symbol ieee80211_request_smps
[   19.631738] iwlagn: Unknown symbol ieee80211_request_smps (err -22)

```

---

### Post by praseodym on 2012-01-22
Remove the compat-wireless version via:

```
sudo rm -r /lib/modules/$(uname -r)/updates/net/
sudo depmod -a
sudo update-initramfs -u
```
and try an earlier version. Sometimes the module **dell_laptop** is buggy, try to blacklist it:

```
echo "blacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-dell.conf
```
and reboot. If the computer is not working in any way after that, boot into the recovery mode and remove this file:

```
rm /etc/modprobe.d/blacklist-dell.conf
reboot
```

---

