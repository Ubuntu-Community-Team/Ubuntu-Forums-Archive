---
title: "Belkin wireless USB stick Ubuntu 10.10 - days of trying and not working"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by bazsound on 2012-11-21
Ok so i have been trying for days to get this thing working, im not one for asking questions as usually the answer is out there, but i just cant find anyuthing that works, ive been at this for hours tonight. and hours days and days before that. Tried every guide i could find and every what i thought was the answer

first off, important information.

this is a branded Belkin USB enhanced wireless adapter.

Model - FSD4050 V1

Inserting the USB stick it appears as if its recognised and installed. it seems to be picked up by USB network manager, but no networks show.

Ifconfig shows an adapter at wlan0, running a scan reports scan not supported.

lsusb to get device info
Bus 001 Device 006: ID 148f:2870 Ralink Technology, Corp. RT2870 Wireless Adapter


searched that to find posts with that id but no usefull info that doesnt work

have blacklisted modules, edited configs.

nothing same deal no networks show scans dont work

a friend suggested downloading the source code from ralink and compiling a drive.

same thing, downloaded firmware

same thing

spent hours searching and trying different things and adapting help from forums to match my id

Nothing nada.


now that ive been messing around
My dmesg output has changed
```

[  364.120308] device disconnected
[  364.120311] device disconnected
[  364.120314] device disconnected
[  364.120318] device disconnected
[  364.120321] device disconnected
[  364.120324] device disconnected
[  364.120328] device disconnected
[  364.120331] device disconnected
[  364.120335] device disconnected
[  364.120338] device disconnected
[  364.120342] device disconnected
[  364.120345] device disconnected
[  364.120348] device disconnected
[  364.120352] device disconnected
[  364.120355] device disconnected
[  364.120358] device disconnected
[  364.120362] device disconnected
[  364.120365] device disconnected
[  364.120369] device disconnected
[  364.120372] device disconnected
[  364.120375] device disconnected
[  364.120379] device disconnected
[  364.120382] device disconnected
[  364.120386] device disconnected
[  364.120389] device disconnected
[  364.120392] device disconnected
[  364.120396] device disconnected
[  364.120399] device disconnected
[  364.120402] device disconnected
[  364.120406] device disconnected
[  364.120409] device disconnected
[  364.120412] device disconnected
[  364.120416] device disconnected
[  364.120419] device disconnected
[  364.120423] device disconnected
[  364.120426] device disconnected
[  364.120429] ERROR! H2M_MAILBOX still hold by MCU. command fail
[  364.120432] device disconnected
[  364.120434] Retry count exhausted or device removed!!!
[  364.120436] device disconnected
[  364.120437] Retry count exhausted or device removed!!!
[  364.120438] device disconnected
[  364.120440] Retry count exhausted or device removed!!!
[  364.120441] device disconnected
[  364.120443] device disconnected
[  364.120444] device disconnected
[  364.120446] device disconnected
[  364.121447] device disconnected
[  364.122448] device disconnected
[  364.123449] device disconnected
[  364.124450] device disconnected
[  364.125451] device disconnected
[  364.126453] device disconnected
[  364.127454] device disconnected
[  364.128455] device disconnected
[  364.129456] device disconnected
[  364.130477] device disconnected
[  364.131479] device disconnected
[  364.132480] device disconnected
[  364.133481] device disconnected
[  364.134482] device disconnected
[  364.135484] device disconnected
[  364.136485] device disconnected
[  364.137486] device disconnected
[  364.138487] device disconnected
[  364.139489] device disconnected
[  364.140511] device disconnected
[  364.141512] device disconnected
[  364.142513] device disconnected
[  364.143515] device disconnected
[  364.144516] device disconnected
[  364.145517] device disconnected
[  364.146518] device disconnected
[  364.147520] device disconnected
[  364.148521] device disconnected
[  364.149522] device disconnected
[  364.150544] device disconnected
[  364.151546] device disconnected
[  364.152547] device disconnected
[  364.153548] device disconnected
[  364.154549] device disconnected
[  364.155551] device disconnected
[  364.156552] device disconnected
[  364.157553] device disconnected
[  364.158554] device disconnected
[  364.159556] device disconnected
[  364.160578] device disconnected
[  364.161579] device disconnected
[  364.162580] device disconnected
[  364.163581] device disconnected
[  364.164583] device disconnected
[  364.165584] device disconnected
[  364.166585] device disconnected
[  364.167586] device disconnected
[  364.168587] device disconnected
[  364.169588] device disconnected
[  364.170617] device disconnected
[  364.171618] device disconnected
[  364.172619] device disconnected
[  364.173621] device disconnected
[  364.174622] device disconnected
[  364.175623] device disconnected
[  364.176624] device disconnected
[  364.177625] device disconnected
[  364.178627] device disconnected
[  364.179628] device disconnected
[  364.180650] device disconnected
[  364.181652] device disconnected
[  364.182653] device disconnected
[  364.183654] device disconnected
[  364.184655] device disconnected
[  364.185657] device disconnected
[  364.186658] device disconnected
[  364.187659] device disconnected
[  364.188660] device disconnected
[  364.189661] device disconnected
[  364.190684] device disconnected
[  364.191685] device disconnected
[  364.192687] device disconnected
[  364.193688] device disconnected
[  364.194689] device disconnected
[  364.195690] device disconnected
[  364.196691] device disconnected
[  364.197693] device disconnected
[  364.198694] device disconnected
[  364.199695] device disconnected
[  364.200718] device disconnected
[  364.201719] device disconnected
[  364.202720] device disconnected
[  364.203721] device disconnected
[  364.204723] device disconnected
[  364.205724] device disconnected
[  364.206725] device disconnected
[  364.207726] device disconnected
[  364.208728] device disconnected
[  364.209729] device disconnected
[  364.210750] device disconnected
[  364.211751] device disconnected
[  364.212752] device disconnected
[  364.213754] device disconnected
[  364.214755] device disconnected
[  364.215756] device disconnected
[  364.216757] device disconnected
[  364.217758] device disconnected
[  364.218760] device disconnected
[  364.219761] device disconnected
[  364.220783] device disconnected
[  364.221784] device disconnected
[  364.221786] device disconnected
[  364.221787] device disconnected
[  364.221789] device disconnected
[  364.221792] device disconnected
[  364.221796] device disconnected
[  364.221799] device disconnected
[  364.221803] device disconnected
[  364.221806] device disconnected
[  364.221809] device disconnected
[  364.221813] device disconnected
[  364.221816] device disconnected
[  364.221820] device disconnected
[  364.221823] device disconnected
[  364.221826] device disconnected
[  364.221830] device disconnected
[  364.221833] device disconnected
[  364.221836] device disconnected
[  364.221840] device disconnected
[  364.221843] device disconnected
[  364.221847] device disconnected
[  364.221850] device disconnected
[  364.221853] device disconnected
[  364.221857] device disconnected
[  364.221860] device disconnected
[  364.221864] device disconnected
[  364.221867] device disconnected
[  364.221871] device disconnected
[  364.221874] device disconnected
[  364.221877] device disconnected
[  364.221881] device disconnected
[  364.221884] device disconnected
[  364.221888] device disconnected
[  364.221891] device disconnected
[  364.221894] device disconnected
[  364.221898] device disconnected
[  364.221901] device disconnected
[  364.221905] device disconnected
[  364.221908] device disconnected
[  364.221912] device disconnected
[  364.221915] device disconnected
[  364.221918] device disconnected
[  364.221922] device disconnected
[  364.221925] device disconnected
[  364.221928] device disconnected
[  364.221932] device disconnected
[  364.221935] device disconnected
[  364.221939] device disconnected
[  364.221942] device disconnected
[  364.221946] device disconnected
[  364.221949] device disconnected
[  364.221952] device disconnected
[  364.221956] device disconnected
[  364.221959] device disconnected
[  364.221962] device disconnected
[  364.221966] device disconnected
[  364.221969] device disconnected
[  364.221973] device disconnected
[  364.221976] device disconnected
[  364.221979] device disconnected
[  364.221983] device disconnected
[  364.221986] device disconnected
[  364.221989] device disconnected
[  364.221993] device disconnected
[  364.221996] device disconnected
[  364.222000] device disconnected
[  364.222003] device disconnected
[  364.222007] device disconnected
[  364.222010] device disconnected
[  364.222013] device disconnected
[  364.222017] device disconnected
[  364.222020] device disconnected
[  364.222024] device disconnected
[  364.222027] device disconnected
[  364.222030] device disconnected
[  364.222034] device disconnected
[  364.222037] device disconnected
[  364.222041] device disconnected
[  364.222044] device disconnected
[  364.222047] device disconnected
[  364.222051] device disconnected
[  364.222054] device disconnected
[  364.222058] device disconnected
[  364.222061] device disconnected
[  364.222065] device disconnected
[  364.222068] device disconnected
[  364.222072] device disconnected
[  364.222075] device disconnected
[  364.222078] device disconnected
[  364.222082] device disconnected
[  364.222085] device disconnected
[  364.222089] device disconnected
[  364.222092] device disconnected
[  364.222095] device disconnected
[  364.222099] device disconnected
[  364.222102] device disconnected
[  364.222106] device disconnected
[  364.222109] device disconnected
[  364.222112] device disconnected
[  364.222116] device disconnected
[  364.222119] device disconnected
[  364.222123] device disconnected
[  364.222126] device disconnected
[  364.222129] device disconnected
[  364.222133] ERROR! H2M_MAILBOX still hold by MCU. command fail
[  364.277342] ---> RTMPFreeTxRxRingMemory
[  364.277375] <--- RTMPFreeTxRxRingMemory
[  364.334924]  RTUSB disconnect successfully
[  461.750040] usb 1-1: new high speed USB device using ehci_hcd and address 6
[  461.901118] === pAd = ffffc90013582000, size = 504952 ===
[  461.901123] <-- RTMPAllocAdapterBlock, Status=0
[  461.932593] #
[  461.942598] #
[  461.952604] #
[  461.962608] #
[  461.972618] #
[  461.982624] #
[  461.992630] #
[  462.012644] #
[  462.052547] #
[  462.062689] #
[  462.082568] #
[  462.092573] #
[  462.102581] #
[  462.112585] #
[  462.122594] #
[  462.132600] #
[  462.142608] #
[  462.152614] #
[  462.162619] #
[  462.172628] #
[  462.202648] #
[  462.212653] #
[  462.232544] #
[  462.252556] #
[  462.262562] #
[  462.272570] #
[  462.282579] #
[  462.292584] #
[  462.302591] #
[  462.312596] #
[  462.322604] #
[  462.332614] #
[  462.342619] #
[  462.352625] #
[  462.362630] #
[  462.382643] #
[  462.402658] #
[  462.412664] #
[  462.422669] #
[  462.432679] #
[  462.442561] #
[  462.452567] #
[  462.471653] <-- RTMPAllocTxRxRingMemory, Status=0
[  462.473331] -->RTUSBVenderReset
[  462.473455] <--RTUSBVenderReset
[  462.482720] #
[  462.492598] #
[  462.512609] #
[  462.522617] #
[  462.532621] #
[  462.542628] #
[  462.582655] #
[  462.602545] #
[  462.622559] #
[  462.632690] #
[  462.642572] #
[  462.652579] #
[  462.662589] #
[  462.672592] #
[  462.682598] #
[  462.692606] #
[  462.702613] #
[  462.712621] #
[  462.730513] #
[  462.752644] #
[  462.780546] #
[  462.792548] #
[  462.812564] #
[  462.830704] #
[  462.852588] #
[  462.862596] #
[  462.872602] #
[  462.882609] #
[  462.892617] #
[  462.902623] #
[  462.912628] #
[  462.932643] #
[  462.952532] #
[  462.962663] #
[  462.982554] #
[  463.000067] #
[  463.006443] 1. Phy Mode = 0
[  463.006445] 2. Phy Mode = 0
[  463.006448] NVM is Efuse and its size =2d[2d0-2fc] 
[  463.012697] #
[  463.022580] #
[  463.032712] #
[  463.042593] #
[  463.052599] #
[  463.062605] #
[  463.072615] #
[  463.082620] #
[  463.092626] #
[  463.122648] #
[  463.132655] #
[  463.152543] #
[  463.160923] 3. Phy Mode = 0
[  463.162673] #
[  463.171807] RTMPSetPhyMode: channel is out of range, use first channel=1 
[  463.171810] MCS Set = 00 00 00 00 00
[  463.182560] #
[  463.192570] #
[  463.202577] #
[  463.212584] #
[  463.222594] #
[  463.232603] #
[  463.248361] <==== rt28xx_init, Status=0
[  463.249858] 0x1300 = 00073200
[  463.876853] ---> RTMPFreeTxRxRingMemory
[  463.876885] <--- RTMPFreeTxRxRingMemory
[  463.902553] #
[  463.932571] #
[  463.952582] #
[  463.982607] #
[  464.002616] #
[  464.022630] #
[  464.032636] #
[  464.052649] #
[  464.082548] #
[  464.102558] #
[  464.112567] #
[  464.122574] #
[  464.132705] #
[  464.142589] #
[  464.152594] #
[  464.162601] #
[  464.172608] #
[  464.182613] #
[  464.192642] #
[  464.202630] #
[  464.232649] #
[  464.252660] #
[  464.272549] #
[  464.282555] #
[  464.292564] #
[  464.312578] #
[  464.322585] #
[  464.332592] #
[  464.342598] #
[  464.352605] #
[  464.362612] #
[  464.372621] #
[  464.382623] #
[  464.403741] <-- RTMPAllocTxRxRingMemory, Status=0
[  464.405389] -->RTUSBVenderReset
[  464.405515] <--RTUSBVenderReset
[  464.422652] #
[  464.432658] #
[  464.452548] #
[  464.472573] #
[  464.482693] #
[  464.492575] #
[  464.502581] #
[  464.522601] #
[  464.532600] #
[  464.542610] #
[  464.552618] #
[  464.562622] #
[  464.572630] #
[  464.582634] #
[  464.629043] #
[  464.640054] #
[  464.672570] #
[  464.682576] #
[  464.692585] #
[  464.702595] #
[  464.712598] #
[  464.722607] #
[  464.732613] #
[  464.742619] #
[  464.752626] #
[  464.762632] #
[  464.802659] #
[  464.822553] #
[  464.842564] #
[  464.872591] #
[  464.882593] #
[  464.892595] #
[  464.902601] #
[  464.912608] #
[  464.922617] #
[  464.932623] #
[  464.942630] #
[  464.972650] #
[  464.990912] 1. Phy Mode = 0
[  464.990914] 2. Phy Mode = 0
[  464.990917] NVM is Efuse and its size =2d[2d0-2fc] 
[  465.000195] #
[  465.022556] #
[  465.032564] #
[  465.052578] #
[  465.062586] #
[  465.072592] #
[  465.082599] #
[  465.092605] #
[  465.102612] #
[  465.112619] #
[  465.122624] #
[  465.134009] 3. Phy Mode = 0
[  465.138889] MCS Set = 00 00 00 00 00
[  465.152645] #
[  465.187800] <==== rt28xx_init, Status=0
[  465.189295] 0x1300 = 00073200
[  465.242595] #
[  466.152572] #
[  466.452649] #
[  466.602625] #
[  466.752601] #
[  466.902578] #
[  475.402513] wlan0: no IPv6 routers present
[  481.652541] #
[  481.662672] #
[  485.232650] #
[  485.531974] #
[  485.672564] #
[  496.682621] #
[  496.692620] #
[  501.702599] #
[  515.522649] #
[  515.672618] #
[  515.820099] #
[  515.972560] #
[  516.122653] #
[  516.272622] #
[  516.710277] #
[  532.722637] #
[  543.732688] #
[  545.742618] #
[  546.192642] #
[  556.252597] #
[  556.702629] #
[  558.742592] #
[  573.752636] #
[  582.772549] #
[  586.372646] #
[  586.672571] #
[  586.822658] #
[  586.832662] #
[  593.782704] #
[  595.792596] #
[  595.802603] #
[  596.102663] #
[  596.852597] #
[  597.302598] #
[  597.452551] #
[  605.232632] #
[  605.382592] #
[  605.532552] #
[  605.970816] #
[  605.982557] #
[  606.271349] #
[  606.282605] #
[  608.792639] #
alex@ubuntu:~$ 

ive never seen that much empty space in dmsg.

and ive even uninstalled the ralink driver.

dmesg | grep rt28 gives

[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Movable zone start PFN for each node
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:46c00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] Checking aperture...
[    0.000000] Node 0: aperture @ 5e54000000 size 32 MB
[    0.000000] Aperture beyond 4GB. Ignoring.
[    0.015944] mce: CPU supports 5 MCE banks
[    0.026017] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.291176] node 0 link 0: io port [1000, ffffff]
[    0.308220] ACPI: (supports S0 S3 S4 S5)
[    0.338927] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.339538] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.339618] pci 0000:00:02.0: supports D1 D2
[    0.339620] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.339671] pci 0000:00:02.1: supports D1 D2
[    0.339673] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.339762] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.339858] pci 0000:00:07.0: supports D1 D2
[    0.339860] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.339953] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.340012] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.340049] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.628641] pcieport 0000:00:09.0: setting latency timer to 64
[    0.628672] pcieport 0000:00:09.0: irq 40 for MSI/MSI-X
[    0.628791] pcieport 0000:00:0b.0: setting latency timer to 64
[    0.628814] pcieport 0000:00:0b.0: irq 41 for MSI/MSI-X
[    0.628902] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.628924] pcieport 0000:00:0c.0: irq 42 for MSI/MSI-X
[    0.633493] Linux agpgart interface v0.103
[    0.633498] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.637470] ehci_hcd 0000:00:02.1: debug port 1
[    0.637478] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.650018] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.650160] hub 1-0:1.0: 8 ports detected
[    0.712153] hub 2-0:1.0: 8 ports detected
[    0.714526] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.714533] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.714737] rtc_cmos 00:02: RTC can wake from S4
[    0.714788] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.714827] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.717075] rtc_cmos 00:02: setting system clock to 2012-11-22 00:02:15 UTC (1353542535)
[    0.742591] udev[102]: starting version 163
[    1.599939] ata2: port disabled. ignoring.
[    1.920772] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.991242] udev[365]: starting version 163
[   22.401480] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   22.435035] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   22.443006] rtusb init --->
[   22.443876] usbcore: registered new interface driver rt2870
[   25.996869] ppdev: user-space parallel port driver
[   50.383466] UDF-fs: Partition marked readonly; forcing readonly mount
[   82.218416] <==== rt28xx_init, Status=0
[   84.110971] <==== rt28xx_init, Status=0
[  364.082720] rtusb_disconnect: unregister usbnet usb-0000:00:02.1-1
[  463.248361] <==== rt28xx_init, Status=0
[  465.187800] <==== rt28xx_init, Status=0
alex@ubuntu:~$
```

