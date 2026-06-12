---
title: "Mythbuntu, FireWire &amp; Digital Tuner"
date: 2008-07-15
forum: Mythbuntu
---

### Post by CrimsonRider on 2008-07-15
Hey guys,

I've had the oppertunity, recently, to play around with a box and FloppyDTV card. Basicly an internal tuner card, that communicates via firewire. However, I can not seem to get it to work with MythTV.

This is the card; [http://www.digital-everywhere.com/en/alcms/index.php?sid=1190057723](http://www.digital-everywhere.com/en/alcms/index.php?sid=1190057723)

I can't seem to get the thing "primed", whatever that might be. I've spend many a fruitless hour mucking around with the thing, but to no avail. I cannot get any sort of communcation going with it. Also, Google, Wiki search and the likes either turn up nothing, or very old posts. So I am asking for you help. The current status is, it doesn't work, but I can detect something plugged into the FireWire card. The FireWire GUID does not show up in MythTV.

I've tinkered around quite a bit already, it's a clean system, nothing in there but Mythbuntu standard install. I've checked some Wiki entries and followed the steps, but they didn't help. I am afraid I am missing some basic ideas here. 

Here are the pages I checked already;
[http://www.mythtv.org/wiki/index.php/FireWire](http://www.mythtv.org/wiki/index.php/FireWire)

Any help would be greatly appreciated. I would hate to have to build this into a Windows based media center.

These are the specs;
FireWire; off the shelf VIA VT6306 based
```
02:11.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at dc00 [size=128]
        Capabilities: <access denied>
```

PlugReport;
```
crimson@MythTV:/usr/share/doc$ plugreport
Host Adapter 0
==============

Node 0 GUID 0x0012872602001fc0
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=0
oPCR[0] online=0, bcast_connection=0, n_p2p_connections=0
        channel=0, data_rate=1, overhead_id=0, payload=0
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x0011060000005bf2
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

```
Mythprime;
```
crimson@MythTV:/usr/share/doc$ mythprime
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
1 devices detected.  checking avc subtypes...

Priming errors encountered, trying again...
Priming Errors encountered: 0 stbs primed, 0 stbs failed to prime, 0 non-stbs ignored and 0 ghost nodes skipped on 1 ports in 3 runs.
```

---

### Post by theophile on 2008-07-16
I'm not sure this device is currently usable in Linux. The priming script is designed for set top boxes which already have an operating system installed and running. To get the FloppyDTV card to work, I believe you will need kernel-level drivers which do not exist.

I read somewhere that there is currently no CableCard compatible tuner that works in Linux.

You may be out of luck (for now).

---

