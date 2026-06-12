---
title: "unable to connect to internet ..(.org.freedesktop  errors)"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by bhavit on 2012-09-08
hi guy ,
i am a beginner in ubuntu, unable to do anything without internet connection in my ubuntu desktop, every .deb file i download from internet has some dependency ..:mad::mad::mad::mad:

when tryin to  connect to internet from ubuntu networking penal, just after inserting my datacard.. i click enable mobile broadband...
i get following error in syslog
Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) starting connection 'Reliance connection 1'

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): device state change: disconnected -> prepare (reason 'none') [30 40 0]

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): device state change: prepare -> need-auth (reason 'none') [40 60 0]

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): device state change: need-auth -> prepare (reason 'none') [60 40 0]

Sep  8 21:23:33 bhavit-Vostro-1088 NetworkManager[836]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: <warn> CDMA connection failed: (32) No service

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): device state change: prepare -> failed (reason 'none') [40 120 0]

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: <warn> Activation (ttyUSB0) failed.

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): device state change: failed -> disconnected (reason 'none') [120 30 0]

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: <info> (ttyUSB0): deactivating device (reason 'none') [0]

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed

Sep  8 21:24:33 bhavit-Vostro-1088 NetworkManager[836]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed

also modem-manager has following error..
could not acquire the org.freedesktop.modemmanager
message:  connection is not allowed to own the service " org.freedesktop.modemmanager" due to security policies in config file

please tell how to connect to internet......now..

---

