---
title: "Some bluetooth profiles not working"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by rickbeton on 2012-02-03
I have a new laptop (Novatech) running Ubuntu 11.10 and a new Plantronics BB903+ bluetooth headset.

* A2DP Works

When I connect the headset using the "audio service" (aka A2DP) it works fine. I can happily listen to Banshee on my headset. The headset works just as well when I connect A2DP to my HTC Desire instead of the laptop.

* HSP Doesn't Work

When I try to connect the headset using the "headset service" (aka HSP) it fails to connect. /var/log/syslog has the unhelpful "permission denied" message

```
Feb  3 23:03:35 krum bluetoothd[1236]: Disconnected from F0:65:DD:28:F4:1C, /org/bluez/1236/hci0/dev_F0_65_DD_28_F4_1C
Feb  3 23:03:50 krum bluetoothd[1236]: Permission denied (13)
Feb  3 23:04:05 krum kernel: [ 4238.270712] input: F0:65:DD:28:F4:1C as /devices/virtual/input/input21
Feb  3 23:04:05 krum pulseaudio[2024]: [pulseaudio] module-bluetooth-device.c: Default profile not connected, selecting off profile
Feb  3 23:04:34 krum bluetoothd[1236]: Operation not supported (95)
Feb  3 23:04:34 krum bluetoothd[1236]: headset_resume_complete: resume failed
Feb  3 23:04:34 krum pulseaudio[2024]: [bluetooth] module-bluetooth-device.c: Received error condition: Input/output error
Feb  3 23:05:02 krum kernel: [ 4295.333948] iwlagn 0000:03:00.0: receive reply tx with bt_kill
```

So I can't use Skype or similar apps with my headset.

However, the headset works just fine in HSP mode with my HTC Desire, allowing me to make hands-free voice calls.

So I'm wondering what's wrong with Ubuntu support for HSP and bluetooth headsets like the BB903+?

Rick

---

### Post by rickbeton on 2012-07-18
Is anyone able to answer this question?

---