---

### Post by chili555 on 2012-11-21
Let's have a look at:```
modinfo rt2870sta
lsmod | grep -e rt2 -e ndis
rfkill list all
```Thanks.

---

### Post by bazsound on 2012-11-22
a```
lex@ubuntu:~$ modinfo rt2870sta
filename:       /lib/modules/2.6.35-32-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93E93E3E336F412601AF0FA
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.35-32-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
alex@ubuntu:~$ 


alex@ubuntu:~$ lsmod | grep -e rt2 -e ndis
rndis_host              7580  0 
cdc_ether               4920  1 rndis_host
usbnet                 20985  2 rndis_host,cdc_ether
rt2870sta             446110  1 
crc_ccitt               1699  1 rt2870sta

```

rfkill listall returned nothing.

---

### Post by bazsound on 2012-11-22
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:72:31:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12032 (12.0 KB)  TX bytes:12032 (12.0 KB)

usb0      Link encap:Ethernet  HWaddr d2:48:7f:fc:94:5d  
          inet addr:192.168.42.90  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::d048:7fff:fefc:945d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8539 errors:1 dropped:0 overruns:0 frame:1
          TX packets:6786 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7635906 (7.6 MB)  TX bytes:1710103 (1.7 MB)

wlan0     Link encap:Ethernet  HWaddr 04:06:07:07:06:05  
          inet6 addr: fe80::606:7ff:fe07:605/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:44880 (44.8 KB)

```

