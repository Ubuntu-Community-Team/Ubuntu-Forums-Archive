---
title: "TwinhanDTV Alpha tv card (usb), doesn't work =("
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by kimara on 2006-12-05
Hi

I bought today TwinhanDTV Alpha tv card and I cannot get it to work.

```
kimmo@ob:~$ dmesg | grep dvb
[17179589.556000] dvb-usb: found a 'Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)' in warm state.
[17179589.816000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17179589.948000] dvb-usb: MAC address: 08:ca:00:00:00:ff
[17179589.972000] dvb-usb: schedule remote query interval to 400 msecs.
[17179590.132000] dvb-usb: Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II) successfully initialized and connected.
[17179590.132000] usbcore: registered new driver dvb_usb_vp7045

```

```
kimmo@ob:~$ lsusb
Bus 002 Device 002: ID 13d3:3206 IMC Networks 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04a9:1056 Canon, Inc. BJC-2110 Color Printer
Bus 001 Device 001: ID 0000:0000  

```
It is that IMC Networks device

```
kimmo@ob:~$ lsmod | grep dvb
dvb_usb_vp7045         10884  2 
dvb_usb                25996  1 dvb_usb_vp7045
dvb_core               85160  1 dvb_usb
dvb_pll                15620  1 dvb_usb
i2c_core               23424  5 i2c_ec,dvb_usb,nvidia,dvb_pll,i2c_nforce2
usbcore               134912  6 dvb_usb_vp7045,dvb_usb,usblp,ehci_hcd,ohci_hcd

```

When I try to search channels in Kaffeine it give me this.

```
Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Using DVB device 0:0 "Twinhan VP7045/46 USB DVB-T"
tuning DVB-T to 898167000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4

```

and I installed v4l-dvb, using this guide [http://www.linuxtv.org/wiki/index.php/How_to_install_DVB]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB") and dvb-utils..

and scan give me this.
```
kimmo@ob:~$ scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Lahti
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Lahti
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 570000000 0 2 9 3 1 2 0
initial transponder 682000000 0 2 9 3 1 2 0
initial transponder 762000000 0 2 9 3 1 2 0
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 570000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 682000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 682000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 762000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 762000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Card work with windows xp..

Thank you

---

### Post by kimara on 2006-12-06
There is 7045 version which work with linux and 7045A version which I have.

Does anyone know, will it work with in linux..

---

### Post by josesanders on 2006-12-06
Have you seen this:
[http://www.flamingspork.com/blog/2006/09/05/twinhan-usb-dtv-dongle-not-working/](http://www.flamingspork.com/blog/2006/09/05/twinhan-usb-dtv-dongle-not-working/)

In the comments to that page, someone suggests using dvbscan to create a channel config file.  I've never done this before, but here is a link to some more info:

[http://www.mythtv.org/wiki/index.php/Dvbscan](http://www.mythtv.org/wiki/index.php/Dvbscan)

---

### Post by kirini on 2007-01-04
Is there knowledge is driver/firmware coming to this new 7045A device?
I have same problem kaffeine detects device ok, but channels are not found.
I have not tried that myth scan thing.

is module detected ok if it says dvb_usb_vp7045? should it say 7045A if device is 7045A

---

### Post by dudeskeeroo on 2007-01-11
I am having the same problems *sigh*

I tried the scan method (mentioned by josesanders) to program the channels into a Twinhan USB card ('Twinhan USB2.0 DVB-T receiver (TwinhanDTV Alpha/MagicBox II)') but could not get a signal to lock on.

Here is the output of tzap on the USB tuner:

```
potato@puppymyth:~$ tzap -a 1  "TEN Digital"
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
tuning to 219500000 Hz
video pid 0x0200, audio pid 0x028a
status 02 | signal ffff | snr 9898 | ber 00980098 | unc 00009800 |
status 02 | signal ffff | snr 9898 | ber 00980098 | unc 00009800 |
*snip...goes forever*

```

Compare with a PCI tuner doing the same thing:

```
potato@puppymyth:~$ tzap -a 0  "TEN Digital"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 219500000 Hz
video pid 0x0200, audio pid 0x028a
status 00 | signal 0000 | snr 0000 | ber b7e854fc | unc b7e7fff8 |
status 1f | signal 5f00 | snr 5a00 | ber b7e854fc | unc b7e7fff8 | FE_HAS_LOCK
```

Does anyone have any other ideas?

Cheers.

---

