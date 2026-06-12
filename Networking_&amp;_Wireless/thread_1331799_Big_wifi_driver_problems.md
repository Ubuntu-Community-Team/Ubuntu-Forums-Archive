---
title: "Big wifi driver problems"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Ganjafreak on 2009-11-19
Okay, My problem is this: I have a ubuntu 8.0 cd and I installed it and I had 100% connection(Wireless) and Now when I upgraded to 9.04 Jaunty I have 40% or less. 

NOTE: I have not moved my computer, It still is in the same place.

I have been told to find what my wifi driver was and search for a update but I have a app called sysinfo and it don't say anything about it and in system>administration>hardware drivers

and all that pop up is something about my graphics card

Can anyone tell me how to get my wifi card information so I can update

---

### Post by Ganjafreak on 2009-11-19
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Device 2a3e
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f200 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth

I typed something in and got that information along with all my drivers

Is that it it's my ethernet

---

### Post by Dude-PWB- on 2009-11-19
That looks like your wired ethernet adapter.

lspci -vv will give you a readout of all applicable pci devices, your wireless should be listed  in there somewhere, unless it's a usb adapter, then you would use lsusb.

---

### Post by Ganjafreak on 2009-11-19
Region 4: I/O ports at fd00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: Hewlett-Packard Company Device 2a3e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 23
    Region 0: I/O ports at 09f0 [size=8]
    Region 1: I/O ports at 0bf0 [size=4]
    Region 2: I/O ports at 0970 [size=8]
    Region 3: I/O ports at 0b70 [size=4]
    Region 4: I/O ports at f800 [size=16]
    Region 5: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: Hewlett-Packard Company Device 2a3e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (750ns min, 250ns max)
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at 09e0 [size=8]
    Region 1: I/O ports at 0be0 [size=4]
    Region 2: I/O ports at 0960 [size=8]
    Region 3: I/O ports at 0b60 [size=4]
    Region 4: I/O ports at f300 [size=16]
    Region 5: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: fdc00000-fdcfffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a3e
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (500ns min, 1250ns max)
    Interrupt: pin B routed to IRQ 22
    Region 0: Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
    Subsystem: Hewlett-Packard Company Device 2a3e
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0 (250ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at f200 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:0a.0 Communication controller: 3Com Corp, Modem Division USR 56k Internal WinModem
    Subsystem: 3Com Corp, Modem Division Device 00c2
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 255
    Region 0: Memory at fdcff000 (32-bit, prefetchable) [size=64]
    Region 1: Memory at fdce0000 (32-bit, prefetchable) [size=64K]
    Region 2: Memory at fdcf0000 (32-bit, prefetchable) [size=32K]
    Region 3: I/O ports at df00 [size=64]
    Capabilities: <access denied>

ganjafreak@ganjafreak-desktop:~$ rt- >SERR- <PERR- INTx-
 
bash: PERR-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (750ns min, 250ns max)
bash: syntax error near unexpected token `('
x
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin A routed to IRQ 20
2
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: ohci_hcd
t
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Company Device 2a3e
p
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (750ns min, 250ns max)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin B routed to IRQ 21
2
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: ehci_hcd
e
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Company Device 2a3e
a
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (750ns min, 250ns max)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
t
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 4: I/O ports at fd00 [size=16]
t
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: pata_amd
6
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Company Device 2a3e
>
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
o
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (750ns min, 250ns max)
bash: syntax error near unexpected token `('
+
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin A routed to IRQ 23
5
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: I/O ports at 09f0 [size=8]
t
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 1: I/O ports at 0bf0 [size=4]
t
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 2: I/O ports at 0970 [size=8]
t
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 3: I/O ports at 0b70 [size=4]
4
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 4: I/O ports at f800 [size=16]
f
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 5: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: sata_nv
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Company Device 2a3e
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (750ns min, 250ns max)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin A routed to IRQ 22
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: I/O ports at 09e0 [size=8]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 1: I/O ports at 0be0 [size=4]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 2: I/O ports at 0960 [size=8]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 3: I/O ports at 0b60 [size=4]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 4: I/O ports at f300 [size=16]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Region 5: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: sata_nv
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0
Latency:: command not found
ganjafreak@ganjafreak-desktop:~$ Bus: primary=00, secondary=03, subordinate=03, sec-latency=128
Bus:: command not found
ganjafreak@ganjafreak-desktop:~$ I/O behind bridge: 0000d000-0000dfff
bash: I/O: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Memory behind bridge: fdd00000-fddfffff
Memory: command not found
ganjafreak@ganjafreak-desktop:~$ Prefetchable memory behind bridge: fdc00000-fdcfffff
Prefetchable: command not found
ganjafreak@ganjafreak-desktop:~$ Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
BridgeCtl:: command not found
ganjafreak@ganjafreak-desktop:~$ 
Display all 2407 possibilities? (y or n)
:
!
./
[
[[
]]
{
}
2to3
2to3-2.6
a2p
aa-audit
aa-autodep
aa-complain
aa-enforce
aa-genprof
aa-logprof
aa-status
aa-unconfined
abrowser
abrowser-3.5
accept
accessdb
aconnect
acpi_available
acpid
acpi_fakekey
acpi_listen
add-apt-repository
addgroup
_add_members
addpart
addr2line
add-shell
adduser
alacarte
alias
_alias
alsa
alsactl
alsamixer
amidi
amixer
amuFormat.sh
anacron
aplay
aplaymidi
apm
apm_available
apmd
apmsleep
apparmor_parser
apparmor_status
apport-bug
apport-cli
apport-collect
apport-unpack
appres
apropos
_apt_cache
apt-cache
apt-cdrom
apt-config
aptd
aptdcon
apt-extracttemplates
apt-ftparchive
_apt_get
apt-get
ganjafreak@ganjafreak-desktop:~$ -
-: command not found
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Company Device 2a3e
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- 
Status:: command not found
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (500ns min, 1250ns max
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin B routed to IRQ 22
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: HDA Int
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ Kernel modules: snd-hda-intel
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Subsystem: Hewlett-Packard Comp
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Latency: 0 (250ns min, 5000ns max)
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin A routed to IRQ 2
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 1: I/O ports at f200 [size=8]
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access de
bash: access: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: forcedeth
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ Kernel modules: forcedeth
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra
00:18.0: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.1: command not found
ganjafreak@ganjafreak-desktop:~$ Cont
Cont: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
bash: MAbort-: No such file or directory
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.2: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Stat
No command 'Stat' found, did you mean:
 Command 'stat' from package 'coreutils' (main)
Stat: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon6
00:18.3: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ Kernel driver in use: k8temp
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ Kernel modules: k8temp
Kernel: command not found
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ 03:0a.0 Communication controller: 3Com Corp, Mo03:0a.0: command not found
ganjafreak@ganjafreak-desktop:~$ Subsystem: 3Com Corp, Modem Division Device 00c2
Subsystem:: command not found
ganjafreak@ganjafreak-desktop:~$ Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- 
Control:: command not found
ganjafreak@ganjafreak-desktop:~$ Status: Cap+ 66MHz- UDF- FastB2B+
Status:: command not found
ganjafreak@ganjafreak-desktop:~$ Interrupt: pin A routed to IRQ 25
Interrupt:: command not found
ganjafreak@ganjafreak-desktop:~$ Region 0: Memory at fdcff000 (32-bit
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 1: Memory at fdce0000 (32-bit
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 2: Memory at fdcf0000 (32-bit
bash: syntax error near unexpected token `('
ganjafreak@ganjafreak-desktop:~$ Region 3: I/O ports at df00 [size=64
Region: command not found
ganjafreak@ganjafreak-desktop:~$ Capabilities: <access denied>
bash: syntax error near unexpected token `newline'
ganjafreak@ganjafreak-desktop:~$ 
ganjafreak@ganjafreak-desktop:~$ ganjaf
ganjaf: command not found
ganjafreak@ganjafreak-desktop:~$ 


And what you were talking about it being a usb I have a wireless usb device plugged in getting my internet a SMC card is that it.

---

### Post by Dude-PWB- on 2009-11-19
Yeah, we need to know what your wireless device is before we can look for or direct you towards drivers for it. Wireless is your problem right? Not your ethernet?

All we need is your wireless info, if that's what your problem is?

---

### Post by Ganjafreak on 2009-11-19
K I have AT&T and it comes with phone and Wireless internet it's all working at the moment and I'm using my SMC wireless card plugged into the front of my pc into a usb hole
and it's getting wireless from my AT&T modem

---

