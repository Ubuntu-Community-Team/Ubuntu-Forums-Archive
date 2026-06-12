---
title: "sansa c200 not reconized in ubuntu Harty"
date: 2008-05-18
forum: Multimedia Software
---

### Post by justin13 on 2008-05-18
Hey I just did a frimware update on my sansa c200 and now I cant get the damn thing to work it works with winblows fine but now it just keep swtiching between the write screen and the music screen it not even showing up on my lsusb and when I do a dmesg I nothing but failure I have know idea what I need to do things I have done is install pmount libmtc I have even check my fdisk and it is nowhere to be see I would like to use it. info is what I do to check to see if it is seen.

sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0869

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         182     1461883+  82  Linux swap / Solaris
/dev/sda2   *         183        1398     9767520   83  Linux
/dev/sda3            1399        8693    58597087+  83  Linux
/dev/sda4            8694       24792   129315217+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4d6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

dmesg

[99265.815532] usb-storage: device found at 93
[99265.815539] usb-storage: waiting for device to settle before scanning
[99266.612516] usb 5-5: USB disconnect, address 93
[99270.101030] usb 5-5: new high speed USB device using ehci_hcd and address 94
[99270.594652] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99270.594669] hub 5-0:1.0: hub_port_status failed (err = -32)
[99271.039184] usb 5-5: new high speed USB device using ehci_hcd and address 95
[99271.184478] usb 5-5: configuration #1 chosen from 1 choice
[99271.193727] scsi556 : SCSI emulation for USB Mass Storage devices
[99271.194202] usb-storage: device found at 95
[99271.194208] usb-storage: waiting for device to settle before scanning
[99271.994634] usb 5-5: USB disconnect, address 95
[99275.487492] usb 5-5: new high speed USB device using ehci_hcd and address 96
[99275.992025] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99275.992048] hub 5-0:1.0: hub_port_status failed (err = -32)
[99276.437643] usb 5-5: new high speed USB device using ehci_hcd and address 97
[99276.583533] usb 5-5: configuration #1 chosen from 1 choice
[99276.621320] scsi557 : SCSI emulation for USB Mass Storage devices
[99276.633303] usb-storage: device found at 97
[99276.633311] usb-storage: waiting for device to settle before scanning
[99277.378767] usb 5-5: USB disconnect, address 97
[99280.860108] usb 5-5: new high speed USB device using ehci_hcd and address 98
[99281.344523] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99281.344540] hub 5-0:1.0: hub_port_status failed (err = -32)
[99281.795186] usb 5-5: new high speed USB device using ehci_hcd and address 99
[99281.940690] usb 5-5: configuration #1 chosen from 1 choice
[99281.952337] scsi558 : SCSI emulation for USB Mass Storage devices
[99281.953092] usb-storage: device found at 99
[99281.953099] usb-storage: waiting for device to settle before scanning
[99282.752894] usb 5-5: USB disconnect, address 99
[99286.234498] usb 5-5: new high speed USB device using ehci_hcd and address 100
[99286.719090] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99286.719107] hub 5-0:1.0: hub_port_status failed (err = -32)
[99287.168684] usb 5-5: new high speed USB device using ehci_hcd and address 101
[99287.313848] usb 5-5: configuration #1 chosen from 1 choice
[99287.325346] scsi559 : SCSI emulation for USB Mass Storage devices
[99287.325798] usb-storage: device found at 101
[99287.325804] usb-storage: waiting for device to settle before scanning
[99288.126013] usb 5-5: USB disconnect, address 101
[99291.607391] usb 5-5: new high speed USB device using ehci_hcd and address 102
[99292.112628] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99292.112652] hub 5-0:1.0: hub_port_status failed (err = -32)
[99292.561143] usb 5-5: new high speed USB device using ehci_hcd and address 103
[99292.706920] usb 5-5: configuration #1 chosen from 1 choice
[99292.716468] scsi560 : SCSI emulation for USB Mass Storage devices
[99292.716952] usb-storage: device found at 103
[99292.716958] usb-storage: waiting for device to settle before scanning
[99293.511086] usb 5-5: USB disconnect, address 103
[99297.000501] usb 5-5: new high speed USB device using ehci_hcd and address 104
[99297.498076] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99297.498099] hub 5-0:1.0: hub_port_status failed (err = -32)
[99297.943640] usb 5-5: new high speed USB device using ehci_hcd and address 105
[99298.001056] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99298.001072] hub 5-0:1.0: hub_port_status failed (err = -32)
[99301.503658] usb 5-5: new high speed USB device using ehci_hcd and address 106
[99301.980202] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99301.980216] hub 5-0:1.0: hub_port_status failed (err = -32)
[99302.429973] usb 5-5: new high speed USB device using ehci_hcd and address 107
[99305.891095] usb 5-5: new high speed USB device using ehci_hcd and address 108
[99306.376592] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99306.376602] hub 5-0:1.0: hub_port_status failed (err = -32)
[99306.826272] usb 5-5: new high speed USB device using ehci_hcd and address 109
[99306.883603] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99306.883614] hub 5-0:1.0: hub_port_status failed (err = -32)
[99310.275522] usb 5-5: new high speed USB device using ehci_hcd and address 110
[99310.768049] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99310.768063] hub 5-0:1.0: hub_port_status failed (err = -32)
[99311.216681] usb 5-5: new high speed USB device using ehci_hcd and address 111
[99311.363058] usb 5-5: configuration #1 chosen from 1 choice
[99311.379178] scsi561 : SCSI emulation for USB Mass Storage devices
[99311.382514] usb-storage: device found at 111
[99311.382522] usb-storage: waiting for device to settle before scanning
[99312.167258] usb 5-5: USB disconnect, address 111
[99315.660011] usb 5-5: new high speed USB device using ehci_hcd and address 112
[99316.153590] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99316.153608] hub 5-0:1.0: hub_port_status failed (err = -32)
[99316.603167] usb 5-5: new high speed USB device using ehci_hcd and address 113
[99316.747185] usb 5-5: configuration #1 chosen from 1 choice
[99316.754492] scsi562 : SCSI emulation for USB Mass Storage devices
[99316.754861] usb-storage: device found at 113
[99316.754867] usb-storage: waiting for device to settle before scanning
[99317.560366] usb 5-5: USB disconnect, address 113
[99321.058455] usb 5-5: new high speed USB device using ehci_hcd and address 114
[99321.554036] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99321.554071] hub 5-0:1.0: hub_port_status failed (err = -32)
[99322.011621] usb 5-5: new high speed USB device using ehci_hcd and address 115
[99322.157242] usb 5-5: configuration #1 chosen from 1 choice
[99322.167594] scsi563 : SCSI emulation for USB Mass Storage devices
[99322.168043] usb-storage: device found at 115
[99322.168048] usb-storage: waiting for device to settle before scanning
[99322.949453] usb 5-5: USB disconnect, address 115
[99326.431234] usb 5-5: new high speed USB device using ehci_hcd and address 116
[99326.931552] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99326.931587] hub 5-0:1.0: hub_port_status failed (err = -32)
[99327.382095] usb 5-5: new high speed USB device using ehci_hcd and address 117
[99327.526361] usb 5-5: configuration #1 chosen from 1 choice
[99327.556757] scsi564 : SCSI emulation for USB Mass Storage devices
[99327.558480] usb-storage: device found at 117
[99327.558488] usb-storage: waiting for device to settle before scanning
[99328.323567] usb 5-5: USB disconnect, address 117
[99331.806037] usb 5-5: new high speed USB device using ehci_hcd and address 118
[99332.312913] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99332.313036] hub 5-0:1.0: hub_port_status failed (err = -32)
[99332.759598] usb 5-5: new high speed USB device using ehci_hcd and address 119
[99332.908489] usb 5-5: configuration #1 chosen from 1 choice
[99332.913477] scsi565 : SCSI emulation for USB Mass Storage devices
[99332.913925] usb-storage: device found at 119
[99332.913932] usb-storage: waiting for device to settle before scanning
[99333.698706] usb 5-5: USB disconnect, address 119
[99337.182941] usb 5-5: new high speed USB device using ehci_hcd and address 120
[99337.806219] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99337.806245] hub 5-0:1.0: hub_port_status failed (err = -32)
[99338.252856] usb 5-5: new high speed USB device using ehci_hcd and address 121
[99338.398510] usb 5-5: configuration #1 chosen from 1 choice
[99338.408474] scsi566 : SCSI emulation for USB Mass Storage devices
[99338.409279] usb-storage: device found at 121
[99338.409285] usb-storage: waiting for device to settle before scanning
[99339.081845] usb 5-5: USB disconnect, address 121
[99342.571493] usb 5-5: new high speed USB device using ehci_hcd and address 122
[99343.049456] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99343.049467] hub 5-0:1.0: hub_port_status failed (err = -32)
[99343.498599] usb 5-5: new high speed USB device using ehci_hcd and address 123
[99343.643752] usb 5-5: configuration #1 chosen from 1 choice
[99343.657122] scsi567 : SCSI emulation for USB Mass Storage devices
[99343.657679] usb-storage: device found at 123
[99343.657686] usb-storage: waiting for device to settle before scanning
[99344.463919] usb 5-5: USB disconnect, address 123
[99347.956896] usb 5-5: new high speed USB device using ehci_hcd and address 124
[99348.451371] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99348.451922] hub 5-0:1.0: hub_port_status failed (err = -32)
[99348.899053] usb 5-5: new high speed USB device using ehci_hcd and address 125
[99349.044865] usb 5-5: configuration #1 chosen from 1 choice
[99349.055914] scsi568 : SCSI emulation for USB Mass Storage devices
[99349.056049] usb-storage: device found at 125
[99349.056053] usb-storage: waiting for device to settle before scanning
[99349.858030] usb 5-5: USB disconnect, address 125
[99353.351359] usb 5-5: new high speed USB device using ehci_hcd and address 126
[99353.846894] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99353.846924] hub 5-0:1.0: hub_port_status failed (err = -32)
[99354.296573] usb 5-5: new high speed USB device using ehci_hcd and address 127
[99354.443963] usb 5-5: configuration #1 chosen from 1 choice
[99354.456839] scsi569 : SCSI emulation for USB Mass Storage devices
[99354.457417] usb-storage: device found at 127
[99354.457425] usb-storage: waiting for device to settle before scanning
[99355.243154] usb 5-5: USB disconnect, address 127
[99358.744818] usb 5-5: new high speed USB device using ehci_hcd and address 2
[99359.242484] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99359.242495] hub 5-0:1.0: hub_port_status failed (err = -32)
[99359.690961] usb 5-5: new high speed USB device using ehci_hcd and address 3
[99359.837068] usb 5-5: configuration #1 chosen from 1 choice
[99359.845993] scsi570 : SCSI emulation for USB Mass Storage devices
[99359.846825] usb-storage: device found at 3
[99359.846832] usb-storage: waiting for device to settle before scanning
[99360.635292] usb 5-5: USB disconnect, address 3
[99364.130315] usb 5-5: new high speed USB device using ehci_hcd and address 4
[99364.618051] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99364.618089] hub 5-0:1.0: hub_port_status failed (err = -32)
[99365.068445] usb 5-5: new high speed USB device using ehci_hcd and address 5
[99365.211215] usb 5-5: configuration #1 chosen from 1 choice
[99365.216154] scsi571 : SCSI emulation for USB Mass Storage devices
[99365.216620] usb-storage: device found at 5
[99365.216627] usb-storage: waiting for device to settle before scanning
[99366.029324] usb 5-5: USB disconnect, address 5
[99369.526744] usb 5-5: new high speed USB device using ehci_hcd and address 6
[99370.016277] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99370.016288] hub 5-0:1.0: hub_port_status failed (err = -32)
[99370.466055] usb 5-5: new high speed USB device using ehci_hcd and address 7
[99370.611222] usb 5-5: configuration #1 chosen from 1 choice
[99370.623804] scsi572 : SCSI emulation for USB Mass Storage devices
[99370.624221] usb-storage: device found at 7
[99370.624228] usb-storage: waiting for device to settle before scanning
[99371.427409] usb 5-5: USB disconnect, address 7
[99374.921220] usb 5-5: new high speed USB device using ehci_hcd and address 8
[99375.418040] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99375.418059] hub 5-0:1.0: hub_port_status failed (err = -32)
[99379.299636] usb 5-5: new high speed USB device using ehci_hcd and address 10
[99379.919910] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99379.919933] hub 5-0:1.0: hub_port_status failed (err = -32)
[99380.370683] usb 5-5: new high speed USB device using ehci_hcd and address 11
[99380.515625] usb 5-5: configuration #1 chosen from 1 choice
[99380.527799] scsi573 : SCSI emulation for USB Mass Storage devices
[99380.529106] usb-storage: device found at 11
[99380.529114] usb-storage: waiting for device to settle before scanning
[99381.188025] usb 5-5: USB disconnect, address 11
[99384.670144] usb 5-5: new high speed USB device using ehci_hcd and address 12
[99385.173660] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99385.173678] hub 5-0:1.0: hub_port_status failed (err = -32)
[99385.620313] usb 5-5: new high speed USB device using ehci_hcd and address 13
[99385.765905] usb 5-5: configuration #1 chosen from 1 choice
[99385.776708] scsi574 : SCSI emulation for USB Mass Storage devices
[99385.777191] usb-storage: device found at 13
[99385.777197] usb-storage: waiting for device to settle before scanning
[99386.562056] usb 5-5: USB disconnect, address 13
[99390.046656] usb 5-5: new high speed USB device using ehci_hcd and address 14
[99390.543227] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99390.543264] hub 5-0:1.0: hub_port_status failed (err = -32)
[99390.992994] usb 5-5: new high speed USB device using ehci_hcd and address 15
[99391.137043] usb 5-5: configuration #1 chosen from 1 choice
[99391.150850] scsi575 : SCSI emulation for USB Mass Storage devices
[99391.151589] usb-storage: device found at 15
[99391.151596] usb-storage: waiting for device to settle before scanning
[99391.937388] usb 5-5: USB disconnect, address 15
[99395.433913] usb 5-5: new high speed USB device using ehci_hcd and address 16
[99395.929385] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99395.929423] hub 5-0:1.0: hub_port_status failed (err = -32)
[99396.378291] usb 5-5: new high speed USB device using ehci_hcd and address 17
[99396.524132] usb 5-5: configuration #1 chosen from 1 choice
[99396.535990] scsi576 : SCSI emulation for USB Mass Storage devices
[99396.537098] usb-storage: device found at 17
[99396.537105] usb-storage: waiting for device to settle before scanning
[99397.325308] usb 5-5: USB disconnect, address 17
[99400.825580] usb 5-5: new high speed USB device using ehci_hcd and address 18
[99401.314173] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99401.314190] hub 5-0:1.0: hub_port_status failed (err = -32)
[99401.763766] usb 5-5: new high speed USB device using ehci_hcd and address 19
[99401.908209] usb 5-5: configuration #1 chosen from 1 choice
[99401.913205] scsi577 : SCSI emulation for USB Mass Storage devices
[99401.913697] usb-storage: device found at 19
[99401.913703] usb-storage: waiting for device to settle before scanning
[99402.725396] usb 5-5: USB disconnect, address 19
[99406.228042] usb 5-5: new high speed USB device using ehci_hcd and address 20
[99406.719584] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99406.719600] hub 5-0:1.0: hub_port_status failed (err = -32)
[99407.169227] usb 5-5: new high speed USB device using ehci_hcd and address 21
[99407.315312] usb 5-5: configuration #1 chosen from 1 choice
[99407.331014] scsi578 : SCSI emulation for USB Mass Storage devices
[99407.345906] usb-storage: device found at 21
[99407.345914] usb-storage: waiting for device to settle before scanning
[99408.119486] usb 5-5: USB disconnect, address 21
[99411.612516] usb 5-5: new high speed USB device using ehci_hcd and address 22
[99412.110120] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99412.110140] hub 5-0:1.0: hub_port_status failed (err = -32)
[99412.555668] usb 5-5: new high speed USB device using ehci_hcd and address 23
[99412.701411] usb 5-5: configuration #1 chosen from 1 choice
[99412.711409] scsi579 : SCSI emulation for USB Mass Storage devices
[99412.711910] usb-storage: device found at 23
[99412.711919] usb-storage: waiting for device to settle before scanning
[99413.503603] usb 5-5: USB disconnect, address 23
[99416.993983] usb 5-5: new high speed USB device using ehci_hcd and address 24
[99417.491054] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99417.491079] hub 5-0:1.0: hub_port_status failed (err = -32)
[99417.940142] usb 5-5: new high speed USB device using ehci_hcd and address 25
[99418.084536] usb 5-5: configuration #1 chosen from 1 choice
[99418.101402] scsi580 : SCSI emulation for USB Mass Storage devices
[99418.103676] usb-storage: device found at 25
[99418.103683] usb-storage: waiting for device to settle before scanning
[99418.896696] usb 5-5: USB disconnect, address 25
[99422.387451] usb 5-5: new high speed USB device using ehci_hcd and address 26
[99423.007707] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99423.007719] hub 5-0:1.0: hub_port_status failed (err = -32)
[99423.461349] usb 5-5: new high speed USB device using ehci_hcd and address 27
[99423.607463] usb 5-5: configuration #1 chosen from 1 choice
[99423.615927] scsi581 : SCSI emulation for USB Mass Storage devices
[99423.616047] usb-storage: device found at 27
[99423.616051] usb-storage: waiting for device to settle before scanning
[99424.279808] usb 5-5: USB disconnect, address 27
[99427.765940] usb 5-5: new high speed USB device using ehci_hcd and address 28
[99428.261447] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99428.261465] hub 5-0:1.0: hub_port_status failed (err = -32)
[99428.712270] usb 5-5: new high speed USB device using ehci_hcd and address 29
[99428.856659] usb 5-5: configuration #1 chosen from 1 choice
[99428.870858] scsi582 : SCSI emulation for USB Mass Storage devices
[99428.875394] usb-storage: device found at 29
[99428.875401] usb-storage: waiting for device to settle before scanning
[99429.664855] usb 5-5: USB disconnect, address 29
[99433.151431] usb 5-5: new high speed USB device using ehci_hcd and address 30
[99433.652711] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99433.652836] hub 5-0:1.0: hub_port_status failed (err = -32)
[99434.101555] usb 5-5: new high speed USB device using ehci_hcd and address 31
[99434.248848] usb 5-5: configuration #1 chosen from 1 choice
[99434.262439] scsi583 : SCSI emulation for USB Mass Storage devices
[99434.262987] usb-storage: device found at 31
[99434.262996] usb-storage: waiting for device to settle before scanning
[99435.044059] usb 5-5: USB disconnect, address 31
[99438.532899] usb 5-5: new high speed USB device using ehci_hcd and address 32
[99439.030703] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99439.030722] hub 5-0:1.0: hub_port_status failed (err = -32)
[99439.481553] usb 5-5: new high speed USB device using ehci_hcd and address 33
[99439.622941] usb 5-5: configuration #1 chosen from 1 choice
[99439.638522] scsi584 : SCSI emulation for USB Mass Storage devices
[99439.639000] usb-storage: device found at 33
[99439.639007] usb-storage: waiting for device to settle before scanning
[99440.435160] usb 5-5: USB disconnect, address 33
[99443.929408] usb 5-5: new high speed USB device using ehci_hcd and address 34
[99444.417945] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99444.417964] hub 5-0:1.0: hub_port_status failed (err = -32)
[99444.867875] usb 5-5: new high speed USB device using ehci_hcd and address 35
[99445.016261] usb 5-5: configuration #1 chosen from 1 choice
[99445.030348] scsi585 : SCSI emulation for USB Mass Storage devices
[99445.032286] usb-storage: device found at 35
[99445.032293] usb-storage: waiting for device to settle before scanning
[99445.821261] usb 5-5: USB disconnect, address 35
[99449.314856] usb 5-5: new high speed USB device using ehci_hcd and address 36
[99449.808407] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99449.808423] hub 5-0:1.0: hub_port_status failed (err = -32)
[99450.254006] usb 5-5: new high speed USB device using ehci_hcd and address 37
[99455.385795] usb 5-5: configuration #1 chosen from 1 choice
[99455.402551] scsi586 : SCSI emulation for USB Mass Storage devices
[99455.402982] usb-storage: device found at 37
[99455.402989] usb-storage: waiting for device to settle before scanning
[99456.201937] usb 5-5: USB disconnect, address 37
[99459.699566] usb 5-5: new high speed USB device using ehci_hcd and address 38
[99460.192976] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99460.193011] hub 5-0:1.0: hub_port_status failed (err = -32)
[99460.645686] usb 5-5: new high speed USB device using ehci_hcd and address 39
[99460.790038] usb 5-5: configuration #1 chosen from 1 choice
[99460.801880] scsi587 : SCSI emulation for USB Mass Storage devices
[99460.802395] usb-storage: device found at 39
[99460.802401] usb-storage: waiting for device to settle before scanning
[99461.599060] usb 5-5: USB disconnect, address 39
[99465.094603] usb 5-5: new high speed USB device using ehci_hcd and address 40
[99465.585485] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99465.585516] hub 5-0:1.0: hub_port_status failed (err = -32)
[99466.031169] usb 5-5: new high speed USB device using ehci_hcd and address 41
[99466.177022] usb 5-5: configuration #1 chosen from 1 choice
[99466.181997] scsi588 : SCSI emulation for USB Mass Storage devices
[99466.182089] usb-storage: device found at 41
[99466.182092] usb-storage: waiting for device to settle before scanning
[99466.995172] usb 5-5: USB disconnect, address 41
[99470.491585] usb 5-5: new high speed USB device using ehci_hcd and address 42
[99470.983405] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99470.983420] hub 5-0:1.0: hub_port_status failed (err = -32)
[99471.427630] usb 5-5: new high speed USB device using ehci_hcd and address 43
[99471.572117] usb 5-5: configuration #1 chosen from 1 choice
[99471.584850] scsi589 : SCSI emulation for USB Mass Storage devices
[99471.585731] usb-storage: device found at 43
[99471.585739] usb-storage: waiting for device to settle before scanning
[99472.390270] usb 5-5: USB disconnect, address 43
[99476.006681] usb 5-5: new high speed USB device using ehci_hcd and address 44
[99476.495197] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99476.495208] hub 5-0:1.0: hub_port_status failed (err = -32)
[99476.945977] usb 5-5: new high speed USB device using ehci_hcd and address 45
[99477.089066] usb 5-5: configuration #1 chosen from 1 choice
[99477.100568] scsi590 : SCSI emulation for USB Mass Storage devices
[99477.100989] usb-storage: device found at 45
[99477.100996] usb-storage: waiting for device to settle before scanning
[99477.898232] usb 5-5: USB disconnect, address 45
[99481.389148] usb 5-5: new high speed USB device using ehci_hcd and address 46
[99481.896655] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99481.896721] hub 5-0:1.0: hub_port_status failed (err = -32)
[99482.346314] usb 5-5: new high speed USB device using ehci_hcd and address 47
[99482.493107] usb 5-5: configuration #1 chosen from 1 choice
[99482.498106] scsi591 : SCSI emulation for USB Mass Storage devices
[99482.498203] usb-storage: device found at 47
[99482.498206] usb-storage: waiting for device to settle before scanning
[99483.282341] usb 5-5: USB disconnect, address 47
[99486.766664] usb 5-5: new high speed USB device using ehci_hcd and address 48
[99487.270377] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99487.270413] hub 5-0:1.0: hub_port_status failed (err = -32)
[99487.720800] usb 5-5: new high speed USB device using ehci_hcd and address 49
[99487.868367] usb 5-5: configuration #1 chosen from 1 choice
[99487.907422] scsi592 : SCSI emulation for USB Mass Storage devices
[99487.907850] usb-storage: device found at 49
[99487.907860] usb-storage: waiting for device to settle before scanning
[99488.658484] usb 5-5: USB disconnect, address 49
[99492.144137] usb 5-5: new high speed USB device using ehci_hcd and address 50
[99492.623745] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99492.623764] hub 5-0:1.0: hub_port_status failed (err = -32)
[99493.078319] usb 5-5: new high speed USB device using ehci_hcd and address 51
[99493.222412] usb 5-5: configuration #1 chosen from 1 choice
[99493.233756] scsi593 : SCSI emulation for USB Mass Storage devices
[99493.234283] usb-storage: device found at 51
[99493.234289] usb-storage: waiting for device to settle before scanning
[99494.033589] usb 5-5: USB disconnect, address 51
[99497.512912] usb 5-5: new high speed USB device using ehci_hcd and address 52
[99498.013194] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99498.013213] hub 5-0:1.0: hub_port_status failed (err = -32)
[99498.463792] usb 5-5: new high speed USB device using ehci_hcd and address 53
[99498.607551] usb 5-5: configuration #1 chosen from 1 choice
[99498.623023] scsi594 : SCSI emulation for USB Mass Storage devices
[99498.625220] usb-storage: device found at 53
[99498.625227] usb-storage: waiting for device to settle before scanning
[99499.405717] usb 5-5: USB disconnect, address 53
[99502.898122] usb 5-5: new high speed USB device using ehci_hcd and address 54
[99503.391025] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99503.391058] hub 5-0:1.0: hub_port_status failed (err = -32)
[99503.844288] usb 5-5: new high speed USB device using ehci_hcd and address 55
[99503.987670] usb 5-5: configuration #1 chosen from 1 choice
[99503.999467] scsi595 : SCSI emulation for USB Mass Storage devices
[99503.999872] usb-storage: device found at 55
[99503.999877] usb-storage: waiting for device to settle before scanning
[99504.788852] usb 5-5: USB disconnect, address 55
[99508.284610] usb 5-5: new high speed USB device using ehci_hcd and address 56
[99508.777095] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99508.777106] hub 5-0:1.0: hub_port_status failed (err = -32)
[99509.229780] usb 5-5: new high speed USB device using ehci_hcd and address 57
[99509.376744] usb 5-5: configuration #1 chosen from 1 choice
[99509.386873] scsi596 : SCSI emulation for USB Mass Storage devices
[99509.387283] usb-storage: device found at 57
[99509.387288] usb-storage: waiting for device to settle before scanning
[99510.176959] usb 5-5: USB disconnect, address 57
[99513.801077] usb 5-5: new high speed USB device using ehci_hcd and address 58
[99514.294354] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99514.294367] hub 5-0:1.0: hub_port_status failed (err = -32)
[99514.742995] usb 5-5: new high speed USB device using ehci_hcd and address 59
[99514.889698] usb 5-5: configuration #1 chosen from 1 choice
[99514.902108] scsi597 : SCSI emulation for USB Mass Storage devices
[99514.902559] usb-storage: device found at 59
[99514.902565] usb-storage: waiting for device to settle before scanning
[99515.692904] usb 5-5: USB disconnect, address 59
[99519.187307] usb 5-5: new high speed USB device using ehci_hcd and address 60
[99519.683193] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99519.683208] hub 5-0:1.0: hub_port_status failed (err = -32)
[99520.132745] usb 5-5: new high speed USB device using ehci_hcd and address 61
[99520.278870] usb 5-5: configuration #1 chosen from 1 choice
[99520.288720] scsi598 : SCSI emulation for USB Mass Storage devices
[99520.289550] usb-storage: device found at 61
[99520.289557] usb-storage: waiting for device to settle before scanning
[99521.086978] usb 5-5: USB disconnect, address 61
[99524.575914] usb 5-5: new high speed USB device using ehci_hcd and address 62
[99525.069124] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99525.069144] hub 5-0:1.0: hub_port_status failed (err = -32)
[99525.517970] usb 5-5: new high speed USB device using ehci_hcd and address 63
[99525.575403] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99525.575483] hub 5-0:1.0: hub_port_status failed (err = -32)
[99528.961548] usb 5-5: new high speed USB device using ehci_hcd and address 64
[99529.455718] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99529.455743] hub 5-0:1.0: hub_port_status failed (err = -32)
[99529.913347] usb 5-5: new high speed USB device using ehci_hcd and address 65
[99530.059278] usb 5-5: configuration #1 chosen from 1 choice
[99530.064250] scsi599 : SCSI emulation for USB Mass Storage devices
[99530.064686] usb-storage: device found at 65
[99530.064691] usb-storage: waiting for device to settle before scanning
[99530.850485] usb 5-5: USB disconnect, address 65
[99534.332710] usb 5-5: new high speed USB device using ehci_hcd and address 66
[99534.821276] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99534.821346] hub 5-0:1.0: hub_port_status failed (err = -32)
[99535.267848] usb 5-5: new high speed USB device using ehci_hcd and address 67
[99535.411397] usb 5-5: configuration #1 chosen from 1 choice
[99535.422411] scsi600 : SCSI emulation for USB Mass Storage devices
[99535.422955] usb-storage: device found at 67
[99535.422964] usb-storage: waiting for device to settle before scanning
[99536.224637] usb 5-5: USB disconnect, address 67
[99539.706215] usb 5-5: new high speed USB device using ehci_hcd and address 68
[99540.214692] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99540.215215] hub 5-0:1.0: hub_port_status failed (err = -32)
[99540.656353] usb 5-5: new high speed USB device using ehci_hcd and address 69
[99540.802534] usb 5-5: configuration #1 chosen from 1 choice
[99540.812563] scsi601 : SCSI emulation for USB Mass Storage devices
[99540.812986] usb-storage: device found at 69
[99540.812990] usb-storage: waiting for device to settle before scanning
[99541.597732] usb 5-5: USB disconnect, address 69
[99545.084707] usb 5-5: new high speed USB device using ehci_hcd and address 70
[99545.585246] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99545.585264] hub 5-0:1.0: hub_port_status failed (err = -32)
[99546.031473] usb 5-5: new high speed USB device using ehci_hcd and address 71
[99546.176624] usb 5-5: configuration #1 chosen from 1 choice
[99546.186625] scsi602 : SCSI emulation for USB Mass Storage devices
[99546.187383] usb-storage: device found at 71
[99546.187389] usb-storage: waiting for device to settle before scanning
[99546.983836] usb 5-5: USB disconnect, address 71
[99550.481166] usb 5-5: new high speed USB device using ehci_hcd and address 72
[99550.969727] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99550.969801] hub 5-0:1.0: hub_port_status failed (err = -32)
[99551.415350] usb 5-5: new high speed USB device using ehci_hcd and address 73
[99551.559833] usb 5-5: configuration #1 chosen from 1 choice
[99551.573772] scsi603 : SCSI emulation for USB Mass Storage devices
[99551.574195] usb-storage: device found at 73
[99551.574201] usb-storage: waiting for device to settle before scanning
[99552.381944] usb 5-5: USB disconnect, address 73
[99556.006470] usb 5-5: new high speed USB device using ehci_hcd and address 74
[99556.499908] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99556.499920] hub 5-0:1.0: hub_port_status failed (err = -32)
[99556.949516] usb 5-5: new high speed USB device using ehci_hcd and address 75
[99557.093731] usb 5-5: configuration #1 chosen from 1 choice
[99557.106566] scsi604 : SCSI emulation for USB Mass Storage devices
[99557.107049] usb-storage: device found at 75
[99557.107057] usb-storage: waiting for device to settle before scanning
[99557.898892] usb 5-5: USB disconnect, address 75
[99561.392831] usb 5-5: new high speed USB device using ehci_hcd and address 76
[99561.881333] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99561.881344] hub 5-0:1.0: hub_port_status failed (err = -32)
[99562.330007] usb 5-5: new high speed USB device using ehci_hcd and address 77
[99562.476835] usb 5-5: configuration #1 chosen from 1 choice
[99562.495287] scsi605 : SCSI emulation for USB Mass Storage devices
[99562.496044] usb-storage: device found at 77
[99562.496050] usb-storage: waiting for device to settle before scanning
[99563.284992] usb 5-5: USB disconnect, address 77
[99566.771565] usb 5-5: new high speed USB device using ehci_hcd and address 78
[99567.249904] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99567.249945] hub 5-0:1.0: hub_port_status failed (err = -32)
[99567.700511] usb 5-5: new high speed USB device using ehci_hcd and address 79
[99567.846047] usb 5-5: configuration #1 chosen from 1 choice
[99567.850926] scsi606 : SCSI emulation for USB Mass Storage devices
[99567.851370] usb-storage: device found at 79
[99567.851375] usb-storage: waiting for device to settle before scanning
[99568.662114] usb 5-5: USB disconnect, address 79
[99572.155798] usb 5-5: new high speed USB device using ehci_hcd and address 80
[99572.644349] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99572.644364] hub 5-0:1.0: hub_port_status failed (err = -32)
[99573.093967] usb 5-5: new high speed USB device using ehci_hcd and address 81
[99573.240089] usb 5-5: configuration #1 chosen from 1 choice
[99573.245095] scsi607 : SCSI emulation for USB Mass Storage devices
[99573.245578] usb-storage: device found at 81
[99573.245584] usb-storage: waiting for device to settle before scanning
[99574.056221] usb 5-5: USB disconnect, address 81
[99577.552273] usb 5-5: new high speed USB device using ehci_hcd and address 82
[99578.040361] ehci_hcd 0000:00:1d.7: port 5 reset error -110
[99578.040421] hub 5-0:1.0: hub_port_status failed (err = -32)
masterloki@masterloki-desktop:~$ 

 dmesg | grep usb

