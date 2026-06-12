---
title: "USB DVB-T  problems..."
date: 2010-03-14
forum: Multimedia Software
---

### Post by dejang on 2010-03-14
I managed to install USB DVB-T stick af9015 as described on web. **dmesg | grep** **dvb** gives this output:

dejan@dejan-netbook:~$ dmesg | grep dvb
[   23.339573] dvb-usb: found a 'Afatech USB2.0 DVB-T Recevier' in warm state.
[   23.392090] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   23.408505] dvb-usb: Afatech USB2.0 DVB-T Recevier successfully initialized and connected.
[   23.408596] usbcore: registered new interface driver dvb_usb_af901x
dejan@dejan-netbook:~$ 

In dev/dvb/adapter0/ there are 4 files denux0, dvr0, frontend0, net0. So far everything looks good:D.

When I start w_scan the stick is also recognized, but no channels are found during the scan. Output of **w_scan**:

dejan@dejan-netbook:~$ w_scan -X -c SI > si-osrednja_multipleks_A.conf
w_scan version 20090808 (compiled for DVB API 5.0)
using settings for SLOVENIA
Country identifier SI not defined. Using defaults.
frontend_type DVB-T, channellist 4
output format czap/tzap/szap/xine
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> DVB-T "AF901X USB DVB-T": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.0
frontend AF901X USB DVB-T supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) (time: 00:02) signal ok:
    QAM_AUTO f = 177500 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
184500: (time: 00:16) (time: 00:19) signal ok:
    QAM_AUTO f = 184500 kHz I999B7C999D999T999G999Y999
Info: NIT(actual) filter timeout
191500: (time: 00:33) (time: 00:36) signal ok:
    QAM_AUTO f = 191500 kHz I999B7C999D999T999G999Y999
.......

At the end the .conf file is empty, I always get filter timeout.

I tried scanning with **kaffeine**, the stick is  recognized correctly and after scanning is started nothing is found. 

In WinXP USB stick works, on the same table and on my dual boot PC I receive 7 digital channels :evil:, but my netbook is "ubuntu only" and I do not plan to trash it with dual boot and WinXP...


Can anybody help, I run out of ideas what to do next...](*,)

---

