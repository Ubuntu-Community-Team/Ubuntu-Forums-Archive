---
title: "w_scan finds channels but do not create output"
date: 2009-08-12
forum: Multimedia Software
---

### Post by superdif on 2009-08-12
Hi all,
I bought an "Terratec Cinergy DT USB XS Diversity" (a dvb-t USB device) and I am trying to configure it, but I am having problems to generate the 'channels.conf'.

I am using Kubutu 9.04 64 bit with a self compiled kernal 2.6.30.4.

According to dmesg, the card is recognized:
```
[ 8353.969264] usb 2-1: new high speed USB device using ehci_hcd and address 8
[ 8354.084408] usb 2-1: configuration #1 chosen from 1 choice
[ 8354.084819] dvb-usb: found a 'Terratec Cinergy DT USB XS Diversity' in cold state, will try to load a firmware
[ 8354.084823] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[ 8354.087843] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 8354.293192] dib0700: firmware started successfully.
[ 8354.794029] dvb-usb: found a 'Terratec Cinergy DT USB XS Diversity' in warm state.
[ 8354.794078] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 8354.794280] DVB: registering new adapter (Terratec Cinergy DT USB XS Diversity)
[ 8354.993822] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[ 8355.152819] DiB0070: successfully identified
[ 8355.152824] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 8355.153007] DVB: registering new adapter (Terratec Cinergy DT USB XS Diversity)
[ 8355.291573] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[ 8355.452820] DiB0070: successfully identified
[ 8355.452900] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/input/input12
[ 8355.452945] dvb-usb: schedule remote query interval to 50 msecs.
[ 8355.452948] dvb-usb: Terratec Cinergy DT USB XS Diversity successfully initialized and connected.

```

and:

```
$ lsusb
Bus 002 Device 008: ID 0ccd:0081 TerraTec Electronic GmbH

```

If you need the output of 'lsusb -v', please find attached the file lsusb.txt.tar.gz.

In order to generate the 'channels.conf' I am using 'w_scan' (I can't use dvbscan because I don't have a tuning data file for my city in '/usr/share/dvb/dvb-t/'). I attached the file 'w_scan.txt.tar.gz' with the output of '$ w_scan -X > channels.conf'.

As you can see, it claims it has found 21 channels ("dumping lists (21 services)"), but it does not output their configuration. In theory I should get something like this (that of course it does not apply to my city):
```
zwei:562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_5_6:FEC_1_2:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:163:92:2
TSR1:562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_5_6:FEC_1_2:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:161:84:257
TSI1:562000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_5_6:FEC_1_2:QAM_16:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE:162:88:513
```

I tried to use Kaffeine, but it find no channel at all.

Any idea? Of course, ask me if you need more info.

Thank in advance.


P.S.: if it does matter I am living in Vicenza, Italy.

---

### Post by superdif on 2009-08-13
Any idea?

---

### Post by wirbel2 on 2009-08-13
On two out of three frequencies absolutely no data was delivered from the dvb card (filter timeout).

On the third frequency something was found - however probably incomplete data or non-DVB-T, may be data was lost or corrupted and silently ignored.
Whatever happened there, since neither video PID nor audio PID were found it was assumed those to be 'other services' which you didn't wanted in the output file.

It looks like bad reception for some reason.

---

### Post by superdif on 2009-08-14
> **wirbel2 said:**
> It looks like bad reception for some reason.

Thank for the reply.

Now that I think even on a conventional TV the quality of the channels is far from optimal. :(

Eventually is there a way to manually tune the channels like a conventional TV (I mean to force a program to display a frequency at a time and let me decide to save it or not)?

---

### Post by wirbel2 on 2009-08-14
You should tune your antenna instead.

---

