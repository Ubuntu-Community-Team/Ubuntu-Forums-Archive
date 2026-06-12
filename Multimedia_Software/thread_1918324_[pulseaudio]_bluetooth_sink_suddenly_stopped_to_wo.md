---
title: "[pulseaudio] bluetooth sink suddenly stopped to work"
date: 2012-01-31
forum: Multimedia Software
---

### Post by macross3003 on 2012-01-31
hi everybody,
I have a bt audio receiver which suddenly started to fail while listening (I've lost those logs). I removed the bt device and repairing which works fine but pa refuses to add it again as a sink. Here is the -vvvv log for the moment I add the device in case it would be useful for somebody.
I'm using pulseaudio 1.1

>     D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Adapter, path=/org/bluez/3475/hci0, member=DeviceCreated
    D: [pulseaudio] bluetooth-util.c: Device /org/bluez/3475/hci0/dev_00_02_72_E6_57_A5 created
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Adapter, path=/org/bluez/3475/hci0, member=DeviceCreated
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'disconnected'
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'disconnected'
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Device, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'connecting'
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Audio, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'connecting'
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Audio, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'connected'
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.AudioSink, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: interface=org.bluez.Audio, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
    D: [pulseaudio] bluetooth-util.c: dbus: property 'State' changed to value 'connected'
    D: [pulseaudio] module-bluetooth-discover.c: Loading module-bluetooth-device address="00:02:72:E6:57:A5" path="/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5"
    I: [pulseaudio] module-card-restore.c: Restoring profile for card bluez_card.00_02_72_E6_57_A5.
    I: [pulseaudio] card.c: Created 2 "bluez_card.00_02_72_E6_57_A5"
    bt_audio_service_open: connect() failed: Connection refused (111)
    W: [pulseaudio] module-bluetooth-device.c: Bluetooth audio service not available
    W: [pulseaudio] module-bluetooth-device.c: Service not connected
    I: [pulseaudio] card.c: Freed 2 "bluez_card.00_02_72_E6_57_A5"
    D: [pulseaudio] core-subscribe.c: Dropped redundant event due to remove event.
    E: [pulseaudio] module.c: Failed to load module "module-bluetooth-device" (argument: "address="00:02:72:E6:57:A5" path="/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5""): initialization failed.
    D: [pulseaudio] module-bluetooth-discover.c: Failed to load module for device /org/bluez/3475/hci0/dev_00_02_72_E6_57_A5
    D: [pulseaudio] module-console-kit.c: dbus: interface=org.bluez.Audio, path=/org/bluez/3475/hci0/dev_00_02_72_E6_57_A5, member=PropertyChanged
(via [http://pastebin.com/0GCge9X3](http://pastebin.com/0GCge9X3))

The receiver works fine b/c I tried it from other devices.

Thanks a lot!

---

