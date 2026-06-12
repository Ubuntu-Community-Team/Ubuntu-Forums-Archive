---
title: "Howto install PCI analog/dvb-t tv card?"
date: 2009-06-17
forum: Multimedia Software
---

### Post by qrzysztof-pl on 2009-06-17
Hi all

I have X3M HPC2000 hybrid tv card and Ubuntu 9.04, and I downloaded linux drivers from [their website]("http://www.x3mtv-tuners.pl/support.php?id=3").

I have lot of .i2c.fw files, and I don't know how to install it.

---

My dmesg:
> [   12.916949] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   12.917747] cx88[0]: subsystem: 14f1:8852, board: Geniatech X8000-MT DVBT [card=63,autodetected], frontend(s): 1
[   12.917753] cx88[0]: TV tuner type 71, Radio tuner type 0
[   12.951384] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   13.060214] cx2388x alsa driver version 0.0.7 loaded
[   13.110281] tuner 1-0061: chip found @ 0xc2 (cx88[0])
[   13.256515] xc2028 1-0061: creating new instance
[   13.256521] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   13.256529] cx88[0]: Asking xc2028/3028 to load firmware xc3028-v27.fw
[   13.272032] cx88[0]/2: cx2388x 8802 Driver Manager
[   13.272055] cx88-mpeg driver manager 0000:02:07.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.272067] cx88[0]/2: found at 0000:02:07.2, rev: 5, irq: 16, latency: 64, mmio: 0xe9000000
[   13.273032] cx8800 0000:02:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.273046] cx88[0]/0: found at 0000:02:07.0, rev: 5, irq: 16, latency: 64, mmio: 0xe7000000
[   13.273277] cx88[0]/0: registered device video0 [v4l2]
[   13.273495] cx88[0]/0: registered device vbi0
[   13.273629] cx88[0]/0: registered device radio0
[   13.273704] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[   13.342758] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[   13.350469] cx88_audio 0000:02:07.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.350513] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   13.368171] EMU10K1_Audigy 0000:02:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.397065] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   13.423464] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   13.423470] cx88/2: registering cx8802 driver, type: dvb access: shared
[   13.423475] cx88[0]/2: subsystem: 14f1:8852, board: Geniatech X8000-MT DVBT [card=63]
[   13.423480] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.423482] cx8802_alloc_frontends() allocating 1 frontend(s)
[   13.493672] xc2028 1-0061: attaching existing instance
[   13.493679] xc2028 1-0061: type set to XCeive xc2028/xc3028 tuner
[   13.493684] cx88[0]/2: xc3028 attached
[   13.513365] DVB: registering new adapter (cx88[0])
[   13.513374] DVB: registering adapter 0 frontend 0 (Zarlink ZL10353 DVB-T)...
[   13.784102] lp0: using parport0 (interrupt-driven).
[   14.579655] EXT3 FS on sda1, internal journal
[   16.040682] type=1505 audit(1244041308.431:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2060
[   16.114753] type=1505 audit(1244041308.503:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2064
[   16.115052] type=1505 audit(1244041308.503:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2064
[   16.115210] type=1505 audit(1244041308.503:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2064
[   16.115339] type=1505 audit(1244041308.503:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2064
[   16.316904] type=1505 audit(1244041308.707:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2069
[   16.317318] type=1505 audit(1244041308.707:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2069
[   16.370613] type=1505 audit(1244041308.759:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2073
[   16.414774] type=1505 audit(1244041308.803:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2077
[   24.432142] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[   24.445067] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[   27.638222] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.638227] Bluetooth: BNEP filters: protocol multicast
[   27.713025] Bridge firewalling registered
[   29.106674] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   29.106695] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   29.106728] nvidia 0000:01:05.0: putting AGP V2 device into 4x mode
[   33.610036] skge eth0: enabling interface
[   33.613351] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.673410] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   36.673575] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   46.832034] eth0: no IPv6 routers present
[   50.742848] UDF-fs: No VRS found
[   50.758118] ISO 9660 Extensions: Microsoft Joliet Level 3
[   50.758458] ISOFS: changing to secondary root
[ 2138.229144] ppdev0: registered pardevice
[ 2138.285261] ppdev0: unregistered pardevice
[ 2140.176342] ppdev0: registered pardevice
[ 2140.224200] ppdev0: unregistered pardevice
[ 2141.610047] ppdev0: registered pardevice
[ 2141.656050] ppdev0: unregistered pardevice
[ 2357.968763] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2358.043411] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2358.328753] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2358.333695] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2358.513492] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2358.518538] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2361.124728] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2361.130797] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2361.769168] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2361.776166] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2362.141348] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2362.147902] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2362.475429] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2362.482580] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2362.753460] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2362.760034] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2363.033453] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2363.038642] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2363.313462] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2363.318622] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2365.016776] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2365.023130] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2365.501390] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2365.507607] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2365.830222] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2365.836291] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2366.113426] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2366.119701] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2366.393428] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2366.398485] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2366.673421] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2366.678559] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2366.953435] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2366.958413] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2367.233428] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2367.238401] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2367.513417] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2367.518489] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2367.793427] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2367.798623] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2368.073422] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2368.079929] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2368.462947] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2368.469095] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2368.795458] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2368.803597] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2369.538924] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2369.544927] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2369.833405] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2369.838440] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2370.113396] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2370.118656] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2370.539654] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2370.545878] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2371.117180] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2371.123306] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2371.648310] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2371.654533] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2371.953391] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2371.958277] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2372.233394] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2372.238277] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2372.535554] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2372.541557] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2372.833395] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2372.838515] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2373.113399] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2373.118422] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2373.393386] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2373.398567] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2373.673377] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2373.678601] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2374.561685] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2374.567748] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2374.873365] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2374.878423] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2375.153365] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2375.158560] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2375.935443] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2375.941458] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2376.233363] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2376.238373] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 2376.513361] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 2376.518266] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 3189.132756] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 3189.137772] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 3189.432764] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 3189.439255] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.
[ 3189.619430] cx88-mpeg driver manager 0000:02:07.2: firmware: requesting xc3028-v27.fw
[ 3189.624351] xc2028 1-0061: Error: firmware xc3028-v27.fw not found.

and
lspci -vv
> 02:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: Conexant Systems, Inc. Device 8852
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx8800
	Kernel modules: cx8800

02:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: Conexant Systems, Inc. Device 8852
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1000ns min, 63750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

02:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: Conexant Systems, Inc. Device 8852
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1500ns min, 22000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

---

