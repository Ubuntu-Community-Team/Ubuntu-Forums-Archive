---
title: "Firewire STB"
date: 2011-12-26
forum: Mythbuntu
---

### Post by nightwar on 2011-12-26
I just got a samsung hd box, the model is smt-h3262 on the unit itself. Mythtv recognizes it as a Samsung SMTH3270

the scan for channels is greyed out, and its not picking a channel to start on.. Ive read alot of stuff, i think i am missing something..  any advice?



lspci:
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]

dmesg|grep irewire
    1.772084] firewire_ohci: Added fw-ohci device 0000:06:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    2.272135] firewire_core: created device fw0: GUID 0090270001d463a3, S400
[    2.274729] firewire_core: created device fw1: GUID 0000f002cbea7b5d, S400
[ 2493.536022] firewire_core: phy config: card 0, new root=ffc0, gap_count=63
[ 2497.443691] firewire_core: skipped bus generations, destroying all nodes
[ 2497.940040] firewire_core: rediscovered device fw0
[ 2497.940101] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[ 2525.162545] firewire_core: skipped bus generations, destroying all nodes
[ 2525.660038] firewire_core: rediscovered device fw0
[ 2525.662466] firewire_core: created device fw1: GUID 0000f002cbea7b5d, S400




plugreport:
plugreport
Host Adapter 0
==============

Node 0 GUID 0x0000f002cbea7b5d
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=0, bcast_connection=0, n_p2p_connections=0
        channel=63, data_rate=2, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x0090270001d463a3
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR




Mythtv config:  

Cable Box Model: Generic 
Connection type: Point to Point
Speed: 100 Mbps

---

