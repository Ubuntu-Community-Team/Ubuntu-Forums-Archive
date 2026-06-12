---
title: "Wireless connection in 12.04"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by IamNotANerd on 2013-03-06
Hi,

I can't get my wireless connection working properly. I have a Realtek RTL8111/8168B chip and when I connect to encrypted WPA network it just keeps connecting and after a while network manager asks network password again. 

What I've done so far:

- installed wicd (no success, says bad password, though it's not)
- installed r8168 (latest) driver from Realtek following this: [http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/](http://unixblogger.wordpress.com/2011/10/18/the-pain-of-an-realtek-rtl8111rtl8168-ethernet-card/)

Here's the output of sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 24
       serial: c4:85:08:0a:bb:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-37-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f7200000-f7201fff
```

I'm really in trouble, please help. Any help will be welcomed!

---

### Post by IamNotANerd on 2013-03-06
Oh, I can post outputs from terminal, just ask. I just dunno what commands to run...

---

### Post by praseodym on 2013-03-06
r8168 is your LAN driver. Wireless is Intel, driver "iwlwifi". There is a bug with the N-mode of the driver, therefore, deactivate it via:
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by IamNotANerd on 2013-03-06
Ok, I disabled n-mode (ran all of those commands) but still no connection. Wired works ok. 

> r8168 is your LAN driver.
Thanks for clarifying, praseodym!

Any other ideas? Thx for replying anyway :)

---

### Post by praseodym on 2013-03-06
Please show:
```

lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
route -n
sudo iwlist scan
```

---

### Post by IamNotANerd on 2013-03-06
OK, here's the output:

```
juha@spectre:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
btusb                  18332  2 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
joydev                 17693  0 
pn533                  17957  0 
nfc                    24827  1 pn533
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_usb_audio         122982  1 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hda_intel          33773  7 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  2 snd_usb_audio,snd_hda_codec
snd_pcm                97275  7 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  25 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97485  0 
usbhid                 47238  0 
hid                    99636  1 usbhid
iwlwifi               397059  0 
serio_raw              13211  0 
mac80211              506862  1 iwlwifi
rts_pstor             445241  0 
soundcore              15091  1 snd
cfg80211              205774  2 iwlwifi,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  477602  2 
mei                    41616  0 
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
rfcomm                 47604  12 
bnep                   18281  2 
bluetooth             180153  23 btusb,rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8168                 248895  0
```

```
juha@spectre:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


```

```
juha@spectre:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```


```
juha@spectre:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search opintanner.fi


```

```
juha@spectre:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


```


```
juha@spectre:~$ sudo iwlist scan
[sudo] password for juha: 
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

eth0      Interface doesn't support scanning.


```

Cheers.

---

### Post by IamNotANerd on 2013-03-07
Just tried connecting to an unsecured network AND IT WORKED! I consider this happy news :)

So, what should I do next?

---

### Post by tomerc on 2013-03-07
Are you sure the password you are giving is correct??
Can you paste the relevant logs from /var/log/syslog ?

---

### Post by IamNotANerd on 2013-03-07
I'm not sure exactly what parts to paste but here's entries with iwlwifi:

```
Mar  7 12:06:22 spectre kernel: [    3.564453] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 12:06:22 spectre kernel: [    3.564471] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 12:06:22 spectre kernel: [    3.565102] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 12:06:22 spectre kernel: [    3.565109] iwlwifi 0000:01:00.0: pci_resource_base = ffffc90005090000
Mar  7 12:06:22 spectre kernel: [    3.565115] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 12:06:22 spectre kernel: [    3.565463] iwlwifi 0000:01:00.0: irq 47 for MSI/MSI-X
Mar  7 12:06:22 spectre kernel: [    3.565530] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 12:06:22 spectre kernel: [    3.565611] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 12:06:22 spectre kernel: [    3.583797] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 12:06:22 spectre kernel: [    3.583804] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 12:06:22 spectre kernel: [    3.583811] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 12:06:22 spectre kernel: [    3.593053] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 12:06:22 spectre kernel: [    3.847779] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 12:12:38 spectre kernel: [    3.038524] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 12:12:38 spectre kernel: [    3.038543] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 12:12:38 spectre kernel: [    3.038608] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 12:12:38 spectre kernel: [    3.038615] iwlwifi 0000:01:00.0: pci_resource_base = ffffc90000670000
Mar  7 12:12:38 spectre kernel: [    3.038622] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 12:12:38 spectre kernel: [    3.043914] iwlwifi 0000:01:00.0: irq 46 for MSI/MSI-X
Mar  7 12:12:38 spectre kernel: [    3.044033] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 12:12:38 spectre kernel: [    3.044118] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 12:12:38 spectre kernel: [    3.061312] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 12:12:38 spectre kernel: [    3.061326] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 12:12:38 spectre kernel: [    3.061334] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 12:12:38 spectre kernel: [    3.065583] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 12:12:38 spectre kernel: [    3.770478] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 12:24:15 spectre kernel: [  699.494176] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 12:24:15 spectre kernel: [  699.500777] iwlwifi 0000:01:00.0: Radio type=0x2-0x1-0x0
Mar  7 12:24:15 spectre kernel: [  699.791673] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 12:24:15 spectre kernel: [  699.798259] iwlwifi 0000:01:00.0: Radio type=0x2-0x1-0x0
Mar  7 12:57:29 spectre kernel: [    3.357879] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 12:57:29 spectre kernel: [    3.357899] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 12:57:29 spectre kernel: [    3.357960] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 12:57:29 spectre kernel: [    3.357968] iwlwifi 0000:01:00.0: pci_resource_base = ffffc90005088000
Mar  7 12:57:29 spectre kernel: [    3.357975] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 12:57:29 spectre kernel: [    3.358125] iwlwifi 0000:01:00.0: irq 46 for MSI/MSI-X
Mar  7 12:57:29 spectre kernel: [    3.358200] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 12:57:29 spectre kernel: [    3.358285] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 12:57:29 spectre kernel: [    3.375167] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 12:57:29 spectre kernel: [    3.375179] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 12:57:29 spectre kernel: [    3.375187] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 12:57:29 spectre kernel: [    3.377967] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 12:57:29 spectre kernel: [    3.788258] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 13:14:04 spectre kernel: [    3.282405] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 13:14:04 spectre kernel: [    3.282423] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 13:14:04 spectre kernel: [    3.282527] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 13:14:04 spectre kernel: [    3.282536] iwlwifi 0000:01:00.0: pci_resource_base = ffffc9000066c000
Mar  7 13:14:04 spectre kernel: [    3.282545] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 13:14:04 spectre kernel: [    3.282673] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
Mar  7 13:14:04 spectre kernel: [    3.282743] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 13:14:04 spectre kernel: [    3.282827] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 13:14:04 spectre kernel: [    3.299094] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 13:14:04 spectre kernel: [    3.299107] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 13:14:04 spectre kernel: [    3.299115] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 13:14:04 spectre kernel: [    3.307816] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 13:14:04 spectre kernel: [    3.745022] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 13:28:52 spectre kernel: [  890.605212] iwlwifi 0000:01:00.0: PCI INT A disabled
Mar  7 13:29:04 spectre kernel: [  903.060598] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 13:29:04 spectre kernel: [  903.060609] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 13:29:04 spectre kernel: [  903.060632] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 13:29:04 spectre kernel: [  903.060633] iwlwifi 0000:01:00.0: pci_resource_base = ffffc9000066c000
Mar  7 13:29:04 spectre kernel: [  903.060635] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 13:29:04 spectre kernel: [  903.060713] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
Mar  7 13:29:04 spectre kernel: [  903.060743] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 13:29:04 spectre kernel: [  903.060787] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 13:29:04 spectre kernel: [  903.076284] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 13:29:04 spectre kernel: [  903.076287] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 13:29:04 spectre kernel: [  903.076289] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 13:29:04 spectre kernel: [  903.076320] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 13:29:04 spectre kernel: [  903.078789] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
Mar  7 14:04:39 spectre kernel: [    3.399613] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 14:04:39 spectre kernel: [    3.399630] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 14:04:39 spectre kernel: [    3.400086] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 14:04:39 spectre kernel: [    3.400095] iwlwifi 0000:01:00.0: pci_resource_base = ffffc9000067c000
Mar  7 14:04:39 spectre kernel: [    3.400102] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 14:04:39 spectre kernel: [    3.400227] iwlwifi 0000:01:00.0: irq 46 for MSI/MSI-X
Mar  7 14:04:39 spectre kernel: [    3.400293] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 14:04:39 spectre kernel: [    3.400372] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 14:04:39 spectre kernel: [    3.416528] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 14:04:39 spectre kernel: [    3.416540] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 14:04:39 spectre kernel: [    3.416547] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 14:04:39 spectre kernel: [    3.416631] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 14:04:39 spectre kernel: [    3.799684] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 14:26:04 spectre kernel: [    3.026869] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 14:26:04 spectre kernel: [    3.026889] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 14:26:04 spectre kernel: [    3.026984] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 14:26:04 spectre kernel: [    3.026992] iwlwifi 0000:01:00.0: pci_resource_base = ffffc90005084000
Mar  7 14:26:04 spectre kernel: [    3.026999] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 14:26:04 spectre kernel: [    3.027126] iwlwifi 0000:01:00.0: irq 46 for MSI/MSI-X
Mar  7 14:26:04 spectre kernel: [    3.027192] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 14:26:04 spectre kernel: [    3.039193] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 14:26:04 spectre kernel: [    3.056876] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 14:26:04 spectre kernel: [    3.056887] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 14:26:04 spectre kernel: [    3.056894] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 14:26:04 spectre kernel: [    3.057014] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 14:26:04 spectre kernel: [    3.839057] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 15:43:35 spectre kernel: [    3.348864] iwlwifi 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar  7 15:43:35 spectre kernel: [    3.348884] iwlwifi 0000:01:00.0: setting latency timer to 64
Mar  7 15:43:35 spectre kernel: [    3.348955] iwlwifi 0000:01:00.0: pci_resource_len = 0x00002000
Mar  7 15:43:35 spectre kernel: [    3.348963] iwlwifi 0000:01:00.0: pci_resource_base = ffffc90005084000
Mar  7 15:43:35 spectre kernel: [    3.348970] iwlwifi 0000:01:00.0: HW Revision ID = 0x24
Mar  7 15:43:35 spectre kernel: [    3.349114] iwlwifi 0000:01:00.0: irq 45 for MSI/MSI-X
Mar  7 15:43:35 spectre kernel: [    3.349190] iwlwifi 0000:01:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Mar  7 15:43:35 spectre kernel: [    3.351637] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
Mar  7 15:43:35 spectre kernel: [    3.368599] iwlwifi 0000:01:00.0: device EEPROM VER=0x756, CALIB=0x6
Mar  7 15:43:35 spectre kernel: [    3.368610] iwlwifi 0000:01:00.0: Device SKU: 0X1f0
Mar  7 15:43:35 spectre kernel: [    3.368619] iwlwifi 0000:01:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Mar  7 15:43:35 spectre kernel: [    3.374811] iwlwifi 0000:01:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Mar  7 15:43:35 spectre kernel: [    3.847722] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)


```

What parts should I grep from syslog?
Oh yeah, the pw is correct, I've checked it.

---

### Post by tomerc on 2013-03-07
cat /var/log/syslog | grep wlan

---

### Post by IamNotANerd on 2013-03-07
```
Mar  7 12:06:22 spectre NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:06:22 spectre NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 12:06:22 spectre NetworkManager[814]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): now managed
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): bringing up device.
Mar  7 12:06:22 spectre NetworkManager[814]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 12:06:22 spectre kernel: [    3.956471] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 12:06:22 spectre NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:06:22 spectre NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 12:12:38 spectre NetworkManager[845]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:12:38 spectre NetworkManager[845]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 12:12:38 spectre NetworkManager[845]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): now managed
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): bringing up device.
Mar  7 12:12:38 spectre NetworkManager[845]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 12:12:38 spectre kernel: [    3.913917] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 12:12:38 spectre NetworkManager[845]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:12:38 spectre NetworkManager[845]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 12:24:15 spectre NetworkManager[845]: <info> (wlan0): bringing up device.
Mar  7 12:24:15 spectre kernel: [  699.904275] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 12:24:15 spectre NetworkManager[845]: <info> (wlan0): supplicant interface state: starting -> ready
Mar  7 12:24:15 spectre NetworkManager[845]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar  7 12:24:15 spectre NetworkManager[845]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) starting connection 'kotiWlan'
Mar  7 12:24:20 spectre NetworkManager[845]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 12:24:20 spectre NetworkManager[845]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 12:24:20 spectre NetworkManager[845]: <info> (wlan0): preparing device.
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0/wireless): connection 'kotiWlan' has security, and secrets exist.  No new secrets needed.
Mar  7 12:24:20 spectre NetworkManager[845]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 12:24:20 spectre NetworkManager[845]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar  7 12:24:23 spectre NetworkManager[845]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar  7 12:24:23 spectre kernel: [  707.610364] wlan0: authenticate with 00:24:a5:6f:47:fd (try 1)
Mar  7 12:24:23 spectre kernel: [  707.613074] wlan0: 00:24:a5:6f:47:fd denied authentication (status 1)
Mar  7 12:24:45 spectre NetworkManager[845]: <info> (wlan0): device state change: config -> disconnected (reason 'user-requested') [50 30 39]
Mar  7 12:24:45 spectre NetworkManager[845]: <info> (wlan0): deactivating device (reason 'user-requested') [39]
Mar  7 12:24:45 spectre NetworkManager[845]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar  7 12:24:49 spectre NetworkManager[845]: <info> (wlan0): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
Mar  7 12:24:49 spectre NetworkManager[845]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  7 12:24:49 spectre NetworkManager[845]: <info> (wlan0): taking down device.
Mar  7 12:57:29 spectre NetworkManager[823]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:57:29 spectre NetworkManager[823]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 12:57:29 spectre NetworkManager[823]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): now managed
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): bringing up device.
Mar  7 12:57:29 spectre NetworkManager[823]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 12:57:29 spectre kernel: [    3.930620] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 12:57:29 spectre NetworkManager[823]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 12:57:29 spectre NetworkManager[823]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 13:14:04 spectre NetworkManager[814]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): now managed
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): bringing up device.
Mar  7 13:14:04 spectre NetworkManager[814]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 13:14:04 spectre kernel: [    3.783512] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 13:14:04 spectre NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 13:14:04 spectre NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 13:28:52 spectre avahi-daemon[599]: Withdrawing workstation service for wlan0.
Mar  7 13:28:52 spectre NetworkManager[814]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 13:28:52 spectre NetworkManager[814]: <info> (wlan0): now unmanaged
Mar  7 13:28:52 spectre NetworkManager[814]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Mar  7 13:29:04 spectre NetworkManager[814]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 13:29:04 spectre NetworkManager[814]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 13:29:04 spectre NetworkManager[814]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): now managed
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): bringing up device.
Mar  7 13:29:04 spectre NetworkManager[814]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 13:29:04 spectre kernel: [  903.094722] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 14:04:39 spectre NetworkManager[838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 14:04:39 spectre NetworkManager[838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 14:04:39 spectre NetworkManager[838]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): now managed
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): bringing up device.
Mar  7 14:04:39 spectre NetworkManager[838]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 14:04:39 spectre kernel: [    3.877755] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 14:04:39 spectre NetworkManager[838]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 14:04:39 spectre NetworkManager[838]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 14:26:04 spectre NetworkManager[829]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): now managed
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): bringing up device.
Mar  7 14:26:04 spectre NetworkManager[829]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 14:26:04 spectre NetworkManager[829]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 14:26:04 spectre NetworkManager[829]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 14:26:04 spectre kernel: [    3.996897] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 15:43:35 spectre NetworkManager[855]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 15:43:35 spectre NetworkManager[855]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): using nl80211 for WiFi device control
Mar  7 15:43:35 spectre NetworkManager[855]: <warn> (wlan0): driver supports Access Point (AP) mode
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): now managed
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): bringing up device.
Mar  7 15:43:35 spectre NetworkManager[855]: <info> (wlan0): deactivating device (reason 'managed') [2]
Mar  7 15:43:35 spectre kernel: [    3.962886] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 15:43:35 spectre NetworkManager[855]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0)
Mar  7 15:43:35 spectre NetworkManager[855]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Mar  7 15:54:30 spectre NetworkManager[855]: <info> (wlan0): bringing up device.
Mar  7 15:54:30 spectre kernel: [  657.598524] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar  7 15:54:30 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: starting -> ready
Mar  7 15:54:30 spectre NetworkManager[855]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Mar  7 15:54:30 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: ready -> inactive
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) starting connection 'kotiWlan'
Mar  7 15:54:34 spectre NetworkManager[855]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 15:54:34 spectre NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 15:54:34 spectre NetworkManager[855]: <info> (wlan0): preparing device.
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'kotiWlan' has security, and secrets exist.  No new secrets needed.
Mar  7 15:54:34 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 15:54:34 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar  7 15:54:38 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar  7 15:54:38 spectre kernel: [  665.268875] wlan0: authenticate with 00:24:a5:6f:47:fd (try 1)
Mar  7 15:54:38 spectre kernel: [  665.271756] wlan0: 00:24:a5:6f:47:fd denied authentication (status 1)
Mar  7 15:55:35 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Mar  7 15:55:35 spectre NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar  7 15:55:35 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar  7 15:55:35 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar  7 15:55:39 spectre NetworkManager[855]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar  7 15:55:39 spectre NetworkManager[855]: <warn> Activation (wlan0) failed for access point (kotiWlan)
Mar  7 15:55:39 spectre NetworkManager[855]: <warn> Activation (wlan0) failed.
Mar  7 15:55:39 spectre NetworkManager[855]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  7 15:55:39 spectre NetworkManager[855]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) starting connection 'kotiWlan'
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0/wireless): access point 'kotiWlan' has security, but secrets are required.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'kotiWlan' has security, and secrets exist.  No new secrets needed.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 15:59:24 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar  7 15:59:27 spectre kernel: [  954.371381] wlan0: authenticate with 00:24:a5:6f:47:fd (try 1)
Mar  7 15:59:27 spectre kernel: [  954.374195] wlan0: 00:24:a5:6f:47:fd denied authentication (status 1)
Mar  7 15:59:27 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar  7 16:00:24 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Mar  7 16:00:24 spectre NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar  7 16:00:24 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar  7 16:00:24 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar  7 16:00:30 spectre NetworkManager[855]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar  7 16:00:30 spectre NetworkManager[855]: <warn> Activation (wlan0) failed for access point (kotiWlan)
Mar  7 16:00:30 spectre NetworkManager[855]: <warn> Activation (wlan0) failed.
Mar  7 16:00:30 spectre NetworkManager[855]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  7 16:00:30 spectre NetworkManager[855]: <info> (wlan0): deactivating device (reason 'none') [0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) starting connection 'kotiWlan'
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0/wireless): access point 'kotiWlan' has security, but secrets are required.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0/wireless): connection 'kotiWlan' has security, and secrets exist.  No new secrets needed.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar  7 16:00:37 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Mar  7 16:00:40 spectre kernel: [ 1026.935348] wlan0: authenticate with 00:24:a5:6f:47:fd (try 1)
Mar  7 16:00:40 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Mar  7 16:00:40 spectre kernel: [ 1026.938064] wlan0: 00:24:a5:6f:47:fd denied authentication (status 1)
Mar  7 16:01:37 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long.
Mar  7 16:01:37 spectre NetworkManager[855]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Mar  7 16:01:37 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): asking for new secrets
Mar  7 16:01:37 spectre NetworkManager[855]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Mar  7 16:01:59 spectre NetworkManager[855]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Mar  7 16:01:59 spectre NetworkManager[855]: <warn> Activation (wlan0) failed for access point (kotiWlan)
Mar  7 16:01:59 spectre NetworkManager[855]: <warn> Activation (wlan0) failed.
Mar  7 16:01:59 spectre NetworkManager[855]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar  7 16:01:59 spectre NetworkManager[855]: <info> (wlan0): deactivating device (reason 'none') [0]


