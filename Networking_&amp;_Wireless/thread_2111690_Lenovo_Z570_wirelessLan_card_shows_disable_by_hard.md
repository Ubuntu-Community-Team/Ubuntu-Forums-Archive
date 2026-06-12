---
title: "Lenovo Z570 wirelessLan card shows disable by hardware switch"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by ykaratm on 2013-02-02
Hello,
I purchased a Lenovo ideapad Z570 in September 2011 with windows 7 installed in it. Then i installed Ubuntu 11.10 on a separate partition, and used the laptop for dual boot. It worked fine until 2 days ago when i installed Ubuntu 12.10. I formatted the drive i had ubuntu 11.10 installed before i installed 12.10.

The first and the the most important error i noticed when i saw that the wireless internet is not working because the "WirelessLan card is disabled by hardware switch". I am sure i have the hardware switch on. Now the wireless doesnot work in windows 7 either because of the same error.

I have looked into various forums and websites to resolve this problem. Few websites had similar issue, but it was not exactly the same as mine. I still tried to used those methods to resolve the problem, but it didn't help.

Here are some terminal codes that should give the status of my intel 1000 BGN Wireless Card. 

taraky@taraky-Ideapad-Z570:~$ dmesg | grep iwl
[    9.858339] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    9.858341] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[    9.858454] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[    9.858456] iwlwifi 0000:02:00.0: pci_resource_base = ffffc9000514c000
[    9.858457] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[    9.858578] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[    9.926563] iwlwifi 0000:02:00.0: loaded firmware version 39.31.5.1 build 35138
[    9.926661] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.926663] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.926664] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.926665] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    9.926666] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    9.926668] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    9.926776] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    9.934161] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[    9.946366] iwlwifi 0000:02:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    9.946368] iwlwifi 0000:02:00.0: Device SKU: 0x50
[    9.946369] iwlwifi 0000:02:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[    9.946377] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   10.186354] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

taraky@taraky-Ideapad-Z570:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

Please Help.
Let me know if i should provide you with some other information. Please provide the codes as well since i do not know any linux commands. I simply follow the internet forums without knowing what and why i'm typing those.

---

### Post by praseodym on 2013-02-02
Did you try
```
sudo rfkill unblock all
rfkill list [COLOR="Red"]#check[/COLOR]
```
Please show also
```
lsmod
```

---

### Post by ykaratm on 2013-02-02
> **praseodym said:**
> Did you try
```
sudo rfkill unblock all
rfkill list [COLOR=Red]#check[/COLOR]
```Please show also
```
lsmod
```

Thank you for the quick reply.
I did try "rfkill unblock all", it didn't work. However, here is the result: 

taraky@taraky-Ideapad-Z570:~$ sudo rfkill unblock all
taraky@taraky-Ideapad-Z570:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
taraky@taraky-Ideapad-Z570:~$ lsmod
Module                  Size  Used by
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  12 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78048  1 
arc4                   12530  2 
joydev                 17458  0 
acer_wmi               32454  0 
coretemp               13401  0 
kvm                   414071  0 
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
microcode              22804  0 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
ideapad_laptop         18087  0 
sparse_keymap          13891  2 acer_wmi,ideapad_laptop
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
rts5139               356200  0 
wmi                    19071  1 acer_wmi
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13206  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  22475  0 
i915                  520621  3 
bluetooth             209249  22 bnep,rfcomm,btusb
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
iwlwifi               386874  0 
mac80211              539958  1 iwlwifi
psmouse                95595  0 
serio_raw              13216  0 
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
cfg80211              206797  2 iwlwifi,mac80211
i2c_algo_bit           13414  1 i915
lp                     17760  0 
lpc_ich                17062  0 
parport                46346  3 parport_pc,ppdev,lp
soundcore              15048  1 snd
mei                    40691  0 
video                  19336  2 acer_wmi,i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
r8169                  61651  0

---

### Post by praseodym on 2013-02-03
Unload the module acer_wmi:

```
sudo rmmod acer_wmi
```

---

### Post by ykaratm on 2013-02-03
> **praseodym said:**
> Unload the module acer_wmi:

```
sudo rmmod acer_wmi
```

No change in status. Here are the terminal output:

taraky@taraky-Ideapad-Z570:~$ sudo rmmod acer_wmi
[sudo] password for taraky: 
taraky@taraky-Ideapad-Z570:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by praseodym on 2013-02-03
I am translating this:

[http://wiki.ubuntuusers.de/rfkill#ThinkPad-ohne-Hardwareschalter-zeigt-hard-blocked-yes](http://wiki.ubuntuusers.de/rfkill#ThinkPad-ohne-Hardwareschalter-zeigt-hard-blocked-yes)

Check these 3 opportunities one by one:
[LIST=1]
[*]Check in your BIOS: "Config -> Network -> Wireless LAN ..." if it is activated


[*]Hardware-reset:
[LIST]
[*]shutdown, shut off, remove the current cable and the battery

[*]Press the power button for at least 30 seconds

[*]put the battery/current back in and restart
[/LIST]

[*]BIOS default:
[LIST]
[*]Go into your BIOS with e.g. F1

[*]Reset with F9

[*]Save & Exit with F10

[*]When the Logo occurs, press the power button for ca. 10 seconds for shutting off

[*]Restart
[/LIST]
[/LIST]

---

### Post by ykaratm on 2013-02-03
> **praseodym said:**
> I am translating this:

[http://wiki.ubuntuusers.de/rfkill#ThinkPad-ohne-Hardwareschalter-zeigt-hard-blocked-yes](http://wiki.ubuntuusers.de/rfkill#ThinkPad-ohne-Hardwareschalter-zeigt-hard-blocked-yes)

Check these 3 opportunities one by one:
[LIST=1]
[*]Check in your BIOS: "Config -> Network -> Wireless LAN ..." if it is activated
[*]Hardware-reset:
[LIST]
[*]shutdown, shut off, remove the current cable and the battery
[*]Press the power button for at least 30 seconds
[*]put the battery/current back in and restart
[/LIST]
 
[*]BIOS default:
[LIST]
[*]Go into your BIOS with e.g. F1
[*]Reset with F9
[*]Save & Exit with F10
[*]When the Logo occurs, press the power button for ca. 10 seconds for shutting off
[*]Restart
[/LIST]
 
[/LIST]


I have not try any of those before. I followed your instruction and this is the result.

taraky@taraky-Ideapad-Z570:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

The hard block is finally off!!! :D
I have not done anything to take the soft block off. Waiting for further instruction from you.

---

### Post by praseodym on 2013-02-03
Now try

```
sudo rfkill unblock all
```

---

### Post by ykaratm on 2013-02-03
> **praseodym said:**
> Now try

```
sudo rfkill unblock all
```

here is the result:

taraky@taraky-Ideapad-Z570:~$ sudo rfkill unblock all
taraky@taraky-Ideapad-Z570:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

This is my first message sent via wireless network! Everything is working fine. Thank you very much!

---

