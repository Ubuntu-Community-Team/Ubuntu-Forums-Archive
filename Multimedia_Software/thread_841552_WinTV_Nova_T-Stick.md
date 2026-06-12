---
title: "WinTV Nova T-Stick"
date: 2008-06-26
forum: Multimedia Software
---

### Post by strongboww on 2008-06-26
hey,
does anyone know to to get this bloody thing working?

obviously it is recognized by ubuntu

ls -l /dev/dvb/ shows
```

insgesamt 0
drwxr-xr-x 2 root root 120 2008-06-26 19:29 adapter0

```

ls -l /dev/dvb/adapter0 shows
```

insgesamt 0
crw-rw----+ 1 root video 212, 4 2008-06-26 19:29 demux0
crw-rw----+ 1 root video 212, 5 2008-06-26 19:29 dvr0
crw-rw----+ 1 root video 212, 3 2008-06-26 19:29 frontend0
crw-rw----+ 1 root video 212, 7 2008-06-26 19:29 net0

```

do you know what type of dvb-card you must select in mythtv?

i fixed nearly all my things since the full migration to ubuntu, but this here wont work

tia
b.

edited:
dmesg says:
```

[ 2252.869281] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 2252.927963] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[ 2253.131391] dib0700: firmware started successfully.
[ 2253.633120] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[ 2253.633182] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2253.633762] DVB: registering new adapter (Hauppauge Nova-T Stick)
[ 2253.977668] DVB: registering frontend 0 (DiBcom 7000PC)...
[ 2254.035731] MT2060: successfully identified (IF1 = 1220)
[ 2254.511509] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[ 2254.511825] usbcore: registered new interface driver dvb_usb_dib0700
[ 3278.676540] usb 3-6: USB disconnect, address 3
[ 3278.677233] mt2060 I2C write failed

```

---

