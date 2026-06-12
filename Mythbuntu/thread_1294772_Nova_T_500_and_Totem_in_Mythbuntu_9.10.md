---
title: "Nova T 500 and Totem in Mythbuntu 9.10"
date: 2009-10-18
forum: Mythbuntu
---

### Post by AJ1000 on 2009-10-18
I have a Nova T 500 card and have upgraded to 9.10. I have mythfrontend and mythbackend working, so I can watch TV programmes. What I cannot do is to get Totem to work with the Nova T 500 card.

The problem is that all the information about making the channels.conf file (needed by totem) does not work as karmic has dvb-apps instead of dvb-utils. 

Does anyone know the commands I should use? I am in the uk-WinterHill area.

I used the guide on [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) but 

scan /usr/share/dvb/dvb-t/uk-WinterHill > /root/.tzap/channels.conf

does not work ... I keep getting tuning failed!!!

I am a relative newbie in Linux, so any help would be appreciated.

This is what the scan command produces:
scanning /usr/share/dvb/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754167000 0 3 9 1 0 0 0
initial transponder 834167000 0 2 9 3 0 0 0
initial transponder 850167000 0 2 9 3 0 0 0
initial transponder 842167000 0 3 9 1 0 0 0
initial transponder 786167000 0 3 9 1 0 0 0
initial transponder 810167000 0 3 9 1 0 0 0
initial transponder 650000000 0 3 9 1 0 0 0
initial transponder 626000000 0 3 9 1 0 0 0
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 834167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 834167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 850167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 850167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 842167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 842167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 786167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 786167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 810167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 810167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)

I am using the 0.1 version of the firmware.

Please help.

---

### Post by AJ1000 on 2009-10-18
Additionally: This is what I get for the command 

dmesg | grep dvb-usb

[   15.973523] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   15.973533] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   16.599638] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   17.372033] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   17.372132] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.128677] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   18.719764] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.

where dvb-usb-dib0700-1.20.fw is actually the dvb-usb-dib0700-1.10.fw renamed.

Any help would be appreciated.

---

### Post by AJ1000 on 2009-10-19
Solved. I changed uk-WinterHill to uk-Storeton which appears to be the correct one for Liverpool.

[http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) tutorial now works (with mythtv-backend stopped).

However I cannot get totem to work. I get the following -

totem is missing a channels listing to be able to tune the receiver.

What are the correct locations for the 'channels.conf' file? I have tried '.gstreamer-0.10' and '.xine' folders with no success.

---

### Post by starswan on 2009-10-31
You need to put a file called dvb-channels.conf in ~/gstreamer-0.10

---

### Post by AJ1000 on 2009-10-31
Yes, I have done that but it will not work. I have, however, got meTv and kaffeine working with the Nova T 500 so I am giving up on totem and not worrying about it.

---

### Post by bugritall on 2009-11-01
I have had a similar problem with Totem accepting my chans.conf file in Karmic. 

I used wscan to create "chans.conf" in Jaunty and then I supplied it - under different names - to both Totem and Xine and everything worked nicely. In Karmic, however, the file is only recognised by Xine and not by Totem.

---

### Post by AJ1000 on 2009-11-02
Thanks, I tried that and it did not work for me.

---

