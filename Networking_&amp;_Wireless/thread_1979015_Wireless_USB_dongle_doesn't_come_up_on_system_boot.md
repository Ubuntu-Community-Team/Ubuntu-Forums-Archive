---
title: "Wireless USB dongle doesn't come up on system boot"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by vmalloc on 2012-05-12
Hi,

I have a Zotac ZBOX ID41 machine, running Ubuntu 11.04. I recently bought a wireless USB adapter (an Edimax EW-7612uan), and have been trying to make it work properly ever since with no success.

After having given up on Ubuntu 12.04 due to shutdown hangs and such I decided to stay with 11.04.

I followed the installation procedure of the 8712u driver described in [http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html](http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html), blacklisted the stock r8712u module, and had it working for a while. For some other reasons I removed network-manager and am relying on /etc/network/interfaces to define my wlan1 interface (I don't always have gdm running).

In any case, everything works fine until the next boot. I get a kernel panic in dmesg, wlan1 is not present, and the LED on the dongle is off. It stays that way until I remove the dongle and reinsert it. At that point the interface comes up and all is well (I still get the stack traces in the log though).

I also made sure to put the firmware from  [http://www.tuxamito.com/rtl8192/rtl8192sfw.bin.gz](http://www.tuxamito.com/rtl8192/rtl8192sfw.bin.gz) in /lib/firmware/RTL8192SU/, as mentioned in other posts.

the stack traces I get:

```

[   63.689827]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[   63.689833]  [<c105dc90>] ? del_timer_sync+0x40/0x50
[   63.689839]  [<c105dc90>] ? del_timer_sync+0x40/0x50
[   63.689846]  [<c104f962>] ? warn_slowpath_null+0x22/0x30
[   63.689853]  [<c105dc90>] ? del_timer_sync+0x40/0x50
[   63.689878]  [<f8c7bcf0>] ? joinbss_event_callback+0x2d5/0x30d [8712u]
[   63.689885]  [<c13a61ce>] ? usb_submit_urb+0xfe/0x2c0
[   63.689907]  [<f8c6c336>] ? event_handle+0xf8/0x10c [8712u]
[   63.689931]  [<f8c83d80>] ? rxcmd_event_hdl+0x26/0x36 [8712u]
[   63.689953]  [<f8c70a29>] ? usb_read_port_complete+0x89/0x16c [8712u]
[   63.689960]  [<c13a43fd>] ? usb_hcd_giveback_urb+0x4d/0xc0
[   63.689967]  [<c15097cd>] ? _raw_spin_lock+0xd/0x10
[   63.689974]  [<c13b8581>] ? ehci_urb_done+0xc1/0xf0
[   63.689981]  [<c13b877a>] ? qh_completions+0x1ca/0x400
[   63.689988]  [<c13b8ef3>] ? scan_async+0x53/0x190
[   63.689995]  [<c13b8ae9>] ? end_unlink_async+0x139/0x170
[   63.690002]  [<c13b9dfd>] ? ehci_work+0x2d/0x70
[   63.690009]  [<c13ba035>] ? ehci_irq+0x195/0x200
[   63.690015]  [<c15097cd>] ? _raw_spin_lock+0xd/0x10
[   63.690022]  [<c13a3de3>] ? usb_hcd_irq+0x33/0x70
[   63.690028]  [<c10affec>] ? handle_IRQ_event+0x4c/0x160
[   63.690036]  [<c10afa24>] ? irq_to_desc+0x14/0x20
[   63.690042]  [<c10b2258>] ? handle_fasteoi_irq+0x68/0xd0
[   63.690049]  [<c10b21f0>] ? handle_fasteoi_irq+0x0/0xd0
[   63.690053]  <IRQ>  [<c15107a2>] ? do_IRQ+0x42/0xc0
[   63.690064]  [<c10567e0>] ? irq_exit+0x60/0x80
[   63.690072]  [<c151087b>] ? smp_apic_timer_interrupt+0x5b/0x8a
[   63.690079]  [<c1003670>] ? common_interrupt+0x30/0x38
[   63.690086]  [<c105007b>] ? console_unlock+0xdb/0xe0
[   63.690093]  [<c12c2508>] ? intel_idle+0xb8/0x110
[   63.690101]  [<c14061fd>] ? cpuidle_idle_call+0x7d/0x160
[   63.690107]  [<c10019ca>] ? cpu_idle+0x8a/0xc0
[   63.690114]  [<c1038d2e>] ? complete+0x4e/0x60
[   63.690121]  [<c14f0d2d>] ? rest_init+0x5d/0x70
[   63.690128]  [<c178d7e1>] ? start_kernel+0x35f/0x366
[   63.690135]  [<c178d3d5>] ? pass_all_bootoptions+0x0/0xa
[   63.690142]  [<c178d0e0>] ? i386_start_kernel+0xe0/0xe8
[   63.690147] ---[ end trace 65e0170d7a650562 ]---
[   63.690333] fwdbg:join res(00000004, 00000212)

```

lsmod:
```

Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  1 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               9766978  0 
snd_hda_codec_hdmi     27479  4 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 103633  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
mac80211              257001  1 ath9k
usb_storage            43946  0 
ath9k_common           13611  1 ath9k
snd_timer              28659  2 snd_pcm,snd_seq
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
uas                    17676  0 
8712u                 305441  0 
snd                    55295  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    77084  1 usbhid
serio_raw              12990  0 
xhci_hcd               68062  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  42534  0 

```

lsusb:
```

Bus 006 Device 002: ID 2109:0811  
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b4:0100 Cypress Semiconductor Corp. Cino FuzzyScan F760-B
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any help would be greatly appreciated...

Thanks,

Rotem

---

### Post by chili555 on 2012-05-12
What is ath9k doing in your lsmod? Do you think it interferes? Should it be blacklisted? What about your internal Atheros doesn't work properly? May I see:```
modinfo 8712u | grep firmware
```

---

### Post by vmalloc on 2012-05-13
The result is empty (no firmware in modinfo output)...

---

### Post by chili555 on 2012-05-13
> **vmalloc said:**
> The result is empty (no firmware in modinfo output)...So we know it's not stumbling on firmware; it doesn't need any!

Let's have a look at:```
cat /etc/network/interfaces
```Obscure any passwords: MYPASSWORD, for example.

Please reboot with the device removed and run and post:```
lsmod | grep 8712
dmesg | grep 8712
```I wonder if there are errors or warnings so far.

---

### Post by vmalloc on 2012-05-13
Ok - apparently blacklisting everything related to atheros worked (I have an on-board wifi which is atheros-based).

I had to add:

blacklist ath9k
blacklist mac80211
blacklist ath9k_common
blacklist ath9k_hw
blacklist ath
blacklist cfg80211

I guess I can live without the onboard one.

Thanks!

---

### Post by vmalloc on 2012-05-13
Ok - partial correction: the boot is fine, but the stack traces still apear in dmesg every minute or so on network activity... :-(

---

### Post by chili555 on 2012-05-13
Did you get many warnings when you compiled this little beauty? Do you think, with ath9k blacklisted, the original in-kernel r8712u version might work trouble-free?> I guess I can live without the onboard one.Didn't you buy the USB because you wanted to ditch the on-board?

---

### Post by wilee-nilee on 2012-05-13
Here is a wiki on ones that work I would return the one you have and get one that does work as a plug and play. Not everyone possible is listed, but this may be a good start.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by vmalloc on 2012-05-14
Update: apparently after disabling the ath9k drivers, the driver that comes bundled with 11.04 works ok (r8712u). 

Thanks again for the help! it means a lot!

---

