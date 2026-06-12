---
title: "No wireless after last update"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by 2boats on 2011-09-21
The last update has made my wireless disappear...I have wired.
I also cannot start my virtual native boot WinXP as a result of this error.

If someone can help me I'd be very thankful.  The thought of having to go back to using only Windows.....can't even think about it.

Some info:

doug@doug-laptop:~$ uname -a
Linux doug-laptop 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
doug@doug-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:01d4]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
doug@doug-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
doug@doug-laptop:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
i915                  451033  2 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
b44                    35301  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ssb                    45942  1 b44
vboxnetadp             13323  0 
vboxnetflt             27855  0 
wl                   2642531  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
pcmcia                 39671  0 
snd_timer              28659  2 snd_pcm,snd_seq
dell_wmi               12601  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
drm                   184164  3 i915,drm_kms_helper
joydev                 17322  0 
yenta_socket           27230  0 
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              12990  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

vboxnet0  no wireless extensions.

eth0      no wireless extensions.

doug@doug-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
doug@doug-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by chili555 on 2011-09-21
I don't believe the driver *wl* is correct for your device. Please see: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04?highlight=%28ManufacturerModel%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04?highlight=%28ManufacturerModel%29)

---

### Post by 2boats on 2011-09-21
Thanks so much for the quick reply.

That did the trick!!  
 Thanks again for your time.

---

