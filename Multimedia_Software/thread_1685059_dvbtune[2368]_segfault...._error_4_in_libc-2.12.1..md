---
title: "dvbtune[2368]: segfault.... error 4 in libc-2.12.1.so"
date: 2011-02-10
forum: Multimedia Software
---

### Post by Dooa on 2011-02-10
Hi All, 
I've hit a bick wall, hope you can give me some tips.

I  installed a ebay USB DVBT stick on Ubuntu 10 Maverick 64 bit. USB stick works ok on Vista.

Mythtv or Kaffine can not tune the stick. 
I am no way a Linux expert but got following ,hope one of you know what I should do next.
Thanks
Dooha

----------------------------------------------------------------------------------------------
xbmc@xbmc-H55M-UD2H:~$ scan /usr/share/dvb/dvb-t/au-Melbourne
scanning /usr/share/dvb/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
xbmc@xbmc-H55M-UD2H:~$ 

-------------------------------------------------------------------------------------------------------
xbmc@xbmc-H55M-UD2H:~$ grep -i dvb /var/log/messages
Feb  6 20:35:07 xbmc-H55M-UD2H kernel: [20449.904016] usbcore: registered new interface driver dvb_usb_ec168
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.151602] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in cold state, will try to load a firmware
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.153876] dvb-usb: downloading firmware from file 'dvb-usb-ec168.fw'
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.309688] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in warm state.
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.309751] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.309944] DVB: registering new adapter (E3C EC168 DVB-T USB2.0 reference design)
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.331101] DVB: registering adapter 0 frontend 0 (E3C EC100 DVB-T)...
Feb  6 20:35:22 xbmc-H55M-UD2H kernel: [20465.331368] dvb-usb: E3C EC168 DVB-T USB2.0 reference design successfully initialized and connected.
Feb  6 20:38:34 xbmc-H55M-UD2H kernel: [20656.059107] dvb-usb: E3C EC168 DVB-T USB2.0 reference design successfully deinitialized and disconnected.
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20665.851768] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in cold state, will try to load a firmware
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20665.853715] dvb-usb: downloading firmware from file 'dvb-usb-ec168.fw'
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20666.022899] dvb-usb: found a 'E3C EC168 DVB-T USB2.0 reference design' in warm state.
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20666.022966] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20666.023131] DVB: registering new adapter (E3C EC168 DVB-T USB2.0 reference design)
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20666.052565] DVB: registering adapter 0 frontend 0 (E3C EC100 DVB-T)...
Feb  6 20:38:44 xbmc-H55M-UD2H kernel: [20666.052815] dvb-usb: E3C EC168 DVB-T USB2.0 reference design successfully initialized and connected.
Feb  6 21:21:52 xbmc-H55M-UD2H kernel: [ 1077.996221] dvbtune[2368]: segfault at 0 ip 00007fee224306c2 sp 00007fff4133fa90 error 4 in libc-2.12.1.so[7fee223f6000+17a000]
xbmc@xbmc-H55M-UD2H:~$ 
-----------------------------------------------------------------------------------------------------

---

