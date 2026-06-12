---
title: "Bluetooth to T-DEX not appearing in Sound Settings"
date: 2012-10-12
forum: Multimedia Software
---

### Post by lordbah on 2012-10-12
I have a device which acts as a bridge from the Bluetooth on my cell phone to the telecoils in my hearing aids. Model name is "T-DEX". It works fine with a cell phone. I also want it to work with my desktop (Ubuntu 12.04). It makes the Bluetooth connection, but never gets added as an option in Sound Settings for input or output. I also have a Logitech Mini Boombox, and the desktop makes a Bluetooth connection with it, and that does get added as an option in Sound Settings. So each piece of hardware works in some combination with the others, it's just the T-DEX + Ubuntu combination doesn't let me direct sound to it, which is kinda the entire point of that device.

In Bluetooth settings they both say Type: Headset.

sdptool browse <address>
returns no output for either T-DEX or Mini Boombox. I was hoping that would tell me what protocols the devices provided/required.

hcitool info <address>
	BD Address:  00:1B:08:00:07:0A
	Device Name: T-DEX
	LMP Version: 2.0 (0x3) LMP Subversion: 0x103a
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xff 0xff 0x8f 0x78 0x18 0x18 0x00 0x80
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<power control> <transparent SCO> <broadcast encrypt> 
		<enhanced iscan> <interlaced iscan> <interlaced pscan> 
		<inquiry with RSSI> <AFH cap. slave> <AFH class. slave> 
		<AFH cap. master> <AFH class. master> <extended features> 


/var/log/syslog has this:
Oct 12 18:06:55 arctic bluetoothd[1491]: Connection refused (111)
Oct 12 18:06:55 arctic pulseaudio[6668]: [pulseaudio] module-bluetooth-device.c: Default profile not connected, selecting off profile

Of course I don't know what it's trying to connect to, or what the default profile is, or why there's a problem with it, or how to change any of that.

I don't know where to go from here.

---

### Post by lordbah on 2012-10-18
Any Bluetooth experts around?

---

