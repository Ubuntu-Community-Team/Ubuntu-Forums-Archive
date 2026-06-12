---
title: "Master Backend Locking Up"
date: 2008-11-14
forum: Mythbuntu
---

### Post by coastalbendnetworks on 2008-11-14
My setup is 1 Master Backend with 2 dedicated frontends.

The master backend has the following hardware:

AMD Athlon XP 2500+
2 GB RAM
1 SATA 250GB HDD
1 SATA 160GB HDD
1 IDE 250GB HDD
The 3 HDD's above are in an LVM volume
1 IDE 80GB HDD (OS HDD)
1 IDE DVD-ROM Drive
Cheap nVidia Graphics card
Onboard sound
nForce 2 chipset I believe
2 PVR-150 Tuner Cards
1 WinTV-Go Tuner Card

The system will completely lock up (no video or keyobard/mouse response, no VNC or SSH), but the system will still be running, as in fans and hdd's still spinning.

I'm not 100% certain, but I believe it happens when all 3 tuner cards are in use, as in the 2 150's recording and the WinTV doing LiveTV or recording.

I have tested all HDD's to not have bad sectors and not be overheating. I even got a blower to blow constantly on them just to test.

All 2G of RAM passed memtest (Ran it for 2 days straight)

I'm wondering if it could be when the WinTV kicks on with the other two going since it is a software tuner or could it be the combo of SATA & IDE drives?

I have checked the logs and there is nothing in them that would hint as to why the lockup. Once I power it down, and then back up, it works like nothing ever happened.

Also, as a side note, whenever the machine is rebooted, the tuners get detected differently than they were before and I have to redo the config in mythtv-setup. I know this has been discussed before as to how to make them use the same device name (i.e. /dev/videoX), but I could not find it in my searches.

I am willing to replace the WinTV card if that could be the culprit. I would also like to know if any of you think the combo of IDE & SATA could possibly be doing it.

TIA

Alan

---

### Post by klc5555 on 2008-11-14
> **coastalbendnetworks said:**
> My setup is 1 Master Backend with 2 dedicated frontends.

The master backend has the following hardware:

AMD Athlon XP 2500+
2 GB RAM
1 SATA 250GB HDD
1 SATA 160GB HDD
1 IDE 250GB HDD
The 3 HDD's above are in an LVM volume
1 IDE 80GB HDD (OS HDD)
1 IDE DVD-ROM Drive
Cheap nVidia Graphics card
Onboard sound
nForce 2 chipset I believe
2 PVR-150 Tuner Cards
1 WinTV-Go Tuner Card

The system will completely lock up (no video or keyobard/mouse response, no VNC or SSH), but the system will still be running, as in fans and hdd's still spinning.

I'm not 100% certain, but I believe it happens when all 3 tuner cards are in use, as in the 2 150's recording and the WinTV doing LiveTV or recording.

I have tested all HDD's to not have bad sectors and not be overheating. I even got a blower to blow constantly on them just to test.

All 2G of RAM passed memtest (Ran it for 2 days straight)

I'm wondering if it could be when the WinTV kicks on with the other two going since it is a software tuner or could it be the combo of SATA & IDE drives?

I have checked the logs and there is nothing in them that would hint as to why the lockup. Once I power it down, and then back up, it works like nothing ever happened.

Also, as a side note, whenever the machine is rebooted, the tuners get detected differently than they were before and I have to redo the config in mythtv-setup. I know this has been discussed before as to how to make them use the same device name (i.e. /dev/videoX), but I could not find it in my searches.

I am willing to replace the WinTV card if that could be the culprit. I would also like to know if any of you think the combo of IDE & SATA could possibly be doing it.

TIA

Alan

Rather than checking the HDDs for overheating, I'd be more inclined to wonder whether the notoriously hot-running AMD processor was overheating under the load of all three cards running with/without livetv. I have a remote frontend machine running a similar AMD Athlon XP processor and a NVidia 6200 that exhibits the same symptoms with no tuners at all, usually while watching livetv from the master backend.

A quick reset to the hardware setup screen usually shows that the processor temp has shot up to about 120 degrees C, whereas the Athlon XP processor is not ever supposed to be run over 95 C. No combination of CPU coolers and case fans (in two different cases) has ever been able to keep this thing running to the temperature specs, which is why I'm in the midst of assembling an Intel box to replace it with.

Another possibility is a hardware conflict lockup requiring a hard reset. If replacing the WinTV card solves the lockups, then you've found it. If it only happens during livetv, then your video card is the more likely culprit. Some NVidia models are  reputed to be more prone to lockups than others; but I'm not familiar with your particular one.

I've never heard of the combining of SATA and EIDE drives in the same machine ever causing any problems of any sort, let alone this sort --I think the disks can be safely dismissed as "persons of interest" in this case.

Good luck!

---

### Post by coastalbendnetworks on 2008-11-14
I greatly appreciate the quick reply and your experience with a similar issue.

I will definitely check the processor temp the next time it locks up, though it seems strange to me that it would work perfectly fine for days at a time immediately after it locks up. Then again, sometimes it will be locked up for a while before anyone notices or can reset it. Especially if it happens while at work. Maybe it has the time to cool off.

This machine did used to get hot before I changed the heatsink/fan combo with a larger one. After that, I had it running as a combo email web server for over year with about 10 fairly heavily bombarded email domains and never locked up once. I do understand that MythTV is using more resources (Processor, memory, I/O) than what it did as a web/email/SQL server.

Anyway, I will report if removing the card seems to help.

I think when I get home I am going to force all tuners to record simultaneously and see what happens.

---

