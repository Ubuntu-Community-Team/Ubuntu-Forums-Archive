---
title: "wlan0 does not exist? no wifi"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by GiladGressel on 2011-10-05
HI All,
  I have been using compat wireless drivers and had no problems until recently.

problem began recently -- i was in a house that had wpa password.  my wifi would not connect so I tried installing new realtek drivers from their website.  THen nothing showed.  Since then I have uninstalled all drivers and reinstalled the compat.  still no wifi shows.

this morning i downloaded new kernel headers as part of the ubuntu updates.  previously that had reset my drivers so I hoped it would do the same today.  I re-compiled the compat drivers but still have no success.

i am running an asus 1201n.   rtl8192seVa

my current problem is not that I cannot see any wireless networks at all. 
It seems my wlan0 does not exist. 
 here is some results from terminal
you can see i have the rtl8192se driver up and running.  I blacklisted the ubuntu driver (r8192se_pci) so it should not be conflicting.

any help would be great.  I am travelling so may not be able to respond quickly -- but I will check when I can.   Obviously it's hard to use my computer right 

 here is some results from terminal -- i'm not sure what to show, let me know what you'd like to see. 
thanks ahead of time!

lspci

```
gilad@maya:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
05:00.0 VGA compatible controller: nVidia Corporation ION VGA [GeForce 9400M] (rev b1)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
09:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
gilad@maya:~$
```
lsmod
```
gilad@maya:~$ lsmod
Module                  Size  Used by
ipheth                 13238  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
vboxnetadp             13348  0 
ppdev                  12849  0 
vboxnetflt             27855  0 
vesafb                 13449  1 
rfcomm                 38125  10 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
nvidia              10675438  114 
joydev                 17322  0 
snd_hda_intel          24113  2 
uvcvideo               66851  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
btusb                  18160  2 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
videodev               75143  1 uvcvideo
snd_hwdep              13274  1 snd_hda_codec
eeepc_wmi              18771  0 
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sparse_keymap          13666  1 eeepc_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
rtl8192se              92400  0 
video                  18951  0 
rtlwifi                94805  1 rtl8192se
mac80211              276698  2 rtl8192se,rtlwifi
cfg80211              167576  2 rtlwifi,mac80211
compat                 15406  1 mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
atl1c                  36237  0 
libahci                25548  1 ahci
gilad@maya:~$ 
```iwconfig wlan0

```
gilad@maya:~$ iwconfig wlan0
wlan0     No such device
```rfkill list all

```
gilad@maya:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: eeepc-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
gilad@maya:~$ 

```dmesg

```
gilad@maya:~$ dmesg | grep -e wlan -e 819
[    0.004819] mce: CPU supports 5 MCE banks
[    0.488193] pci 0000:00:18.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.588190] pnp 00:06: [io  0x00a2-0x00bf]
[    0.588198] pnp 00:06: [io  0x00e0-0x00ef]
[    0.713980] type=2000 audit(1317819402.708:1): initialized
[    1.389819] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.395468] rtc_cmos 00:08: setting system clock to 2011-10-05 12:56:44 UTC (1317819404)
[    1.548199] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.694512] ata1: SATA max UDMA/133 abar m8192@0xf9f76000 port 0xf9f76100 irq 40
[   13.241235] rtl8192se 0000:07:00.0: PCI INT A -> Link[LN4A] -> GSI 18 (level, low) -> IRQ 18
[   13.241259] rtl8192se 0000:07:00.0: setting latency timer to 64
[   13.253039] rtl8192se: rtl8192ce: FW Power Save off (module option)
[   13.253349] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   13.253357] Loading firmware rtlwifi/rtl8192sefw.bin
[   17.030410] rtl8192se:rtl92s_init_sw_vars():<0-0> Failed to request firmware!
[   17.030495] rtl8192se 0000:07:00.0: PCI INT A disabled
gilad@maya:~$ 



```

---

### Post by praseodym on 2011-10-05
Hi,

> [   13.253357] Loading firmware rtlwifi/rtl8192sefw.bin
[   17.030410] rtl8192se:rtl92s_init_sw_vars():<0-0> Failed to request firmware!

The firmware can be installed from linux-firmware, starting from Natty version:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb)

---

