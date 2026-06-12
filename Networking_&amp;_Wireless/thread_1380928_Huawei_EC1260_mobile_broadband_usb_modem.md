---
title: "Huawei EC1260 mobile broadband usb modem"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by sgondhale on 2010-01-14
Hello,

I am using Huawei EC1260 mobile broadband usb modem to connect to internet from Ubuntu 9.10, i have configured it network connection section but I am getting following error when I am trying to connect 

Jan 14 18:01:07 ubuntu NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Tata Indicom (Photon+) connection 1'

Jan 14 18:01:07 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jan 14 18:01:07 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...

Jan 14 18:01:07 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...

Jan 14 18:01:07 ubuntu NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.

Jan 14 18:01:07 ubuntu modem-manager: (ttyUSB0) opening serial device...

Jan 14 18:01:07 ubuntu modem-manager: (ttyUSB2) opening serial device...

Jan 14 18:02:08 ubuntu NetworkManager: <WARN>  stage1_prepare_done(): CDMA modem connection failed: No service

Jan 14 18:02:08 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 0)

Jan 14 18:02:08 ubuntu NetworkManager: <info>  Marking connection 'Tata Indicom (Photon+) connection 1' invalid.

Jan 14 18:02:08 ubuntu NetworkManager: <info>  Activation (ttyUSB0) failed.

Jan 14 18:02:08 ubuntu NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)

Jan 14 18:02:08 ubuntu NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).

Jan 14 18:02:08 ubuntu NetworkManager: flush_routes: assertion `iface_idx >= 0' failed

Jan 14 18:02:08 ubuntu NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed

Jan 14 18:02:08 ubuntu modem-manager: (ttyUSB2) closing serial device...

Jan 14 18:02:08 ubuntu modem-manager: (ttyUSB0) closing serial device...

---

### Post by pdc on 2010-01-14
with your modem plugged in, can you tell us

> lsusb

and 

> uname -r

from a terminal; if you copy and paste the results back here

---

