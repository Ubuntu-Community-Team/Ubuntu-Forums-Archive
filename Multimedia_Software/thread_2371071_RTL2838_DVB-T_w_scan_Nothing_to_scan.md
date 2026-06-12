---
title: "RTL2838 DVB-T w_scan Nothing to scan"
date: 2017-09-10
forum: Multimedia Software
---

### Post by andrew772 on 2017-09-10
Hello. I have a "NooElec R820T2 SDR & DVB-T NESDR Mini 2" receiver connected via USB and connected to a television aerial socket. I have tested the connections by running gqrx which can receive radio ok (despite it being a TV antenna). But w_scan refuses to find any DVB-T channels. The following is a terminal extract of the scan attempt itself and some diagnostic information.

```

> w_scan -X -c GB                            

w_scan -X -c GB 
w_scan version 20141122 (compiled for DVB API 5.10)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
scan type TERRESTRIAL, channellist 6
output format czap/tzap/szap/xine
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
        /dev/dvb/adapter0/frontend0 -> TERRESTRIAL "Realtek RTL2832 (DVB-T)": good :-)
Using TERRESTRIAL frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.10
frontend 'Realtek RTL2832 (DVB-T)' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (174.00MHz ... 862.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning DVB-T...
Scanning 7MHz frequencies...
177500: (time: 00:00.895) 
184500: (time: 00:03.155) 
<snip>
858167: (time: 05:34.002) 
857833: (time: 05:36.178) 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

> dmesg

<snip>
[ 1596.553355] usb 3-5: new high-speed USB device number 4 using xhci_hcd
[ 1596.704983] usb 3-5: New USB device found, idVendor=0bda, idProduct=2838
[ 1596.704984] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1596.704985] usb 3-5: Product: RTL2838UHIDIR
[ 1596.704986] usb 3-5: Manufacturer: Realtek
[ 1596.704987] usb 3-5: SerialNumber: 00000001
[ 1596.711794] usb 3-5: dvb_usb_v2: found a 'Realtek RTL2832U reference design' in warm state
[ 1596.765431] usb 3-5: dvb_usb_v2: will pass the complete MPEG2 transport stream to the software demuxer
[ 1596.765448] dvbdev: DVB: registering new adapter (Realtek RTL2832U reference design)
[ 1596.765454] usb 3-5: media controller created
[ 1596.766106] dvbdev: dvb_create_media_entity: media entity 'dvb-demux' registered.
[ 1596.770047] i2c i2c-4: Added multiplexed i2c bus 5
[ 1596.770051] rtl2832 4-0010: Realtek RTL2832 successfully attached
[ 1596.770061] usb 3-5: DVB: registering adapter 0 frontend 0 (Realtek RTL2832 (DVB-T))...
[ 1596.770068] dvbdev: dvb_create_media_entity: media entity 'Realtek RTL2832 (DVB-T)' registered.
[ 1596.770234] r820t 5-001a: creating new instance
[ 1596.777074] r820t 5-001a: Rafael Micro r820t successfully identified
[ 1596.779474] rtl2832_sdr rtl2832_sdr.1.auto: Registered as swradio0
[ 1596.779476] rtl2832_sdr rtl2832_sdr.1.auto: Realtek RTL2832 SDR attached
[ 1596.779478] rtl2832_sdr rtl2832_sdr.1.auto: SDR API is still slightly experimental and functionality changes may follow
[ 1596.786527] Registered IR keymap rc-empty
[ 1596.786568] rc rc0: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.0/usb3/3-5/rc/rc0
[ 1596.786620] input: Realtek RTL2832U reference design as /devices/pci0000:00/0000:00:14.0/usb3/3-5/rc/rc0/input14
[ 1596.786903] rc rc0: lirc_dev: driver ir-lirc-codec (dvb_usb_rtl28xxu) registered at minor = 0
[ 1596.786907] usb 3-5: dvb_usb_v2: schedule remote query interval to 200 msecs
[ 1596.798823] usb 3-5: dvb_usb_v2: 'Realtek RTL2832U reference design' successfully initialized and connected

> lsusb

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:2838 Realtek Semiconductor Corp. RTL2838 DVB-T
Bus 003 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Any suggestions would be greatly appreciated!

Andrew.

---

### Post by Bucky Ball on 2017-09-10
For a simple test, you could install MeTV (in the respositories) and see what results you get running an auto-scan with that, if any. Lot easier than trying to put together a channel.conf file yourself, which I assume that is what you are trying to do.

You don't need to use MeTV after that, but at least you'll have a channel.conf.

---

### Post by andrew772 on 2017-09-11
> **Bucky Ball said:**
> For a simple test, you could install MeTV (in the respositories) and see what results you get running an auto-scan with that, if any. Lot easier than trying to put together a channel.conf file yourself, which I assume that is what you are trying to do.

You don't need to use MeTV after that, but at least you'll have a channel.conf.

Thanks for the reply. I have installed MeTV and done the auto-scan for the UK but unfortunately it's given me very similar results. I'm assuming the Gtk warning is due to me running KDE, I'm not so sure about the ibus warning but the application still opens, recognises the receiver, and runs the scan. 

```