### Post by lordbah on 2012-10-23
Looking in /var/lib/bluetooth the entries are identical for the T-DEX (which doesn't appear in Sound Settings) and the Mini Boombox (which does) in 'classes' and 'profiles'.

classes:
00:1B:08:00:07:0A 0x240404

profiles:
00:1B:08:00:07:0A 00001108-0000-1000-8000-00805f9b34fb 0000110b-0000-1000-8000-00805f9b34fb 0000110e-0000-1000-8000-00805f9b34fb 0000111e-0000-1000-8000-00805f9b34fb

I haven't figured out where to look to find out what that mess means, but since they are identical, it doesn't seem like it should matter.

Reviewing this thread, the current error message is different from what it was before. The only change I recall making was in /etc/bluetooth/audio.conf adding Enable=Socket, per something I found on the web, but that's commented back out now since it didn't fix the problem.

/var/log/syslog:
Oct 23 07:59:07 arctic bluetoothd[1468]: Protocol not supported (93)
Oct 23 07:59:07 arctic pulseaudio[4483]: [pulseaudio] bluetooth-util.c: Failed to acquire transport fd: Input/output error
Oct 23 07:59:07 arctic pulseaudio[4483]: [pulseaudio] module.c: Failed to load module "module-bluetooth-device" (argument: "address="00:1B:08:00:07:0A" path="/org/bluez/1468/hci0/dev_00_1B_08_00_07_0A""): initialization failed.

---

### Post by lordbah on 2012-11-14
I ran bluetoothd -d -n and this is what was output when I tried to connect. Does it give a clue to anyone? The "Host is down" part seems really odd - isn't this desktop the "host"?


```
bluetoothd[31374]: audio/avdtp.c:avdtp_ref() 0x7fb529cabe00: ref=2
bluetoothd[31374]: audio/avdtp.c:avdtp_ref() 0x7fb529cabe00: ref=3
bluetoothd[31374]: audio/sink.c:sink_set_state() State changed /org/bluez/31374/hci0/dev_09_17_01_00_02_00: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cabe00: ref=2
bluetoothd[31374]: Host is down (112)
bluetoothd[31374]: audio/avdtp.c:connection_lost() Disconnected from 09:17:01:00:02:00
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cabe00: ref=1
bluetoothd[31374]: audio/sink.c:sink_set_state() State changed /org/bluez/31374/hci0/dev_09_17_01_00_02_00: SINK_STATE_CONNECTING -> SINK_STATE_DISCONNECTED
bluetoothd[31374]: audio/sink.c:discovery_complete() connect:connect XCASE detected
bluetoothd[31374]: audio/sink.c:sink_set_state() State changed /org/bluez/31374/hci0/dev_09_17_01_00_02_00: SINK_STATE_DISCONNECTED -> SINK_STATE_DISCONNECTED
bluetoothd[31374]: audio/device.c:device_set_state() state change attempted from disconnected to disconnected
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cabe00: ref=0
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cabe00: freeing session and removing from list
bluetoothd[31374]: plugins/hciops.c:conn_complete() status 0x04
bluetoothd[31374]: src/event.c:btd_event_conn_failed() status 0x04
bluetoothd[31374]: audio/sink.c:stream_setup_retry() Stream setup failed, after XCASE connect:connect

```

---

### Post by lordbah on 2012-11-14
Tried it again and got more output. Here I actually see the "Protocol not supported".


```
bluetoothd[31374]: audio/headset.c:headset_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: HEADSET_STATE_DISCONNECTED -> HEADSET_STATE_CONNECTING
bluetoothd[31374]: audio/media.c:headset_state_changed() 
bluetoothd[31374]: audio/media.c:media_endpoint_async_call() Calling SetConfiguration: name = :1.62 path = /MediaEndpoint/HFPAG
bluetoothd[31374]: plugins/hciops.c:conn_complete() status 0x00
bluetoothd[31374]: src/adapter.c:adapter_get_device() 00:1B:08:00:07:0A
bluetoothd[31374]: plugins/hciops.c:remote_features_information() hci0 status 0
bluetoothd[31374]: plugins/hciops.c:remote_name_information() hci0 status 0
bluetoothd[31374]: audio/headset.c:headset_set_channel() Discovered Handsfree service on channel 1
bluetoothd[31374]: audio/headset.c:rfcomm_connect() /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: Connecting to 00:1B:08:00:07:0A channel 1
bluetoothd[31374]: plugins/hciops.c:link_key_request() hci0 dba 00:1B:08:00:07:0A
bluetoothd[31374]: plugins/hciops.c:get_auth_info() hci0 dba 00:1B:08:00:07:0A
bluetoothd[31374]: plugins/hciops.c:link_key_request() kernel auth requirements = 0x04
bluetoothd[31374]: plugins/hciops.c:link_key_request() Matching key found
bluetoothd[31374]: plugins/hciops.c:link_key_request() link key type 0x00
bluetoothd[31374]: plugins/hciops.c:auth_complete() hci0 status 0
bluetoothd[31374]: plugins/hciops.c:bonding_complete() status 0x00
bluetoothd[31374]: src/adapter.c:adapter_get_device() 00:1B:08:00:07:0A
bluetoothd[31374]: src/device.c:device_bonding_complete() bonding (nil) status 0x00
bluetoothd[31374]: audio/headset.c:headset_connect_cb() /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: Connected to 00:1B:08:00:07:0A
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+BRSF=24
bluetoothd[31374]: audio/headset.c:print_hf_features() HFP HF features: "Voice recognition activation" "Remote volume control" 
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+CIND=?
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+CIND?
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+CMER=3, 0, 0, 1
bluetoothd[31374]: audio/headset.c:event_reporting() Event reporting (CMER): mode=3, ind=1
bluetoothd[31374]: audio/headset.c:hfp_slc_complete() HFP Service Level Connection established
bluetoothd[31374]: audio/telephony.c:telephony_device_connected() telephony-dummy: device 0x7fb529ca50c0 connected
bluetoothd[31374]: audio/headset.c:headset_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: HEADSET_STATE_CONNECTING -> HEADSET_STATE_CONNECTED
bluetoothd[31374]: audio/media.c:headset_state_changed() 
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+VGS=12
bluetoothd[31374]: audio/headset.c:handle_event() Received AT+VGM=12
bluetoothd[31374]: audio/avdtp.c:avdtp_ref() 0x7fb529cab200: ref=2
bluetoothd[31374]: audio/avdtp.c:avdtp_ref() 0x7fb529cab200: ref=3
bluetoothd[31374]: audio/sink.c:sink_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: SINK_STATE_DISCONNECTED -> SINK_STATE_CONNECTING
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cab200: ref=2
bluetoothd[31374]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected signaling channel to 00:1B:08:00:07:0A
bluetoothd[31374]: audio/avdtp.c:avdtp_connect_cb() AVDTP imtu=672, omtu=895
bluetoothd[31374]: audio/avctp.c:avctp_set_state() AVCTP Connecting
bluetoothd[31374]: audio/avdtp.c:session_cb() 
bluetoothd[31374]: audio/avdtp.c:avdtp_parse_resp() DISCOVER request succeeded
bluetoothd[31374]: audio/avdtp.c:avdtp_discover_resp() seid 1 type 1 media 0 in use 0
bluetoothd[31374]: audio/avdtp.c:session_cb() 
bluetoothd[31374]: audio/avdtp.c:avdtp_parse_resp() GET_CAPABILITIES request succeeded
bluetoothd[31374]: audio/avdtp.c:avdtp_get_capabilities_resp() seid 1 type 1 media 0
bluetoothd[31374]: audio/sink.c:discovery_complete() Discovery complete
bluetoothd[31374]: audio/avdtp.c:avdtp_ref() 0x7fb529cab200: ref=3
bluetoothd[31374]: audio/a2dp.c:setup_ref() 0x7fb529c92310: ref=1
bluetoothd[31374]: audio/a2dp.c:a2dp_config() a2dp_config: selected SEP 0x7fb529c9a180
bluetoothd[31374]: audio/a2dp.c:setup_ref() 0x7fb529c92310: ref=2
bluetoothd[31374]: audio/avdtp.c:avdtp_set_configuration() 0x7fb529cab200: int_seid=1, acp_seid=1
bluetoothd[31374]: audio/a2dp.c:setup_unref() 0x7fb529c92310: ref=1
bluetoothd[31374]: audio/avdtp.c:session_cb() 
bluetoothd[31374]: audio/avdtp.c:avdtp_parse_resp() SET_CONFIGURATION request succeeded
bluetoothd[31374]: audio/a2dp.c:setconf_cfm() Source 0x7fb529c9a180: Set_Configuration_Cfm
bluetoothd[31374]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: IDLE -> CONFIGURED
bluetoothd[31374]: audio/avdtp.c:session_cb() 
bluetoothd[31374]: audio/avdtp.c:avdtp_parse_resp() OPEN request succeeded
bluetoothd[31374]: audio/avctp.c:avctp_connect_cb() AVCTP: connected to 00:1B:08:00:07:0A
bluetoothd[31374]: audio/avctp.c:init_uinput() AVRCP: uinput initialized for 00:1B:08:00:07:0A
bluetoothd[31374]: audio/avctp.c:avctp_set_state() AVCTP Connected
bluetoothd[31374]: audio/avdtp.c:avdtp_connect_cb() AVDTP: connected transport channel to 00:1B:08:00:07:0A
bluetoothd[31374]: audio/avdtp.c:handle_transport_connect() Flushable packets enabled
bluetoothd[31374]: audio/avdtp.c:handle_transport_connect() sk 32, omtu 895, send buffer size 114688
bluetoothd[31374]: audio/a2dp.c:open_cfm() Source 0x7fb529c9a180: Open_Cfm
bluetoothd[31374]: audio/sink.c:stream_setup_complete() Stream successfully created
bluetoothd[31374]: audio/a2dp.c:setup_unref() 0x7fb529c92310: ref=0
bluetoothd[31374]: audio/a2dp.c:setup_free() 0x7fb529c92310
bluetoothd[31374]: audio/avdtp.c:avdtp_unref() 0x7fb529cab200: ref=2
bluetoothd[31374]: audio/avdtp.c:avdtp_sep_set_state() stream state changed: CONFIGURED -> OPEN
bluetoothd[31374]: audio/sink.c:sink_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: SINK_STATE_CONNECTING -> SINK_STATE_CONNECTED
bluetoothd[31374]: audio/unix.c:server_cb() Accepted new client connection on unix socket (fd=34)
bluetoothd[31374]: audio/transport.c:media_transport_acquire() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1: read lock acquired
bluetoothd[31374]: audio/transport.c:media_transport_acquire() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1: write lock acquired
bluetoothd[31374]: audio/transport.c:media_owner_create() Owner created: sender=:1.62 accesstype=rw
bluetoothd[31374]: audio/headset.c:headset_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS
bluetoothd[31374]: audio/media.c:headset_state_changed() 
bluetoothd[31374]: audio/transport.c:media_request_create() Request created: method=Acquire id=6
bluetoothd[31374]: audio/transport.c:media_owner_add() Owner :1.62 Request Acquire
bluetoothd[31374]: audio/transport.c:media_transport_add() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1 Owner :1.62
bluetoothd[31374]: Protocol not supported (93)
bluetoothd[31374]: audio/transport.c:media_transport_remove() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1 Owner :1.62
bluetoothd[31374]: audio/transport.c:media_transport_release() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1: read lock released
bluetoothd[31374]: audio/transport.c:media_transport_release() Transport /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A/fd1: write lock released
bluetoothd[31374]: audio/transport.c:media_request_reply() Request Acquire Reply Input/output error
bluetoothd[31374]: audio/transport.c:media_owner_free() Owner :1.62
bluetoothd[31374]: audio/transport.c:media_owner_remove() Owner :1.62 Request Acquire
bluetoothd[31374]: audio/headset.c:headset_set_state() State changed /org/bluez/31374/hci0/dev_00_1B_08_00_07_0A: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_CONNECTED
bluetoothd[31374]: audio/media.c:headset_state_changed() 
bluetoothd[31374]: audio/unix.c:client_cb() Unix client disconnected (fd=34)
bluetoothd[31374]: audio/unix.c:client_free() client_free(0x7fb529ca7800)

```

---

### Post by _pitch on 2013-02-08
I found a solution for me when reading this bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/972063](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/972063)

Lazy solution:
```
sudo apt-get install pulseaudio-module-bluetooth
```

Cheers
/Patric

---

### Post by lordbah on 2013-02-08
> **_pitch said:**
> I found a solution for me when reading this bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/972063](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/972063)

Lazy solution:
```
sudo apt-get install pulseaudio-module-bluetooth
```

Cheers
/Patric

Glad it works for you. I already had that package installed.

---

