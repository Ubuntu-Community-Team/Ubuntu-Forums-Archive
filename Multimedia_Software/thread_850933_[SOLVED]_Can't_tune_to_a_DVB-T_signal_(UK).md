---
title: "[SOLVED] Can't tune to a DVB-T signal (UK)"
date: 2008-07-06
forum: Multimedia Software
---

### Post by john.ennew on 2008-07-06
Hi,

I recently installed a Hauppauge Nova-T 500 PCI DVB-T TV Tuner card but it won't find any TV channels. I was wondering if anyone could give me any advice as to how to diagnose whether the problem is with my setup or arial or if the card has a fault. My local transmitter is Dover (Kent, UK)

I set the card up as per the Nova-T 500 instructions on the MythTV wiki:
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

I've tried the following commands:

```

dmesg | grep -i dvb

[ 2639.808668] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[ 2639.860406] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[ 2640.674141] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[ 2640.674219] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2640.674641] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[ 2640.806913] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[ 2641.310535] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2641.311011] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[ 2641.320897] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[ 2641.926229] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:02:05.2/usb10/10-1/input/input9
[ 2641.966689] dvb-usb: schedule remote query interval to 150 msecs.
[ 2641.966703] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.


```

My local transmitter is Dover:

```

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Dover > ~/channels.conf

scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Dover
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 850000000 0 3 9 1 0 0 0
initial transponder 794000000 0 2 9 3 0 0 0
initial transponder 746000000 0 2 9 3 0 0 0
initial transponder 770000000 0 3 9 1 0 0 0
initial transponder 762000000 0 3 9 1 0 0 0
initial transponder 786000000 0 3 9 1 0 0 0
>>> tune to: 850000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 850000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 794000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!

 ...

ANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

I also installed dvbsnoop and tried a PID scan. It sits scanning for about 3 minutes then drops back to the command prompt with no results:

```

dvbsnoop -s pidscan
dvbsnoop V1.4.50 -- http://dvbsnoop.sourceforge.net/ 

---------------------------------------------------------
Transponder PID-Scan...
---------------------------------------------------------

```

Any help greatly appreciated!

Thanks,
John

---

### Post by xc3RnbFO8P on 2008-07-06
I see in /usr/share/doc/dvb-utils/examples/scan/dvb-t,
there is **uk-Dover** and **uk-DoverB**.
Does it change anything if try to scan **uk-DoverB**.

---

### Post by john.ennew on 2008-07-06
Thanks for your reply. I have tried uk-DoverB and get the same result. No TV channels are found.  

I assume if the config files for Dover exist, then it is transmitting DVB-T content?!

Thanks,
John

---

### Post by xc3RnbFO8P on 2008-07-06
Can you scan channels in Kaffeine or Me-tv?

---

### Post by john.ennew on 2008-07-07
Hi Ringi, Thanks for your help but it looks like my ariel is pointing at the Chartham transmitter (not Dover). Chartham isn't broadcasting a DVB-T signal and I am probably too far away from the Dover one to receive it even if I moved it so it pointed at it.

---

### Post by xc3RnbFO8P on 2008-07-07
What kind of an antenna do you use?

---

### Post by john.ennew on 2008-07-07
Its on the roof of my landlord's house. I think it will be too difficult and costly to get him to realign it. Would probably then find I am too far away from the Dover transmitter.  I'll then have lost the analogue signal as well and would need to have it put back again!

Do you think a better arial might work?

---

### Post by xc3RnbFO8P on 2008-07-07
Outdoor DVB-T antenna - Compact
[IMG]http://www.av-connection.dk/Include/ShowPicture.asp?PictureID=3034&ContentType=image/jpeg[/IMG]
this antenna works if the station send
digital signal vertical or horizontal 
has a range of  0 - 10°  to catch a signal.

Outdoor DVB-T antenna - Traditionel
[IMG]http://www.av-connection.dk/Include/ShowPicture.asp?PictureID=3029&ContentType=image/jpeg[/IMG]
This antenna will only catch a signal if you point it direct
at the transmitter.

Omnidirectional TV antenna
[IMG]http://img.nauticexpo.com/images_ne/photo-p/71569.jpg[/IMG]
works 360° on the roof,
maybe what you need (needs Power inserter)

Power inserter for active DVB-T antenna
[IMG]http://www.av-connection.dk/Include/ShowPicture.asp?PictureID=3772&ContentType=image/jpeg[/IMG]
amplifies  the signal,
need power supply 5 - 12 V

---

