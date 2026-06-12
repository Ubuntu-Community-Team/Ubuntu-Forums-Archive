---
title: "Problem with Broadcom 4313 l4e4:4727 wireless card"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by SpenserWilde on 2012-01-18
Hi all. 

I have a new *HP Pavilion 9 series* with a **Broadcom 4313 wireless card**.

It detects the wireless connection, but it doesn't recieve the whole signal.
I am setting right next to the reuter, yet still it gives me a very low connection strength (80% at best, but most of the time it never exceeds 50-60%).

Also sometimes it just refuses to connect, and when it does, the internet speed is extremely slow, not a single web page loads.

--

Here are some information that you might find useful:

*lspci -nn | grep 0280*:
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
[/CODE]

*lsmod | grep -e b43 -e ssb -e wl*:
```
wl                   2646601  0 
lib80211               14570  1 wl

```

*dmesg | grep -e b43 -e ssb -e wl*:
```
[    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC      /166F, BIOS F.33 08/30/2011
[   19.318735] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.844607] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
[   19.844613] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
[   19.845776] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
[   19.845967] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

*rfkill list all*:
```
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

```

*lsmod*:
```
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
joydev                 17393  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
uvcvideo               67271  0 
snd_rawmidi            25241  1 snd_seq_midi
videodev               85626  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                63474  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
brcmsmac              591864  0 
rts_pstor             353227  0 
brcmutil               16885  1 brcmsmac
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393459  1 brcmsmac
cfg80211              172392  2 brcmsmac,mac80211
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
crc_ccitt              12595  1 brcmsmac
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
i915                  509290  3 
wmi                    18744  1 hp_wmi
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
r8169                  47200  0 
video                  18908  1 i915

```

*sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35*:
```
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <warn> Activation (wlan0) failed.
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) starting connection 'Thomson02A862'
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0/wireless): access point 'Thomson02A862' has security, but secrets are required.
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <warn> Activation (wlan0) failed for access point (Thomson02A862)
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <warn> Activation (wlan0) failed.
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 05:08:18 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) starting connection 'Thomson02A862'
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0/wireless): access point 'Thomson02A862' has security, but secrets are required.
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <warn> Activation (wlan0) failed for access point (Thomson02A862)
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <warn> Activation (wlan0) failed.
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 19 05:08:19 saad-HP-Pavilion-g6-Notebook-PC NetworkManager[884]: <info> (wlan0): deactivating device (reason 'none') [0]

```

I'm not able to provide some of these (and other) information through the wireless connection because it's currently refusing to connect to it.

Please help.
Thank you very much.

---
**EDIT:**

Here are some more information about the wireless card:

*lspci -nnk | grep -iA2 net*:
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Hewlett-Packard Company Device [103c:1795]
        Kernel driver in use: brcmsmac
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
        Subsystem: Hewlett-Packard Company Device [103c:166f]
        Kernel driver in use: r8169

```

---

### Post by wildmanne39 on 2012-01-19
Hi, please do this:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

---

### Post by SpenserWilde on 2012-01-19
> **wildmanne39 said:**
> Hi, please do this:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

Okay, great!

It recieves the whole signal now!
However, it's still not able to connect for some reason.

When my connection is secure (WPA1/2 Preshared Key), the problem was *a bad password*.
But when I disabled the encryption, it says it couldn't obtain the IP adress.

Note: I'm using *Wicd* here.

---

### Post by SpenserWilde on 2012-01-19
> **wildmanne39 said:**
> Hi, please do this:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

> **wildmanne39 said:**
> Hi, please do this:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot
Thanks

Okay, great!

It recieves the whole signal now!
However, it's still not able to connect for some reason.

When my connection is secure (WPA1/2 Preshared Key), the problem was *a bad password*.
But when I disabled the encryption, it says it couldn't recieve the IP adress.

---

### Post by wildmanne39 on 2012-01-19
Hi, I am not an expert on wicd but you can set a static ip or I believe the setting dhcp needs to be dhclient in wicd.

Also it would be best if you set your encryption in your router to WPA2 AES if possible.

If this does not help please post the output of:
```
nm-tool
```
```
sudo iwlist scan
```
```
lsmod | grep wl
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eht1 -etork | tail -n55
```

---

