---
title: "Enterprise Wireless Xubuntu 12.10 not working"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by rolfinator on 2013-04-12
Hey there!

I just moved from normal Ubuntu 12.04 to Xubuntu 12.10. I don't like Unity, so xfce is a very cool choice :)
On the other site, I noticed, that I am no more able to connect to our University wireless (eduroum -> maybe somebody knows it). It's an enterprise authentication system.
Before I created this thread, some things were checked:
- searched the forum, where some suggestions for similiar problems were discussed -> nothing helped for me (for example, disabling the N-standard of the wireless chip)
- making sure, that the password and username are correct (REALLY checked it :D )
- tried a connection from the windows partition, to make sure the wireless chip is not broken
- tried to connect to any other (normal authentication scheme (open, WEP, WPA, WPA2-Personal) wireless -> with success

May some experts here know a solution...it's quite annoying to have no internet here^^

Some executed commands:
lspci -nnk | grep -i net -A2:
```

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
        Subsystem: Lenovo Device [17aa:21f3]
        Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
        Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
        Kernel driver in use: iwlwifi

```

lsmod:
```
Module                  Size  Used by
usb_storage            48834  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
joydev                 17458  0 
pci_stub               12623  1 
vboxpci                23195  0 
vboxnetadp             25671  0 
vboxnetflt             23480  0 
vboxdrv               287190  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_intel          33492  4 
bnep                   18141  2 
parport_pc             32689  0 
rfcomm                 46620  16 
coretemp               13401  0 
ppdev                  17074  0 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
thinkpad_acpi          81199  1 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
snd_seq_midi           13325  0 
aes_x86_64             17256  1 aesni_intel
snd_rawmidi            30513  1 snd_seq_midi
arc4                   12530  2 
uvcvideo               76750  0 
btusb                  22475  0 
videobuf2_core         32852  1 uvcvideo
snd_seq_midi_event     14900  1 snd_seq_midi
psmouse                95595  0 
bluetooth             209249  22 bnep,rfcomm,btusb
videodev              120310  2 uvcvideo,videobuf2_core
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_vmalloc      12861  1 uvcvideo
i915                  520615  2 
videobuf2_memops       13405  1 videobuf2_vmalloc
iwlwifi               386799  0 
serio_raw              13216  0 
microcode              22804  0 
snd                    78921  21 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                18681  0 
nvram                  14363  1 thinkpad_acpi
wmi                    19071  0 
drm_kms_helper         49113  1 i915
mac80211              540032  1 iwlwifi
drm                   288721  3 i915,drm_kms_helper
i2c_algo_bit           13414  1 i915
cfg80211              206797  2 iwlwifi,mac80211
soundcore              15048  1 snd
mei                    40691  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
lpc_ich                17062  0 
video                  19391  1 i915
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
sdhci_pci              18617  0 
sdhci                  32646  1 sdhci_pci
ahci                   25721  2 
libahci                31192  1 ahci
e1000e                199273  0 

```

This is the logfile while trying to connect. Hopefully I didn't skip important parts (I masked some personal parts), while the real logfile is way longer ;)
```
Apr  4 12:56:19 x230kernel NetworkManager[889]: <info> (wlan0): disconnecting for new activation request.
Apr  4 12:56:19 x230kernel NetworkManager[889]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Apr  4 12:56:19 x230kernel NetworkManager[889]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1583
Apr  4 12:56:20 x230kernel NetworkManager[889]: <warn> DNS: plugin dnsmasq update failed
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> ((null)): removing resolv.conf from /sbin/resolvconf
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) starting connection 'eduroam 1'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0/wireless): connection 'eduroam 1' has security, and secrets exist.  No new secrets needed.
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'ssid' value 'eduroam'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'scan_ssid' value '1'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'key_mgmt' value 'WPA-EAP'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'auth_alg' value 'OPEN'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'password' value '<omitted>'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'eap' value 'TTLS'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'fragment_size' value '1300'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'identity' value 'student0815@student'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: added 'bgscan' value 'simple:30:-45:300'
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> Config: set interface ap_scan to 1
Apr  4 12:56:20 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr  4 12:56:23 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr  4 12:56:24 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr  4 12:56:24 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: associating -> associated
Apr  4 12:56:45 x230kernel NetworkManager[889]: <warn> Activation (wlan0/wireless): association took too long.
Apr  4 12:56:45 x230kernel NetworkManager[889]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr  4 12:56:45 x230kernel NetworkManager[889]: <warn> Activation (wlan0/wireless): asking for new secrets
Apr  4 12:56:45 x230kernel NetworkManager[889]: <info> (wlan0): supplicant interface state: associated -> disconnected
Apr  4 12:56:45 x230kernel NetworkManager[889]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr  4 12:56:59 x230kernel NetworkManager[889]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Activation (wlan0/wireless): connection 'eduroam 1' has security, and secrets exist.  No new secrets needed.
Apr  4 12:56:59 x230kernel NetworkManager[889]: <info> Config: added 'ssid' value 'eduroam'
```

If that's important: I am using a Lenovo X230 (as the kernel says^^).

If you need any more information or command outputs. Let me know!

Thanks for your help!

---

### Post by rolfinator on 2013-04-13
Hmmm...any suggestions?

---

