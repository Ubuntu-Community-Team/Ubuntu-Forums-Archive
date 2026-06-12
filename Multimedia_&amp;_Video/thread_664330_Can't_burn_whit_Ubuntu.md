---
title: "Can't burn whit Ubuntu"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by TrueAncalagon on 2008-01-11
First of all, sorry about my english, but I need your help.
I'm a newbe whit linux, I had come to this OS from XP. In the last months I used Ubuntu, and from dicember I used Ubuntu 7.10. I had burn DVD, DC, ISO, DVDDL. From some day I can't burn anything. Simply the program start (Braseo, K3B or Ubuntu it self) and all work fine, but when it start to burn the OS freeze. I have formated and reinstalled Ubuntu (ONLY root and swap because the /home is in a separated partition), but nothing change. I had started the programs from console for watch if there is some errors, but...

BRASERO

```
(brasero:26790): Pango-CRITICAL **: pango_layout_set_markup_with_accel: assertion `markup != NULL' failed
```

K3B

```
otacon@otacon:~$ k3b > file.txt
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
kbuildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
otacon@otacon:~$ (K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD_DC_DW1670 to device /dev/hdc
/dev/hdc resolved to /dev/hdc
/dev/hdc is block device (0)
/dev/hdc seems to be cdrom
(K3bDevice::Device) /dev/hdc: init()
(K3bDevice::Device) /dev/hdc feature: CD Mastering
(K3bDevice::Device) /dev/hdc feature: CD Track At Once
(K3bDevice::Device) /dev/hdc feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/hdc feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/hdc feature: DVD+R
(K3bDevice::Device) /dev/hdc feature: DVD+RW
(K3bDevice::Device) /dev/hdc feature: DVD+R Double Layer
(K3bDevice::Device) /dev/hdc feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/hdc feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/hdc feature: Layer Jump Recording
(K3bDevice::Device) /dev/hdc unknown profile: 2
(K3bDevice::Device) /dev/hdc: dataLen: 60
(K3bDevice::Device) /dev/hdc: checking for TAO
(K3bDevice::Device) /dev/hdc: checking for SAO
(K3bDevice::Device) /dev/hdc: checking for SAO_R96P
(K3bDevice::Device) /dev/hdc: checking for SAO_R96R
(K3bDevice::Device) /dev/hdc: checking for RAW_R16
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/hdc: checking for RAW_R96P
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/hdc: checking for RAW_R96R
(K3bDevice::ScsiCommand) failed: 
                           command:    MODE SELECT (55)
                           errorcode:  70
                           sense key:  ILLEGAL REQUEST (5)
                           asc:        26
                           ascq:       0
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE dataLen = 72
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE successful with reported length: 68
(K3bDevice::Device) /dev/hdc:  Number of supported write speeds via GET PERFORMANCE: 4
(K3bDevice::Device) /dev/hdc : 22160 KB/s
(K3bDevice::Device) /dev/hdc : 11080 KB/s
(K3bDevice::Device) /dev/hdc : 5540 KB/s
(K3bDevice::Device) /dev/hdc : 2770 KB/s
(K3bDevice::DeviceManager) setting current write speed of device /dev/hdc to 22160
/dev/hdc resolved to /dev/hdc
(K3bDevice::DeviceManager) dev /dev/hdc already found
(K3bDevice::DeviceManager) found config entry for devicetype: BENQ DVD DC DW1670
Devices:
------------------------------
Blockdevice:    /dev/hdc
Generic device: 
Vendor:         BENQ
Description:    DVD DC DW1670
Version:        103
Write speed:    22160
Profiles:       DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Read Cap:       DVD-ROM, DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+RW Dual Layer, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW
Write Cap:      DVD-R, DVD-R Sequential, DVD-R Dual Layer, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-R, CD-RW
Writing modes:  SAO, TAO, SAO/R96P, SAO/R96R, Restricted Overwrite, Layer Jump
Reader aliases: /dev/hdc
------------------------------
First sec data area: 43:41:33 (LBA 196608) (402653184
Last sec data area: 00:00:00 (LBA 0) (0 Bytes)
Last sec layer 1: 00:00:00 (LBA 0) (0 Bytes)
Layer 1 length: 00:00:01 (LBA 1) (2048 Bytes)
Layer 2 length: 00:00:00 (LBA 0) (0 Bytes)
DiskInfo:
Mediatype:       DVD-R Sequential
Current Profile: DVD-R Sequential
Disk state:      empty
Empty:           1
Rewritable:      0
Appendable:      0
Sessions:        0
Tracks:          0
Layers:          1
Capacity:        510:46:46 (LBA 2298496) (4707319808 Bytes)
Remaining size:  510:46:46 (LBA 2298496) (4707319808 Bytes)
Used Size:       00:00:00 (LBA 0) (0 Bytes)
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE dataLen = 72
(K3bDevice::Device) /dev/hdc: GET PERFORMANCE successful with reported length: 68
(K3bDevice::Device) /dev/hdc:  Number of supported write speeds via GET PERFORMANCE: 4
(K3bDevice::Device) /dev/hdc : 22160 KB/s
(K3bDevice::Device) /dev/hdc : 11080 KB/s
(K3bDevice::Device) /dev/hdc : 5540 KB/s
(K3bDevice::Device) /dev/hdc : 2770 KB/s
```

Now I don't know what to do. My forum have not idea and I don't want to leave linux, but if I cant burn...

I think, from my hill of ignorance, there may be some configuration file from /home partition, but don't know

---

### Post by TrueAncalagon on 2008-01-12
Any idea?

---

### Post by henryliao on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/118996](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/118996) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> buildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
> kbuildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file

I have a similar error with Ubuntu 7.10.  It seems to be caused when KDE app was first ran with sudo/gksudo and $HOME/.kde was created/owned by root.  Check the ownership/permission of $HOME/.kde directory if necessary corrected with "chown -R $USER:$USER $HOME/.kde".  Good luck.

---

### Post by Oni-BR- on 2008-01-21
> **henryliao said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/118996](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/118996) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> buildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
> kbuildsycoca: WARNING: Parse error in /home/otacon/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file

I have a similar error with Ubuntu 7.10.  It seems to be caused when KDE app was first ran with sudo/gksudo and $HOME/.kde was created/owned by root.  Check the ownership/permission of $HOME/.kde directory if necessary corrected with "chown -R $USER:$USER $HOME/.kde".  Good luck.

	
I am having the same problem that our TrueAncalagon friend, but I do not know how I can proceed to repair it. You could do a tutorial explaining how to use his tip?

Thanks, Oni-BR-

---

