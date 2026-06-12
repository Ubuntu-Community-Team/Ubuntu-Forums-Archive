---
title: "Please tell me the meaning of &quot;kernel modules: atl1c&quot; from lspci"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Tmora on 2010-01-24
I removed a module, atl1c, by modprobe -r.
 I checked it by lsmod command.
But I still got lines by lspci command,
  "Ethernet controller [0200] : Attansic Technology Corp. Device [1969: 1063] (rev c0)"
  "kernel modules: atl1c"
What is the meaning of the second line?
Is My ethernet controller still using the module I removed?
If anyone knows the meaning of the output of lspci above, please tell me.
Thank  you.

---

### Post by chili555 on 2010-01-25
It means exactly what you are afraid it means. The ethernet card is using *atl1c* as its driver. If you want to stop it, you can blacklist it.```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
atl1c
```Proofread, save and close. Unload the old module and add the new one:```
sudo rmmod -f atl1c
sudo modprobe atl1whatever
```Upon boot, *atl1c* should be safely locked in prison.

---

### Post by Tmora on 2010-01-25
Thank you for response.
I did what you instructed. And I checked modules loaded by modlist | grep atl1c.
I confirmed that atl1c is not loaded but lspci still returns,
   "kernel modules: atl1c"
It is too difficult for me.
So I decided I stop trying connect Ether card to the network for a while.

Thank you very much.

---

### Post by chili555 on 2010-01-25
What does this tell us?```
lsmod | grep atl
```Let it be difficult for me. I have broad shoulders; I can hack it!

---

### Post by Tmora on 2010-01-25
Sorry I miss it.
It was
 lsmod | grep atl1c
Sorry again.
What I wanted to say is I checked modules loaded by the command (and also I checked by my eyes.)

---

### Post by chili555 on 2010-01-25
```
lsmod | grep atl
```This will tell us which, if any, atl is loaded. After we determine that, let's take steps to be sure the one you want is loaded and that *atl1c* is blacklisted.

---

### Post by Tmora on 2010-01-25
(1) I tried lsmod | grep atl . and I got
atl1e   61784    0
After the first posting I tried to install the new driver.
atl1e is the latest driver.
After installing atl1e, output from lspci -vv gave me different lines
  "Kernel modules: atl1c, atl1e"

Thank you very much for giving me informations.

(2) The following is a part of output from lspci -vv command.
07:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
    Subsystem: Toshiba America Info Systems Device ff50
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at be000000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 3000 [size=128]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [58] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
            ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [6c] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [180] Device Serial Number ff-9e-26-00-2c-4f-b4-ff
    Kernel modules: atl1c, atl1e

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8152
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at 4000 [size=256]
    Region 1: Memory at be100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci

(3)Here is my linux version from uname -a.
Linux **** 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

It's 32 bit version(because too many troubles, I abandoned 64bit version).

---

### Post by Tmora on 2010-01-25
I got the error message by dmesg | grep rtl819xSE

[11433.056084] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
[11433.061438] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
[11433.066739] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)
[11493.054086] rtl819xSE:FW_STATUS_LOAD_IMEM FAIL CPU, Status=0
[11493.059445] rtl819xSE:FW_STATUS_LOAD_EMEM FAIL CPU, Status=0
[11493.064756] rtl819xSE:Polling  DMEM code done fail ! CPUStatus(0x0)

I googled the status, but I could not understand what these error mean.
If someone know it, please tell me.

Thank you.

---

### Post by Tmora on 2010-01-25
Sorry, the error message above seems to be related to wireless card.
This means this error message is not related to the topic of this posting.
Sorry it seems I got another problem.
Thank you.

---

### Post by chili555 on 2010-01-26
> I tried lsmod | grep atl . and I got
atl1[COLOR="Red"]e[/COLOR] 61784 0Good! It means the driver you want *is* loaded! So, if you plug an ethernet cable into the computer, does the wired ethernet work? If not, please post:```
dmesg | grep eth
```Thanks.

---

### Post by Tmora on 2010-01-26
I am reintalling Kubuntu now.
So it may take one day to replay your instruction.
Thank you and sorry for late response.

---

### Post by Tmora on 2010-01-27
I tried wired network after I connected network cable to my laptop PC.
But it could not work. I took this procedure before I reintall kubuntu 9.10

For some reasens, I cannot use wired and wireless network and I could not use eclipse with cdt on kubuntu 9.10, 
I decided to use kubuntu 9.04.
I can use wired network kubuntu 9.04 and eclipse cdt.
kubuntu 9.10 may be too new for my laptop pc.

Thank you for your kind supports.

---