```

Thanks for helping!

---

### Post by IamNotANerd on 2013-03-07
```
Mar  7 15:54:38 spectre kernel: [  665.268875] wlan0: authenticate with 00:24:a5:6f:47:fd (try 1) 
Mar  7 15:54:38 spectre kernel: [  665.271756] wlan0: 00:24:a5:6f:47:fd denied authentication (status 1) 
Mar  7 15:55:35 spectre NetworkManager[855]: <warn> Activation (wlan0/wireless): association took too long
```

Hmm, activation takes too long? But it also states that auth denied. I have to check my router admin page and see if it delibaretely refuses to accept my laptop.

Though, there's nothing seriously wrong with the router (a Buffalo Airstation) cause I've got like 5 or 6 devices connected to it without a fuss.

---

### Post by IamNotANerd on 2013-03-07
I FEEL SO STUPID.

I had forgotten that I had a MAC filter enabled in my router settings. No wonder my new laptop couldn't connect. Great.
Wireless now works (duh!) and I feel more or less embarrased BUT the fantastic thing is that *there's nothing wrong with the laptop!*

Thanks to everyone who helped me. I love Ubuntu.

---

### Post by praseodym on 2013-03-07
Greetz.

You can additionally try to deactivate the power management of the card (see "iwconfig"):
```

sudo iwconfig wlan0 power off
```
Now it should be faster and more stable

---

