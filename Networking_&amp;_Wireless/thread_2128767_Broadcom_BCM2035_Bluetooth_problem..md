---
title: "Broadcom BCM2035 Bluetooth problem."
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by Bob McGlob on 2013-03-24
I'm having trouble with my Xubuntu 12.04 install recognising the bluetooth hardware in my Acer Aspire 2000 laptop (circa 2003). 

This laptop has a button that allows the bluetooth radio to be turned on and off. The symptom I am observing when I press this button is that the bluetooth icon appears briefly in the system tray then disappears. It does this each time I turn the radio on.

Here's some machine logs to aid with diagnosis:
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 007: ID 0a5c:200a Broadcom Corp. BCM2035 Bluetooth dongle
```

```
lsmod
Module                  Size  Used by
btusb                  17948  1 
joydev                 17393  0 
arc4                   12473  2 
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
ath9k                 117455  0 
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
mac80211              436493  1 ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
irda                  185517  0 
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
radeon                733929  2 
psmouse                96718  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              13027  0 
crc_ccitt              12627  1 irda
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178877  3 ath9k,mac80211,ath
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
drm                   197641  4 radeon,ttm,drm_kms_helper
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158479  13 btusb,bnep,rfcomm
parport_pc             32114  1 
ppdev                  12849  0 
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
shpchp                 32265  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ext2                   67987  1 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
8139too                23283  0 
8139cp                 22633  0 
crc_itu_t              12627  1 firewire_core
usbhid                 41937  0 
hid                    77428  1 usbhid

```

```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
hcitool dev
Devices:


```
i.e. no devices listed

```
dmesg
[   24.286231] Bluetooth: Core ver 2.16
[   24.286296] NET: Registered protocol family 31
[   24.286300] Bluetooth: HCI device and connection manager initialized
[   24.286305] Bluetooth: HCI socket layer initialized
[   24.286308] Bluetooth: L2CAP socket layer initialized
[   24.286318] Bluetooth: SCO socket layer initialized
[   24.318670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.318676] Bluetooth: BNEP filters: protocol multicast
[   24.331439] Bluetooth: RFCOMM TTY layer initialized
[   24.331450] Bluetooth: RFCOMM socket layer initialized
[   24.331453] Bluetooth: RFCOMM ver 1.11
...
[  262.912054] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[  264.703253] Bluetooth: Generic Bluetooth USB driver ver 0.6
[  264.728113] usbcore: registered new interface driver btusb
[  265.888036] Bluetooth: hci0 command tx timeout
[  266.008227] usb 3-2: USB disconnect, device number 2
[  266.010884] Bluetooth: hci0 urb f4805d00 submission failed
[  266.504078] usb 3-2: new full-speed USB device number 3 using uhci_hcd
...
[ 2832.812076]usb 3-2: new full-speed USB device number 4 using uhci_hcd
[ 2834.216047] Bluetooth: hci0 command tx timeout
[ 2834.312140] usb 3-2: USB disconnect, device number 4
[ 2834.314334] Bluetooth: hci0 urb eebf6e00 submission failed
[ 2835.296074] usb 3-2: new full-speed USB device number 5 using uhci_hcd
...
[ 5543.464130] usb 3-2: USB disconnect, device number 5
[ 5555.848079] usb 3-2: new full-speed USB device number 6 using uhci_hcd
[ 5557.252051] Bluetooth: hci0 command tx timeout
[ 5557.352196] usb 3-2: USB disconnect, device number 6
[ 5557.354820] Bluetooth: hci0 urb ef674400 submission failed
[ 5558.336092] usb 3-2: new full-speed USB device number 7 using uhci_hcd
```

As you can see everytime I press the button to turn on the bluetooth radio the driver appears to timeout and fail.

I read in another forum that I may need proprietry firmware for this hardware so I installed:

```
sudo apt-get install linux-firmware-nonfree
```

However this hasn't helped.

Any suggestions would be appreciated.

---

