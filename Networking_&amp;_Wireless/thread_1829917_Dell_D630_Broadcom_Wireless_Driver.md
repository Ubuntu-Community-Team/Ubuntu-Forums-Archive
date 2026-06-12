---
title: "Dell D630 Broadcom Wireless Driver"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by shadowfax1 on 2011-08-21
Cant get the os to recognize and activate the driver.  After the install it recognized restricted drivers available but after activating it the driver still didn't initialize

---

### Post by praseodym on 2011-08-21
What hardware do you use? Post the following outputs:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
sudo iwlist scan
iwlist chan
```

---

### Post by shadowfax1 on 2011-08-21
ryan@ryan-Latitude-D630 ~ $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: wl, ssb
ryan@ryan-Latitude-D630 ~ $ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2642531  0 
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                73312  0 
lib80211               14570  1 wl
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  450944  3 
drm_kms_helper         40745  1 i915
firewire_ohci          31504  0 
drm                   180037  4 i915,drm_kms_helper
firewire_core          56138  1 firewire_ohci
tg3                   131476  0 
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
ryan@ryan-Latitude-D630 ~ $ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ryan@ryan-Latitude-D630 ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ryan@ryan-Latitude-D630 ~ $ sudo iwlist scan
[sudo] password for ryan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ryan@ryan-Latitude-D630 ~ $ iwlist chan
lo        no frequency information.

eth0      no frequency information.

---

### Post by praseodym on 2011-08-21
For this device you can use the b43 driver, but the firmware has to be installed. Deactivate the STA-driver and uninstall it:

```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
sudo apt-get install --reinstall b43-fwcutter                         #until Maverick
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer  #for Natty
sudo modprobe -v b43
```
controls:

```
iwconfig
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep b43
sudo iwlist scan
```
You may try rebooting your system.

---

### Post by nm_geo on 2011-08-21
+1 on the b43 & firmware..

You might also find blacklist problems ..

[http://ubuntuforums.org/showthread.php?t=1816276&page=6](http://ubuntuforums.org/showthread.php?t=1816276&page=6)

those messages should help after you install b43 and the firmware.

---

### Post by shadowfax1 on 2011-08-21
I get an error when I try to uninstall the sta driver.  This is the same driver as my D430 and it works great
Not sure of the sequence you have listed....Can you simplify...thanxs

---

### Post by praseodym on 2011-08-21
Did you deactivate the Broadcom-STA-driver first?

---

### Post by shadowfax1 on 2011-08-21
Only gives me the option to remove it...and when I try an error occurs.  Tried installing win 7 just to see if the wireless worked and no problem...lit up right away.  What I don't understand is the sta driver works just fine in my d430...

---

### Post by praseodym on 2011-08-21
Uninstall the driver as shown, install the firmware files and reboot

---

### Post by shadowfax1 on 2011-08-21
Problem solved....Managed to de-activate the sta driver went to synaptic and installed b43 installer and
bingo.  What I don't understand is how a identical card on another laptop works fine with the broadcom sta
and doesn't on this one.  I read somewhere that the bw43 driver is slower....Going to 'ping' both laptops and
find out...Thanxs to everyone here for the help!

---

### Post by bkratz on 2011-08-21
> **shadowfax1 said:**
> Problem solved....Managed to de-activate the sta driver went to synaptic and installed b43 installer and
bingo.  What I don't understand is how a identical card on another laptop works fine with the broadcom sta
and doesn't on this one.  I read somewhere that the bw43 driver is slower....Going to 'ping' both laptops and
find out...Thanxs to everyone here for the help!

Is the other one on 11.04 also? Sta was used on earlier versions for this card.

---