[CODE] iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-117 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@ubuntu:~$ uname -mr
2.6.35-32-generic x86_64
[/QUOTE]

---

### Post by chili555 on 2012-11-22
You have the correct driver and only the correct driver loaded and it covers your device. So far, so good. The rt2870sta module that's loaded appears to be the default in-kernel version, not any compiled version.

I suspect Network Manager will not attempt to use the wlan0 device as long as usb0 is connected and has an IP address. Please detach usb0 (your tethered smart(?)phone, I assume) and reboot so we have a clean slate. Run:```
dmesg > baz.txt
sudo iwlist wlan0 scan >> baz.txt
iwconfig >> baz.txt
zip baz.zip baz.txt
```Find the file baz.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by mörgæs on 2012-11-22
Before proceeding I would recommend a fresh install of 12.04 or 12.10. 

10.10 is obsolete.

---

### Post by bazsound on 2012-11-23
Heres the request info.

Without my phone tethered or connected to computer seems to be the same.

I had previously been using a netgear adapter which just worked when plugged in, that used an rndis driver.

[ATTACH]227618[/ATTACH]

---

### Post by chili555 on 2012-11-23
This is kind of scary!> [   25.508396] <-- RTMPAllocTxRxRingMemory, Status=0
[   25.510026] -->RTUSBVenderReset
[   25.510153] <--RTUSBVenderReset
[   25.592525] #
[   25.622647] #
[   25.642647] #
[   25.662523] #
[   25.812274] 1. Phy Mode = 0
[   25.812278] 2. Phy Mode = 0
[   25.812281] NVM is Efuse and its size =2d[2d0-2fc] 
[   25.853648] [COLOR="Red"]ERROR! E2PROM: WRONG VERSION 0x7, should be 1[/COLOR]
[   25.877025] 3. Phy Mode = 0
[   25.881899] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   25.881903] MCS Set = 00 00 00 00 00
[   25.892648] #
[   25.912522] #
[   25.929402] <==== rt28xx_init, Status=0
[   25.930897] 0x1300 = 00073200
[   26.522624] ---> RTMPFreeTxRxRingMemory
[   26.522664] <--- RTMPFreeTxRxRingMemory
[   26.550068] hda_codec: ALC883: BIOS auto-probing.
[   26.808090] <-- RTMPAllocTxRxRingMemory, Status=0
[   26.811900] -->RTUSBVenderReset
[   26.812024] <--RTUSBVenderReset
[   26.860154] #
[   27.107275] 1. Phy Mode = 0
[   27.107278] 2. Phy Mode = 0
[   27.107281] NVM is Efuse and its size =2d[2d0-2fc] 
[   27.152531] ERROR! E2PROM: WRONG VERSION 0x7, should be 1Yikes! I wonder if the old compiled version has corrupted something. Let's see if we can clean up:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those backticks are on the left side of my US keybooard on the same key with ~.

