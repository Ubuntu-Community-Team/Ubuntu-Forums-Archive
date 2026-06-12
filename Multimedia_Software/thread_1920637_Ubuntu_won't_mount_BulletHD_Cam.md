---
title: "Ubuntu won't mount BulletHD Cam"
date: 2012-02-05
forum: Multimedia Software
---

### Post by mguidoux on 2012-02-05
Hi there,

I'm using ubuntu 11.10 and recently got a BulletHD camera which isn't mounting when I plug it in the USB front or rear ports.

The camera turns on when I plug it in and it shows with the lsusb command:

> Protocol spec without prior Class and Subclass spec at line 4297
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 124a:4017 AirVast PC-Chips 802.11b Adapter
Bus 001 Device 004: ID 0546:3304 Polaroid Corp. a500 Digital Camera

Though Ubuntu doesn't mount and so I cannot download the files I've recorded. The device also doesn't show up on the media folder.

Any ideas?

About my computer:
Lançamento 11.10 (oneiric)
Kernel Linux 3.0.0-12-generic
GNOME 3.2.1

---

### Post by mguidoux on 2012-02-11
dmesg output:
> 
[  341.987146] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  341.987161] end_request: critical target error, dev sdb, sector 8192
[  341.993618] sd 8:0:0:0: [sdb] Unhandled sense code
[  341.993624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  341.993632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  341.993640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  341.993648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  341.993663] end_request: critical target error, dev sdb, sector 8192
[  342.000120] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.000126] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.000133] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.000141] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.000150] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.000165] end_request: critical target error, dev sdb, sector 8192
[  342.006617] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.006623] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.006630] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.006638] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.006647] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.006662] end_request: critical target error, dev sdb, sector 8192
[  342.013119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.013125] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.013132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.013140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.013149] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.013164] end_request: critical target error, dev sdb, sector 8192
[  342.019618] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.019624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.019631] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.019639] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.019648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 80 00 00 08 00
[  342.019663] end_request: critical target error, dev sdb, sector 8320
[  342.026118] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.026124] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.026131] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.026139] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.026148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 80 00 00 08 00
[  342.026163] end_request: critical target error, dev sdb, sector 8320
[  342.032619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.032624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.032632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.032640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.032648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 10 00 00 08 00
[  342.032663] end_request: critical target error, dev sdb, sector 8208
[  342.039117] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.039123] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.039130] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.039138] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.039146] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.039161] end_request: critical target error, dev sdb, sector 8192
[  342.045618] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.045623] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.045631] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.045639] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.045647] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.045662] end_request: critical target error, dev sdb, sector 8192
[  342.052120] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.052126] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.052134] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.052141] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.052150] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 08 00 00 08 00
[  342.052165] end_request: critical target error, dev sdb, sector 8200
[  342.058617] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.058623] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.058630] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.058638] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.058647] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 10 00 00 08 00
[  342.058661] end_request: critical target error, dev sdb, sector 8208
[  342.065119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.065124] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.065132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.065140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.065148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.065163] end_request: critical target error, dev sdb, sector 8192
[  342.071618] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.071624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.071631] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.071639] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.071648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.071662] end_request: critical target error, dev sdb, sector 8192
[  342.078117] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.078123] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.078131] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.078138] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.078147] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.078162] end_request: critical target error, dev sdb, sector 8192
[  342.084619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.084625] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.084632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.084640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.084649] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.084664] end_request: critical target error, dev sdb, sector 8192
[  342.091117] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.091123] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.091130] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.091138] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.091147] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.091162] end_request: critical target error, dev sdb, sector 8192
[  342.097619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.097625] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.097632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.097640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.097648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.097663] end_request: critical target error, dev sdb, sector 8192
[  342.104120] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.104125] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.104133] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.104141] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.104149] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 08 00 00 08 00
[  342.104164] end_request: critical target error, dev sdb, sector 8200
[  342.110617] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.110623] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.110630] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.110638] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.110647] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 80 00 00 08 00
[  342.110662] end_request: critical target error, dev sdb, sector 8320
[  342.117119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.117124] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.117132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.117140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.117148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.117163] end_request: critical target error, dev sdb, sector 8192
[  342.123619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.123624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.123632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.123640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.123648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.123663] end_request: critical target error, dev sdb, sector 8192
[  342.130119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.130125] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.130132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.130140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.130148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 30 00 00 00 08 00
[  342.130163] end_request: critical target error, dev sdb, sector 12288
[  342.136619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.136624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.136632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.136640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.136648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.136663] end_request: critical target error, dev sdb, sector 8192
[  342.143117] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.143123] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.143131] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.143140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.143148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.143163] end_request: critical target error, dev sdb, sector 8192
[  342.149619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.149625] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.149632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.149640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.149649] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.149664] end_request: critical target error, dev sdb, sector 8192
[  342.156135] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.156144] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.156153] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.156162] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.156171] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.156187] end_request: critical target error, dev sdb, sector 8192
[  342.162631] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.162640] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.162649] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.162658] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.162667] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.162684] end_request: critical target error, dev sdb, sector 8192
[  342.169119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.169125] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.169132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.169140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.169148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.169163] end_request: critical target error, dev sdb, sector 8192
[  342.175619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.175624] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.175631] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.175639] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.175647] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.175662] end_request: critical target error, dev sdb, sector 8192
[  342.182119] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.182125] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.182132] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.182140] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.182148] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.182163] end_request: critical target error, dev sdb, sector 8192
[  342.188619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.188625] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.188632] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.188639] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.188648] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.188662] end_request: critical target error, dev sdb, sector 8192
[  342.195117] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.195123] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.195130] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.195137] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.195145] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.195160] end_request: critical target error, dev sdb, sector 8192
[  342.201623] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.201631] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.201639] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.201647] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.201656] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.201673] end_request: critical target error, dev sdb, sector 8192
[  342.208127] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.208135] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.208143] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.208152] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.208161] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.208177] end_request: critical target error, dev sdb, sector 8192
[  342.214615] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.214621] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.214629] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.214637] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.214646] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 18 00 00 08 00
[  342.214662] end_request: critical target error, dev sdb, sector 8216
[  342.221105] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.221107] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.221109] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.221112] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.221114] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.221119] end_request: critical target error, dev sdb, sector 8192
[  342.227604] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.227606] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.227608] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.227610] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.227613] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.227617] end_request: critical target error, dev sdb, sector 8192
[  342.234110] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.234113] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.234117] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.234121] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.234125] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.234133] end_request: critical target error, dev sdb, sector 8192
[  342.240627] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.240634] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.240642] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.240650] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.240659] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 38 00 00 08 00
[  342.240675] end_request: critical target error, dev sdb, sector 8248
[  342.247123] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.247130] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.247138] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.247146] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.247155] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.247171] end_request: critical target error, dev sdb, sector 8192
[  342.253626] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.253633] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.253642] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.253650] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.253659] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 20 00 00 00 08 00
[  342.253676] end_request: critical target error, dev sdb, sector 8192
[  342.260257] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.260265] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.260274] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.260283] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.260292] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.260308] end_request: critical target error, dev sdb, sector 0
[  342.266625] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.266632] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.266641] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.266649] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.266658] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.266674] end_request: critical target error, dev sdb, sector 0
[  342.273135] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.273144] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.273153] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.273162] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.273171] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.273188] end_request: critical target error, dev sdb, sector 0
[  342.279620] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.279626] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.279633] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.279640] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.279649] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.279664] end_request: critical target error, dev sdb, sector 0
[  342.286128] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.286137] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.286145] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.286154] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.286163] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.286179] end_request: critical target error, dev sdb, sector 0
[  342.292627] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.292635] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.292644] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.292652] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.292662] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.292678] end_request: critical target error, dev sdb, sector 0
[  342.299118] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.299124] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.299131] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.299139] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.299147] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.299163] end_request: critical target error, dev sdb, sector 0
[  342.305625] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.305633] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.305641] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.305650] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.305660] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 18 00 00 08 00
[  342.305676] end_request: critical target error, dev sdb, sector 24
[  342.312129] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.312136] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.312145] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.312153] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.312163] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.312179] end_request: critical target error, dev sdb, sector 0
[  342.318619] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.318625] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.318633] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.318641] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.318649] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.318664] end_request: critical target error, dev sdb, sector 0
[  342.325127] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.325134] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.325142] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.325150] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.325159] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.325175] end_request: critical target error, dev sdb, sector 0
[  342.331625] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.331632] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.331639] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.331647] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.331656] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 38 00 00 08 00
[  342.331672] end_request: critical target error, dev sdb, sector 56
[  342.338125] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.338132] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.338140] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.338148] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.338157] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.338173] end_request: critical target error, dev sdb, sector 0
[  342.344628] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.344636] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.344645] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.344653] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.344662] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.344678] end_request: critical target error, dev sdb, sector 0
[  342.357879] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.357888] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.357898] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.357907] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.357917] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.357934] end_request: critical target error, dev sdb, sector 0
[  342.364378] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.364386] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.364395] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.364404] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.364413] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.364430] end_request: critical target error, dev sdb, sector 0
[  342.370870] sd 8:0:0:0: [sdb] Unhandled sense code
[  342.370876] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  342.370884] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  342.370892] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  342.370901] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  342.370916] end_request: critical target error, dev sdb, sector 0
[  418.720118] linkstatus=AP_OUTOFRANGE (unhandled)
[  419.724116] linkstatus=AP_INRANGE
[  433.085118] linkstatus=AP_OUTOFRANGE (unhandled)
[  461.927107] linkstatus=AP_INRANGE
[  511.612122] linkstatus=AP_OUTOFRANGE (unhandled)
[  512.566129] linkstatus=AP_INRANGE
[  518.473124] linkstatus=AP_OUTOFRANGE (unhandled)
[  519.522122] linkstatus=AP_INRANGE
[  543.244123] linkstatus=AP_OUTOFRANGE (unhandled)
[  545.702125] linkstatus=AP_INRANGE
[  548.891123] linkstatus=AP_OUTOFRANGE (unhandled)
[  549.892126] linkstatus=AP_INRANGE
[  575.007113] linkstatus=AP_OUTOFRANGE (unhandled)
[  575.962126] linkstatus=AP_INRANGE
[  583.612013] linkstatus=AP_OUTOFRANGE (unhandled)
[  584.611133] linkstatus=AP_INRANGE
[  596.822129] linkstatus=AP_OUTOFRANGE (unhandled)
[  597.825126] linkstatus=AP_INRANGE
[  743.388645] sdhci: Secure Digital Host Controller Interface driver
[  743.388649] sdhci: Copyright(c) Pierre Ossman
[  826.076790] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.076800] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.076810] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.076819] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.076829] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.076847] end_request: critical target error, dev sdb, sector 0
[  826.076856] quiet_error: 203 callbacks suppressed
[  826.076863] Buffer I/O error on device sdb, logical block 0
[  826.083140] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.083144] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.083147] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.083151] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.083154] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.083160] end_request: critical target error, dev sdb, sector 0
[  826.083165] Buffer I/O error on device sdb, logical block 0
[  826.089765] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.089769] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.089772] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.089775] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.089778] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[  826.089784] end_request: critical target error, dev sdb, sector 0
[  826.089787] Buffer I/O error on device sdb, logical block 0
[  826.089792] Buffer I/O error on device sdb, logical block 1
[  826.089794] Buffer I/O error on device sdb, logical block 2
[  826.089796] Buffer I/O error on device sdb, logical block 3
[  826.096254] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.096256] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.096258] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.096261] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.096263] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.096268] end_request: critical target error, dev sdb, sector 0
[  826.096270] Buffer I/O error on device sdb, logical block 0
[  826.102756] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.102758] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.102760] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.102763] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.102765] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 77 a7 f8 00 00 01 00
[  826.102770] end_request: critical target error, dev sdb, sector 7841784
[  826.102772] Buffer I/O error on device sdb, logical block 980223
[  826.109273] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.109279] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.109288] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.109296] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.109305] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 77 a7 f8 00 00 01 00
[  826.109321] end_request: critical target error, dev sdb, sector 7841784
[  826.109328] Buffer I/O error on device sdb, logical block 980223
[  826.115793] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.115800] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.115807] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.115815] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.115824] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 20 00
[  826.115839] end_request: critical target error, dev sdb, sector 0
[  826.115845] Buffer I/O error on device sdb, logical block 0
[  826.122269] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.122274] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.122282] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.122290] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.122299] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.122314] end_request: critical target error, dev sdb, sector 0
[  826.128768] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.128773] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.128781] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.128789] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.128798] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.128813] end_request: critical target error, dev sdb, sector 0
[  826.135266] sd 8:0:0:0: [sdb] Unhandled sense code
[  826.135272] sd 8:0:0:0: [sdb]  Result: hostbyte=invalid driverbyte=DRIVER_SENSE
[  826.135280] sd 8:0:0:0: [sdb]  Sense Key : Medium Error [current] 
[  826.135287] sd 8:0:0:0: [sdb]  Add. Sense: Unrecovered read error
[  826.135296] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  826.135311] end_request: critical target error, dev sdb, sector 0


---

### Post by mguidoux on 2012-02-11
I also found this similar bug reported on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913567](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/913567)

---

