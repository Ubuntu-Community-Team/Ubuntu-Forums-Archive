---
title: "Broadcom 4313 wireless not working after 12.04 upgrade"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by iseutbm on 2012-09-10
It seems a lot of people are having this problem, but none of the posted solutions have worked for me so far. My driver is installed and activated, I have tried removing and re-adding the network, and various other fixes. No networks were picked up on my first boot, the next day wireless worked fine, and since then it does not detect networks, and when I manually try to connect, it repeatedly asks for the password and does not connect. Here's my info:

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01) Subsystem: Dell Inspiron M5010 / XPS 8300 Flags: bus master, fast devsel, latency 0, IRQ 17 Memory at f0500000 (64-bit, non-prefetchable) [size=16K] Capabilities: [40] Power Management version 3 Capabilities: [58] Vendor Specific Information: Len=78 Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+ Capabilities: [d0] Express Endpoint, MSI 00 Capabilities: [100] Advanced Error Reporting Capabilities: [13c] Virtual Channel Capabilities: [160] Device Serial Number 00-00-a1-ff-ff-f3-70-f1 Capabilities: [16c] Power Budgeting Kernel driver in use: wl Kernel modules: wl, bcma, brcmsmac

root@michelle-laptop:/home/michelle# ifconfig eth0 Link encap:Ethernet HWaddr 70:f1:a1:f3:ba:ab
inet6 addr: fe80::72f1:a1ff:fef3:baab/64 Scope:Link UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:29 TX packets:0 errors:30 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) Interrupt:17

eth1 Link encap:Ethernet HWaddr f0:4d:a2:53:83:7a
UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) Interrupt:43

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:104 errors:0 dropped:0 overruns:0 frame:0 TX packets:104 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:8000 (8.0 KB) TX bytes:8000 (8.0 KB)

root@michelle-laptop:/home/michelle# lsmod Module Size Used by dm_crypt 22528 0 snd_hda_codec_hdmi 31775 1 snd_hda_codec_realtek 174313 1 snd_hda_intel 32765 5 snd_hda_codec 109562 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep 13276 1 snd_hda_codec snd_pcm 80845 4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec snd_seq_midi 13132 0 snd_rawmidi 25424 1 snd_seq_midi snd_seq_midi_event 14475 1 snd_seq_midi snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event parport_pc 32114 0 ppdev 12849 0 binfmt_misc 17292 1 lib80211_crypt_tkip 17275 0 bnep 17830 2 rfcomm 38139 0 snd_timer 28931 2 snd_pcm,snd_seq snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq joydev 17393 0 wl 2646601 0 snd 62064 19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device soundcore 14635 1 snd btusb 17912 0 bluetooth 158438 11 bnep,rfcomm,btusb uvcvideo 67203 0 videodev 86588 1 uvcvideo snd_page_alloc 14108 2 snd_hda_intel,snd_pcm lib80211 14040 2 lib80211_crypt_tkip,wl intel_ips 17822 0 psmouse 72919 0 serio_raw 13027 0 mei 36570 0 dell_laptop 17767 0 dell_wmi 12601 0 dcdbas 14098 1 dell_laptop sparse_keymap 13658 1 dell_wmi mac_hid 13077 0 lp 17455 0 parport 40930 3 parport_pc,ppdev,lp usbhid 41906 0 hid 77367 1 usbhid wmi 18744 1 dell_wmi i915 414817 3 atl1c 36718 0 drm_kms_helper 45466 1 i915 drm 197692 4 i915,drm_kms_helper i2c_algo_bit 13199 1 i915 video 19068 1 i915 root@michelle-laptop:/home/michelle# iwlist scan lo Interface doesn't support scanning.

eth1 Interface doesn't support scanning.

eth0 No scan results

root@michelle-laptop:/home/michelle# rfkill list 0: dell-wifi: Wireless LAN Soft blocked: no Hard blocked: no 1: dell-bluetooth: Bluetooth Soft blocked: yes Hard blocked: no 3: brcmwl-0: Wireless LAN Soft blocked: no Hard blocked: no

Obviously I don't know what I'm doing. I'd appreciate any help! Thanks!

---

### Post by chili555 on 2012-09-10
> driver in use: wl Kernel modules: wl, bcma, brcmsmacPlease run:```
lspci -nn
```Is your device 14e4:4727? If so, I wonder if wl is correct. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
```Reboot and let us have your report.

WARNING: If your device ID is *NOT* 14e4:4727, stop and post it before you take any action.

---