Reboot and check dmesg again:```
dmesg | grep -e rt2 -e ERROR
```If that doesn't help, then I wonder if the in-kernel default rt2870sta module requires firmware; check:```
modinfo rt2870sta | grep -i firm
```If none is required, we have nothing to fix there.

Does the device work flawlessly on other computers; that is, can we rule out an electrically defective device?

---

### Post by bazsound on 2012-11-23
```

alex@ubuntu:~$ dmesg | grep -e rt2 -e ERROR
[   23.662987] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   23.749441] usbcore: registered new interface driver rt2870
[   25.002449] ERROR! E2PROM: WRONG VERSION 0x6, should be 1
[   25.121453] <==== rt28xx_init, Status=0
[   26.514829] ERROR! E2PROM: WRONG VERSION 0x6, should be 1
[   26.604460] <==== rt28xx_init, Status=0


alex@ubuntu:~$ modinfo rt2870sta | grep -i firm
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin

```

As far as i know it works in windows machines, i was told it did work.

---

### Post by chili555 on 2012-11-23
Let's see if the firmware is corrupted:```
md5sum /lib/firmware/rt*.bin
```Can you confirm you have all of them?```
ls /lib/firmware | grep -e rt30 -e rt28
```For what it's worth, and I doubt this is material, my 12.10 install doesn't include rt3071.bin.

---

### Post by bazsound on 2012-11-23
```
99bce75086ea635a2f8288d9b835f787  /lib/firmware/rt2561.bin
2878d5eaa4ff907d4df36a834915aa53  /lib/firmware/rt2561s.bin
9998485bc152cf0f39dd61a33b92ad9b  /lib/firmware/rt2661.bin
7f55011396eff4983f26bb7dd7339fb3  /lib/firmware/rt2860.bin
2bb89af3a7d446deb4695c9a3daa7f9d  /lib/firmware/rt2870.bin
7c540794d71ad684c1e97e80a59d8edf  /lib/firmware/rt3070.bin
faf3eb6379501e4282464bd68de9a7fe  /lib/firmware/rt3071.bin
0efb51d2d3f4be99cb491bca0dc025fb  /lib/firmware/rt3090.bin
bd733372ae21a010bf8a5511d7711c2d  /lib/firmware/rt73.bin

