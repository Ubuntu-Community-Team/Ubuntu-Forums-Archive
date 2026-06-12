---
title: "Kaffeine issue / ubuntu reboots"
date: 2008-06-13
forum: Multimedia Software
---

### Post by Domas on 2008-06-13
Hi all,

I have a weird issue with Kaffeine. It works fine, but when I am watching DVB Live TV if I minimize Kaffeine, ubuntu just reboots. Everything is fine when listening mp3 or watching movies, but only when i watch tv with my asus u-3000 tuner. Anyone had similar problem? I really like it, but this thing is really anoying, any help would appreciate.

---

### Post by xc3RnbFO8P on 2008-06-13
Are you using compiz?

---

### Post by Domas on 2008-06-13
no, compiz removed. any idea?

---

### Post by xc3RnbFO8P on 2008-06-13
Just repeating myself:
> Check in Synaptic Package Manager if you got (and install if you haven't)
kdebase-bin, kdebase-bin-kde3, kdelibs4c2a,
kdelibs-data, kipi-plugins

Restart the computer

---

### Post by Domas on 2008-06-13
Thank you for help, I will try this and let u know if that worked. Thanks !

---

### Post by Domas on 2008-06-13
ok I just installed then and got an error opening TV

19:40:38: input_file: File empty: >/home/domas/DVBLive-20080613T194038.m2t<
19:40:38: xine: found input plugin  : file input plugin
19:40:37: xine: found demuxer plugin: MPEG Transport Stream demuxer
19:40:37: xine: found input plugin  : file input plugin
19:39:14: xine: found demuxer plugin: MPEG audio demux plugin
19:39:14: xine: found input plugin  : file input plugin
19:35:07: input_file: File empty: >/home/domas/DVBLive-20080613T193507.m2t<
19:35:07: xine: found input plugin  : file input plugin
19:35:05: xine: found demuxer plugin: MPEG Transport Stream demuxer
19:35:05: xine: found input plugin  : file input plugin
19:35:04: xine: found demuxer plugin: image demux plugin
19:35:04: xine: found input plugin  : file input plugin

What could be wrong?

---

### Post by xc3RnbFO8P on 2008-06-13
In Synaptic Package Manager install **kaffeine-gstreamer**
and reinstall Kaffeine.

---

### Post by Domas on 2008-06-13
I will do that now, thanks for quick reply !

---

### Post by Domas on 2008-06-13
completely removed kaffeine and installed kaffeine-gstreamer, but still the same error:
20:04:48: input_file: File empty: >/home/domas/DVBLive-20080613T200447.m2t<
20:04:48: xine: found input plugin : file input plugin
20:04:46: xine: found demuxer plugin: MPEG Transport Stream demuxer
20:04:46: xine: found input plugin : file input plugin
20:04:46: xine: found demuxer plugin: image demux plugin
20:04:46: xine: found input plugin : file input plugin

Rebooted / Rescaned channels - still no luck, the same error...

---

### Post by xc3RnbFO8P on 2008-06-13
Delete /home/domas/_.kde_/share/apps/**kaffeine folder**
restart the computer
Reinstall Kaffeine
start Kaffeine
scan channels

---

### Post by Domas on 2008-06-13
did that, but know luck, the same error :( any other idea? appreciate for help.

---

### Post by xc3RnbFO8P on 2008-06-13
Kaffeine is trying to open this file **DVBLive-20080613T194038.m2t**
check Trash and restore it, if it is there.

---

### Post by Domas on 2008-06-13
Its not there, but Kaffeine is allways tryes to open different file (when i double click on the channel) for eg. now error msg : 

21:47:31: input_file: File empty: >/home/domas/DVBLive-20080613T214731.m2t<

after the error msg I got a file in my home/domas folder DVBLive-20080613T214731.m2t

But next time I try to open channel it gives error msg and creates another file.

The file tipe it creates: MPEG video

---

### Post by xc3RnbFO8P on 2008-06-13
Its very strange,
like a bad install of Hardy Heron.
Did you check md5 sum of the download iso?
Did you check CD for errors?

Do you dual boot?
Did you defrag Windows partition and check it for errors?

---

### Post by Domas on 2008-06-13
Hardy CD had no errors after checking. I have dual boot, but I dont understand why it could be the issue? tv worked ok, but only when I install previous packages..very strange

---

### Post by xc3RnbFO8P on 2008-06-13
Start Kaffeine in Terminal:
> kaffeine
and show the output after you have chose the channel.

---

### Post by Domas on 2008-06-13
domas@aspire:~$ kaffeine
kbuildsycoca running...
/dev/dvb/adapter0/frontend0 : opened ( DiBcom 7000PC )
0 EPG plugins loaded for device 0:0.
Loaded epg data : 0 events (0 msecs)
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
domas@aspire:~$ Tuning to: RTE 1 / autocount: 0
DvbCam::probe(): /dev/dvb/adapter0/ca0: : No such file or directory
Using DVB device 0:0 "DiBcom 7000PC"
tuning DVB-T to 738000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
. LOCKED.
NOUT: 1
dvbEvents 0:0 started
Tuning delay: 657 ms
pipe opened
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
xine pipe opened /home/domas/.kaxtv.ts
out pipe closed
Asked to stop
Live stopped
dvbstream::run() end
dvbEvents 0:0 ended
fdDvr closed
Frontend closed
domas@aspire:~$

---

### Post by Domas on 2008-06-13
just checked again if my tuner is working properly:

domas@aspire:~$ ls -l /dev/dvb/
total 0
drwxr-xr-x 2 root root 120 2008-06-13 22:23 adapter0
domas@aspire:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-06-13 22:23 demux0
crw-rw----+ 1 root video 212, 5 2008-06-13 22:23 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-13 22:23 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-13 22:23 net0
domas@aspire:~$ dmesg | grep dvb
[  117.411265] dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in cold state, will try to load a firmware
[  117.476530] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[  118.186421] dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in warm state.
[  118.186479] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  118.656239] dvb-usb: ASUS My Cinema U3000 Mini DVBT Tuner successfully initialized and connected.
[  118.656520] usbcore: registered new interface driver dvb_usb_dib0700
domas@aspire:~$

---

### Post by Domas on 2008-06-14
Anyone?

---

