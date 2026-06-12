---
title: "&quot;dvb-t&quot;, &quot;ati radeon x300&quot;, &quot;terratec cinergy t usb xe&quot;"
date: 2009-03-01
forum: Multimedia Software
---

### Post by mate.ri on 2009-03-01
hi people, 

i need some help.

I' ve installed DVB-T usb tuner (terratec cinergy t usb xe) and judging by dmesg output it works fine.
> [ 1763.661029] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 1763.842252] usb 1-2: configuration #1 chosen from 1 choice
[ 1763.885031] dvb-usb: found a 'TerraTec Cinergy T USB XE' in cold state, will try to load a firmware
[ 1763.885045] firmware: requesting dvb-usb-af9015.fw
[ 1763.912427] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[ 1764.206049] dvb-usb: found a 'TerraTec Cinergy T USB XE' in warm state.
[ 1764.206147] dvb-usb: will use the device's hardware PID filter (table count: 32).
[ 1764.207040] DVB: registering new adapter (TerraTec Cinergy T USB XE)
[ 1764.762016] af9013: firmware version:4.95.0
[ 1764.786019] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[ 1764.795290] mc44s803: successfully identified (ID = 14)
[ 1764.799022] dvb-usb: TerraTec Cinergy T USB XE successfully initialized and connected.


Problem is that videos are completely distorted.  tried with xine, MeTv, mythtv, Totem etc.. 

Since im kind of a begginer i don't understand everything but i think that the problem might be with Ati proprietary driver. Also i don't know what do you need to help me so please be patient and I'll provide anything u ask.

tnx

---

### Post by DomNewToLinux on 2009-08-11
Not really able to help, but I was just wondering how you got the terratec USB stick to work on your system. Are you using Jaunty? I have the same stick but it absolutely wont show on dmesg...

---