alex@ubuntu:/lib64/firmware$ ls /lib/firmware | grep -e rt30 -e rt28
rt2860.bin
rt2870.bak
rt2870.bin
rt3070.bin
rt3071.bin
rt3090.bin

```

---

### Post by chili555 on 2012-11-23
My firmware files, for comparison, are different; for example:> 36c944c3138125605d28c0a3a1338be9  /lib/firmware/rt2870.binOf course, that could be a result of 64-bit 10.10 vs. 32-bit 12.10. Please try:```
sudo apt-get install --reinstall linux-firmware
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta
```Now check:```
dmesg | tail -n20
```Any change/improvement/miracles?

---

### Post by bazsound on 2012-11-23
> **chili555 said:**
> My firmware files, for comparison, are different; for example:Of course, that could be a result of 64-bit 10.10 vs. 32-bit 12.10. Please try:```
sudo apt-get install --reinstall linux-firmware
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta
```Now check:```
dmesg | tail -n20
```Any change/improvement/miracles?

```
[   27.582475] 1. Phy Mode = 0
[   27.582479] 2. Phy Mode = 0
[   27.582482] NVM is Efuse and its size =2d[2d0-2fc] 
[   27.625974] ERROR! E2PROM: WRONG VERSION 0x6, should be 1
[   27.642597] #
[   27.656102] 3. Phy Mode = 0
[   27.660975] MCS Set = 00 00 00 00 00
[   27.672599] #
[   27.702597] #
[   27.713733] <==== rt28xx_init, Status=0

