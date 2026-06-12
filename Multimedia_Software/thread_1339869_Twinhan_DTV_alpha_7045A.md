---
title: "Twinhan DTV alpha 7045A"
date: 2009-11-28
forum: Multimedia Software
---

### Post by mr_skater99 on 2009-11-28
Hi All,

I can't get this digital tv tuner to work - although i think i am close.

So far i have installed linux-firmware-nonfree

Then when i plug in the tuner it's recognized: (/var/log/messages)

Nov 28 16:03:53 photon kernel: [ 3652.431271] usb 2-5: new high speed USB device using ehci_hcd and address 15
Nov 28 16:03:53 photon kernel: [ 3652.580472] usb 2-5: configuration #1 chosen from 1 choice
Nov 28 16:03:53 photon kernel: [ 3652.580678] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in cold state, will try to load a firmware
Nov 28 16:03:53 photon kernel: [ 3652.580683] usb 2-5: firmware: requesting dvb-usb-vp7045-01.fw
Nov 28 16:03:53 photon kernel: [ 3652.587135] dvb-usb: downloading firmware from file 'dvb-usb-vp7045-01.fw'
Nov 28 16:03:53 photon kernel: [ 3652.653392] usb 2-5: USB disconnect, address 15
Nov 28 16:03:53 photon kernel: [ 3652.670054] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
Nov 28 16:03:55 photon kernel: [ 3654.440016] usb 2-5: new high speed USB device using ehci_hcd and address 16
Nov 28 16:03:55 photon kernel: [ 3654.592635] usb 2-5: configuration #1 chosen from 1 choice
Nov 28 16:03:55 photon kernel: [ 3654.593090] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in warm state.
Nov 28 16:03:55 photon kernel: [ 3654.750198] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Nov 28 16:03:55 photon kernel: [ 3654.750447] DVB: registering new adapter (Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II))
Nov 28 16:03:56 photon kernel: [ 3654.870196] dvb-usb: MAC address: 08:ca:00:00:00:ff
Nov 28 16:03:56 photon kernel: [ 3654.901451] DVB: registering adapter 0 frontend 0 (Twinhan VP7045/46 USB DVB-T)...
Nov 28 16:03:56 photon kernel: [ 3654.901569] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/input/input9
Nov 28 16:03:56 photon kernel: [ 3654.901595] dvb-usb: schedule remote query interval to 400 msecs.
Nov 28 16:03:56 photon kernel: [ 3655.070223] dvb-usb: Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II) successfully initialized and connected.


Then if i run up femon:

$ femon -H
FE: Twinhan VP7045/46 USB DVB-T (DVBT)
status SCVYL | signal   0% | snr 100% | ber 16777215 | unc 65535 | FE_HAS_LOCK
status SCVYL | signal   0% | snr 100% | ber 16777215 | unc 65535 | FE_HAS_LOCK
status SCVYL | signal   0% | snr 100% | ber 16777215 | unc 65535 | FE_HAS_LOCK
status SCVYL | signal   0% | snr 100% | ber 16777215 | unc 65535 | FE_HAS_LOCK

And this continues until i run scan /usr/share/dvb/dvb-t/au-Brisbane, then femon changes to:

status  CVYL | signal 100% | snr  47% | ber 7995514 | unc 31232 | FE_HAS_LOCK
status  CVYL | signal 100% | snr  47% | ber 7995514 | unc 31232 | FE_HAS_LOCK


and scan outputs the following:

$ scan /usr/share/dvb/dvb-t/au-Brisbane
scanning /usr/share/dvb/dvb-t/au-Brisbane
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 3 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 585625000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.


I've tried this on several aerials (including the roof one that we watch all our HDTV on with the STB in the lounge) and the same results - a slightly different SnR (47-50%).

The remote works perfectly (volume up/down power off etc).  If i open Me TV and use a channels.conf that i found on the net for Brisbane - it just freezes for a bit - then fails with a "timeout while reading"

Any suggestions?

Seems like i am close.....

---

