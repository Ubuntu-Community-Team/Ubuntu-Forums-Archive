---
title: "Help - &quot;Error: SetChannelByString(8): Failed to initialize multiplex options&quot;!"
date: 2009-05-17
forum: Multimedia Software
---

### Post by BB2008 on 2009-05-17
Hi All:

I am a newbie to mythTV. I installed a HVR-1250 in my HTPC recently.
After some effort I am able to have mythTV scan channels with this
tuner, and I see that the tuner does see all the OTA channels available
in my area as it lists them all down as found during the scan.

The problem comes when I turn the frontend on - on the same PC - and try
to watch TV. On the frontend, when I choose "Watch TV", the screen goes
black for half a second and then reverts back to the startup menu page.

I see the following entries in the backend log:

```
2009-05-17 12:40:44.182 MainServer::HandleAnnounce Playback
2009-05-17 12:40:44.185 adding: XXXXXX as a client (events: 0)
2009-05-17 12:40:44.188 TVRec(4): Changing from None to WatchingLiveTV
2009-05-17 12:40:44.196 TVRec(4): HW Tuner: 4->4
2009-05-17 12:40:44.223 DVBChan(4:0) Error: SetChannelByString(8):
Failed to initialize multiplex options
2009-05-17 12:40:44.223 TVRec(4) Error: Failed to set channel to 8.
Reverting to kState_None
2009-05-17 12:40:44.224 TVRec(4): Changing from WatchingLiveTV to None
```


I see the following entries in the frontend log:

```
2009-05-17 12:42:20.568 TV: Attempting to change from None to WatchingLiveTV
2009-05-17 12:42:20.569 Using protocol version 40
2009-05-17 12:42:21.017 GetEntryAt(-1) failed.
2009-05-17 12:42:21.018 EntryToProgram(0@Wed Dec 31 19:00:00 1969)
failed to get pginfo
2009-05-17 12:42:21.018 TV Error: LiveTV not successfully started
2009-05-17 12:42:21.019 TV Error: LiveTV not successfully started
2009-05-17 12:42:21.070 TV: Deleting TV Chain in destructor
2009-05-17 12:42:21.118 DPMS Deactivated 
2009-05-17 12:42:21.118 DPMS Reactivated.
```

Please help! I have posted the output of some relevant commands below.
Please let me know if more information is needed.

Thanks in advance!

```
uname -a
Linux XXXXXX 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686
GNU/Linux
```


```
sudo lspci -vvnn
03:00.0 Multimedia video controller [0400]: Conexant Systems, Inc.
CX23885 PCI Video and Audio Decoder [14f1:8852] (rev 03)
        Subsystem: Hauppauge computer works Inc. Device [0070:7911]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 4 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
        Capabilities: [40] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0
<2us, L1 <4us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive-
BWMgmt- ABWMgmt-
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot
+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [90] Vital Product Data <?>
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0
Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [200] Virtual Channel <?>
        Kernel driver in use: cx23885
        Kernel modules: cx23885
```

```
dmesg
[   16.069672] cx23885 driver version 0.0.2 loaded
[   16.104538] ivtv: Start initialization, version 1.4.1
[   16.155096] cx23885 0000:03:00.0: PCI INT A -> GSI 16 (level, low) ->
IRQ 16
[   16.155169] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge
WinTV-HVR1250 [card=3,autodetected]
[   16.282465] tveeprom 1-0050: Encountered bad packet header [ff].
Corrupt or not a Hauppauge eeprom.
[   16.282469] cx23885[0]: warning: unknown hauppauge model #0
[   16.282471] cx23885[0]: hauppauge eeprom: model=0
[   16.282473] cx23885_dvb_register() allocating 1 frontend(s)
[   16.282647] cx23885[0]: cx23885 based dvb card
[   16.312989] ndiswrapper: driver mrv8335 (TRENDnet,08/22/2005,3.2.1.3)
loaded
[   16.313211] ndiswrapper 0000:05:07.0: PCI INT A -> GSI 21 (level,
low) -> IRQ 21
[   16.314220] ndiswrapper: using IRQ 21
[   16.403456] MT2131: successfully identified at address 0x61
[   16.403461] DVB: registering new adapter (cx23885[0])
[   16.403464] DVB: registering adapter 0 frontend 0 (Samsung S5H1409
QAM/8VSB Frontend)...
[   16.403769] cx23885_dev_checkrevision() Hardware revision = 0xc0
[   16.403777] cx23885[0]/0: found at 0000:03:00.0, rev: 3, irq: 16,
latency: 0, mmio: 0xfd600000
[   16.403785] cx23885 0000:03:00.0: setting latency timer to 64
```

---

### Post by diurnambule on 2009-09-17
I have same problem with a NOVA-T-500 (Everything worked fine for a while but now it seems to be dead).

I also tried to reload the module (modprobe -r dvb-usb-dib0700;modprobe dvb-usb-dib0700) which show this on dmesg:
(modprobe -r)
```
[96207.832623] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully deinitialized and disconnected.
```
(modprobe)
```
[96213.037060] dib0700: loaded with support for 8 different device-types
[96213.040342] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[96213.040474] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[96213.043282] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[96213.169357] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[96213.173744] MT2060: successfully identified (IF1 = 1231)
[96213.664303] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[96213.664837] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[96213.671842] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[96213.677707] MT2060: successfully identified (IF1 = 1233)
[96214.264889] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.2/usb2/2-1/input/input5
[96214.296768] dvb-usb: schedule remote query interval to 50 msecs.
[96214.296783] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[96214.297089] usbcore: registered new interface driver dvb_usb_dib0700

```
I tried to restart mythbackend without sucess.

uname: 2.6.28-15-generic
release: Ubuntu 9.04

---

