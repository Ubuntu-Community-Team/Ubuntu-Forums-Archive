---
title: "iPod not showing up in Banshee... think I need to add haldaemon to plugdev"
date: 2008-05-13
forum: Multimedia Software
---

### Post by cmlewin on 2008-05-13
> 
justin@justin-desktop:~$ banshee
/home/justin/.themes/Human Hardy Heron/gtk-2.0/gtkrc:14: Unable to find include file: "toolbar-custom.rc"
Debug: [5/13/2008 4:47:08 PM] (Loading audio profiles) - /usr/share/banshee/audio-profiles
Debug: [5/13/2008 4:47:09 PM] (Default player engine) - GStreamer 0.10
Debug: [5/13/2008 4:47:09 PM] (Audio CD Core Initialized) - 
Debug: [5/13/2008 4:47:09 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_bede1b54_e419_434f_a9bd_be24363a1847
Debug: [5/13/2008 4:47:09 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_bede1b54_e419_434f_a9bd_be24363a1847
Debug: [5/13/2008 4:47:09 PM] (Enabled multimedia keys support) - Using org.gnome.SettingsDaemon
Could not fetch recommendations: Sharing violation on path /home/justin/.config/banshee/plugins/recommendation/76/760e6621
Debug: [5/13/2008 4:54:32 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A270018D22137_0_0
Debug: [5/13/2008 4:54:32 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/storage_serial_Apple_iPod_000A270018D22137_0_0
Debug: [5/13/2008 4:54:32 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
Debug: [5/13/2008 4:54:32 PM] (Waiting for possible DAP to mount) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
Debug: [5/13/2008 4:54:32 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
Debug: [5/13/2008 4:54:33 PM] (Possible DAP has mounted) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
Debug: [5/13/2008 4:54:33 PM] (Testing device for DAP support) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
System.Exception: org.freedesktop.Hal.NoSuchProperty: No property org.podsleuth.ipod.serial_number on device with id /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
  at IDeviceProxy.GetPropertyString (System.String ) [0x00000] 
  at Hal.Device.GetPropertyString (System.String key) [0x00000] 
  at IPod.HalClient.HalDevice+HalProductionInfo..ctor (Hal.Volume volume) [0x00000] 
  at IPod.HalClient.HalDevice..ctor (Hal.Volume volume) [0x00000] 
  at Banshee.Dap.Ipod.IpodDap.LoadIpod () [0x00000] 
Debug: [5/13/2008 4:54:33 PM] (DAP has not been added) - /org/freedesktop/Hal/devices/volume_uuid_0ED1_BB46
Could not load: /media/MYPOD
Setting IO Backend to Banshee.IO.Unix.IOConfig (unix)


I installed podsleuth as some forums say to do, then it says I need to 'add haldaemon to plugdev'... problem is I have no idea what that means nor do I have a clue how to do that... Anyone know?

---

### Post by ianatkin on 2008-07-17
I'd like to echo this question because I'm in the same situation.

I have a haldaemon group but no haldaemon user and I don't have a plugdev group that I can see... do I really need to add a new user for this purpose?  Any pointers would be much appreciated!

Ian

---