> me-tv

Me TV 1.3.7
(me-tv:5009): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
(me-tv:5009): Gtk-WARNING **: Unable to locate theme engine in module_path: "adwaita",
11/09/17 12:16:13: Device: 'Realtek RTL2832 (DVB-T)' (DVB-T) at "/dev/dvb/adapter0/frontend0"
(me-tv:5009): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused
11/09/17 12:16:25: Frontend::tune_to(474000000)
11/09/17 12:16:25: Waiting for signal lock ...
11/09/17 12:16:27: Frontend::tune_to(482000000)
11/09/17 12:16:27: Waiting for signal lock ...
<snip>
11/09/17 12:18:25: Frontend::tune_to(842000000)
11/09/17 12:18:25: Waiting for signal lock ...
11/09/17 12:18:28: Frontend::tune_to(850000000)
11/09/17 12:18:28: Waiting for signal lock ...

```
[FONT=Verdana]
[/FONT]

---

### Post by tea for one on 2017-09-11
Good evening

> ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

I have also noticed that, occasionally, w_scan returns similar results for GB and, regrettably, I do not have any further suggestions for using w_scan.

However, I have recently installed **tvheadend** and the built-in scanner seems to recognise my DVB devices - including a device with RTL2832 internals.

The website is [https://tvheadend.org/](https://tvheadend.org/) and the software is managed by a web browser so it is distro agnostic.

The instructions for installing on Ubuntu 16.04 are here :- [https://tvheadend.org/projects/tvheadend/wiki/AptRepository](https://tvheadend.org/projects/tvheadend/wiki/AptRepository)

You can output a channel list (both DVB TV and radio sources) to use with VLC.

Tvheadend also includes a TV viewing programme and a PVR.

Best wishes

---

### Post by andrew772 on 2017-09-12
I[FONT=verdana] have installed tvheadend, it recognises the device, which is enabled under TV adapter settings, and have selected my local pre-defined muxes, but the Muxes page shows Scan statuses as "FAIL".

I have tried restarting the service using "[COLOR=#000000]/etc/init.d/tvheadend stop" and "[/COLOR][/FONT][FONT=monospace][FONT=verdana][COLOR=#000000]/etc/init.d/tvheadend start". I also need to use "[/COLOR][/FONT][/FONT][FONT=monospace][COLOR=#000000]sudo modprobe dvb-usb-rtl28xxu" for it to recognise the device at all.

[/COLOR]Any suggestions would be greatly appreciated.

EDIT: I swapped it to another USB port and reinstalled tvheadend and it seems to be scanning now. Thanks![/FONT]

---

### Post by tea for one on 2017-09-12
> **andrew772 said:**
> EDIT: I swapped it to another USB port and reinstalled tvheadend and it seems to be scanning now. Thanks!

Splendid - I hope that the scan has now found the channels.

I have also noticed other users reporting that some USB ports work on certain devices and others don't, especially when trying to boot an ISO to test drive a "live" Linux OS.

It is often a mystery.

I plug my DVB-T stick into a hub which, in turn, is constantly attached to a **rear** USB port on my desktop. I only have USB 2.00 available.

Kind regards

---

### Post by andrew772 on 2017-09-12
I have noticed there are no HD channels though. I have 8 Muxes, 3 of which are the HD frequencies and the ones that show FAIL. I have checked the frequencies are correct.

---

### Post by tea for one on 2017-09-12
> **andrew772 said:**
> I have noticed there are no HD channels though. I have 8 Muxes, 3 of which are the HD frequencies and the ones that show FAIL. I have checked the frequencies are correct.

Hello again

I think that your DVB device is SD only. 

My device with RTL2832 does not process DVB-T2 HD channels. 

Does your device have anything printed on the body?

Generally DVB-T is SD and DVB-T2 is both SD and HD.

I purchased a TechnoTrend TT-TVStick CT2-4400 USB-TV-Karte (DVB-C/T/T2 Antenne) (TT-CT-4400) earlier this year and it works pretty good. You have to download firmware.

Here are some links for further exploration:-

[http://engl.technotrend.eu/2990/TT-TVStick__CT2-4400.html](http://engl.technotrend.eu/2990/TT-TVStick__CT2-4400.html)

[https://www.dvbshop.net/TechnoTrend-TT-TVStick-CT2-4400-USB-TV-Karte-DVB-C-T-T2-Antenne](https://www.dvbshop.net/TechnoTrend-TT-TVStick-CT2-4400-USB-TV-Karte-DVB-C-T-T2-Antenne)

[https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices](https://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices)

---

### Post by Bucky Ball on 2017-09-12
Now try it with MeTV with the USB in the other socket. If MeTV didn't work to scan, usually nothing will, so perhaps nothing to do with tvheadend but the USB socket you were using.

Please confirm this by swapping the USB to the other socket and trying then to the one that is currently working.

---

### Post by andrew772 on 2017-09-13
@tea for one, It says DVB-T on it so maybe you're right, no HD, oh well!

@Bucky Ball, MeTV work now too, thanks.

Is there any way to get the EPG in CSV format?

---

