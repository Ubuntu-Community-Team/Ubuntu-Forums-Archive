---
title: "Bluetooth headphones do not work."
date: 2010-01-06
forum: Multimedia Software
---

### Post by walkeraj on 2010-01-06
Running the latest pulseaudio from the development ppa, I am unable to get my Motorola s805 headphones working with Ubuntu Karmic.

When I powered up the headphones, the following messages appeared in syslog:
```
Jan  6 10:21:26 tachyon bluetoothd[1497]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
Jan  6 10:21:30 tachyon kernel: [770181.894467] input: 00:1A:0E:9A:CC:30 as /devices/virtual/input/input10
Jan  6 10:21:30 tachyon rtkit-daemon[1793]: Failed to make ourselves RT: Invalid argument
```

When I attempted to use them, for instance by firing up Audacious, the following messages were generated:

```
Jan  6 10:21:30 tachyon rtkit-daemon[1793]: Failed to make ourselves RT: Invalid argument
Jan  6 10:22:10 tachyon bluetoothd[1497]: HUP or ERR on socket

```

Thinking perhaps it was related to [bug #406702]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702"), I followed the steps to remove rtkit, since the version of pulseaudio I'm using ( 1:0.9.21-0ubuntu3~~karmic~ubuntuaudiodev1 )no longer depends on it, but it still doesn't work:

```
Jan  6 10:41:00 tachyon bluetoothd[1497]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
Jan  6 10:41:04 tachyon kernel: [771355.881269] input: 00:1A:0E:9A:CC:30 as /devices/virtual/input/input13
```

**fire up audacious or even go to sound preferences**

**long pause**

```
Jan  6 10:41:44 tachyon bluetoothd[1497]: HUP or ERR on socket
```

**EDIT:**

Here is the output in syslog from running bluetoothd -d --udev:

_Turning on headset:_

```

bluetoothd[27845]: adapter_get_device(00:1A:0E:9A:CC:30)
bluetoothd[27845]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
bluetoothd[27845]: kernel auth requirements = 0x00
bluetoothd[27845]: stored link key type = 0x00
bluetoothd[27845]: hcid_dbus_bonding_process_complete: status=00
bluetoothd[27845]: adapter_get_device(00:1A:0E:9A:CC:30)
bluetoothd[27845]: hcid_dbus_bonding_process_complete: no pending auth request
bluetoothd[27845]: State changed /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_DISCONNECTED -> HEADSET_STATE_CONNECT_IN_PROGRESS
bluetoothd[27845]: /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: Connected to 00:1A:0E:9A:CC:30
bluetoothd[27845]: Received AT+BRSF=27
bluetoothd[27845]: HFP HF features: "EC and/or NR function" "Call waiting and 3-way calling" "Voice recognition activation" "Remote volume control" 
bluetoothd[27845]: Received AT+CIND=?
bluetoothd[27845]: Received AT+CIND?
bluetoothd[27845]: Received AT+CMER=3, 0, 0, 1
bluetoothd[27845]: Event reporting (CMER): mode=3, ind=1
bluetoothd[27845]: HFP Service Level Connection established
bluetoothd[27845]: telephony-dummy: device 0x7fd934820eb0 connected
bluetoothd[27845]: State changed /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_CONNECT_IN_PROGRESS -> HEADSET_STATE_CONNECTED
bluetoothd[27845]: avdtp_ref(0x7fd93481e0f0): ref=2
bluetoothd[27845]: avdtp_ref(0x7fd93481e0f0): ref=3
bluetoothd[27845]: avdtp_unref(0x7fd93481e0f0): ref=2
bluetoothd[27845]: AVDTP: connected signaling channel to 00:1A:0E:9A:CC:30
bluetoothd[27845]: AVDTP imtu=672, omtu=895
bluetoothd[27845]: session_cb
bluetoothd[27845]: DISCOVER request succeeded
bluetoothd[27845]: seid 1 type 1 media 0 in use 0
bluetoothd[27845]: session_cb
bluetoothd[27845]: GET_CAPABILITIES request succeeded
bluetoothd[27845]: seid 1 type 1 media 0
bluetoothd[27845]: Discovery complete
bluetoothd[27845]: a2dp_config: selected SEP 0x7fd93481c140
bluetoothd[27845]: avdtp_ref(0x7fd93481e0f0): ref=3
bluetoothd[27845]: setup_ref(0x7fd9348221b0): ref=1
bluetoothd[27845]: avdtp_set_configuration(0x7fd93481e0f0): int_seid=1, acp_seid=1
bluetoothd[27845]: session_cb
bluetoothd[27845]: SET_CONFIGURATION request succeeded
bluetoothd[27845]: Source 0x7fd93481c140: Set_Configuration_Cfm
bluetoothd[27845]: stream state changed: IDLE -> CONFIGURED
bluetoothd[27845]: session_cb
bluetoothd[27845]: OPEN request succeeded
bluetoothd[27845]: AVCTP: connected to 00:1A:0E:9A:CC:30
bluetoothd[27845]: AVRCP: uinput initialized for 00:1A:0E:9A:CC:30
kernel: [772778.950377] input: 00:1A:0E:9A:CC:30 as /devices/virtual/input/input15
bluetoothd[27845]: AVDTP: connected transport channel to 00:1A:0E:9A:CC:30
bluetoothd[27845]: Source 0x7fd93481c140: Open_Cfm
bluetoothd[27845]: setup_ref(0x7fd9348221b0): ref=2
bluetoothd[27845]: Stream successfully created
bluetoothd[27845]: setup_unref(0x7fd9348221b0): ref=1
bluetoothd[27845]: setup_unref(0x7fd9348221b0): ref=0
bluetoothd[27845]: setup_free(0x7fd9348221b0)
bluetoothd[27845]: avdtp_unref(0x7fd93481e0f0): ref=2
bluetoothd[27845]: stream state changed: CONFIGURED -> OPEN
bluetoothd[27845]: Accepted new client connection on unix socket (fd=28)
bluetoothd[27845]: Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
bluetoothd[27845]: Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
bluetoothd[27845]: Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
bluetoothd[27845]: Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
bluetoothd[27845]: Audio API: BT_REQUEST <- BT_OPEN
bluetoothd[27845]: open sco - object=/org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30 source=ANY destination=ANY lock=readwrite
bluetoothd[27845]: Audio API: BT_RESPONSE -> BT_OPEN
bluetoothd[27845]: Audio API: BT_REQUEST <- BT_SET_CONFIGURATION
bluetoothd[27845]: Audio API: BT_RESPONSE -> BT_SET_CONFIGURATION
bluetoothd[27845]: Audio API: BT_REQUEST <- BT_START_STREAM
bluetoothd[27845]: State changed /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS

```

_Turning on Audacious_
*A few moments pass, and then playback begins on the regular speakers*

```
bluetoothd[27845]: HUP or ERR on socket
bluetoothd[27845]: Audio API: BT_RESPONSE -> BT_START_STREAM
bluetoothd[27845]: Audio API: BT_INDICATION -> BT_NEW_STREAM
bluetoothd[27845]: State changed /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_CONNECTED
bluetoothd[27845]: Unix client disconnected (fd=28)
bluetoothd[27845]: client_free(0x7fd9348221b0)
```

_Turning off the headset_

```
bluetoothd[27845]: session_cb
bluetoothd[27845]: Received CLOSE_CMD
bluetoothd[27845]: Source 0x7fd93481c140: Close_Ind
bluetoothd[27845]: stream state changed: OPEN -> CLOSING
bluetoothd[27845]: AVCTP session 0x7fd9348212a0 got disconnected
bluetoothd[27845]: ERR or HUP on RFCOMM socket
bluetoothd[27845]: telephony-dummy: device 0x7fd934820eb0 disconnected
bluetoothd[27845]: State changed /org/bluez/27844/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_CONNECTED -> HEADSET_STATE_DISCONNECTED
bluetoothd[27845]: Timed out waiting for peer to close the transport channel
bluetoothd[27845]: stream state changed: CLOSING -> IDLE
bluetoothd[27845]: avdtp_unref(0x7fd93481e0f0): ref=1
bluetoothd[27845]: session_cb
bluetoothd[27845]: Disconnected from 00:1A:0E:9A:CC:30
bluetoothd[27845]: avdtp_unref(0x7fd93481e0f0): ref=0
bluetoothd[27845]: avdtp_unref(0x7fd93481e0f0): freeing session and removing from list
```

---

### Post by markbuntu on 2010-01-06
You probably need the latest bluez to go with the latest pulse since they are sort of developing in tandem and work closely together.

---

### Post by walkeraj on 2010-01-06
Any suggestions? The ppa found at [https://launchpad.net/~bluetooth/+archive/ppa]("https://launchpad.net/~bluetooth/+archive/ppa") hasn't been updated in over a year and the index fails to download.

---

### Post by markbuntu on 2010-01-06
Try bluez.org

---

### Post by richwillal on 2010-01-09
I've had success getting the Motorola S9-HD headphones working with the OOTB pulse and bluez.  The only steps required were to pair the headphones, and power off the headphones, the power on the headphones.  (Connecting and disconnecting the headphones did not have the same effect.)  After the power up and automatic connect, I was able to open the Sound Preferences from the tray icon, select the hardware tab and select the A2DP profile for the headphones, then change to the Output tab and select the headphones for the output device.

While I haven't done any research, it appears that I'm getting the error below because the default profile for the headphones is HSP/HFP which isn't supported.

Output from syslog:
```
Jan  9 08:17:51 hdx bluetoothd[2640]: link_key_request (sba=00:21:86:88:DD:77, dba=00:0D:FD:30:D4:85)
Jan  9 08:17:55 hdx bluetoothd[2640]: Can't open input device: No such file or directory (2)
Jan  9 08:17:55 hdx bluetoothd[2640]: AVRCP: failed to init uinput for 00:0D:FD:30:D4:85
Jan  9 08:18:01 hdx bluetoothd[2640]: No matching connection found for handle 6
```

Output from `uname -a`
```
Linux hdx 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
```

---

### Post by walkeraj on 2010-01-18
Latest bluez (from source) and pulseaudio 0.9.21.  Still broken.  I'm at my wit's end here.

```

bluetoothd[11108]: adapter_get_device(00:1A:0E:9A:CC:30)
bluetoothd[11108]: link_key_request (sba=00:11:67:D7:F4:42, dba=00:1A:0E:9A:CC:30)
bluetoothd[11108]: kernel auth requirements = 0x00
bluetoothd[11108]: stored link key type = 0x00
bluetoothd[11108]: hcid_dbus_bonding_process_complete: status=00
bluetoothd[11108]: adapter_get_device(00:1A:0E:9A:CC:30)
bluetoothd[11108]: hcid_dbus_bonding_process_complete: no pending auth request
bluetoothd[11108]: State changed /org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_DISCONNECTED -> HEADSET_STATE_CONNECTING
bluetoothd[11108]: /org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30: Connected to 00:1A:0E:9A:CC:30
bluetoothd[11108]: Received AT+BRSF=27
bluetoothd[11108]: HFP HF features: "EC and/or NR function" "Call waiting and 3-way calling" "Voice recognition activation" "Remote volume control" 
bluetoothd[11108]: Received AT+CIND=?
bluetoothd[11108]: Received AT+CIND?
bluetoothd[11108]: Received AT+CMER=3, 0, 0, 1
bluetoothd[11108]: Event reporting (CMER): mode=3, ind=1
bluetoothd[11108]: HFP Service Level Connection established
bluetoothd[11108]: telephony-dummy: device 0x7fb84a233c00 connected
bluetoothd[11108]: State changed /org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_CONNECTING -> HEADSET_STATE_CONNECTED
bluetoothd[11108]: avdtp_ref(0x7fb84a232c00): ref=2
bluetoothd[11108]: avdtp_ref(0x7fb84a232c00): ref=3
bluetoothd[11108]: avdtp_unref(0x7fb84a232c00): ref=2
bluetoothd[11108]: AVDTP: connected signaling channel to 00:1A:0E:9A:CC:30
bluetoothd[11108]: AVDTP imtu=672, omtu=895
bluetoothd[11108]: AVCTP Connecting
bluetoothd[11108]: session_cb
bluetoothd[11108]: DISCOVER request succeeded
bluetoothd[11108]: seid 1 type 1 media 0 in use 0
bluetoothd[11108]: session_cb
bluetoothd[11108]: GET_CAPABILITIES request succeeded
bluetoothd[11108]: seid 1 type 1 media 0
bluetoothd[11108]: Discovery complete
bluetoothd[11108]: a2dp_config: selected SEP 0x7fb84a22f900
bluetoothd[11108]: avdtp_ref(0x7fb84a232c00): ref=3
bluetoothd[11108]: setup_ref(0x7fb84a2355d0): ref=1
bluetoothd[11108]: avdtp_set_configuration(0x7fb84a232c00): int_seid=1, acp_seid=1
bluetoothd[11108]: session_cb
bluetoothd[11108]: SET_CONFIGURATION request succeeded
bluetoothd[11108]: Source 0x7fb84a22f900: Set_Configuration_Cfm
bluetoothd[11108]: stream state changed: IDLE -> CONFIGURED
bluetoothd[11108]: AVCTP: connected to 00:1A:0E:9A:CC:30
bluetoothd[11108]: AVRCP: uinput initialized for 00:1A:0E:9A:CC:30
bluetoothd[11108]: AVCTP Connected
kernel: [1021623.816917] input: 00:1A:0E:9A:CC:30 as /devices/virtual/input/input10
bluetoothd[11108]: session_cb
bluetoothd[11108]: OPEN request succeeded
bluetoothd[11108]: AVDTP: connected transport channel to 00:1A:0E:9A:CC:30
bluetoothd[11108]: Source 0x7fb84a22f900: Open_Cfm
bluetoothd[11108]: setup_ref(0x7fb84a2355d0): ref=2
bluetoothd[11108]: Stream successfully created
bluetoothd[11108]: setup_unref(0x7fb84a2355d0): ref=1
bluetoothd[11108]: setup_unref(0x7fb84a2355d0): ref=0
bluetoothd[11108]: setup_free(0x7fb84a2355d0)
bluetoothd[11108]: avdtp_unref(0x7fb84a232c00): ref=2
bluetoothd[11108]: stream state changed: CONFIGURED -> OPEN
bluetoothd[11108]: Accepted new client connection on unix socket (fd=28)
bluetoothd[11108]: Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
bluetoothd[11108]: Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
bluetoothd[11108]: Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
bluetoothd[11108]: Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
bluetoothd[11108]: Audio API: BT_REQUEST <- BT_OPEN
bluetoothd[11108]: open sco - object=/org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30 source=ANY destination=ANY lock=readwrite
bluetoothd[11108]: Audio API: BT_RESPONSE -> BT_OPEN
bluetoothd[11108]: Audio API: BT_REQUEST <- BT_SET_CONFIGURATION
bluetoothd[11108]: Audio API: BT_RESPONSE -> BT_SET_CONFIGURATION
bluetoothd[11108]: Audio API: BT_REQUEST <- BT_START_STREAM
bluetoothd[11108]: State changed /org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS
bluetoothd[11108]: HUP or ERR on socket
bluetoothd[11108]: Audio API: BT_RESPONSE -> BT_START_STREAM
bluetoothd[11108]: Audio API: BT_INDICATION -> BT_NEW_STREAM
bluetoothd[11108]: State changed /org/bluez/11107/hci0/dev_00_1A_0E_9A_CC_30: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_CONNECTED
bluetoothd[11108]: Unix client disconnected (fd=28)
bluetoothd[11108]: client_free(0x7fb84a235b60)

```

These headphones have worked properly elsewhere (on my aspireOne, for instance).

---

### Post by vertago1 on 2010-02-22
It may be a stupid question but do you have the pulseaudio-module-bluetooth package installed?

I was able to get it my headset to work by the following:

First one of the times I put my headset in pair mode, kbluetooth popped up the pairing dialog for entering the 4 digit pin. After entering the pin it was able to connect.

To get pulseaudio to recognize it I had to:

> 
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover


I also installed pavucontrol for changing the headset between duplex and high-quality audio modes.

I tried to get the buttons to work by modprobing uinput but I haven't had any luck yet.

---

### Post by MystaMax on 2010-07-11
Hi,

Did you ever get this to work? I have the same bluetooth headphones, and they don't work. They're paired correctly, connect correctly, but do not show up under the hardware tab under sound preferences (I'm still running 9.10). 

I have the Sony DR-BT100X bluetooth headphones, and they work just fine. 

I have no idea where to begin when troubleshooting bluetooth issues such as this one. I really would like to get these working.

Any help is appreciated!

*** EDIT ***
I also tried this using a Ubuntu 10.04 LiveCD with the same results.

---

