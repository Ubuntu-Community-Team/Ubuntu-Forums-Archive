---
title: "cinergy t usb xe"
date: 2010-10-08
forum: Multimedia Software
---

### Post by Elvis99 on 2010-10-08
hi everybody,

I'm trying to watch dvb-t on my netbook with ubuntu 10.04; when I plug in the card, dmesg | grep gives me the following output

```

[  114.447216] dvb-usb: found a 'TerraTec Cinergy T USB XE' in cold state, will try to load a firmware
[  114.447247] usb 5-2: firmware: requesting af9005.fw
[  114.558584] dvb-usb: downloading firmware from file 'af9005.fw'
[  114.905262] dvb-usb: found a 'TerraTec Cinergy T USB XE' in warm state.
[  114.908712] dvb-usb: will use the device's hardware PID filter (table count: 32).
[  114.909345] DVB: registering new adapter (TerraTec Cinergy T USB XE)
[  114.922404] DVB: registering adapter 0 frontend 0 (AF9005 USB DVB-T)...
[  114.924466] dvb-usb: TerraTec Cinergy T USB XE successfully initialized and connected.
[  114.924569] usbcore: registered new interface driver dvb_usb_af9005
[  175.165627] MT2060: successfully identified (IF1 = 1228)

```

So I think it's safe to say that the system recognizes the stick. When I run a channel search via kaffeine, the stick lights up with a blue led and searches, but finds nothing. Then, suddenly it claims "no available device found" and refuses to scan.

Sometimes the "lsusb" command isn't recognized after this error message, and I have to reboot to get the command "lsusb" working again .. 

Has anyone any ideas how to get this §$%& thingy working? 

Thanks in advance!

---

