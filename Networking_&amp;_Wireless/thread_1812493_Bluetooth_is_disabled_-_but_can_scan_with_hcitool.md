---
title: "Bluetooth is disabled - but can scan with hcitool?"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by lbirunner on 2011-07-26
I need help to re-enable my previously working bluetooth on a Dell laptop (D630) with a "Wireless 360 Bluetooth" adapter.

When I click on my Bluetooth manager icon->preferences, it says "Bluetooth is disabled" and there is a big Button with "Turn On Bluetooth" which doesn't do anything that I can see. And /etc/init.d/start also doesn't appear to do anything.

If I use "hciconfig -a" I can see the internal adapter. And with "sudo hciconfig hci0 up" I can enable the interface. Then I can scan with "hcitool scan".
Here is an example session immediately following a reboot:
```

$ /etc/init.d/bluetooth status
 * bluetooth is not running
$ /etc/init.d/bluetooth start
$ /etc/init.d/bluetooth status
 * bluetooth is not running
$ hciconfig -a
hci0:	Type: USB
	BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:0 acl:0 sco:0 commands:0 errors:0

$ sudo hciconfig hci0 up
$ hcitool dev
Devices:
	hci0	00:21:86:82:C2:EA
$ hcitool scan
Scanning ...
	00:19:0E:0C:D7:01	BlueZ (0)
	E4:E0:C5:35:12:B4	DTVBluetooth

```

But I have been unable to get gnome-bluetooth (Bluetooth GUI) to work and have not been able to use hcitool to connect to a device.

Any help getting gnome-bluetooth GUI to work would be much appreciated. 
I've searched through many threads and tried everything that might be remotely related to my problem but to no avail.

Here is dmesg info (dmesg |grep -i blue):
```

$ dmesg|grep -i blue
[   21.031234] Bluetooth: Core ver 2.15
[   21.036482] Bluetooth: HCI device and connection manager initialized
[   21.036484] Bluetooth: HCI socket layer initialized
[   21.037887] Bluetooth: Generic Bluetooth USB driver ver 0.6

```

---

### Post by gandaran on 2011-08-09
> When I click on my Bluetooth manager icon->preferences, it says "Bluetooth is disabled" and there is a big Button with "Turn On Bluetooth" which doesn't do anything that I can see. And /etc/init.d/start also doesn't appear to do anything.
install blueman from software center, blueman can turn on bluetooth easily then you can use or setup your bluetooth devices even with gnome bluetooth manager.

---

### Post by lbirunner on 2011-08-09
Ok, that was worth a shot but I get an error when I click "System->Preferences->Bluetooth Manager". See attached.

And:

> 
~$ ps aux|grep blue
root       763  0.0  0.0      0     0 ?        S    09:13   0:00 [bluetooth]
ms  1864  0.0  0.2 102564  9108 ?        S    09:14   0:00 bluetooth-applet
ms  6649  0.0  0.0   3328   904 pts/1    S+   15:08   0:00 grep --color=auto blue


And: 
> 
~$ dmesg|grep -i blue
[    7.681908] Bluetooth: Core ver 2.15
[    7.682109] Bluetooth: HCI device and connection manager initialized
[    7.682112] Bluetooth: HCI socket layer initialized
[    8.272131] Bluetooth: Generic Bluetooth USB driver ver 0.6
[ 8201.770548] Modules linked in: aes_i586 aes_generic binfmt_misc vmnet ppdev parport_pc vmblock vsock vmci vmmon snd_hda_codec_idt fbcon tileblit font bitblit softcursor snd_hda_intel vga16fb vgastate snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss arc4 snd_seq_midi iwl3945 i915 snd_rawmidi iwlcore hid_apple snd_seq_midi_event mac80211 snd_seq led_class snd_timer snd_seq_device drm_kms_helper drm usbhid snd pcmcia joydev soundcore i2c_algo_bit hid snd_page_alloc yenta_socket cfg80211 rsrc_nonstatic pcmcia_core psmouse serio_raw video intel_agp agpgart btusb dell_wmi cdc_ether output bluetooth cdc_subset dell_laptop dcdbas usbnet mii lp parport ohci1394 ieee1394 tg3
[ 8201.770787]  [<f882ac61>] hci_free_dev+0x21/0x30 [bluetooth]


And if it helps:

> 
~$ lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:8140 Dell Computer Corp. Wireless 360 Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0525:a4a2 Netchip Technology, Inc. Linux-USB Ethernet/RNDIS Gadget
Bus 002 Device 006: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 002 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
msheehan@mslap:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


---

### Post by gandaran on 2011-08-10
try removing bluez then install again, use the command line to uninstall
```
sudo apt-get remove --purge bluez
```
watch the terminal output, if any message that some configuration file or folder is left behind you will have to manually delete it as you will need to completely remove everything to do with bluez from the system then re-install, bluez should work again if you succeeded removing all previous configurations.

---

### Post by lbirunner on 2011-08-10
gandaran,

Thank you for your persistence.
That "--purge" option did it. I know because I removed and re-installed bluez several times without success.

So bluetooth is now working again!
Thanks again.

---

### Post by jaithehulk on 2012-09-03
Thank you !! Bluetooth has started working on my Asus K53SD Laptop

---

### Post by OriTheEep on 2012-10-25
After installing 12.04 from scratch following an upgrade failure (Grrrrrrr!) and abandoning Unity for Gnome Classic-without-gubbins, I plugged a USB bluetooth adaptor in and found the same problem as started this thread. Following advice on purging bluez appeared to solve this, as there were suddenly lots of options available from the icon in the notification area.

Unfortunately, an attempt to adjust bluetooth settings failed to open the relevant window, caused the options to disappear from said icon in the notification area and removed the bluetooth icon from system settings. Rather than mess further inexpertly, I'll wait a bit hoping for informed advice :)

---

