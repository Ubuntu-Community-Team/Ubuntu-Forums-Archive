---
title: "USB DVB-S2 adapters: Technotrend S2-3600 and PCTV DVB-S2 (460e) not working"
date: 2012-03-31
forum: Mythbuntu
---

### Post by mcc1975 on 2012-03-31
Dear all

I did check all possible resources before coming to the forum, so I hope you all can still help me.

I had a running Mythbuntu 11.10 system running with 2 PCI DVB-S(2) adapters + a USB DVB-T adapter. This system stopped working 5 days ago (seems MB is damaged).

As this system was quite loud for the living room, I've decided to replace it with a ultra-slim Zotac Zbox ID70 Plus and two new USB DVB-S2 adapters. Mythbuntu Version: 11.10, Mythtv version: 0.24.0+fixes.20110908.

I've tried them separately:
* PCTV adapter was recognised out of the box. Any kind of channel scanning (kaffeine, mythtv-setup) has failed
* the S2-3600 wasn't recognised but after following the steps in [http://wiki.ubuntuusers.de/v4l-dvb#DVB-S2]("http://wiki.ubuntuusers.de/v4l-dvb#DVB-S2"), I was able to (sometimes) scan for channels and generally make it work. This is completely random behaviour as it somtimes will work, most of the time it will show "Frontend-ID: could not get card info..." and "Subtype: unknown error"
* the WinTV Nova-T Stick 3 (DVB-T) is the most reliable, almost always working as it used to.

If I connect all of them to the system, I always get the "Frontend-ID: Could not get card info:.." error for the WinTV Nova-T and the S2-3600, the PCTV 460e always shows up correctly. If I only connect the S2-3600 and the Nova-T adapter, I (once only) managed to have them both working. This is not reproduceable, however.

I've followed some postings for the PCTV 460e and for the S2-3600 but I never get to have them all working. In fact, it's hard to have even only the S2-3600 working.

My dmesg output for the devices:
S2-3600:
> [   15.978857] dvb-usb: found a 'Technotrend TT Connect S2-3600' in warm state.
[   20.971789] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   25.964161] DVB: registering new adapter (Technotrend TT Connect S2-3600)
[   25.967488] dvb-usb: MAC address: 00:d0:5c:0b:94:bb
[   26.038832] DVB: registering adapter 0 frontend 0 (STB0899 Multistandard)...

[   36.088554] dvb-usb: schedule remote query interval to 100 msecs.
[   36.088561] dvb-usb: Technotrend TT Connect S2-3600 successfully initialized and connected.

WinTV Nova DVB-T-stick:
> [  263.878596] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[  263.881147] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[  264.586638] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[  264.586706] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  264.586802] DVB: registering new adapter (Hauppauge Nova-T Stick)
[  264.805411] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...

[  265.046329] dvb-usb: schedule remote query interval to 50 msecs.
[  265.046335] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

PCTV DVB-S2 (460e):
> [ 5486.479953] em28xx: DVB interface 0 found
[ 5486.813814] em28xx #0: Identified as PCTV DVB-S2 Stick (460e) (card=80)
[ 5486.924880] DVB: registering new adapter (em28xx #0)
[ 5486.924884] DVB: registering adapter 2 frontend 0 (NXP TDA10071)...
[ 5486.925209] em28xx #0: Successfully loaded em28xx-dvb
[ 5486.925212] Em28xx: Initialized (Em28xx dvb Extension) extension

They all seem to initialise correctly. I guess I might have made things more difficult by switching the USB adapters (sometimes the S2-3600 shows as adapter0, sometimes as adapter1 or adapter2).

It might help to make them work reliably one by one.

Any help is very welcomed.

BR, Marcio

---

