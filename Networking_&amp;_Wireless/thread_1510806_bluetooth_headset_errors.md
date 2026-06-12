---
title: "bluetooth headset errors"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by glenb77 on 2010-06-16
i installed a bluetooth headset (lg hbm-20) into lucid 64 bit; and it worked fine. after setting up in windows same headset; it will no longer work in linux; after removing and setting up several times, the applet shows it connected and paired, but it does not show up as a hardware device in the sound preferences; i get the following errors from the log:


g-laptop kernel: [ 3178.313068] btusb_isoc_complete: hci0 corrupted SCO packet
Jun 15 22:13:02 g-laptop kernel: [ 3178.313114] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop kernel: [ 3178.313139] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop kernel: [ 3178.313151] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop bluetoothd[6421]: Connection refused (111)
Jun 15 22:13:02 g-laptop bluetoothd[6421]: headset_resume_complete: resume failed
Jun 15 22:13:02 g-laptop pulseaudio[1349]: module-bluetooth-device.c: Received error condition: Input/output error
Jun 15 22:13:02 g-laptop kernel: [ 3178.323097] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop kernel: [ 3178.323121] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop kernel: [ 3178.323140] hci_scodata_packet: hci0 SCO packet for unknown connection handle 92
Jun 15 22:13:02 g-laptop bluetoothd[6421]: Badly formated or unrecognized command: AT+CSRSF=1,1,1,1,1,7

i would really like to use this in linux; any help on how to fix this would be appreciated; thank you.

---