```

No change it seems

---

### Post by bazsound on 2012-11-23
ive just came across something which might be an indication as to why its complaining of e2prom wrong.

i renamed some of the firmware files in /lib/firmware from .bin to .bak to try and figure out what firmware is being loaded.

Leaving the rt2780 file and renaming others.

The error e2prom wrong version goes away and instead failed to load firmware.

I rename rt3070 back to a bin file, and the e2prom error returns, so it may look like its loading the rt3070 firmware, which doesnt seam right since lsusb reports it as a 2870 chipset.

So after more reading this should work with the rt2800usb driver, i blacklist rt2879sta rmmod it, then plug adapter back in

```
Nov 24 00:48:25 ubuntu kernel: [ 2888.252525] usb 1-1: new high speed USB device using ehci_hcd and address 13
Nov 24 00:48:25 ubuntu kernel: [ 2888.447430] cfg80211: Calling CRDA to update world regulatory domain
Nov 24 00:48:25 ubuntu kernel: [ 2888.494906] cfg80211: World regulatory domain updated:
Nov 24 00:48:25 ubuntu kernel: [ 2888.494911]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 24 00:48:25 ubuntu kernel: [ 2888.494914]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 24 00:48:25 ubuntu kernel: [ 2888.494917]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 24 00:48:25 ubuntu kernel: [ 2888.494920]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 24 00:48:25 ubuntu kernel: [ 2888.494923]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 24 00:48:25 ubuntu kernel: [ 2888.494925]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 24 00:48:26 ubuntu kernel: [ 2888.791464] usbcore: registered new interface driver rt2800usb
Nov 24 00:48:27 ubuntu kernel: [ 2890.003553] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

driver seems to load fine but link not ready, and no networks show.

iwlist scan - no scan results

---

### Post by chili555 on 2012-11-23
I believe rt2800usb also requires the same firmware; I suggest you restore the original names and reboot.

---

### Post by bazsound on 2012-11-28
ok i think this adapter is faulty just tried it on a windows 7 machine. device installs and comes up as an 802.11 wireless usb lan adapter. no networks show. download belkin software (though there are no windows 7 drivers) restart device reinstalls same result except i now have a miniport driver along with the 802.11 driver.

This seems broken. thanks for all the help and suppert :D

---

### Post by mörgæs on 2012-11-29
Well, at least you now have a conclusion. Please mark your thread 'solved'.

---

