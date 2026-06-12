---
title: "Bluetooth HSP Not Working"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by pbrthemaster on 2010-10-30
I bought a DELL Bluetooth Headset and paired with my laptop running Ubuntu 10.10.

I can connect to Audio Sink service on my bluetooth headset and it works but I couldn't connect to Headset service on my bluetooth headset. Bluez daemon quits when I try to connect to Headset service.

The same bluetooth headset works fine with my XP. I can connect to Audio Sink and HSP service in my XP.

Any ideas how to solve this problem?

---

### Post by pbrthemaster on 2010-10-31
I tried using btsco but it gives the following error,

Error: control open (hw:1): No such file or directory
Error: Can't find device. Bail

I used strace btsco to find more details and got the following,

open("/dev/snd/controlC1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
open("/dev/aloadC1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)

The files /dev/snd/controlC1 and /dev/aloadC1 are not present. Any ideas how to get those files?

---

### Post by pbrthemaster on 2010-11-01
I re-installed the bluez package and I'm getting following in kern.log when I connect to Headset service,

Nov  1 14:12:12 pbr kernel: [19828.610304] btusb_isoc_complete: hci0 corrupted SCO packet
Nov  1 14:12:12 pbr kernel: [19828.610338] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Nov  1 14:12:12 pbr kernel: [19828.610342] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Nov  1 14:12:12 pbr kernel: [19828.610346] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Nov  1 14:12:12 pbr kernel: [19828.610350] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
Nov  1 14:12:12 pbr kernel: [19828.610354] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0

Can anyone plz tell how to fix this?

---