[99067.964221] usb 5-5: new high speed USB device using ehci_hcd and address 29
[99071.413279] usb 5-5: new high speed USB device using ehci_hcd and address 30
[99072.352430] usb 5-5: new high speed USB device using ehci_hcd and address 31
[99072.500681] usb 5-5: configuration #1 chosen from 1 choice
[99072.512174] usb-storage: device found at 31
[99072.512179] usb-storage: waiting for device to settle before scanning
[99073.314819] usb 5-5: USB disconnect, address 31
[99076.819715] usb 5-5: new high speed USB device using ehci_hcd and address 32
[99077.760867] usb 5-5: new high speed USB device using ehci_hcd and address 33
[99077.905755] usb 5-5: configuration #1 chosen from 1 choice
[99077.916247] usb-storage: device found at 33
[99077.916250] usb-storage: waiting for device to settle before scanning
[99078.718962] usb 5-5: USB disconnect, address 33
[99082.212171] usb 5-5: new high speed USB device using ehci_hcd and address 34
[99083.150399] usb 5-5: new high speed USB device using ehci_hcd and address 35
[99086.591926] usb 5-5: new high speed USB device using ehci_hcd and address 36
[99087.533840] usb 5-5: new high speed USB device using ehci_hcd and address 37
[99090.980046] usb 5-5: new high speed USB device using ehci_hcd and address 38
[99091.921202] usb 5-5: new high speed USB device using ehci_hcd and address 39
[99092.067671] usb 5-5: configuration #1 chosen from 1 choice
[99092.079731] usb-storage: device found at 39
[99092.079738] usb-storage: waiting for device to settle before scanning
[99092.874795] usb 5-5: USB disconnect, address 39
[99096.357522] usb 5-5: new high speed USB device using ehci_hcd and address 40
[99097.306760] usb 5-5: new high speed USB device using ehci_hcd and address 41
[99097.453706] usb 5-5: configuration #1 chosen from 1 choice
[99097.465156] usb-storage: device found at 41
[99097.465161] usb-storage: waiting for device to settle before scanning
[99098.249936] usb 5-5: USB disconnect, address 41
[99101.735036] usb 5-5: new high speed USB device using ehci_hcd and address 42
[99102.806235] usb 5-5: new high speed USB device using ehci_hcd and address 43
[99102.950676] usb 5-5: configuration #1 chosen from 1 choice
[99102.964671] usb-storage: device found at 43
[99102.964678] usb-storage: waiting for device to settle before scanning
[99103.627033] usb 5-5: USB disconnect, address 43
[99107.112527] usb 5-5: new high speed USB device using ehci_hcd and address 44
[99108.061671] usb 5-5: new high speed USB device using ehci_hcd and address 45
[99111.502939] usb 5-5: new high speed USB device using ehci_hcd and address 46
[99112.446094] usb 5-5: new high speed USB device using ehci_hcd and address 47
[99112.594339] usb 5-5: configuration #1 chosen from 1 choice
[99112.607015] usb-storage: device found at 47
[99112.607022] usb-storage: waiting for device to settle before scanning
[99113.395521] usb 5-5: USB disconnect, address 47
[99116.888399] usb 5-5: new high speed USB device using ehci_hcd and address 48
[99117.826754] usb 5-5: new high speed USB device using ehci_hcd and address 49
[99117.973476] usb 5-5: configuration #1 chosen from 1 choice
[99117.987258] usb-storage: device found at 49
[99117.987266] usb-storage: waiting for device to settle before scanning
[99118.777650] usb 5-5: USB disconnect, address 49
[99122.272136] usb 5-5: new high speed USB device using ehci_hcd and address 50
[99123.213046] usb 5-5: new high speed USB device using ehci_hcd and address 51
[99123.358601] usb 5-5: configuration #1 chosen from 1 choice
[99123.369209] usb-storage: device found at 51
[99123.369213] usb-storage: waiting for device to settle before scanning
[99124.163763] usb 5-5: USB disconnect, address 51
[99127.660541] usb 5-5: new high speed USB device using ehci_hcd and address 52
[99128.598530] usb 5-5: new high speed USB device using ehci_hcd and address 53
[99128.741703] usb 5-5: configuration #1 chosen from 1 choice
[99128.754554] usb-storage: device found at 53
[99128.754562] usb-storage: waiting for device to settle before scanning
[99129.560850] usb 5-5: USB disconnect, address 53
[99133.060818] usb 5-5: new high speed USB device using ehci_hcd and address 54
[99133.999991] usb 5-5: new high speed USB device using ehci_hcd and address 55
[99134.145821] usb 5-5: configuration #1 chosen from 1 choice
[99134.157664] usb-storage: device found at 55
[99134.157672] usb-storage: waiting for device to settle before scanning
[99134.956904] usb 5-5: USB disconnect, address 55
[99138.451267] usb 5-5: new high speed USB device using ehci_hcd and address 56
[99139.393434] usb 5-5: new high speed USB device using ehci_hcd and address 57
[99139.537860] usb 5-5: configuration #1 chosen from 1 choice
[99139.553004] usb-storage: device found at 57
[99139.553011] usb-storage: waiting for device to settle before scanning
[99140.342081] usb 5-5: USB disconnect, address 57
[99143.963516] usb 5-5: new high speed USB device using ehci_hcd and address 58
[99144.917638] usb 5-5: new high speed USB device using ehci_hcd and address 59
[99145.064722] usb 5-5: configuration #1 chosen from 1 choice
[99145.077638] usb-storage: device found at 59
[99145.077647] usb-storage: waiting for device to settle before scanning
[99145.863944] usb 5-5: USB disconnect, address 59
[99149.346016] usb 5-5: new high speed USB device using ehci_hcd and address 60
[99150.300196] usb 5-5: new high speed USB device using ehci_hcd and address 61
[99150.443908] usb 5-5: configuration #1 chosen from 1 choice
[99150.455251] usb-storage: device found at 61
[99150.455258] usb-storage: waiting for device to settle before scanning
[99151.246223] usb 5-5: USB disconnect, address 61
[99154.731472] usb 5-5: new high speed USB device using ehci_hcd and address 62
[99155.677625] usb 5-5: new high speed USB device using ehci_hcd and address 63
[99155.823055] usb 5-5: configuration #1 chosen from 1 choice
[99155.833721] usb-storage: device found at 63
[99155.833728] usb-storage: waiting for device to settle before scanning
[99156.630232] usb 5-5: USB disconnect, address 63
[99160.115948] usb 5-5: new high speed USB device using ehci_hcd and address 64
[99161.046128] usb 5-5: new high speed USB device using ehci_hcd and address 65
[99164.503375] usb 5-5: new high speed USB device using ehci_hcd and address 66
[99165.449531] usb 5-5: new high speed USB device using ehci_hcd and address 67
[99165.595639] usb 5-5: configuration #1 chosen from 1 choice
[99165.600948] usb-storage: device found at 67
[99165.600954] usb-storage: waiting for device to settle before scanning
[99166.389785] usb 5-5: USB disconnect, address 67
[99169.880898] usb 5-5: new high speed USB device using ehci_hcd and address 68
[99170.823125] usb 5-5: new high speed USB device using ehci_hcd and address 69
[99200.905500] usb 5-5: configuration #1 chosen from 1 choice
[99201.737929] usb-storage: device found at 69
[99201.737935] usb-storage: waiting for device to settle before scanning
[99201.739056] usb 5-5: USB disconnect, address 69
[99205.243404] usb 5-5: new high speed USB device using ehci_hcd and address 70
[99206.178128] usb 5-5: new high speed USB device using ehci_hcd and address 71
[99206.322454] usb 5-5: configuration #1 chosen from 1 choice
[99206.335529] usb-storage: device found at 71
[99206.335535] usb-storage: waiting for device to settle before scanning
[99207.131617] usb 5-5: USB disconnect, address 71
[99210.621252] usb 5-5: new high speed USB device using ehci_hcd and address 72
[99211.563417] usb 5-5: new high speed USB device using ehci_hcd and address 73
[99211.712667] usb 5-5: configuration #1 chosen from 1 choice
[99211.725762] usb-storage: device found at 73
[99211.725771] usb-storage: waiting for device to settle before scanning
[99212.513735] usb 5-5: USB disconnect, address 73
[99216.134485] usb 5-5: new high speed USB device using ehci_hcd and address 74
[99217.072653] usb 5-5: new high speed USB device using ehci_hcd and address 75
[99217.216511] usb 5-5: configuration #1 chosen from 1 choice
[99217.227795] usb-storage: device found at 75
[99217.227803] usb-storage: waiting for device to settle before scanning
[99218.022683] usb 5-5: USB disconnect, address 75
[99221.515968] usb 5-5: new high speed USB device using ehci_hcd and address 76
[99222.462113] usb 5-5: new high speed USB device using ehci_hcd and address 77
[99222.608636] usb 5-5: configuration #1 chosen from 1 choice
[99222.620343] usb-storage: device found at 77
[99222.620352] usb-storage: waiting for device to settle before scanning
[99223.416851] usb 5-5: USB disconnect, address 77
[99226.901486] usb 5-5: new high speed USB device using ehci_hcd and address 78
[99227.847601] usb 5-5: new high speed USB device using ehci_hcd and address 79
[99227.993670] usb 5-5: configuration #1 chosen from 1 choice
[99228.005827] usb-storage: device found at 79
[99228.005833] usb-storage: waiting for device to settle before scanning
[99228.793908] usb 5-5: USB disconnect, address 79
[99232.274944] usb 5-5: new high speed USB device using ehci_hcd and address 80
[99233.233068] usb 5-5: new high speed USB device using ehci_hcd and address 81
[99233.378857] usb 5-5: configuration #1 chosen from 1 choice
[99233.384239] usb-storage: device found at 81
[99233.384247] usb-storage: waiting for device to settle before scanning
[99234.169029] usb 5-5: USB disconnect, address 81
[99237.657235] usb 5-5: new high speed USB device using ehci_hcd and address 82
[99238.606581] usb 5-5: new high speed USB device using ehci_hcd and address 83
[99238.754939] usb 5-5: configuration #1 chosen from 1 choice
[99238.760249] usb-storage: device found at 83
[99238.760253] usb-storage: waiting for device to settle before scanning
[99239.555109] usb 5-5: USB disconnect, address 83
[99243.045929] usb 5-5: new high speed USB device using ehci_hcd and address 84
[99243.992630] usb 5-5: new high speed USB device using ehci_hcd and address 85
[99244.140062] usb 5-5: configuration #1 chosen from 1 choice
[99244.154914] usb-storage: device found at 85
[99244.154923] usb-storage: waiting for device to settle before scanning
[99244.938253] usb 5-5: USB disconnect, address 85
[99248.431392] usb 5-5: new high speed USB device using ehci_hcd and address 86
[99249.374523] usb 5-5: new high speed USB device using ehci_hcd and address 87
[99249.520195] usb 5-5: configuration #1 chosen from 1 choice
[99249.536312] usb-storage: device found at 87
[99249.536319] usb-storage: waiting for device to settle before scanning
[99250.323365] usb 5-5: USB disconnect, address 87
[99253.813855] usb 5-5: new high speed USB device using ehci_hcd and address 88
[99254.756001] usb 5-5: new high speed USB device using ehci_hcd and address 89
[99254.901305] usb 5-5: configuration #1 chosen from 1 choice
[99254.906907] usb-storage: device found at 89
[99254.906912] usb-storage: waiting for device to settle before scanning
[99255.706484] usb 5-5: USB disconnect, address 89
[99259.330069] usb 5-5: new high speed USB device using ehci_hcd and address 90
[99260.264252] usb 5-5: new high speed USB device using ehci_hcd and address 91
[99260.411266] usb 5-5: configuration #1 chosen from 1 choice
[99260.453089] usb-storage: device found at 91
[99260.453098] usb-storage: waiting for device to settle before scanning
[99261.220423] usb 5-5: USB disconnect, address 91
[99264.712577] usb 5-5: new high speed USB device using ehci_hcd and address 92
[99265.650732] usb 5-5: new high speed USB device using ehci_hcd and address 93
[99265.796319] usb 5-5: configuration #1 chosen from 1 choice
[99265.815532] usb-storage: device found at 93
[99265.815539] usb-storage: waiting for device to settle before scanning
[99266.612516] usb 5-5: USB disconnect, address 93
[99270.101030] usb 5-5: new high speed USB device using ehci_hcd and address 94
[99271.039184] usb 5-5: new high speed USB device using ehci_hcd and address 95
[99271.184478] usb 5-5: configuration #1 chosen from 1 choice
[99271.194202] usb-storage: device found at 95
[99271.194208] usb-storage: waiting for device to settle before scanning
[99271.994634] usb 5-5: USB disconnect, address 95
[99275.487492] usb 5-5: new high speed USB device using ehci_hcd and address 96
[99276.437643] usb 5-5: new high speed USB device using ehci_hcd and address 97
[99276.583533] usb 5-5: configuration #1 chosen from 1 choice
[99276.633303] usb-storage: device found at 97
[99276.633311] usb-storage: waiting for device to settle before scanning
[99277.378767] usb 5-5: USB disconnect, address 97
[99280.860108] usb 5-5: new high speed USB device using ehci_hcd and address 98
[99281.795186] usb 5-5: new high speed USB device using ehci_hcd and address 99
[99281.940690] usb 5-5: configuration #1 chosen from 1 choice
[99281.953092] usb-storage: device found at 99
[99281.953099] usb-storage: waiting for device to settle before scanning
[99282.752894] usb 5-5: USB disconnect, address 99
[99286.234498] usb 5-5: new high speed USB device using ehci_hcd and address 100
[99287.168684] usb 5-5: new high speed USB device using ehci_hcd and address 101
[99287.313848] usb 5-5: configuration #1 chosen from 1 choice
[99287.325798] usb-storage: device found at 101
[99287.325804] usb-storage: waiting for device to settle before scanning
[99288.126013] usb 5-5: USB disconnect, address 101
[99291.607391] usb 5-5: new high speed USB device using ehci_hcd and address 102
[99292.561143] usb 5-5: new high speed USB device using ehci_hcd and address 103
[99292.706920] usb 5-5: configuration #1 chosen from 1 choice
[99292.716952] usb-storage: device found at 103
[99292.716958] usb-storage: waiting for device to settle before scanning
[99293.511086] usb 5-5: USB disconnect, address 103
[99297.000501] usb 5-5: new high speed USB device using ehci_hcd and address 104
[99297.943640] usb 5-5: new high speed USB device using ehci_hcd and address 105
[99301.503658] usb 5-5: new high speed USB device using ehci_hcd and address 106
[99302.429973] usb 5-5: new high speed USB device using ehci_hcd and address 107
[99305.891095] usb 5-5: new high speed USB device using ehci_hcd and address 108
[99306.826272] usb 5-5: new high speed USB device using ehci_hcd and address 109
[99310.275522] usb 5-5: new high speed USB device using ehci_hcd and address 110
[99311.216681] usb 5-5: new high speed USB device using ehci_hcd and address 111
[99311.363058] usb 5-5: configuration #1 chosen from 1 choice
[99311.382514] usb-storage: device found at 111
[99311.382522] usb-storage: waiting for device to settle before scanning
[99312.167258] usb 5-5: USB disconnect, address 111
[99315.660011] usb 5-5: new high speed USB device using ehci_hcd and address 112
[99316.603167] usb 5-5: new high speed USB device using ehci_hcd and address 113
[99316.747185] usb 5-5: configuration #1 chosen from 1 choice
[99316.754861] usb-storage: device found at 113
[99316.754867] usb-storage: waiting for device to settle before scanning
[99317.560366] usb 5-5: USB disconnect, address 113
[99321.058455] usb 5-5: new high speed USB device using ehci_hcd and address 114
[99322.011621] usb 5-5: new high speed USB device using ehci_hcd and address 115
[99322.157242] usb 5-5: configuration #1 chosen from 1 choice
[99322.168043] usb-storage: device found at 115
[99322.168048] usb-storage: waiting for device to settle before scanning
[99322.949453] usb 5-5: USB disconnect, address 115
[99326.431234] usb 5-5: new high speed USB device using ehci_hcd and address 116
[99327.382095] usb 5-5: new high speed USB device using ehci_hcd and address 117
[99327.526361] usb 5-5: configuration #1 chosen from 1 choice
[99327.558480] usb-storage: device found at 117
[99327.558488] usb-storage: waiting for device to settle before scanning
[99328.323567] usb 5-5: USB disconnect, address 117
[99331.806037] usb 5-5: new high speed USB device using ehci_hcd and address 118
[99332.759598] usb 5-5: new high speed USB device using ehci_hcd and address 119
[99332.908489] usb 5-5: configuration #1 chosen from 1 choice
[99332.913925] usb-storage: device found at 119
[99332.913932] usb-storage: waiting for device to settle before scanning
[99333.698706] usb 5-5: USB disconnect, address 119
[99337.182941] usb 5-5: new high speed USB device using ehci_hcd and address 120
[99338.252856] usb 5-5: new high speed USB device using ehci_hcd and address 121
[99338.398510] usb 5-5: configuration #1 chosen from 1 choice
[99338.409279] usb-storage: device found at 121
[99338.409285] usb-storage: waiting for device to settle before scanning
[99339.081845] usb 5-5: USB disconnect, address 121
[99342.571493] usb 5-5: new high speed USB device using ehci_hcd and address 122
[99343.498599] usb 5-5: new high speed USB device using ehci_hcd and address 123
[99343.643752] usb 5-5: configuration #1 chosen from 1 choice
[99343.657679] usb-storage: device found at 123
[99343.657686] usb-storage: waiting for device to settle before scanning
[99344.463919] usb 5-5: USB disconnect, address 123
[99347.956896] usb 5-5: new high speed USB device using ehci_hcd and address 124
[99348.899053] usb 5-5: new high speed USB device using ehci_hcd and address 125
[99349.044865] usb 5-5: configuration #1 chosen from 1 choice
[99349.056049] usb-storage: device found at 125
[99349.056053] usb-storage: waiting for device to settle before scanning
[99349.858030] usb 5-5: USB disconnect, address 125
[99353.351359] usb 5-5: new high speed USB device using ehci_hcd and address 126
[99354.296573] usb 5-5: new high speed USB device using ehci_hcd and address 127
[99354.443963] usb 5-5: configuration #1 chosen from 1 choice
[99354.457417] usb-storage: device found at 127
[99354.457425] usb-storage: waiting for device to settle before scanning
[99355.243154] usb 5-5: USB disconnect, address 127
[99358.744818] usb 5-5: new high speed USB device using ehci_hcd and address 2
[99359.690961] usb 5-5: new high speed USB device using ehci_hcd and address 3
[99359.837068] usb 5-5: configuration #1 chosen from 1 choice
[99359.846825] usb-storage: device found at 3
[99359.846832] usb-storage: waiting for device to settle before scanning
[99360.635292] usb 5-5: USB disconnect, address 3
[99364.130315] usb 5-5: new high speed USB device using ehci_hcd and address 4
[99365.068445] usb 5-5: new high speed USB device using ehci_hcd and address 5
[99365.211215] usb 5-5: configuration #1 chosen from 1 choice
[99365.216620] usb-storage: device found at 5
[99365.216627] usb-storage: waiting for device to settle before scanning
[99366.029324] usb 5-5: USB disconnect, address 5
[99369.526744] usb 5-5: new high speed USB device using ehci_hcd and address 6
[99370.466055] usb 5-5: new high speed USB device using ehci_hcd and address 7
[99370.611222] usb 5-5: configuration #1 chosen from 1 choice
[99370.624221] usb-storage: device found at 7
[99370.624228] usb-storage: waiting for device to settle before scanning
[99371.427409] usb 5-5: USB disconnect, address 7
[99374.921220] usb 5-5: new high speed USB device using ehci_hcd and address 8
[99379.299636] usb 5-5: new high speed USB device using ehci_hcd and address 10
[99380.370683] usb 5-5: new high speed USB device using ehci_hcd and address 11
[99380.515625] usb 5-5: configuration #1 chosen from 1 choice
[99380.529106] usb-storage: device found at 11
[99380.529114] usb-storage: waiting for device to settle before scanning
[99381.188025] usb 5-5: USB disconnect, address 11
[99384.670144] usb 5-5: new high speed USB device using ehci_hcd and address 12
[99385.620313] usb 5-5: new high speed USB device using ehci_hcd and address 13
[99385.765905] usb 5-5: configuration #1 chosen from 1 choice
[99385.777191] usb-storage: device found at 13
[99385.777197] usb-storage: waiting for device to settle before scanning
[99386.562056] usb 5-5: USB disconnect, address 13
[99390.046656] usb 5-5: new high speed USB device using ehci_hcd and address 14
[99390.992994] usb 5-5: new high speed USB device using ehci_hcd and address 15
[99391.137043] usb 5-5: configuration #1 chosen from 1 choice
[99391.151589] usb-storage: device found at 15
[99391.151596] usb-storage: waiting for device to settle before scanning
[99391.937388] usb 5-5: USB disconnect, address 15
[99395.433913] usb 5-5: new high speed USB device using ehci_hcd and address 16
[99396.378291] usb 5-5: new high speed USB device using ehci_hcd and address 17
[99396.524132] usb 5-5: configuration #1 chosen from 1 choice
[99396.537098] usb-storage: device found at 17
[99396.537105] usb-storage: waiting for device to settle before scanning
[99397.325308] usb 5-5: USB disconnect, address 17
[99400.825580] usb 5-5: new high speed USB device using ehci_hcd and address 18
[99401.763766] usb 5-5: new high speed USB device using ehci_hcd and address 19
[99401.908209] usb 5-5: configuration #1 chosen from 1 choice
[99401.913697] usb-storage: device found at 19
[99401.913703] usb-storage: waiting for device to settle before scanning
[99402.725396] usb 5-5: USB disconnect, address 19
[99406.228042] usb 5-5: new high speed USB device using ehci_hcd and address 20
[99407.169227] usb 5-5: new high speed USB device using ehci_hcd and address 21
[99407.315312] usb 5-5: configuration #1 chosen from 1 choice
[99407.345906] usb-storage: device found at 21
[99407.345914] usb-storage: waiting for device to settle before scanning
[99408.119486] usb 5-5: USB disconnect, address 21
[99411.612516] usb 5-5: new high speed USB device using ehci_hcd and address 22
[99412.555668] usb 5-5: new high speed USB device using ehci_hcd and address 23
[99412.701411] usb 5-5: configuration #1 chosen from 1 choice
[99412.711910] usb-storage: device found at 23
[99412.711919] usb-storage: waiting for device to settle before scanning
[99413.503603] usb 5-5: USB disconnect, address 23
[99416.993983] usb 5-5: new high speed USB device using ehci_hcd and address 24
[99417.940142] usb 5-5: new high speed USB device using ehci_hcd and address 25
[99418.084536] usb 5-5: configuration #1 chosen from 1 choice
[99418.103676] usb-storage: device found at 25
[99418.103683] usb-storage: waiting for device to settle before scanning
[99418.896696] usb 5-5: USB disconnect, address 25
[99422.387451] usb 5-5: new high speed USB device using ehci_hcd and address 26
[99423.461349] usb 5-5: new high speed USB device using ehci_hcd and address 27
[99423.607463] usb 5-5: configuration #1 chosen from 1 choice
[99423.616047] usb-storage: device found at 27
[99423.616051] usb-storage: waiting for device to settle before scanning
[99424.279808] usb 5-5: USB disconnect, address 27
[99427.765940] usb 5-5: new high speed USB device using ehci_hcd and address 28
[99428.712270] usb 5-5: new high speed USB device using ehci_hcd and address 29
[99428.856659] usb 5-5: configuration #1 chosen from 1 choice
[99428.875394] usb-storage: device found at 29
[99428.875401] usb-storage: waiting for device to settle before scanning
[99429.664855] usb 5-5: USB disconnect, address 29
[99433.151431] usb 5-5: new high speed USB device using ehci_hcd and address 30
[99434.101555] usb 5-5: new high speed USB device using ehci_hcd and address 31
[99434.248848] usb 5-5: configuration #1 chosen from 1 choice
[99434.262987] usb-storage: device found at 31
[99434.262996] usb-storage: waiting for device to settle before scanning
[99435.044059] usb 5-5: USB disconnect, address 31
[99438.532899] usb 5-5: new high speed USB device using ehci_hcd and address 32
[99439.481553] usb 5-5: new high speed USB device using ehci_hcd and address 33
[99439.622941] usb 5-5: configuration #1 chosen from 1 choice
[99439.639000] usb-storage: device found at 33
[99439.639007] usb-storage: waiting for device to settle before scanning
[99440.435160] usb 5-5: USB disconnect, address 33
[99443.929408] usb 5-5: new high speed USB device using ehci_hcd and address 34
[99444.867875] usb 5-5: new high speed USB device using ehci_hcd and address 35
[99445.016261] usb 5-5: configuration #1 chosen from 1 choice
[99445.032286] usb-storage: device found at 35
[99445.032293] usb-storage: waiting for device to settle before scanning
[99445.821261] usb 5-5: USB disconnect, address 35
[99449.314856] usb 5-5: new high speed USB device using ehci_hcd and address 36
[99450.254006] usb 5-5: new high speed USB device using ehci_hcd and address 37
[99455.385795] usb 5-5: configuration #1 chosen from 1 choice
[99455.402982] usb-storage: device found at 37
[99455.402989] usb-storage: waiting for device to settle before scanning
[99456.201937] usb 5-5: USB disconnect, address 37
[99459.699566] usb 5-5: new high speed USB device using ehci_hcd and address 38
[99460.645686] usb 5-5: new high speed USB device using ehci_hcd and address 39
[99460.790038] usb 5-5: configuration #1 chosen from 1 choice
[99460.802395] usb-storage: device found at 39
[99460.802401] usb-storage: waiting for device to settle before scanning
[99461.599060] usb 5-5: USB disconnect, address 39
[99465.094603] usb 5-5: new high speed USB device using ehci_hcd and address 40
[99466.031169] usb 5-5: new high speed USB device using ehci_hcd and address 41
[99466.177022] usb 5-5: configuration #1 chosen from 1 choice
[99466.182089] usb-storage: device found at 41
[99466.182092] usb-storage: waiting for device to settle before scanning
[99466.995172] usb 5-5: USB disconnect, address 41
[99470.491585] usb 5-5: new high speed USB device using ehci_hcd and address 42
[99471.427630] usb 5-5: new high speed USB device using ehci_hcd and address 43
[99471.572117] usb 5-5: configuration #1 chosen from 1 choice
[99471.585731] usb-storage: device found at 43
[99471.585739] usb-storage: waiting for device to settle before scanning
[99472.390270] usb 5-5: USB disconnect, address 43
[99476.006681] usb 5-5: new high speed USB device using ehci_hcd and address 44
[99476.945977] usb 5-5: new high speed USB device using ehci_hcd and address 45
[99477.089066] usb 5-5: configuration #1 chosen from 1 choice
[99477.100989] usb-storage: device found at 45
[99477.100996] usb-storage: waiting for device to settle before scanning
[99477.898232] usb 5-5: USB disconnect, address 45
[99481.389148] usb 5-5: new high speed USB device using ehci_hcd and address 46
[99482.346314] usb 5-5: new high speed USB device using ehci_hcd and address 47
[99482.493107] usb 5-5: configuration #1 chosen from 1 choice
[99482.498203] usb-storage: device found at 47
[99482.498206] usb-storage: waiting for device to settle before scanning
[99483.282341] usb 5-5: USB disconnect, address 47
[99486.766664] usb 5-5: new high speed USB device using ehci_hcd and address 48
[99487.720800] usb 5-5: new high speed USB device using ehci_hcd and address 49
[99487.868367] usb 5-5: configuration #1 chosen from 1 choice
[99487.907850] usb-storage: device found at 49
[99487.907860] usb-storage: waiting for device to settle before scanning
[99488.658484] usb 5-5: USB disconnect, address 49
[99492.144137] usb 5-5: new high speed USB device using ehci_hcd and address 50
[99493.078319] usb 5-5: new high speed USB device using ehci_hcd and address 51
[99493.222412] usb 5-5: configuration #1 chosen from 1 choice
[99493.234283] usb-storage: device found at 51
[99493.234289] usb-storage: waiting for device to settle before scanning
[99494.033589] usb 5-5: USB disconnect, address 51
[99497.512912] usb 5-5: new high speed USB device using ehci_hcd and address 52
[99498.463792] usb 5-5: new high speed USB device using ehci_hcd and address 53
[99498.607551] usb 5-5: configuration #1 chosen from 1 choice
[99498.625220] usb-storage: device found at 53
[99498.625227] usb-storage: waiting for device to settle before scanning
[99499.405717] usb 5-5: USB disconnect, address 53
[99502.898122] usb 5-5: new high speed USB device using ehci_hcd and address 54
[99503.844288] usb 5-5: new high speed USB device using ehci_hcd and address 55
[99503.987670] usb 5-5: configuration #1 chosen from 1 choice
[99503.999872] usb-storage: device found at 55
[99503.999877] usb-storage: waiting for device to settle before scanning
[99504.788852] usb 5-5: USB disconnect, address 55
[99508.284610] usb 5-5: new high speed USB device using ehci_hcd and address 56
[99509.229780] usb 5-5: new high speed USB device using ehci_hcd and address 57
[99509.376744] usb 5-5: configuration #1 chosen from 1 choice
[99509.387283] usb-storage: device found at 57
[99509.387288] usb-storage: waiting for device to settle before scanning
[99510.176959] usb 5-5: USB disconnect, address 57
[99513.801077] usb 5-5: new high speed USB device using ehci_hcd and address 58
[99514.742995] usb 5-5: new high speed USB device using ehci_hcd and address 59
[99514.889698] usb 5-5: configuration #1 chosen from 1 choice
[99514.902559] usb-storage: device found at 59
[99514.902565] usb-storage: waiting for device to settle before scanning
[99515.692904] usb 5-5: USB disconnect, address 59
[99519.187307] usb 5-5: new high speed USB device using ehci_hcd and address 60
[99520.132745] usb 5-5: new high speed USB device using ehci_hcd and address 61
[99520.278870] usb 5-5: configuration #1 chosen from 1 choice
[99520.289550] usb-storage: device found at 61
[99520.289557] usb-storage: waiting for device to settle before scanning
[99521.086978] usb 5-5: USB disconnect, address 61
[99524.575914] usb 5-5: new high speed USB device using ehci_hcd and address 62
[99525.517970] usb 5-5: new high speed USB device using ehci_hcd and address 63
[99528.961548] usb 5-5: new high speed USB device using ehci_hcd and address 64
[99529.913347] usb 5-5: new high speed USB device using ehci_hcd and address 65
[99530.059278] usb 5-5: configuration #1 chosen from 1 choice
[99530.064686] usb-storage: device found at 65
[99530.064691] usb-storage: waiting for device to settle before scanning
[99530.850485] usb 5-5: USB disconnect, address 65
[99534.332710] usb 5-5: new high speed USB device using ehci_hcd and address 66
[99535.267848] usb 5-5: new high speed USB device using ehci_hcd and address 67
[99535.411397] usb 5-5: configuration #1 chosen from 1 choice
[99535.422955] usb-storage: device found at 67
[99535.422964] usb-storage: waiting for device to settle before scanning
[99536.224637] usb 5-5: USB disconnect, address 67
[99539.706215] usb 5-5: new high speed USB device using ehci_hcd and address 68
[99540.656353] usb 5-5: new high speed USB device using ehci_hcd and address 69
[99540.802534] usb 5-5: configuration #1 chosen from 1 choice
[99540.812986] usb-storage: device found at 69
[99540.812990] usb-storage: waiting for device to settle before scanning
[99541.597732] usb 5-5: USB disconnect, address 69
[99545.084707] usb 5-5: new high speed USB device using ehci_hcd and address 70
[99546.031473] usb 5-5: new high speed USB device using ehci_hcd and address 71
[99546.176624] usb 5-5: configuration #1 chosen from 1 choice
[99546.187383] usb-storage: device found at 71
[99546.187389] usb-storage: waiting for device to settle before scanning
[99546.983836] usb 5-5: USB disconnect, address 71
[99550.481166] usb 5-5: new high speed USB device using ehci_hcd and address 72
[99551.415350] usb 5-5: new high speed USB device using ehci_hcd and address 73
[99551.559833] usb 5-5: configuration #1 chosen from 1 choice
[99551.574195] usb-storage: device found at 73
[99551.574201] usb-storage: waiting for device to settle before scanning
[99552.381944] usb 5-5: USB disconnect, address 73
[99556.006470] usb 5-5: new high speed USB device using ehci_hcd and address 74
[99556.949516] usb 5-5: new high speed USB device using ehci_hcd and address 75
[99557.093731] usb 5-5: configuration #1 chosen from 1 choice
[99557.107049] usb-storage: device found at 75
[99557.107057] usb-storage: waiting for device to settle before scanning
[99557.898892] usb 5-5: USB disconnect, address 75
[99561.392831] usb 5-5: new high speed USB device using ehci_hcd and address 76
[99562.330007] usb 5-5: new high speed USB device using ehci_hcd and address 77
[99562.476835] usb 5-5: configuration #1 chosen from 1 choice
[99562.496044] usb-storage: device found at 77
[99562.496050] usb-storage: waiting for device to settle before scanning
[99563.284992] usb 5-5: USB disconnect, address 77
[99566.771565] usb 5-5: new high speed USB device using ehci_hcd and address 78
[99567.700511] usb 5-5: new high speed USB device using ehci_hcd and address 79
[99567.846047] usb 5-5: configuration #1 chosen from 1 choice
[99567.851370] usb-storage: device found at 79
[99567.851375] usb-storage: waiting for device to settle before scanning
[99568.662114] usb 5-5: USB disconnect, address 79
[99572.155798] usb 5-5: new high speed USB device using ehci_hcd and address 80
[99573.093967] usb 5-5: new high speed USB device using ehci_hcd and address 81
[99573.240089] usb 5-5: configuration #1 chosen from 1 choice
[99573.245578] usb-storage: device found at 81
[99573.245584] usb-storage: waiting for device to settle before scanning
[99574.056221] usb 5-5: USB disconnect, address 81
[99577.552273] usb 5-5: new high speed USB device using ehci_hcd and address 82
masterloki@masterloki-desktop:~$ 

I do know that in order for me to fix I know that it has to be seen so I can mount it 

also there is no oopsion to change the usb to mtc or msd inthe device 
and it would do this even before I did a frimware update

---

