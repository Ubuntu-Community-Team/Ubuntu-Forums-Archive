---
title: "Very very slow transfer speeds between Windows 7 and samba server running on Ubuntu 1"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by kasunt on 2012-08-21
Hi guys,

As mentioned in the title I tried transferring files between Windows 7 and the samba server running on both Ubuntu 11.10 and 12.04 but both showed very slow transfer speeds.

Can someone please guide me in the right direction to debug this problem ?

```
wget  --output-document=/dev/null http://tokyo1.linode.com/100MB-tokyo.bin
--2012-08-21 22:02:17--  http://tokyo1.linode.com/100MB-tokyo.bin
Resolving tokyo1.linode.com (tokyo1.linode.com)... 106.187.33.12
Connecting to tokyo1.linode.com (tokyo1.linode.com)|106.187.33.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 104857600 (100M) [application/octet-stream]
Saving to: `/dev/null'

 8% [=============>                                                                                                                                                       ] 8,923,980   64.8K/s  eta 15m 0s


wlan0     IEEE 802.11abgn  ESSID:"TNET"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 58:6D:8F:26:20:7A
          Bit Rate=117 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:101  Invalid misc:2448   Missed beacon:0


03:00.0 Network controller: Atheros Communications Inc. AR9300 Wireless LAN adaptor (rev 01)
        Subsystem: Atheros Communications Inc. Device 3112
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=128K]
        Expansion ROM at fea20000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
                Address: 0000000000000000  Data: 0000
                Masking: 00000000  Pending: 00000000
        Capabilities: [70] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <1us, L1 <8us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <64us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Not Supported, TimeoutDis+
                DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
                CEMsk:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
        Capabilities: [140 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=01
                        Status: NegoPending- InProgress-
        Capabilities: [300 v1] Device Serial Number 00-00-00-00-00-00-00-00
        Kernel driver in use: ath9k
        Kernel modules: ath9k
```

---

### Post by kasunt on 2012-08-21
I may have fixed it just by taking few simple steps.

First and foremost installed the latest compat-wireless drivers, and then made few changes in the samba configuration to improve the transfer rate. Its a definite case of having a buggy driver....I was able to verify by downloading files. Download rates were up 1.0+ MB/s after installing the latest drivers.

To download and installing the latest driver,

```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1.tar.bz2 
tar jxvf compat-wireless-3.5.1-1.tar.bz2; cd compat-wireless-3.5.1-1
```

Compiling the driver:

```
./scripts/driver-select ath9k
make
sudo make install
```

Made the following changes to the samba configuration,

```
[global]
   max protocol = NT1
   socket options = TCP_NODELAY
```

The samba transfer rates were up 1.0 MB/s as well. Let me know if this helps with your problems too ;)

---

### Post by redmk2 on 2012-08-21
> **kasunt said:**
> I may have fixed it just by taking few simple steps.

First and foremost installed the latest compat-wireless drivers, and then made few changes in the samba configuration to improve the transfer rate. Its a definite case of having a buggy driver....I was able to verify by downloading files. Download rates were up 1.0+ MB/s after installing the latest drivers.

To download and installing the latest driver,

```
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1.tar.bz2 
tar jxvf compat-wireless-3.5.1-1.tar.bz2; cd compat-wireless-3.5.1-1
```

Compiling the driver:

```
./scripts/driver-select ath9k
make
sudo make install
```

Made the following changes to the samba configuration,

```
[global]
   max protocol = NT1
   socket options = TCP_NODELAY
```

The samba transfer rates were up 1.0 MB/s as well. Let me know if this helps with your problems too ;)

It must have been the driver.  The Samba settings are the defaults, see the man pages.

---

### Post by kasunt on 2012-08-21
The samba configuration entries were not there by default. So I did have to add them.

---

### Post by redmk2 on 2012-08-21
> **kasunt said:**
> The samba configuration entries were not there by default. So I did have to add them.

The defaults are there even when they are not in the smb.conf file.  If you would like to see all the parameters you can use this command from the CLI ```
testparm -v
```

To see all of the possibilities you can look at the man pages```
man smb.conf
```...or view them [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

---

