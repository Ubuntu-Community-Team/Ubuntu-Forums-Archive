---
title: "mobile broadband connect-&gt;disconnect-&gt;connect-disconnect etc"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by jaykee on 2010-03-03
Hey everyone. Got some problems with my mobile broadband. The drivers are installed and the hardware(huawei E220) is recognized. The problem is that as soon as i connect then the connection is beeing disconnected, than back again and so on. Their isnt any pattern it follows so the hangups comes once in a while. 

Following is from the log:

Mar  3 22:44:47 js-laptop kernel: [  684.290447] usb 5-1: USB disconnect, address 5
Mar  3 22:44:47 js-laptop kernel: [  684.293083] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Mar  3 22:44:47 js-laptop kernel: [  684.293140] option 5-1:1.0: device disconnected
Mar  3 22:44:47 js-laptop kernel: [  684.293476] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Mar  3 22:44:47 js-laptop kernel: [  684.293524] option 5-1:1.1: device disconnected
Mar  3 22:45:11 js-laptop kernel: [  707.550106] usb 5-2: new full speed USB device using uhci_hcd and address 6
Mar  3 22:45:11 js-laptop kernel: [  707.712761] usb 5-2: configuration #1 chosen from 1 choice
Mar  3 22:45:11 js-laptop kernel: [  707.720321] option 5-2:1.0: GSM modem (1-port) converter detected
Mar  3 22:45:11 js-laptop kernel: [  707.720500] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
Mar  3 22:45:11 js-laptop kernel: [  707.723705] option 5-2:1.1: GSM modem (1-port) converter detected
Mar  3 22:45:11 js-laptop kernel: [  707.723816] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
Mar  3 22:45:11 js-laptop kernel: [  707.734620] scsi16 : SCSI emulation for USB Mass Storage devices
Mar  3 22:45:16 js-laptop kernel: [  712.735134] scsi 16:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Mar  3 22:45:16 js-laptop kernel: [  712.758176] sr1: scsi-1 drive
Mar  3 22:45:16 js-laptop kernel: [  712.758596] sr 16:0:0:0: Attached scsi generic sg2 type 5
Mar  3 22:45:27 js-laptop kernel: [  723.521564] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:27 js-laptop kernel: [  723.521572] sr: Add. Sense: No additional sense information
Mar  3 22:45:27 js-laptop kernel: [  723.893747] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:27 js-laptop kernel: [  723.893756] sr: Add. Sense: No additional sense information
Mar  3 22:45:27 js-laptop kernel: [  723.994821] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Mar  3 22:45:27 js-laptop kernel: [  723.994856] option 5-2:1.0: device disconnected
Mar  3 22:45:27 js-laptop kernel: [  723.994917] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Mar  3 22:45:27 js-laptop kernel: [  723.994935] option 5-2:1.1: device disconnected
Mar  3 22:45:27 js-laptop kernel: [  724.110307] usb 5-2: reset full speed USB device using uhci_hcd and address 6
Mar  3 22:45:27 js-laptop kernel: [  724.271152] option 5-2:1.1: GSM modem (1-port) converter detected
Mar  3 22:45:27 js-laptop kernel: [  724.271327] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB0
Mar  3 22:45:27 js-laptop kernel: [  724.275165] option 5-2:1.0: GSM modem (1-port) converter detected
Mar  3 22:45:27 js-laptop kernel: [  724.275342] usb 5-2: GSM modem (1-port) converter now attached to ttyUSB1
Mar  3 22:45:28 js-laptop kernel: [  724.330933] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:28 js-laptop kernel: [  724.330942] sr: Add. Sense: No additional sense information
Mar  3 22:45:28 js-laptop kernel: [  724.358999] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:28 js-laptop kernel: [  724.359008] sr: Add. Sense: No additional sense information
Mar  3 22:45:28 js-laptop kernel: [  724.386972] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:28 js-laptop kernel: [  724.386981] sr: Add. Sense: No additional sense information
Mar  3 22:45:28 js-laptop kernel: [  724.428960] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:28 js-laptop kernel: [  724.428969] sr: Add. Sense: No additional sense information
Mar  3 22:45:28 js-laptop kernel: [  724.518279] sr: Sense Key : Hardware Error [current] 
Mar  3 22:45:28 js-laptop kernel: [  724.518288] sr: Add. Sense: No additional sense information
Mar  3 22:45:58 js-laptop pppd[2491]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Mar  3 22:45:58 js-laptop pppd[2491]: pppd 2.4.5 started by root, uid 0
Mar  3 22:45:58 js-laptop pppd[2491]: Using interface ppp0
Mar  3 22:45:58 js-laptop pppd[2491]: Connect: ppp0 <--> /dev/ttyUSB1
Mar  3 22:45:58 js-laptop pppd[2491]: CHAP authentication succeeded
Mar  3 22:45:58 js-laptop pppd[2491]: CHAP authentication succeeded
Mar  3 22:46:05 js-laptop pppd[2491]: Could not determine remote IP address: defaulting to 10.64.64.64
Mar  3 22:46:05 js-laptop pppd[2491]: local  IP address 79.138.211.156
Mar  3 22:46:05 js-laptop pppd[2491]: remote IP address 10.64.64.64
Mar  3 22:46:05 js-laptop pppd[2491]: primary   DNS address 80.251.201.177
Mar  3 22:46:05 js-laptop pppd[2491]: secondary DNS address 80.251.201.178
Mar  3 22:49:19 js-laptop kernel: [  955.950360] usb 2-3: new high speed USB device using ehci_hcd and address 6
Mar  3 22:49:19 js-laptop kernel: [  956.149663] usb 2-3: configuration #3 chosen from 1 choice
Mar  3 22:49:19 js-laptop kernel: [  956.285817] cdc_acm 2-3:3.1: ttyACM0: USB ACM device
Mar  3 22:49:19 js-laptop kernel: [  956.288013] cdc_acm 2-3:3.3: ttyACM1: USB ACM device
Mar  3 22:49:19 js-laptop kernel: [  956.288725] usbcore: registered new interface driver cdc_acm
Mar  3 22:49:19 js-laptop kernel: [  956.288733] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Mar  3 22:49:19 js-laptop kernel: [  956.319790] usb0: register 'cdc_ether' at usb-0000:00:1d.7-3, CDC Ethernet Device, 02:80:37:0a:03:00
Mar  3 22:49:19 js-laptop kernel: [  956.319814] usbcore: registered new interface driver cdc_ether
Mar  3 22:49:19 js-laptop kernel: [  956.321602] cdc_wdm 2-3:3.7: cdc-wdm0: USB WDM device
Mar  3 22:49:19 js-laptop kernel: [  956.321616] usbcore: registered new interface driver cdc_wdm
Mar  3 22:49:35 js-laptop pppd[2613]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Mar  3 22:49:35 js-laptop pppd[2613]: pppd 2.4.5 started by root, uid 0
Mar  3 22:49:35 js-laptop pppd[2613]: Using interface ppp1
Mar  3 22:49:35 js-laptop pppd[2613]: Connect: ppp1 <--> /dev/ttyACM0
Mar  3 22:49:35 js-laptop pppd[2613]: CHAP authentication succeeded: Congratulations!
Mar  3 22:49:35 js-laptop pppd[2613]: CHAP authentication succeeded
Mar  3 22:49:37 js-laptop pppd[2613]: LCP terminated by peer
Mar  3 22:49:37 js-laptop pppd[2613]: Modem hangup
Mar  3 22:49:37 js-laptop pppd[2613]: Connection terminated.
Mar  3 22:49:38 js-laptop pppd[2613]: Exit.

---

