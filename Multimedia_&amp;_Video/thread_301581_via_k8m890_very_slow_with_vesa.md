---
title: "via k8m890 very slow with vesa"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by rsdavis9 on 2006-11-17
I have the following hardware:
via k8m890ce
averatec av4145-eh1
lshw reports:
product: 2200 Series
vendor: Averatec

Software:
ubuntu edgy 6.10
xorg 7.1.1
vesa 1.2.0

What I have already done:
1. I have been to openchrome.org and compiled and installed the branch vt3336_branch.
The driver comes up and is reasonably fast but it leaves missdraws all over the screen. (call them birdies?)
2. I have been to viaarena and thats where I found I had "via chrome 9 igp" by looking up the devid of 3230.
3. I downloaded the driver from via and got a makefile from a viaarena list but am having troubles with the compile. make fails with:
make: *** [via_driver.o] Error 1.
I am working on it.
4. With ubuntu 6.06 dapper and xorg 7.0.0 vesa 1.0.1 it was reasonably fast.
5. WIth knoppix 5.01 it was even faster. Same xorg and vesa
6. with the current edgy it is abysmally slow on scrolls and window drags. It probably takes 1/2 second per scroll line.
7. I added
Option "AIGLX" "off"
and
Option "Composite" "Disable"
to xorg.conf. No affect.
8. I dont want to go back to dapper because the new kernel(2.6.17) fixed a lockup(slow down) with the thermal module.

Questions:
1. I appear to be stuck with the vesa driver for now. How do I get it to perform as fast as dapper?
2. If I recompile xserver-xorg can I speed up the vesa driver by leaving things out?
3. Is there any other places other then what I have listed where I could find a working via driver? Or is there some simple way to fix the openchrome. I will probably cross post this to the xorg list.

---------------
bob@bobt64:~$ sudo lspci -vv -s 1:0
01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3230 (rev 01) (prog-if 00 [VGA])
Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device a002
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- SERR-
Latency: 64 (500ns min)
Interrupt: pin A routed to IRQ 11
Region 0: Memory at a0000000 (32-bit, prefetchable) [size=256M]
Region 1: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
Expansion ROM at fe3f0000 [disabled] [size=64K]
Capabilities: [60] Power Management version 2
Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Capabilities: [70] AGP version 3.0
Status: RQ=256 Iso- ArqSz=0 Cal=7 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=

---

