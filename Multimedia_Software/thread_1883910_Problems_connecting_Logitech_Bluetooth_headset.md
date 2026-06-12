---
title: "Problems connecting Logitech Bluetooth headset"
date: 2011-11-20
forum: Multimedia Software
---

### Post by moreira on 2011-11-20
Hello everyone,

I hope someone can help me find out what could possibly be wrong with my system.

I am trying to get my new Logitech bluetooth headset to work [http://www.logitech.com/en-ch/tablet-accessories/for-ipad/devices/8452](http://www.logitech.com/en-ch/tablet-accessories/for-ipad/devices/8452)

I am facing several problems, to get it work.

Some info:
```

moreira@WS-LSO3:~$ uname -a
Linux WS-LSO3 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
moreira@WS-LSO3:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

```I have put the bluetoothd and the pulseaudio to verbose the output. This is what I am getting after pairing:
```

Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:server_cb() Accepted new client connection on unix socket (fd=30)
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_sendmsg() Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Audio API: BT_REQUEST <- BT_GET_CAPABILITIES
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_sendmsg() Audio API: BT_RESPONSE -> BT_GET_CAPABILITIES
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Audio API: BT_REQUEST <- BT_OPEN
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:handle_sco_open() open sco - object=/org/bluez/3606/hci0/dev_00_0D_44_A5_8C_E2 source=ANY destination=ANY lock=readwrite
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_sendmsg() Audio API: BT_RESPONSE -> BT_OPEN
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Audio API: BT_REQUEST <- BT_SET_CONFIGURATION
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_sendmsg() Audio API: BT_RESPONSE -> BT_SET_CONFIGURATION
Nov 20 11:58:40 WS-LSO3 rtkit-daemon[1296]: Successfully made thread 3628 of process 3301 (n/a) owned by '1000' RT at priority 5.
Nov 20 11:58:40 WS-LSO3 rtkit-daemon[1296]: Supervising 4 threads of 1 processes of 1 users.
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Audio API: BT_REQUEST <- BT_START_STREAM
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/headset.c:headset_set_state() State changed /org/bluez/3606/hci0/dev_00_0D_44_A5_8C_E2: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: Operation not supported (95)
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: headset_resume_complete: resume failed
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_error() sending error Input/output error(5)
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_sendmsg() Audio API: BT_ERROR -> BT_START_STREAM
Nov 20 12:58:40 WS-LSO3 pulseaudio[3301]: [bluetooth] module-bluetooth-device.c: Received error condition: Input/output error
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/headset.c:headset_set_state() State changed /org/bluez/3606/hci0/dev_00_0D_44_A5_8C_E2: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_CONNECTED
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_cb() Unix client disconnected (fd=30)
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:client_free() client_free(0x7f830f181120)

```Even though the headset is added to the list of paired items, it is not possible to use it right away. This is probably because of the error:
```

Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/headset.c:headset_set_state() State changed /org/bluez/3606/hci0/dev_00_0D_44_A5_8C_E2: HEADSET_STATE_CONNECTED -> HEADSET_STATE_PLAY_IN_PROGRESS
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: Operation not supported (95)
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: headset_resume_complete: resume failed
Nov 20 12:58:40 WS-LSO3 bluetoothd[3606]: audio/unix.c:unix_ipc_error() sending error Input/output error(5)

```At some point after turning on and off, the device and bluetooth, and maybe also restarting my pc, I was able to make my headset to appear in the list of audio devices as disabled. When I selected the A2DP profile I could get some sound. When I tried to select the telephony profile (HFP), nothing worked anymore.

Any help is very welcome!

---

### Post by moreira on 2011-11-21
Any ideas on this topic would be very much appreciated. If you need any additional log, I will be more than happy to send!

---

