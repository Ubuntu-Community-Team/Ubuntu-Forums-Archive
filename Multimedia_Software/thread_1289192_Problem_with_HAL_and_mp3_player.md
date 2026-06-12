---
title: "Problem with HAL and mp3 player"
date: 2009-10-12
forum: Multimedia Software
---

### Post by djbushido on 2009-10-12
I am having problems with my mp3 player (Sony Walkman) mounting as an mtp device. I followed the instructions [here]("http://kubuntuforums.net/forums/index.php?topic=3096598") to try and see if that helped. Not really. So as it stands, I am running a patched version of HAL, but not enough to do anything different for my mp3 player (I didn't do the mtp section). Ubuntu tells the mp3 player to go to mtp mode - connecting it with xfce running more often than not places it in standard usb mode. I am trying to figure out why this is, and if possible, fix it such that I can seamlessly use my mp3 player. Usually, if it gets mounted as mtp, I have to restart my computer, restarting hal only apparently doesn't work. 
Also, output of lshal --moniter for successful mount: ```
lshal -m

Start monitoring devicelist:
-------------------------------------------------
06:47:58.320: usb_device_54c_35c_F9F465018828 added
06:47:59.880: usb_device_54c_35c_F9F465018828_if0 added
06:47:59.880: usb_device_54c_35c_F9F465018828_if0_scsi_host added
06:48:03.336: usb_device_54c_35c_F9F465018828_if0_scsi_host_0 added
06:48:03.336: usb_device_54c_35c_F9F465018828_if0_scsi_host_0_scsi_device_lun0 added
06:48:05.680: usb_device_54c_35c_F9F465018828_if0_scsi_host_0_scsi_device_lun0_scsi_generic added
06:48:06.731: storage_serial_Sony_WALKMAN_F9F465018828 added
06:48:06.740: storage_serial_Sony_WALKMAN_F9F465018828 property info.interfaces = {'org.freedesktop.Hal.Device.Storage.Removable'} (new)
06:48:07.100: volume_uuid_0000_0002 added
06:48:44.722: volume_uuid_0000_0002 property volume.mount_point = '/media/WALKMAN'
06:48:44.732: volume_uuid_0000_0002 property volume.is_mounted = true

```
And unsuccessful: ```
lshal -m

Start monitoring devicelist:
-------------------------------------------------
22:05:41.372: usb_device_54c_35c_F9F465018828 added
22:05:41.529: usb_device_54c_35c_F9F465018828 property info.linux.driver = 'usb' (new)
22:05:41.576: usb_device_54c_35c_F9F465018828_if0 added
22:05:41.625: usb_device_54c_35c_F9F465018828_if0_scsi_host added
22:05:42.303: usb_device_54c_35c_F9F465018828_if0_scsi_host removed
22:06:08.641: usb_device_54c_35c_F9F465018828_if0 removed
22:06:08.694: usb_device_54c_35c_F9F465018828 removed

```Noting that the succesful mount only shows the device being mounted, the unsuccessful shows the device being connected and then removed.

---

