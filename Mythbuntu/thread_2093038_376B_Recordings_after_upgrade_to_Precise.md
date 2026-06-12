---
title: "376B Recordings after upgrade to Precise"
date: 2012-12-09
forum: Mythbuntu
---

### Post by thatsreal on 2012-12-09
Hi,

I recently upgraded my mythbuntu machine from Lucid to Precise. I've been using Lucid for many years and everything worked like a charm. 

However, after upgrading I got an odd problem that often scheduled recordings are not recorded probably. They are shown with a size of 376B in the frontend and won't play. The odd thing is that in some cases it works but in most cases it does not. I cannot isolate the problem to a certain channel - it appears on all channels. However, LiveTv works just fine. 

When the problem appears the mythtv-backend process hangs and can only be quit by using kill -9. 

The log says:

```

Nov 10 18:54:38 entertain mythbackend[2153]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Nov 10 18:54:39 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Nov 10 18:54:39 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 1 items in 0.1 = 0.01 match + 0.06 place
Nov 10 18:55:37 entertain mythbackend[2153]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Nov 10 18:59:45 entertain mythbackend[2153]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Nov 10 18:59:50 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Nov 10 18:59:50 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 1 items in 0.1 = 0.01 match + 0.09 place
Nov 10 19:01:49 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(1): ASK_RECORDING 1 9 0 0
Nov 10 19:01:50 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(2): ASK_RECORDING 2 9 0 0
Nov 10 19:01:50 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(3): ASK_RECORDING 3 9 0 0
Nov 10 19:01:50 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:1536 (HandlePendingRecordings) TVRec(6): ASK_RECORDING 6 9 0 0
Nov 10 19:02:00 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(3): Changing from None to RecordingOnly
Nov 10 19:02:00 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(3): HW Tuner: 3->3
Nov 10 19:02:00 entertain mythbackend[2153]: N Scheduler autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
Nov 10 19:02:00 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2514 (HandleRecordingStatusChange) Tuning recording: Galileo: channel 17403 on cardid 3, sourceid 1
Nov 10 19:02:01 entertain mythbackend[2153]: E DVBRead dtvsignalmonitor.cpp:321 (HandlePAT) DTVSM(/dev/dvb/adapter0/frontend0): Program #2 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(29) extension(0x2201)#012      version(23) current(1) section(0) last_section(0)#012      tsid(8705) programCount(5)#012  program number     0 has PID 0x0010#012  program number 16394 has PID 0x00a0#012  program number 16398 has PID 0x00e0#012  program number 16403 has PID 0x0130#012  program number 16408 has PID 0x0180
Nov 10 19:02:01 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id 0.
Nov 10 19:02:01 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 1 items in 0.1 = 0.00 match + 0.07 place
Nov 10 19:02:01 entertain mythbackend[2153]: E DVBRead mpeg/mpegstreamdata.cpp:819 (ProcessPAT) ProcessPAT: Program not found in PAT. Rescan your transports.
***Nov 10 19:02:01 entertain mythbackend[2153]: E DVBRead mpeg/mpegstreamdata.cpp:425 (CreatePATSingleProgram) Desired program #2 not found in PAT.#012#011#011#011Cannot create single program PAT.***
Nov 10 19:02:02 entertain mythbackend[2153]: I CoreContext scheduler.cpp:637 (UpdateRecStatus) Updating status for Galileo on cardid 3 (Tuning => Aufnehmen)
Nov 10 19:02:02 entertain mythbackend[2153]: I TVRecEvent tv_rec.cpp:3989 (TuningNewRecorder) TVRec(3): rec->GetPathname(): '/home/tv/17403_20121110190200.mpg'
Nov 10 19:03:03 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2033 (HandleReschedule) Reschedule requested for id -1.
Nov 10 19:03:03 entertain mythbackend[2153]: I Scheduler scheduler.cpp:2093 (HandleReschedule) Scheduled 1 items in 0.1 = 0.01 match + 0.06 place
Nov 10 19:04:46 entertain mythbackend[2153]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread

```

I am using DVB-T in Germany. My card is KNC-ONE DVB-T PCI card. 

Some info about the card:

```

root@entertain:/var/log/mythtv# lspci -v

0b:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
        Subsystem: KNC One Device 0030
        Flags: bus master, fast Back2Back, medium devsel, latency 123, IRQ 21
        Memory at f0200000 (32-bit, non-prefetchable) [size=512]
        Kernel driver in use: budget_av
        Kernel modules: budget-av
        
        
dmesg 
        
[   12.095372] saa7146: register extension 'budget_av'
[   12.095431] budget_av 0000:0b:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.095472] saa7146: found saa7146 @ mem f803c000 (revision 1, irq 21) (0x1894,0x0030)
[   12.095480] saa7146 (0): dma buffer size 192512
[   12.095484] DVB: registering new adapter (KNC1 DVB-T)
[   12.129012] adapter failed MAC signature check
[   12.129017] encoded MAC from EEPROM was ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff:ff
[   12.392399] budget_av: KNC1-0: MAC addr = 00:09:d6:6d:25:82
[   12.659664] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x085C
[   12.659704] usbcore: registered new interface driver usblp
[   13.174520] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   13.174893] budget_av: ci interface initialised


```

Mythtv version:
mythbackend version: fixes/0.25 [v0.25.2-15-g46cab93] [www.mythtv.org](www.mythtv.org)

Does anyone have an idea how to fix the problem? Any help is appreciated.

Thank you
thatsreal

---

### Post by nickrout on 2012-12-09
Your version of 0.25-fixes is quite old. Try updating via mythbuntu-repos.

---

### Post by thatsreal on 2012-12-17
Thank you very much, this helped!

Why don't they bring these updates into the normal repositorys?

---

### Post by nickrout on 2012-12-17
> **thatsreal said:**
> Thank you very much, this helped!

Why don't they bring these updates into the normal repositorys?ubuntu packages are pretty well kept at the same version for an entire release, except for security updates.

---

### Post by ian dobson on 2012-12-17
Hi,

Looks as if the tuner table (in mythTV) is incorrect. Try running myth-setup and rescan all your transports.

Regards
Ian Dobson

---

