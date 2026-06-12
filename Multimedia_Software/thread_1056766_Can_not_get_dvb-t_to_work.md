---
title: "Can not get dvb-t to work"
date: 2009-02-01
forum: Multimedia Software
---

### Post by LonelyStar on 2009-02-01
Hi,

I am trying to get my Hauppauge WinTV Nova-T to work. I installed the newest firmware, as described here:
[http://wiki.ubuntuusers.de/Hauppauge_WinTV_Nova-T_Stick#Firmwareinstallation]("http://wiki.ubuntuusers.de/Hauppauge_WinTV_Nova-T_Stick#Firmwareinstallation")

Pluggin in the device gives this in dmesg:

```
[  312.144896] firmware: requesting dvb-usb-dib0700-1.10.fw
[  312.208307] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  312.411150] dib0700: firmware started successfully.
[  312.912092] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[  312.912479] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  312.912945] DVB: registering new adapter (Hauppauge Nova-T Stick)
[  313.256407] DVB: registering frontend 0 (DiBcom 7000MA/MB/PA/PB/MC)...
[  313.261768] MT2060: successfully identified (IF1 = 1245)
[  313.747706] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb5/5-5/input/input10
[  313.788377] dvb-usb: schedule remote query interval to 150 msecs.
[  313.788387] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

```
 Looks good, I think.

Doing w_scan > channels.conf gives me this file:
```
ZDF:474000:I999B8C23D12M16T8G4Y0:T:27500:545:546=deu,547=2ch:551:0:514:8468:514:0
3sat:474000:I999B8C23D12M16T8G4Y0:T:27500:561:562=deu,563=2ch:567:0:515:8468:514:0
Doku/KiKa:474000:I999B8C23D12M16T8G4Y0:T:27500:593:594=deu:599:0:517:8468:514:0
ZDFinfokanal:474000:I999B8C23D12M16T8G4Y0:T:27500:577:578=deu:551:0:516:8468:514:0

```

This are the same channels I can get under windows.
OK, now I copy channels.conf to .mplayer/channels.conf and do
```

 mplayer dvb://3sat
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://3sat.
dvb_tune Freq: 474000
ERROR IN SETTING DMX_FILTER 8468 for fd 4: ERRNO: 22ERROR, COULDN'T SET CHANNEL  1: Failed to open dvb://3sat.


Exiting... (End of file)

```

Bad, at the end of dmesg, I now find:
```

[  887.186880] dvb_demux_feed_del: feed not in list (type=0 state=0 pid=ffff)

```

What could be wrong?

Thanks!
Nathan

---

### Post by wirbel2 on 2009-02-14
> **LonelyStar said:**
> 
Doing w_scan > channels.conf gives me this file:
```
ZDF:474000:I999B8C23D12M16T8G4Y0:T:27500:545:546=deu,547=2ch:551:0:514:8468:514:0
3sat:474000:I999B8C23D12M16T8G4Y0:T:27500:561:562=deu,563=2ch:567:0:515:8468:514:0
Doku/KiKa:474000:I999B8C23D12M16T8G4Y0:T:27500:593:594=deu:599:0:517:8468:514:0
ZDFinfokanal:474000:I999B8C23D12M16T8G4Y0:T:27500:577:578=deu:551:0:516:8468:514:0

```

This are the same channels I can get under windows.
OK, now I copy channels.conf to .mplayer/channels.conf and do
...
What could be wrong?

Thanks!
Nathan

Wouldn't it be good to use **mplayer** with a **mplayer type channels.conf**? You have choosen *VDR *(see [www.cadsoft.de/vdr](www.cadsoft.de/vdr)) channels.conf as output file type.

Please read w_scans help and rescan with correct options to get correct file type.

---

