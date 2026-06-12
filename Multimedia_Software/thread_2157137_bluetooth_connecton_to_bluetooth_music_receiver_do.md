---
title: "bluetooth connecton to bluetooth music receiver doesnt work"
date: 2013-06-24
forum: Multimedia Software
---

### Post by sisqonrw on 2013-06-24
hi sadly the connection to the 

[http://www.lintech.de/produkte/kategorie/bluetooth-musikempfaenger/bluelino-home/](http://www.lintech.de/produkte/kategorie/bluetooth-musikempfaenger/bluelino-home/)

doesnt works.

how can i fix the problem.

i am using lubuntu 13.04.

i tried it with kubuntu before on the same pc and it has worked.

---

### Post by sisqonrw on 2013-07-14
i need urgend help. i can add a audio bluetooth device but i can not connect it. with kubuntu on the sampe notebook i can connect it. where is the problem?

---

### Post by monkeybrain2012 on 2013-07-15
Can you give more detailed descriptions of the problem if you want people to help? E.g did blueman detect the device? What happened when you try to pair and at which point did it fail?

---

### Post by chorca on 2013-07-15
[xubuntu 13.04]

I'm having a similar problem. This worked in 12.10, but after the upgrade last night to 13.04, bluetooth no longer works properly with A2DP.

I have pulseaudio-module-bluetooth installed.

I am able to see and pair with the device, at which point I attempt to connect to the Audio Sink on it with Blueman. Blueman responds after a few seconds with "Connection Failed: Stream setup failed"

Running bluetoothd in debug mode, I see the following:

```
bluetoothd[2588]: audio/avdtp.c:avdtp_ref() 0x7f49c33da6b0: ref=2
bluetoothd[2588]: audio/sink.c:sink_set_state() State changed /org/bluez/2588/hci0/dev_00_02_3C_41_CA_0D: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[2588]: audio/sink.c:sink_connect() stream creation in progress
bluetoothd[2588]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[2588]: plugins/mgmtops.c:mgmt_event() Received 34 bytes from management socket
bluetoothd[2588]: plugins/mgmtops.c:mgmt_device_connected() hci0 device 00:02:3C:41:CA:0D connected eir_len 15
bluetoothd[2588]: src/adapter.c:adapter_get_device() 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected signaling channel to 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/avdtp.c:avdtp_connect_cb() AVDTP imtu=672, omtu=895
bluetoothd[2588]: audio/avctp.c:avctp_set_state() AVCTP Connecting
bluetoothd[2588]: audio/avdtp.c:session_cb() 
bluetoothd[2588]: audio/avdtp.c:avdtp_parse_resp() DISCOVER request succeeded
bluetoothd[2588]: audio/avdtp.c:avdtp_discover_resp() seid 1 type 1 media 0 in use 0
bluetoothd[2588]: audio/avdtp.c:session_cb() 
bluetoothd[2588]: audio/avdtp.c:avdtp_parse_resp() GET_CAPABILITIES request succeeded
bluetoothd[2588]: audio/avdtp.c:avdtp_get_capabilities_resp() seid 1 type 1 media 0
bluetoothd[2588]: audio/sink.c:discovery_complete() Discovery complete
bluetoothd[2588]: Unable to select SEP
bluetoothd[2588]: audio/avdtp.c:avdtp_unref() 0x7f49c33da6b0: ref=1
bluetoothd[2588]: audio/avctp.c:avctp_connect_cb() AVCTP: connected to 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/avctp.c:init_uinput() AVRCP: uinput initialized for 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/avctp.c:avctp_set_state() AVCTP Connected
bluetoothd[2588]: audio/avdtp.c:connection_lost() Disconnected from 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/sink.c:sink_set_state() State changed /org/bluez/2588/hci0/dev_00_02_3C_41_CA_0D: SINK_STATE_CONNECTING -> SINK_STATE_DISCONNECTED
bluetoothd[2588]: audio/avctp.c:avctp_set_state() AVCTP Disconnected
bluetoothd[2588]: audio/avctp.c:avctp_disconnected() AVCTP: closing uinput for 00:02:3C:41:CA:0D
bluetoothd[2588]: audio/avdtp.c:avdtp_unref() 0x7f49c33da6b0: ref=0
bluetoothd[2588]: audio/avdtp.c:avdtp_unref() 0x7f49c33da6b0: freeing session and removing from list
bluetoothd[2588]: plugins/mgmtops.c:mgmt_event() cond 1
bluetoothd[2588]: plugins/mgmtops.c:mgmt_event() Received 14 bytes from management socket
bluetoothd[2588]: plugins/mgmtops.c:mgmt_device_disconnected() hci0 device 00:02:3C:41:CA:0D disconnected
bluetoothd[2588]: src/event.c:btd_event_disconn_complete() 
bluetoothd[2588]: src/adapter.c:adapter_remove_connection() 

```


The "Unable to select SEP" message is in a few different spots around the web, but it seems to be related between PulseAudio using a connection type that Bluez has mentioned would become deprecated, namely the "Enable=Socket" that can be added in /etc/bluetooth/audio.conf. From what I have gathered, PulseAudio needs to change the way they handle this and start using dbus, which has not happened yet, and a commit was made to Bluez which (accidentally or not) broke this.

I attempted to put the Enable=Socket into my audio.conf, but then I am unable to switch to a2dp mode on the device, with blueman coming back and saying "Failed to change profile to a2dp". There are no messages from bluetoothd when this is done. The device shows up in the Configuration section of the PulseAudio mixer, but changing it to A2DP mode does nothing, the device does not show under "Output Devices".

There is a ticket open for this, which appears to not have gotten much traction, so not sure how long this will be broken for.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1181106](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1181106)

There is also a RedHat bug for this, which has been marked resolved with a newer version of Bluez.
[https://bugzilla.redhat.com/show_bug.cgi?id=964031](https://bugzilla.redhat.com/show_bug.cgi?id=964031)
However, it appears some devices are still affected by the "Unable to select SEP" error.

A more appropriate bug for the SEP issue would be the following:
[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1199059](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1199059)

---

### Post by monkeybrain2012 on 2013-07-15
There seems to be a bug in Blueman in 13.04, I am able to connect to my bluetooth A2DP speaker using just the default gnome-bluetooth applet (I have also installed the package bluetooth support and pulseaudio bluetooth module) reliably, but Blueman always fails with the error message "stream setup failed"

[http://ubuntuforums.org/showthread.php?t=2144841](http://ubuntuforums.org/showthread.php?t=2144841)


Edited: Blueman works on Ubuntu12.04, but doesn't seem to work in Lubuntu 12.04. Somehow in Lubuntu when trying to connect with Blueman a window  always pops up asking for device code(???) and is not able to add the device complaining authentication failure.I don't see this in Ubuntu 12.04.May have something to do with the bluetooth adapter (?? sorry, don't really know a lot about the details of bluetooth)

---

