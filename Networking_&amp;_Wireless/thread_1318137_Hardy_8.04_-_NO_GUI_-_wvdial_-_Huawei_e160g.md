---
title: "Hardy 8.04 - NO GUI - wvdial - Huawei e160g"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by superFerra on 2009-11-07
Hello,
I'm tring to setup an internet backup line over umts.
My machine is an Hardy 8.04 server without gui (and i'm not going to set an X server over there and i'm not going to upgrade to other server release)
My dongle is an Huawei E160G UMTS modem.
But wvdial isn't able to let it work.
After system boot if i plug the key:

lsusb
```

Bus 005 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

lsmod | grep usb

```

usbserial              48880  2 option,airprime
usb_storage            89792  1 
libusual               30688  1 usb_storage
scsi_mod              185784  9 usb_storage,sbp2,sg,sr_mod,sd_mod,mptspi,mptscsih,scsi_transport_spi,libata
usbcore               177200  8 option,airprime,usbserial,usb_storage,libusual,ehci_hcd,uhci_hcd

```

dmesg:
```

...
[  448.585035] usb 5-8: new high speed USB device using ehci_hcd and address 2
[  448.748277] usb 5-8: configuration #1 chosen from 1 choice
[  448.848077] usbcore: registered new interface driver libusual
[  448.870160] Initializing USB Mass Storage driver...
[  448.872398] usb 5-8: USB disconnect, address 2
[  448.872558] scsi6 : SCSI emulation for USB Mass Storage devices
[  448.872683] usb-storage: device found at 2
[  448.872692] usb-storage: waiting for device to settle before scanning
[  449.024670] usbcore: registered new interface driver usb-storage
[  449.024677] usbcore: registered new interface driver usbserial
[  449.024741] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  449.024779] usbcore: registered new interface driver usbserial_generic
[  449.024785] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  449.025676] USB Mass Storage support registered.
[  449.035223] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[  449.035267] usbcore: registered new interface driver airprime
[  454.349411] usb 5-8: new high speed USB device using ehci_hcd and address 3
[  454.510634] usb 5-8: configuration #1 chosen from 1 choice
[  454.512649] usb-storage: probe of 5-8:1.0 failed with error -5
[  454.512679] airprime 5-8:1.0: airprime converter detected
[  454.512878] usb 5-8: airprime converter now attached to ttyUSB0
[  454.512966] usb 5-8: airprime converter now attached to ttyUSB1
[  454.513038] usb 5-8: airprime converter now attached to ttyUSB2
[  454.513297] usb-storage: probe of 5-8:1.1 failed with error -5
[  454.513315] airprime 5-8:1.1: airprime converter detected
[  454.513404] usb 5-8: airprime converter now attached to ttyUSB3
[  454.513484] usb 5-8: airprime converter now attached to ttyUSB4
[  454.513555] usb 5-8: airprime converter now attached to ttyUSB5
[  454.592586] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[  464.499679] scsi9 : SCSI emulation for USB Mass Storage devices
[  464.501609] usb-storage: device found at 3
[  464.501617] usb-storage: waiting for device to settle before scanning
[  470.493813] usb-storage: device scan complete
[  470.495281] scsi 9:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  474.489980] scsi10 : SCSI emulation for USB Mass Storage devices
[  474.492014] usbcore: registered new interface driver option
[  474.492026] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[  474.493832] usb-storage: device found at 3
[  474.493840] usb-storage: waiting for device to settle before scanning
[  474.640900] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  475.059250] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  475.668641] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  476.268063] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  476.759340] sr1: scsi3-mmc drive: 0x/0x caddy
[  476.759448] sr 9:0:0:0: Attached scsi CD-ROM sr1
[  476.759526] sr 9:0:0:0: Attached scsi generic sg3 type 5
[  476.878717] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  477.476896] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  478.076310] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  478.679521] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  479.275129] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  479.765375] usb-storage: device scan complete
[  479.894526] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  480.386827] scsi 10:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  480.503955] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  481.093368] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  481.704027] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  482.312473] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  482.806225] sd 10:0:0:0: [sdc] 3862528 512-byte hardware sectors (1978 MB)
[  482.809220] sd 10:0:0:0: [sdc] Write Protect is off
[  482.809231] sd 10:0:0:0: [sdc] Mode Sense: 0f 0e 00 00
[  482.809238] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  482.818214] sd 10:0:0:0: [sdc] 3862528 512-byte hardware sectors (1978 MB)
[  482.821203] sd 10:0:0:0: [sdc] Write Protect is off
[  482.821210] sd 10:0:0:0: [sdc] Mode Sense: 0f 0e 00 00
[  482.821212] sd 10:0:0:0: [sdc] Assuming drive cache: write through
[  482.821218]  sdc: sdc1
[  482.827657] sd 10:0:0:0: [sdc] Attached SCSI removable disk
[  482.827754] sd 10:0:0:0: Attached scsi generic sg4 type 0
[  482.954048] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  483.523719] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  484.124164] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  484.729830] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  485.341734] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  485.948634] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  486.568027] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  487.161213] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  487.769365] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  488.380022] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  488.985695] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  489.607578] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  490.224470] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  490.807654] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  491.433298] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  492.023831] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  492.635892] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  493.251537] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  493.854683] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  494.452855] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  495.059770] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  495.671671] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  496.282349] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  496.889240] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  497.491141] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  498.096803] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  498.698725] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  499.305638] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  499.926281] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  500.514453] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  501.127600] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  501.723278] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  502.322697] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  502.942093] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  503.552745] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  504.150906] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  504.750326] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  505.349746] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  505.949167] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  506.558575] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  507.169229] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  507.767388] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  508.370555] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  508.966225] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  509.569394] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  510.167604] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  510.764479] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  511.366391] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  511.967057] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  512.566478] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  513.165887] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  513.774042] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  514.380957] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  514.984117] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  515.579786] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  516.189201] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  516.802337] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  517.398014] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  517.997433] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  518.610582] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  519.208743] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  519.809409] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  520.405101] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  521.004511] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  521.626469] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  522.223309] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  522.845208] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  523.443376] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  524.051538] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  524.660941] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  525.279142] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  525.872264] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  526.469175] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  527.069058] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  527.678004] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  528.288660] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  528.886855] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  529.499976] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  530.109377] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  530.715045] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  531.314472] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  531.923870] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  532.523280] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  533.145174] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  533.735849] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  534.345262] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  534.949533] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  535.542865] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  536.139759] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  536.739173] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  537.348596] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  537.950504] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  538.551188] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  539.156884] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  539.767476] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  540.366900] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  540.977551] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  541.584480] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  542.183877] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  542.803271] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  543.415190] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  544.002887] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  544.601531] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  545.200932] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  545.800349] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  546.399775] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  546.896512] Buffer I/O error on device sr1, logical block 0
[  546.896522] Buffer I/O error on device sr1, logical block 1
[  546.896525] Buffer I/O error on device sr1, logical block 2
[  546.896531] Buffer I/O error on device sr1, logical block 3
[  546.896534] Buffer I/O error on device sr1, logical block 4
[  546.896536] Buffer I/O error on device sr1, logical block 5
[  546.896539] Buffer I/O error on device sr1, logical block 6
[  546.896542] Buffer I/O error on device sr1, logical block 7
[  546.896545] Buffer I/O error on device sr1, logical block 8
[  546.896548] Buffer I/O error on device sr1, logical block 9
[  547.011671] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  547.618587] usb 5-8: reset high speed USB device using ehci_hcd and address 3
[  548.219255] usb 5-8: reset high speed USB device using ehci_hcd and address 3


```

Finally
sudo wvdialconf:
```

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyUSB0<Info>: Invalid argument
Modem Port Scan<*1>: USB0 
ttyUSB1<Info>: Exec format error
Modem Port Scan<*1>: USB1 
ttyUSB2<Info>: Exec format error
Modem Port Scan<*1>: USB2 
WvModem<*1>: Cannot get information for serial port.
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 9600 baud
ttyUSB3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyUSB4<Info>: Exec format error
Modem Port Scan<*1>: USB4 
ttyUSB5<Info>: Exec format error
Modem Port Scan<*1>: USB5 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://open.nit.ca/wiki/?WvDial

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

```

Any Idea?
Should I update anything?
Thanks in advance

---

