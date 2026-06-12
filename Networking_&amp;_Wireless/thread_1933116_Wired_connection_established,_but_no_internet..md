---
title: "Wired connection established, but no internet."
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by garragoal2 on 2012-02-28
Hello everybody! I am new to Linux, I just installed Ubuntu 11.04 on my Hp Pavillion dv7 laptop. I'm writing from my desktop windows PC, because I can't get the internet to work. I can't get wireless connection because the wireless adapter is turned off (the f12 key which is used as a wireless on/off switch is stuck on the orange light and doesn't want to change it). I read in the forum that this may be repaired by upgrading the drivers of the wireless adapter. So i plugged an Ethernet cable to the laptop and connected it to my router. Although there is an indicator that the wired connection is established, there is no internet. I tried to set up the network settings manually, by copying them from my windows PC, which is connected to the same router, but still nothing. I can't even ping the router, it says "Destination Host Unreachable". I looked in the forum, tried some solutions, but none seems to work. What do I have to do to fix this?
Thanks!

---

### Post by praseodym on 2012-02-28
Please show the terminal (CTRL+ALT+T) outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
cat /etc/network/interfaces
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by garragoal2 on 2012-02-28
```
lspci -nnk | grep -iA2 net
 01:00.0 Ethernet  controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI  Express Gigabit Ethernet controller [10ec:8168] (rev 06)
     Subsystem: Hewlett-Packard Company Device [103c:3591]
     Kernel driver in use: r8169
 --
 02:00.0 Network controller [0280]: Ralink corp. Device [1814:5390]
     Subsystem: Hewlett-Packard Company Device [103c:1636]
 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
``````
lsusb
 Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 004 Device 002: ID 138a:0018 DigitalPersona, Inc 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 002: ID 5986:04a9 Acer, Inc 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Flash Drive
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
 lsmod
 Module                  Size  Used by
 r8712u                307592  0 
 nls_iso8859_1          12713  1 
 nls_cp437              16991  1 
 vfat                   21708  1 
 fat                    61374  1 vfat
 usb_storage            53538  1 
 uas                    17996  0 
 parport_pc             36959  0 
 ppdev                  17113  0 
 vesafb                 13761  1 
 joydev                 17606  0 
 usbhid                 46956  0 
 binfmt_misc            17565  1 
 snd_hda_codec_idt      71137  1 
 hid                    91020  1 usbhid
 snd_hda_codec_hdmi     28103  1 
 snd_hda_intel          33211  4 
 snd_hda_codec         103804  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
 snd_hwdep              13604  1 snd_hda_codec
 snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
 snd_seq_midi           13324  0 
 snd_rawmidi            30486  1 snd_seq_midi
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
 hp_wmi                 13706  0 
 snd_timer              29602  2 snd_pcm,snd_seq
 uvcvideo               72195  0 
 snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
 sparse_keymap          13898  1 hp_wmi
 videodev               82052  1 uvcvideo
 snd                    67382  17  snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
 v4l2_compat_ioctl32    17078  1 videodev
 i2c_piix4              13303  0 
 psmouse                73535  0 
 soundcore              12680  1 snd
 serio_raw              13166  0 
 k10temp                13119  0 
 xhci_hcd               77643  0 
 snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
 rts_pstor             440614  0 
 hp_accel               21880  0 
 lis3lv02d              19893  1 hp_accel
 input_polldev          14007  1 lis3lv02d
 video                  19438  0 
 lp                     17825  0 
 parport                46458  3 parport_pc,ppdev,lp
 ahci                   25951  2 
 libahci                26642  1 ahci
 pata_atiixp            13165  0 
 r8169                  48022  0 
```This file used to have only the first two lines, but I edited it when I was trying to find a solution earlier and added the last four lines (without any effect).
```
 cat /etc/network/interfaces
 auto lo
 iface lo inet loopback
 iface etho0 inet static
 address 192.168.0.9
 netmask 255.255.255.0
 gateway 192.168.0.1
``````
 iwconfig
 lo        no wireless extensions.
 
 eth0      no wireless extensions.
 
```I didn't get any output for "rfkill list"
```
 cat /var/lib/NetworkManager/NetworkManager.state
 
 [main]
 NetworkingEnabled=true
 WirelessEnabled=true
 WWANEnabled=true
  
```

---

### Post by Iowan on 2012-02-28
You can try adding **auto eth0**to */etc/network/interfaces*... but you may have problems trying to bypass Network Manager. You might also restore */etc/network/interfaces* and set a manual address from Network Manager. What problems did you have with a DHCP address?

---

### Post by gordintoronto on 2012-02-28
> **garragoal2 said:**
> the f12 key which is used as a wireless on/off switch is stuck on the orange light and doesn't want to change it...

On my HP G62, that light stays orange -- but the wireless works just fine.

---

### Post by praseodym on 2012-02-29
Errrr, why is a Realtek driver installed (r8712u) for a Ralink device?

```
sudo modprobe -rfv r8712u
echo "blacklist r8712u" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -v rt2800pci
```
Check:
```

lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | grep rt2
```
Edit: Remove those lines and try to connect via network-manager applet

---

