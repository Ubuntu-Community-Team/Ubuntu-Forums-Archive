---
title: "command-line access to a USB-mounted camera"
date: 2014-09-21
forum: Multimedia Software
---

### Post by George Heine on 2014-09-21
Have worked with several cameras over the years and usually, to access the photos, I attach the camera cable to a USB port on my system.  After a few seconds, running "mount" will give a message like

```
/dev/sdb1 on /media/3765-6534 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```

The name of the mount point varies depending on the camera and memory card, but it doesn't matter.  I can use bash commands to access the photos in subdirectories under the DCIM directory under the mount point.  They can be viewed, edited, deleted, moved to storage, and in general treated like ordinary files.   When finished, I run "umount" and disconnect the camera.

Recently acquired a Nikon Coolpix S9700. Running "mount" does not show this camera on a SCSI port.  I initially thought that the system was simply not recognizing the camera.  However, after searching this forum and others, I tried installing gphoto2.  Running "gphoto-2 --auto-detect"  gives a message like
```
Model                          Port
----------------------------------------------------------
USB PTP Class Camera           usb:001,009 
```

but trying to do anything else with gphoto2 resulted in errors about "could not lock the device".

After further research in the forums, I tried opening a Nautilus "File" window, and under "Devices," found an entry labeled "NIKON DSC COOLPIX S9700-PTP" and pointing to "/gphoto2://[usb:001,009]", and under this entry found DCIM and the photo subdirectories. The photos were accessible using GUI operations such as drag-and-drop, but there must be a way to get at them using the command line.

Question: how can I bypass Nautilus, and get command-line access to the photos on the camera, either with or without the use of gphoto2?

I never use Nautilus.  In fact, have used dconf-editor to disable automount-open of a Nautilus window when a device is mounted.

Versions: Ubuntu 12.04, gphoto2 2.4.11.

thanks for any assistance

---

### Post by George Heine on 2014-09-23
bump.  tried connecting the Nikon to another computer with 14.04 LTS, virtually identical results.  The new system does not have gphoto2 installed.  Here's the output from /var/log/sysog:

```
Sep 23 18:17:02 kali CRON[24454]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 18:33:58 kali kernel: [10205.968122] usb 1-6: new high-speed USB device number 4 using ehci-pci
Sep 23 18:33:58 kali kernel: [10206.101348] usb 1-6: New USB device found, idVendor=04b0, idProduct=034b
Sep 23 18:33:58 kali kernel: [10206.101361] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 23 18:33:58 kali kernel: [10206.101369] usb 1-6: Product: NIKON DSC COOLPIX S9700-PTP
Sep 23 18:33:58 kali kernel: [10206.101377] usb 1-6: Manufacturer: NIKON
Sep 23 18:33:58 kali kernel: [10206.101384] usb 1-6: SerialNumber: 000030038441
Sep 23 18:33:59 kali mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6"
Sep 23 18:33:59 kali mtp-probe: bus: 1, device: 4 was not an MTP device
Sep 23 18:34:00 kali colord: Device added: sysfs-NIKON-NIKON_DSC_COOLPIX_S9700-PTP
Sep 23 18:34:00 kali colord: Device added: sysfs-(null)
Sep 23 18:36:07 kali dbus[593]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Sep 23 18:36:07 kali kernel: [10335.345804] systemd-hostnamed[24503]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Sep 23 18:36:07 kali dbus[593]: [system] Successfully activated service 'org.freedesktop.hostname1'
Sep 23 18:37:42 kali wpa_supplicant[993]: message repeated 29 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Sep 23 18:38:35 kali wpa_supplicant[993]: wlan0: WPA: Group rekeying completed with 00:24:7b:a6:76:a6 [GTK=TKIP]

```

Why isn't there just a mount point that I can CD to?

---

### Post by George Heine on 2014-11-19
bump.  eight weeks, no responses.  is there another forum that would be better to post to?

---

### Post by steeldriver on 2014-11-19
I have no experience on this topic, but based on the info you've posted above I would guess that it is part of the gvfs (gnome virtual file system) and that you would find the files under the usual gvfs tree - either ~/.gvfs (Ubuntu 12.04 and earlier) or /run/user/<uid>/gvfs (13.10 on)

You could also try simply using URI style gphoto2://[usb:001,009]

---

### Post by George Heine on 2014-11-20
> I have no experience on this topic, but based on the info you've posted  above I would guess that it is part of the gvfs (gnome virtual file  system) and that you would find the files under the usual gvfs tree -  either ~/.gvfs (Ubuntu 12.04 and earlier) or /run/user/<uid>/gvfs  (13.10 on)


Thank you, that was exactly what I needed.  I saw the gvfs directory from "mount" (must have been there before), I have 14.04, so   cd'd to /run/user/<uid>/gvfs, found the camera, was able to access photos with normal command-line operations, and ran umount (as sudo) when finished.

> You could also try simply using URI style gphoto2://[usb:001,009]

Will try this when I get a chance.

---

