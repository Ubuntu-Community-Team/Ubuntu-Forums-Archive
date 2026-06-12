---
title: "Reading DVB -S2/T2 PCI card"
date: 2014-07-17
forum: Multimedia Software
---

### Post by Jonners59 on 2014-07-17
```
Linux mediaserver 3.13.0-30-generic
Ausus Rampage IV Extreme
Intel(R) Core(TM) i7-4820K CPU @ 3.70GHz
```

```
[   22.854748] CORE cx23885[0]: subsystem: 4254:9580, board: DVBSKY T9580 [card=48,autodetected][   23.834956] cx23885_dvb_register() allocating 1 frontend(s)
[   23.834958] cx23885[0]: cx23885 based dvb card
[   23.897344] m88ds3103_load_firmware: Waiting for firmware upload (dvb-fe-ds3103.fw)...
[   24.855965] DVB: registering new adapter (cx23885[0])
[   24.855969] cx23885 0000:05:00.0: DVB: registering adapter 0 frontend 0 (Montage DS3103/TS2022)...
[   24.883600] DVBSKY PCIe MAC= 00:17:42:54:09:82
[   24.883603] cx23885_dvb_register() allocating 1 frontend(s)
[   24.883611] cx23885[0]: cx23885 based dvb card
[   24.884445] DVB: registering new adapter (cx23885[0])
[   24.884448] cx23885 0000:05:00.0: DVB: registering adapter 1 frontend 0 (Sit2 DVB-T2/C)...
[   24.912003] DVBSKY PCIe MAC= 00:18:42:54:09:83
[   24.933861] Registered IR keymap rc-dvbsky
[   24.933893] input: cx23885 IR (DVBSKY T9580) as /devices/pci0000:00/0000:00:1c.0/0000:05:00.0/rc/rc0/input20
[   24.937470] rc0: cx23885 IR (DVBSKY T9580) as /devices/pci0000:00/0000:00:1c.0/0000:05:00.0/rc/rc0]
```

OK, that's the techie stuff out the way.

I have the above SKYDVB Tv/Satellite PCi card and am trying to get it to work on the PC "mediaserver".  I have a number of applications I am trying to use, but none detect it.
MyTv, MeTv, Plex, XBMC, Zapping Tv Viewer, Digitalk Tv, VLC, and MythTv which has been a complete waste of time, it just goes in loops and will not exit setup....

Can anyone help, please?

---

### Post by dask2 on 2014-10-27
Hi Jonners59,
i have the same card working with ubuntu 14.10, kernelversion 3.16.0-23.
i followed the guide from dvbsky.net ([http://www.dvbsky.net/download/doc/Linux_Driver_installation_en.pdf](http://www.dvbsky.net/download/doc/Linux_Driver_installation_en.pdf))
i genereated the channels.conf with w-scan (wiki.ubuntuusers.de/w_scan).

So, now you have to know, which DVB you want to use:
DVB-S is adapter0/frontend0
DVB-T is adapter1/frontend0
DVB-C is adapter1/frontend1

So you start i.e. me-tv with this parameters:
> me-tv --devices=/dev/dvb/adapter1/frontend1
The Assist starts, give him the Path to your channels.conf.

thats it,

good luck,
dask2

---

### Post by Jonners59 on 2014-11-23
Thanks Dask2
Appologies for not replying earlier.  Will take a look at this when I am allowed on the PC!!!!

Best

Jonners

---

